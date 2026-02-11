## Visão Geral

Este documento apresenta o planejamento arquitetural para migração da aba **Experiment Validation** do Model Manager de Python (Streamlit) para Angular (TypeScript).

#### 1. Refatoração back-end
- Principal mudança se dá pela refatoração do endpoint em python ``experiment_validation_by_date()`` para acomodar o novo body request. 
	- A lógica do novo endpoint deve ser atualizada para acomodar as versões mais recentes das bibliotecas do sientia.

#### 2. Alterações no layout e lógica front-end
- Seletor de tratamento de valores NaN's deve ser removido
- Seletor de formato de data deve ser removido
- Gráfico utilizado deve ser o ``predictionChart()`` já implementado com o d3
	- O gráfico atual usando o plotlyJs e a atual implementação parecem inclusive _freezar_ a página.
- Seletores de separador devem dispor da mesma ideia de detecção automática utilizada na página ``Soft Sensor``.


