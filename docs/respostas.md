# Respostas e observações da prática

## Etapa 3 — Identificador do commit

O código exibido por `git log` identifica um objeto commit. Neste repositório, ele é um hash SHA-1 de 40 caracteres. O commit referencia a árvore de arquivos, seus pais e metadados. `--oneline` usa um prefixo abreviado que deve ser suficiente para identificar o objeto sem ambiguidade no repositório.

## Etapa 4 — Restore e staging

Foram executados dois experimentos locais depois do primeiro commit:

1. Alterar a primeira palavra, observar `git diff` e executar `git restore cancao.txt`: a alteração sem staging foi descartada.
2. Fazer a mesma alteração, executar `git add cancao.txt` e só então `git restore cancao.txt`: a alteração continuou no arquivo, pois `restore`, sem opções, restaura o diretório de trabalho a partir do índice. O `git status` indicou a alteração preparada para commit.

Para voltar ao estado do último commit nesse segundo caso, foram usados `git restore --staged cancao.txt` e depois `git restore cancao.txt`. O primeiro retira a mudança do índice; o segundo descarta a mudança que ficou no diretório de trabalho. Os experimentos não criaram commits adicionais.

## Etapas 7 e 9 — Fast-forward

Seria impossível avançar diretamente a develop até a ponta da feature se a develop tivesse recebido um commit próprio após a criação da feature, com divergência dos históricos. Nesta prática, a develop ainda apontava para o ancestral da `feature/cabecalho`, então `git merge --ff-only feature/cabecalho` avançou o ponteiro sem criar commit novo.

No PR #1 foi usado merge commit: `ae8436c` tem dois pais e registra explicitamente a integração da versão vencer, mesmo sendo possível um fast-forward fora do GitHub.

## Etapa 10 — Origem e resolução do conflito

As versões vencer e crescer partiram do mesmo commit e substituíram a última palavra da mesma linha 4. Depois da integração da primeira versão, a tentativa de executar `git merge origin/develop` dentro da segunda feature produziu `CONFLICT (content)` e o estado `UU cancao.txt`.

A resolução foi feita na `feature/versao-crescer`: a linha passou a terminar em **vencer e crescer**, os marcadores foram removidos, o arquivo foi adicionado ao índice e foi criado o commit `1ad7396`, com dois pais. Depois do push, o PR #2 pôde ser integrado por merge commit.

A previsão sobre a próxima feature foi registrada antes de sua integração: não haveria conflito porque ela adicionava versos no final, em outra região do arquivo. O resultado confirmou a previsão.

## Etapas 11 e 12 — Squash e ancestralidade

O PR #3 está marcado como integrado no GitHub, mas `feature/versos-novos` não aparece em `git branch --merged develop`. O squash gerou um novo commit, `b613774`, com o efeito combinado dos dois commits originais. Esses commits originais continuam na feature e não passaram a integrar a ancestralidade da develop.

O GitHub registra a conclusão do pedido de integração; `git branch --merged` verifica se a ponta de uma branch é ancestral da referência consultada. São critérios diferentes, sem contradição. Essa resposta também está na descrição do PR **Release 1.0**.

## Reflexões finais

1. **Três áreas:** o diretório de trabalho contém os arquivos editáveis; o índice seleciona o conteúdo do próximo commit; o repositório armazena os objetos e o histórico dos commits. `git add` atualiza o índice e `git commit` grava a versão preparada.
2. **Tipos de integração:** fast-forward só avança uma referência; merge commit cria um commit com dois pais e preserva os commits da feature; squash cria um commit novo com o resultado acumulado, sem incluir os commits originais como ancestrais.
3. **Mesmo arquivo, regiões diferentes:** as duas versões disputavam a linha 4. A feature de versos acrescentava conteúdo ao final, por isso sua integração foi automática.
4. **Decisão sobre o conteúdo:** a escolha de combinar as duas versões foi feita na resolução; o Git apenas detectou a incompatibilidade. Em um time, a decisão deve considerar a intenção de quem fez cada mudança.
5. **Branches longas:** semanas de trabalho isolado acumulam divergências e tornam a integração difícil. Integrações pequenas e frequentes, acompanhadas de testes, reduzem esse acúmulo.
6. **Produção:** nesta política, a master representa a versão publicada. As alterações chegam a ela por um PR de release a partir da develop, e a tag identifica uma versão específica.
7. **Resolver na feature:** permite revisar e validar a resolução antes de atualizar a branch que integra o trabalho de todos. Assim, a develop recebe o resultado já reconciliado.
