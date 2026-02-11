## 1. Visão Geral

### Objetivo

Implementar um backend Java (Spring Boot) que expõe um endpoint para carregar dados de **Model Monitoring**, realizando **filtros, agregações e alinhamento** antes de responder ao front Angular.

### Fontes de dados

- **MongoDB**: metadados do modelo (modelId, target) e registro de modelos
- **PostgreSQL**: métricas pré-computadas e séries:
    - simple_metrics
    - drift_metrics
    - real_pred

### Princípios

- Backend retorna dados **normalizados, ordenados e agregados**
- Reduz payload e CPU no cliente
- Resposta em **camelCase**, timestamps em **ISO 8601 / UTC**
- FE não faz recomputação estatística

---

## 2. Endpoint e Contrato

### Endpoint

- POST /api/mlops/monitoring/load
- Content-Type: application/json

### Request

{ "modelName": "my_model_v1", "limits": { "realPred": 5000 } }

Campos:

- modelName (obrigatório)
- limits.realPred (opcional, default 5000)

---

## 3. Contrato de Resposta — Compatível com o FE

> Ajuste recomendado: alinhar com o contrato do Angular (usar points e incluir methods).

```
{
  "modelName": "my_model_v1",
  "modelTarget": "sales",
  "kpis": {
    "rmseNow": 1.2345,
    "rmseDelta": -0.1234,
    "mseNow": 1.5678,
    "mseDelta": 0.0123,
    "maeNow": 0.789,
    "maeDelta": -0.045,
    "r2Now": 0.92,
    "r2Delta": 0.01,
    "driftAlertsCount": 2,
    "lastDriftAlertTs": "2025-01-12T14:30:00Z",
    "predictionStatusText": "Good",
    "predictionConfidence": 12
  },
  "realPred": {
    "points": [
      {
        "timestamp": "2025-01-12T14:00:00Z",
        "variable": "sales(target)",
        "value": 100.2,
        "prediction": 98.7,
        "predictionConfidence": 10,
        "predictionStatus": "Good"
      }
    ]
  },
  "simpleMetrics": {
    "points": [
      { "timestamp": "2025-01-12T00:00:00Z", "metric": "RMSE", "value": 1.2345 }
    ]
  },
  "driftMetrics": {
    "methods": ["kolmogorov_smirnov"],
    "points": [
      {
        "timestamp": "2025-01-12T14:30:00Z",
        "method": "kolmogorov_smirnov",
        "feature": "age",
        "alert": true,
        "y": 101.2
      }
    ]
  }
}
```

**Notas de alinhamento**

- FE espera predictionStatusText (opcional). Backend no esboço usa predictionStatus. Padronizar para um nome só.
- FE espera driftMetrics.methods[] para preencher o dropdown.

---

## 4. Stack e Dependências

- Spring Boot 3.x
- Spring Web
- Spring Data JPA
- Spring Data MongoDB
- PostgreSQL Driver, MongoDB Driver
- Jackson, java.time (Instant, OffsetDateTime)
- Flyway/Liquibase (opcional)

---

## 5. Modelo de Dados (referência)

### MongoDB (models)

- name (string, unique)
- id (string ou long)
- target (string)

### PostgreSQL

- simple_metrics(id, model_id, metric, value, timestamp, ...)
- drift_metrics(id, model_id, feature, method, value, alert, timestamp, ...)
- real_pred(model_id, timestamp, variable, value, prediction, prediction_confidence, prediction_status)

---

## 6. DTOs (Java) — versão final compatível FE

### Request

`public record MonitoringLoadRequest(     String modelName,     Limits limits ) {   public record Limits(Integer realPred) {} }`

### Response

