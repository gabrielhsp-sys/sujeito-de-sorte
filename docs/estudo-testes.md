# Apoio de estudo — Testes e DevOps

O enunciado pede leitura sobre testes, mas sugere o [capítulo 10, DevOps](https://engsoftmoderna.info/cap10.html). O tema testes está no [capítulo 8](https://engsoftmoderna.info/cap8.html), de Marco Tulio Valente. Este material é apoio de revisão, sem atestar leitura pessoal.

## Testes

- **Unidade:** verificam pequenas partes isoladas do programa; tendem a ser rápidos e numerosos.
- **Integração:** verificam a colaboração entre componentes, podendo envolver serviços externos.
- **Sistema:** exercitam fluxos completos, próximos ao uso real; custam mais para executar e manter.
- **Estrutura:** preparar o cenário, executar a operação e comparar o resultado com o esperado por meio de asserções.
- **Regressão:** repetir testes após mudanças ajuda a detectar comportamentos que deixaram de funcionar.
- **Cobertura:** indica quais partes do código foram exercitadas; uma cobertura alta não garante ausência de defeitos.
- **Mocks:** substituem dependências para controlar cenários e observar interações.
- **TDD:** escrever um teste que falha, implementar o necessário para passar e refatorar mantendo os testes aprovados.

## Relação com a prática de Git

DevOps aproxima desenvolvimento e operação. Controle de versões, integração frequente e automação de build e testes ajudam a tornar a entrega repetível. Resolver um conflito textual é só uma parte da integração: em projetos de software, o resultado também precisa continuar correto. Nesta atividade o arquivo é texto, por isso não há aplicação a compilar ou testes de software a implementar.
