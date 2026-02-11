#### Com vilela:
Tamanho médio e máximo de um arquivo  de modelo .pkl 


#### Comigo msm:
-> No model card, por que não usar o p-card no lugar de um panzoom?

-> Descrever melhor em create new experiment:
- `ModelUploadComponent` 
- `ExistingModelSelectorComponent` 
(eles nao foram listado nem na checklist de implementação)

-> O constraint de numero de linhas é só um conceito "soft" que usarei durante a implementação, não precisa estimar já agora o numero de linhas de cada componente.

-> Obviamente, alguns dos métodos não devem ser replicados no front-end, como por exemplo, o cálculo de métricas que é realizado ao utilizar a opção "Upload test file" no metricsManager, isto deverá ser feito no back-end (que será implementado em python). Gostaria que voce estimasse outros métodos e funções que deverão ser responsabilidade do back-end também.
