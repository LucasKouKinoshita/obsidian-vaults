## Visão Geral

Este documento apresenta o planejamento arquitetural para migração da aba **Download Artifacts** do Model Manager de Python (Streamlit) para Angular (TypeScript).

- O único update necessário nesta página é a atualização da chamada de ``listArtifacts()`` feito diretamente à REST API do MLflow para que inclua paths para ``./prediction_model`` e ``./data_model``