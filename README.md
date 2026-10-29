# Sprint 11 — Git na prática

**Estudante:** Gabriel Henrique · [gabrielhsp-sys](https://github.com/gabrielhsp-sys)

**Entrega:** https://github.com/gabrielhsp-sys/sujeito-de-sorte

Exercício de controle de versões com `cancao.txt`, usando o texto fornecido no roteiro como material de trabalho. A parte individual percorre as 12 etapas: repositório local e remoto, staging, branches, fast-forward, Pull Requests, conflito, squash e publicação de versão.

## Evidências para correção

| Etapa | Evidência |
|---|---|
| 1–4: configuração, primeiro commit e staging | Commit `4f523b8`; [experimentos e respostas](docs/respostas.md) |
| 5: repositório remoto | Este repositório é público |
| 6–7: branches e fast-forward | `feature/cabecalho` em `c4f0e66`; integração local sem criar merge commit |
| 8: trabalho paralelo | `feature/versao-vencer`, `feature/versao-crescer` e `feature/versos-novos` partiram de `c4f0e66` |
| 9: merge commit | [PR #1](https://github.com/gabrielhsp-sys/sujeito-de-sorte/pull/1), incluindo a resposta sobre fast-forward |
| 10: conflito resolvido dentro da feature | [PR #2](https://github.com/gabrielhsp-sys/sujeito-de-sorte/pull/2); commit `1ad7396` com dois pais |
| 11: squash de dois commits | [PR #3](https://github.com/gabrielhsp-sys/sujeito-de-sorte/pull/3); resultado `b613774` na develop |
| 12: versão publicada | [PR Release 1.0](https://github.com/gabrielhsp-sys/sujeito-de-sorte/pull/4) de develop para master; tag [v1.0](https://github.com/gabrielhsp-sys/sujeito-de-sorte/tree/v1.0) |

As quatro branches `feature/…` foram preservadas. A branch padrão é `develop`; `master` guarda a versão publicada. A exclusão automática de branches está desativada.

## Leitura e revisão

- [Respostas às perguntas investigativas e de reflexão](docs/respostas.md)
- [Apoio de estudo sobre testes e DevOps](docs/estudo-testes.md)

O enunciado menciona testes, mas o link sugerido abre o capítulo 10, **DevOps**. O material de apoio também referencia o capítulo 8, **Testes**. O resumo serve à revisão e não registra uma declaração de leitura pessoal do estudante.

## Atividade em dupla

**Pendente de participação de um colega.** Não foi simulada uma segunda pessoa nem atribuídos commits a um participante fictício. A parte individual está separada dessa pendência. O [guia da dupla](docs/dupla.md) deixa os passos preparados para executar o conflito entre duas pessoas reais.

## Conferir o histórico

```bash
git clone https://github.com/gabrielhsp-sys/sujeito-de-sorte.git
cd sujeito-de-sorte
git log --oneline --graph --all --decorate
git branch -a
git tag
```

O squash integra o conteúdo, mas não torna os dois commits originais da feature ancestrais da develop. Por isso, `feature/versos-novos` permanece fora de `git branch --merged develop`, apesar de o PR #3 estar integrado.

O texto-base de `cancao.txt` é de Belchior, conforme o material fornecido pelo professor. Os quatro versos acrescentados são exclusivos do exercício; não foi aplicada licença sobre a letra original.
