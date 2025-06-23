Arquitetura orientada a dados, na qual os programas (filtros) tem como função processar os dados recebidos de entradas e gerar novas saídas.

Os filtros são conectados por meio de pipes que agem como buffers.
- Armazenam a saída de um filtro enquanto ela não é utilizada por outro filtro.

#### Vantagens
- Filtros não precisam conhecer antecessores ou sucessores, o que fornece flexibilidade ao combinar diferentes programas.
- Filtros podem ser executados em paralelo