`public record MonitoringKpisDto(     Double rmseNow, Double rmseDelta,     Double mseNow, Double mseDelta,     Double maeNow, Double maeDelta,     Double r2Now, Double r2Delta,     Integer driftAlertsCount,     Instant lastDriftAlertTs,     String predictionStatusText,     Integer predictionConfidence ) {}  public record RealPredPoint(     Instant timestamp,     String variable,     Double value,     Double prediction,     Integer predictionConfidence,     String predictionStatus ) {}  public record RealPredSeriesDto(List<RealPredPoint> points) {}  public record SimpleMetricPoint(     Instant timestamp,     String metric,     Double value ) {}  public record SimpleMetricsSeriesDto(List<SimpleMetricPoint> points) {}  public record DriftPoint(     Instant timestamp,     String method,     String feature,     Boolean alert,     Double y ) {}  public record DriftMetricsSeriesDto(     List<DriftPoint> points,     List<String> methods ) {}  public record MonitoringLoadResponse(     String modelName,     String modelTarget,     MonitoringKpisDto kpis,     RealPredSeriesDto realPred,     SimpleMetricsSeriesDto simpleMetrics,     DriftMetricsSeriesDto driftMetrics ) {}`

---

## 7. Arquitetura e Fluxo de Dados

---

## 8. Repositórios

### Mongo

`interface ModelRegistryRepository extends MongoRepository<ModelDoc, String> {   Optional<ModelDoc> findByName(String name); }`

### Postgres

Use JPA entity + projection/DTO, ou native query com mapper.

**Sugestão**: para performance e simplicidade, usar **native query com projection interface** (evita Object[]).

Exemplo:

`public interface RealPredRow {   Instant getTimestamp();   String getVariable();   Double getValue();   Double getPrediction();   Integer getPredictionConfidence();   String getPredictionStatus(); }`

---

## 9. Serviço (Fluxo de Negócio)

### Regras principais

1. Resolve modelId e target no Mongo
    
2. Busca séries do Postgres (ASC) com limites
    
3. Drift “merge-asof” para campo y (alinhado ao target)
    
4. KPIs:
    

- now = último valor
    
- delta = último − penúltimo
    
- drift alerts = count(alert==true)
    
- lastDriftAlertTs = max(ts alert==true)
    
- predictionStatus/confidence = do ponto realPred mais recente do target (ou qualquer variável, conforme regra)
    

---

## 10. Pseudo-código do MonitoringService.load()

`load(req):   assert req.modelName != null    limitRealPred = req.limits?.realPred ?? 5000    modelDoc = mongo.findByName(req.modelName)   if modelDoc empty -> 404 MODEL_NOT_FOUND    modelId = modelDoc.id   target = modelDoc.target    realPredRows = pg.realPred(modelId, limitRealPred)  // ORDER BY ts ASC LIMIT   simpleMetricRows = pg.simpleMetrics(modelId)        // ORDER BY ts ASC   driftRows = pg.driftMetrics(modelId)                // ORDER BY ts ASC    // 1) Map rows -> DTOs   realPredPoints = map(realPredRows)   simplePoints = map(simpleMetricRows)   driftPointsBase = map(driftRows)    // 2) Compute methods list   methods = distinct(driftPointsBase.method).sorted()    // 3) Merge-asof drift -> y (target value)   targetSeries = filter(realPredPoints, variable == target + "(target)" OR contains "(target)")   // (se targetSeries vazio, y sempre null)   driftPoints = mergeAsofNearestLeft(driftPointsBase, targetSeries, tolerance=1 day)    // 4) KPIs   kpis = buildKpis(simplePoints, driftPointsBase, targetSeries)    // 5) Build response (points wrapper)   return MonitoringLoadResponse(     modelName=req.modelName,     modelTarget=target,     kpis=kpis,     realPred=RealPredSeriesDto(realPredPoints),     simpleMetrics=SimpleMetricsSeriesDto(simplePoints),     driftMetrics=DriftMetricsSeriesDto(driftPoints, methods)   )`

### Merge-asof com ponteiros (O(N+M))

`mergeAsofNearestLeft(driftPoints, targetSeries, tolerance):   i = 0   for each drift in driftPoints (ASC):     while i+1 < targetSeries.size AND targetSeries[i+1].ts <= drift.ts:       i++      if targetSeries empty:       drift.y = null       continue      candidate = targetSeries[i]     if candidate.ts <= drift.ts AND (drift.ts - candidate.ts) <= tolerance:       drift.y = candidate.value     else:       drift.y = null   return driftPoints`

