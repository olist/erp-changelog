# ERP Changelog

Repositório de changelog público do ERP Olist, construído com [Mintlify](https://mintlify.com). Cada entrada documenta mudanças visíveis ao usuário final — novas funcionalidades, correções e remoções — organizadas por mês.

## Como contribuir

Há duas formas de adicionar entradas ao changelog.

### Usando as skills do ERP (recomendado)

No repositório do ERP, há três skills que automatizam o fluxo:

- **`/changelog`** — ponto de entrada único: gera o bloco a partir do diff da sua branch, conduz a revisão com você e abre o PR no repositório de changelog ao final.
- **`/generate-changelog`** — só a etapa de geração: analisa o diff contra `master` e produz um bloco `<Update>` em linguagem voltada ao usuário final, pronto para revisão.
- **`/publish-changelog-pr`** — só a etapa de publicação: insere o bloco aprovado na página mensal deste repositório e abre o PR no GitHub.

O fluxo típico é invocar `/changelog` na sua sessão do Claude Code enquanto está na branch do ERP. A skill lê o diff, escreve o changelog em linguagem simples, pede sua aprovação e publica o PR aqui.

### Manualmente

Você também pode abrir um PR diretamente neste repositório editando o arquivo mensal em `changelog/YYYY-MM/index.mdx`. Insira o bloco `<Update>` antes dos blocos existentes (o mais recente fica no topo):

```mdx
<Update label="DD/MM/YYYY HH:MM" description="Área alterada" tags={["Tag"]}>
## Título da mudança

Descrição voltada ao usuário final.
</Update>
```

Se o mês ainda não existir, crie o arquivo e registre a entrada em `docs.json` no grupo do ano correspondente.

## Desenvolvimento local

Instale o [Mintlify CLI](https://www.npmjs.com/package/mint):

```bash
npm i -g mint
```

Rode o servidor de preview na raiz do repositório (onde está o `docs.json`):

```bash
mint dev
```

Acesse `http://localhost:3000` para visualizar as mudanças localmente.

## Deploy

As alterações são publicadas automaticamente após o merge na branch `main`, via integração com o GitHub configurada no [dashboard do Mintlify](https://dashboard.mintlify.com).
