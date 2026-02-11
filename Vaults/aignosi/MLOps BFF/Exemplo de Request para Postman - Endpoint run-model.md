
## Endpoint

```

POST http://localhost:8069/api/v1/soft-sensor/run-model

```

  

## Content-Type

```

multipart/form-data

```

  

## Body (form-data)

  

### ⚠️ IMPORTANTE: Configuração do Content-Type no Postman

  

Quando usar `form-data` no Postman, você **DEVE** definir o Content-Type explicitamente para o campo `experimentRun`:

  

1. Na tabela de form-data, você verá uma coluna **"Content-Type"** (pode estar oculta)

2. Para o campo `experimentRun`, clique na coluna Content-Type

3. Digite ou selecione: `application/json`

  

### 1. Campo: `file`

- **Key**: `file`

- **Tipo**: `File` (selecione no dropdown)

- **Value**: Seu arquivo CSV de treinamento

- **Content-Type**: Será definido automaticamente como `text/csv` pelo Postman

  

### 2. Campo: `experimentRun`

- **Key**: `experimentRun`

- **Tipo**: `Text` (selecione no dropdown)

- **Value**: JSON abaixo (cole como texto)

- **Content-Type**: `application/json` ⚠️ **DEFINA EXPLICITAMENTE ESTE VALOR**

  

### Como Definir o Content-Type no Postman:

  

1. **Método 1 - Coluna Content-Type**:

   - Na tabela de form-data, procure pela coluna "Content-Type" (pode estar oculta - clique com botão direito na tabela para mostrar colunas)

   - Clique na célula Content-Type do campo `experimentRun`

   - Digite: `application/json`

  

2. **Método 2 - Editar o campo**:

   - Clique no campo `experimentRun`

   - Procure por "Content-Type" ou "Content Type" nas opções

   - Defina como `application/json`

  

3. **Método 3 - Se não aparecer a coluna**:

   - Clique com botão direito na tabela de form-data

   - Selecione "Show Content-Type column"

   - Agora você verá a coluna e pode definir o valor

  

## JSON do experimentRun

  

```json

{

  "experimentName": "experiment-1",

  "username": "username1@test.com",

  "modelType": "Linear Regression",

  "targetVariable": "03CV022/CORRENTE_N_M1_PV(Value)",

  "variableColumns": [

    "303-WIT-230(Value)"

  ],

  "lagTrain": 0,

  "lagVal": 0,

  "remStaticWin": false,

  "lowLim": {

    "03CV022/CORRENTE_N_M1_PV(Value)": -1E10,

    "303-WIT-230(Value)": -253.0

  },

  "uppLim": {

    "03CV022/CORRENTE_N_M1_PV(Value)": 1E10,

    "303-WIT-230(Value)": 3432.0

  },

  "window": 0,

  "useScaler": false,

  "includeAr": false,

  "trainSize": 80,

  "shuffle": true,

  "lineSeparator": ";",

  "decimalSeparator": ".",

  "removedIntervals": [

    ["2024-08-18", "2024-09-18"]

  ]

}

```

  

## Campos Obrigatórios

  

- `experimentName`: String (3-50 caracteres)

- `username`: String (3-320 caracteres)

- `modelType`: String

- `targetVariable`: String

- `variableColumns`: Array de strings (não vazio)

- `lagTrain`: Integer

- `lagVal`: Integer

- `remStaticWin`: Boolean

- `window`: Integer

- `useScaler`: Boolean

- `includeAr`: Boolean

- `trainSize`: Integer (0-100)

- `shuffle`: Boolean

- `lineSeparator`: String (1 caractere: `,`, `;`, `\t`, ou `|`)

- `decimalSeparator`: String (1 caractere: `.` ou `,`)

  

## Campos Opcionais

  

- `lowLim`: Map<String, BigDecimal> - Limites inferiores das variáveis

- `uppLim`: Map<String, BigDecimal> - Limites superiores das variáveis

- `removedIntervals`: Array de arrays de strings - Intervalos removidos no formato `[["data-inicio", "data-fim"]]`

  

## Exemplo Simplificado (Mínimo)

  

```json

{

  "experimentName": "meu-experimento",

  "username": "usuario@example.com",

  "modelType": "Linear Regression",

  "targetVariable": "VARIAVEL_ALVO",

  "variableColumns": ["VARIAVEL_1", "VARIAVEL_2"],

  "lagTrain": 0,

  "lagVal": 0,

  "remStaticWin": false,

  "window": 0,

  "useScaler": false,

  "includeAr": false,

  "trainSize": 80,

  "shuffle": true,

  "lineSeparator": ";",

  "decimalSeparator": "."

}

```

  

## Valores Válidos

  

- **lineSeparator**: `,` ou `;` ou `\t` (tab) ou `|`

- **decimalSeparator**: `.` ou `,`

- **trainSize**: 0 a 100 (percentual de dados para treino)

- **lagTrain/lagVal**: Números inteiros (geralmente 0 ou positivos)

- **window**: Número inteiro (geralmente 0 ou positivo)

  

## Response Esperado

  

- **201 Created**: Se o upload e início do workflow foram bem-sucedidos

- **400 Bad Request**: Se houver erro de validação

- **422 Unprocessable Entity**: Se houver erro de processamento

- **500 Internal Server Error**: Se houver erro interno (ex: MinIO/Temporal não acessível)