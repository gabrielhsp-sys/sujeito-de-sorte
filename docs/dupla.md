# Etapa em dupla — preparada para participação de um colega

**Situação: ainda não realizada.** Esta etapa depende de duas pessoas reais. O exercício individual e a tag v1.0 não comprovam colaboração em dupla.

## Preparação

1. Gabriel adiciona o colega em **Settings → Collaborators**, usando o usuário GitHub confirmado pelo colega.
2. O colega aceita o convite e usa sua própria conta e identidade de commit. Se o e-mail for privado, deve usar o endereço `noreply` fornecido pelo seu GitHub.
3. As duas pessoas trabalham em cópias locais diferentes do mesmo repositório. Ambas devem começar na mesma versão da develop, sem alterações pendentes.

Para o colega, que ainda não tem uma cópia:

```bash
git clone https://github.com/gabrielhsp-sys/sujeito-de-sorte.git
cd sujeito-de-sorte
git switch develop
git pull --ff-only
```

Gabriel também executa `git switch develop` e `git pull --ff-only` na própria cópia. Antes de editar, ambos conferem que `git rev-parse HEAD` mostra o mesmo identificador.

## Provocar a rejeição de push

1. Cada pessoa altera a **mesma linha 15** de `cancao.txt`, com conteúdos diferentes, e salva o arquivo. As duas devem fazer isso antes do primeiro push.
2. Gabriel executa:

```bash
git add cancao.txt
git commit -m "Altera linha 15: contribuição de Gabriel"
git push origin develop
```

3. O colega, ainda com sua alteração baseada na versão anterior, executa:

```bash
git add cancao.txt
git commit -m "Altera linha 15: contribuição do colega"
git push origin develop
```

Esse segundo push deve ser rejeitado por não ser fast-forward. **Não usar force push.**

## Resolver na cópia do colega

```bash
git fetch origin
git merge origin/develop
```

O conflito deve aparecer em `cancao.txt`. As duas pessoas combinam o conteúdo final. O colega edita o arquivo, remove os marcadores `<<<<<<<`, `=======` e `>>>>>>>`, salva e executa:

```bash
git add cancao.txt
git commit -m "Resolve conflito com o colega"
git push origin develop
```

Gabriel atualiza sua cópia com `git pull --ff-only`. Ambos conferem o arquivo e o histórico. A tag v1.0 deve continuar apontando para a entrega individual original; não deve ser movida.

## Resposta investigativa

O push foi rejeitado porque a develop remota já continha o commit de Gabriel, que não era ancestral do commit local do colega. Permitir substituir a referência sem essa verificação poderia remover do histórico da branch o trabalho recém-enviado. É necessário trazer as mudanças remotas e integrá-las antes de enviar um histórico que preserve os dois trabalhos.

Após executar a atividade de fato, atualizar esta página com os participantes e os identificadores dos commits correspondentes. Não marcar a etapa como concluída apenas por seguir a leitura deste guia.