---

## 11. Controller

`@RestController @RequestMapping("/api/mlops/monitoring") public class MonitoringController {    private final MonitoringService service;    public MonitoringController(MonitoringService service) {     this.service = service;   }    @PostMapping("/load")   public MonitoringLoadResponse load(@RequestBody MonitoringLoadRequest req) {     return service.load(req);   } }`

---

## 12. Tratamento de Erros — MongoDB (integração com MLopsBffExceptionHandler)

O BFF já possui tratamento global via MLopsBffExceptionHandler (@ControllerAdvice + ApiExceptionHandler), retornando payload padronizado (ErrorDto/Error) para o front.

Para o módulo **Model Monitoring**, recomenda-se complementar o handler global com mapeamentos específicos de falhas do **MongoDB** (model registry).

### Objetivo

- Retornar **503** com payload padronizado quando o Mongo estiver indisponível (timeout, socket, conexão)
    
- Evitar que erros Mongo caiam em **500 genérico** sem contexto
    

### Exemplo de Handler (Mongo)

`import com.mongodb.MongoException; import com.mongodb.MongoTimeoutException; import com.mongodb.MongoSocketException; import org.springframework.data.mongodb.UncategorizedMongoDbException; import org.springframework.web.context.request.WebRequest;  import jakarta.servlet.http.HttpServletRequest; import org.springframework.http.ResponseEntity; import org.springframework.web.bind.annotation.ExceptionHandler;  // ...  @ExceptionHandler({     MongoTimeoutException.class,     MongoSocketException.class,     UncategorizedMongoDbException.class }) protected ResponseEntity<Object> handleMongoAvailabilityExceptions(     Exception e,     WebRequest request,     HttpServletRequest httpServletRequest ) {   log.error(e.getMessage(), e);    // Sugestão: usar um Error específico (ex.: MONGO_UNAVAILABLE) se existir   return handleException(e, request, Error.SERVICE_UNAVAILABLE, httpServletRequest); }  /**  * Fallback para outras MongoException não-classificadas como indisponibilidade.  * Evita transformar qualquer erro Mongo em 503, o que pode mascarar bugs.  */ @ExceptionHandler({ MongoException.class }) protected ResponseEntity<Object> handleMongoGenericExceptions(     MongoException e,     WebRequest request,     HttpServletRequest httpServletRequest ) {   log.error(e.getMessage(), e);   return handleException(e, request, Error.INTERNAL_SERVER_ERROR, httpServletRequest); }`

### Observações importantes

- MongoException é ampla: se for tratada sempre como 503, pode mascarar erros de lógica/query.
    
- Se for necessário manter DataAccessException no handler Mongo, recomenda-se filtrar por cause (ex.: instanceof MongoException) para não capturar exceções de outras origens.
    
- Idealmente, introduzir um Error dedicado (ex.: MONGO_UNAVAILABLE) mantendo status 503 para facilitar troubleshooting no front e nos logs.
    

---

## 13. Considerações de Desempenho

### 13.1 Compressão HTTP (recomendado)

Ativar compressão HTTP no Spring Boot é suficiente; o browser descomprime automaticamente (Angular não precisa “descompactar”). A compressão pode ser habilitada via properties.

### 13.2 Limites

- limits.realPred com default e hard cap (ex.: max 50k)
    
- Opcionalmente adicionar limites para drift/simple
    

### 13.3 Índices

- Postgres: índices por (model_id, timestamp) para todas as séries
    

---

## 14. Segurança e Observabilidade

- Spring Security/JWT (se aplicável)
    
- Logs estruturados:
    
    - modelName, modelId, tempos por query e total
        
- Métricas (Micrometer/Prometheus)
    

---

## 15. Consultas SQL (referência do Streamlit)

- Drift / Simple Metrics (por modelo)
    

