#### Testes Caixa-Preta e Caixa-Branca
**Caixa-preta** (funcionais): testes escritos com base apenas na interface do sistema sob testes.
**Caixa-branca** (estruturais): escrita dos testes considera informações sobre o código e a estrutura do sistema sob teste.
##### Seleção de Dados de Teste
Quando se adota testes caixa-preta, existem técnicas para auxiliar na seleção das entradas que serão verificadas no teste. Partição via Classe de Equivalência é uma técnica que recomenda dividir as entradas de um problema em conjuntos de valores que têm a mesma chance de apresentar um bug. 
##### Análise de Valor Limite
é uma técnica complementar que recomenda testar uma unidade com os valores limites de cada classe de equivalência e seus valores subsequentes (ou antecedentes). O motivo é que bugs com frequência são causados por um tratamento inadequado desses valores de fronteira

#### Testes de Aceitação
São testes realizados pelo cliente, com dados do cliente. Os resultados desses testes irão determinar se o cliente está de acordo ou não com a implementação realizada

#### Testes de Requisitos Não-Funcionais
Existem ferramentas que permitem a realização de testes de desempenho, para verificar o comportamento de um sistema com alguma carga