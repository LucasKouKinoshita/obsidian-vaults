- Também conhecidos como testes de serviços
- Verificaram uma funcionalidade ou transação completa de um sistema
- Usam diversas classes, de pacotes distintos, podem testar componentes externos como BD's
- Demandam maior esforço para serem implementados do que [[Testes de Unidade]]
- Mais lentos que [[Testes de Unidade]]
- Sem mocks, as classes são testadas com dependencias reais (exceto aqueles relacionados com a interface gráfica, que será testada em [[Testes de Sistema]])

Assim, o objetivo deixa de ser o teste de uma unidade pequena de código, como uma classe apenas. Em vez disso, testes de integração exercitam um serviço completo, isto é, uma funcionalidade de maior granularidade do sistema.