`SELECT     id,     model_id,     feature,     "method",     value,     alert,     chunk_index,     chunk_start_date,     chunk_end_date,     accurate,     "timestamp",     created_at FROM :SCHEMA.drift_metrics WHERE CAST(model_id AS TEXT) = CAST(:MODEL_ID AS TEXT) ORDER BY "timestamp" ASC;  -- Simple performance metrics for model monitoring SELECT     id,     model_id,     metric,     value,     "timestamp",     data_size,     interval_minutes,     created_at FROM :SCHEMA.simple_metrics WHERE CAST(model_id AS TEXT) = CAST(:MODEL_ID AS TEXT) ORDER BY "timestamp" ASC;`

- Real vs Pred (com limite)
    

` ```WITH real_data AS (     SELECT          model_id,          "timestamp",          variable,          value     FROM :SCHEMA.laborious_data     WHERE CAST(model_id AS TEXT) = CAST(:MODEL_ID AS TEXT) ), predictions_data AS (     SELECT          "timestamp",          model_id,          prediction,          prediction_confidence     FROM :SCHEMA.predictions     WHERE CAST(model_id AS TEXT) = CAST(:MODEL_ID AS TEXT) ) SELECT      real_data.*,      pred.prediction,      pred.prediction_confidence FROM real_data INNER JOIN predictions_data pred  ON real_data."timestamp" = pred."timestamp" ORDER BY real_data."timestamp" DESC LIMIT :LIMIT_REAL_PRED; `

---

## 16. Checklist de Implementação

- Repositórios Mongo e Postgres
    
- Service load() (KPIs + merge-asof + methods)
    
- Controller /load
    
- Config: UTC + Jackson ISO + compressão + limites
    
- Tests:
    
    - unit: merge-asof (ponteiros), KPIs
        
    - integration: queries
        
    - contract: JSON básico
        

---

# 17. ANALISAR (dicas práticas)

## 17.1 Spring Boot: Mongo + JPA (múltiplas conexões)

Ver Spring Boot - multiple Database connections

---

## 17.2 Compactação no BFF e consumo no Angular

### Recomendação

Use **compressão HTTP** (gzip) no backend.

- O servidor envia Content-Encoding: gzip
    
- O browser/HttpClient recebe o JSON já descomprimido automaticamente.
    

Evite “compactar no corpo” (Base64 + gzip manual), salvo necessidade específica.

---

## 17.3 Paginador temporal/cursor para janelas enormes

Para volumes muito altos, prefira **keyset/cursor pagination** (mais eficiente que offset).

Cursor robusto: (timestamp, id) para estabilidade.

---

## 17.4 Definir limites: maxPoints e maxPayload

Regras recomendadas:

- Hard cap por série (ex.: realPred max 50k)
    
- Hard cap de payload (ex.: 5 MB)
    
- Retornar erro “PAYLOAD_TOO_LARGE” com sugestão de diminuir janela/limit
    

---

## 17.5 Grande volume: paginação por timestamp e consumo no Angular

Duas estratégias:

### Estratégia A (mantém 1 endpoint “load”)

- load aceita fromTs/toTs e limita pontos
    
- Usuário ajusta período e recarrega
    

### Estratégia B (cursor para gráficos com scroll/zoom)

- load retorna KPIs + primeira página + nextCursor
    
- endpoints para buscar próximas páginas por série (ver seção abaixo)
    

---

## 17.6 Endpoints opcionais de paginação por cursor (se necessário)

Se o volume exigir:

- POST /api/mlops/monitoring/load  
    Retorna KPIs + metadados + primeira página de cada série + cursors
    
- GET /api/mlops/monitoring/series/real-pred?modelName=...&cursorTs=...&cursorId=...&limit=...
    
- GET /api/mlops/monitoring/series/simple-metrics?modelName=...&cursorTs=...&cursorId=...&limit=...
    
- GET /api/mlops/monitoring/series/drift?modelName=...&cursorTs=...&cursorId=...&limit=...
    

Cada response inclui nextCursor quando houver mais dados.