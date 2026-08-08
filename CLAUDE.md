# Contexto do projeto

> Este arquivo é lido automaticamente pelo Claude Code a cada sessão neste repositório.
> Mantenha-o curto. O detalhe vive em `docs/`.

## O produto

SaaS de organização de trabalho para escritórios de serviços profissionais (advocacia, contabilidade, consultoria, arquitetura,empresas) com 2 a 10 pessoas. Público que hoje vive em planilha, WhatsApp e e-mail.

**Promessa central:** você abre uma tela e sabe o que fazer hoje.

**Concorrente real:** a planilha e a agenda solta. Não Jira, Notion ou Bitrix24 — esses são repertório de padrões, nunca alvo de paridade.

**Estágio:** Fase 1, 38 itens, 14 semanas, um desenvolvedor. Ver `docs/10-plano-desenvolvimento.md`.

## Idioma

- **Conversa comigo:** português do Brasil.
- **Código, tabelas, colunas, variáveis, endpoints, chaves de i18n:** Português.
- **Mensagens de commit:** português, texto livre (decisão `A5` do Bloco 4).
- **Interface do produto:** pt-BR, mas **sempre** através da camada de i18n. Nunca texto literal em componente.

## Pilha

| Camada | Escolha |
|---|---|
| Frontend | Next.js App Router · React · TypeScript estrito |
| Estado servidor | TanStack Query |
| Estado de UI | Zustand, apenas para o que precisa ser global |
| Estilo | Tailwind · shadcn/ui como base de componentes |
| Editor | TipTap · dnd-kit para arrastar e soltar |
| API | tRPC · Zod na borda, schema compartilhado com o formulário |
| Banco | PostgreSQL no Supabase |
| Testes | Vitest (lógica) · Playwright (fluxos críticos) |
| Hospedagem | Vercel |

## Regras que não se negociam

Detalhe completo em `docs/09-requisitos-imutaveis.md`. O resumo operacional:

1. **RLS em toda tabela.** Nenhuma consulta depende só de filtro em código. Toda tabela nova exige política escrita.
2. **O tenant vem do JWT**, nunca de URL, cabeçalho ou corpo da requisição.
3. **O frontend nunca fala com o banco direto.** Toda leitura e escrita passa pela camada tRPC.
4. **Lógica de negócio em TypeScript**, na camada de serviço. Nunca em trigger ou função de banco.
5. **Datas em UTC** no banco (`timestamptz`). Conversão só na borda de apresentação.
6. **Log nunca contém conteúdo** de item, nota ou comentário. Só identificadores.
7. **Toda migração é reversível.** Sem script de volta, não vai para produção.
8. **Contexto pessoal isolado por schema.** Tabelas de dados pessoais sem chave estrangeira para workspace. Nenhuma consulta capaz de retornar os dois lados.
9. **Exportação completa** em formato aberto, disponível a todos, sempre.

## Convenções

- **Banco:** `snake_case` plural em inglês — `work_items`, `time_entries`, `workspace_members`.
- **Identificadores:** UUID v7.
- **Exclusão:** `deleted_at`, filtrado pela RLS. Nunca `DELETE` físico em conteúdo.
- **Auditoria:** `created_at`, `created_by`, `updated_at`, `updated_by` em toda tabela de conteúdo.
- **Ordenação manual:** índice fracionário. Mover um item grava **uma** linha, nunca renumera a lista.
- **Campos customizados:** coluna JSONB `custom_fields` + tabela `field_definitions`. Não EAV, não colunas dinâmicas.
- **Os três tipos** (tarefa, nota, evento) vivem na **mesma tabela** `work_items`, com discriminador `type`. A visão Hoje depende disso.
- **Pastas:** por funcionalidade. Cada módulo com suas telas, serviços e tipos juntos.
- **Erros:** de domínio, nomeados, mapeados para HTTP numa camada só.
- **Branches:** trunk-based. Branch curta por tarefa, integrada na main no mesmo dia.
- **ADR:** toda decisão irreversível vira um arquivo curto em `docs/adr/`.

## Não faça

- Não crie tabela sem política de RLS.
- Não use `Date.now()` para gravar data de negócio — use o relógio do banco.
- Não escreva texto literal em componente. Use i18n mesmo para uma palavra.
- Não instale biblioteca nova sem me perguntar. O projeto tem orçamento zero e a pilha está fechada.
- Não implemente nada que não esteja na Fase 1 sem confirmar comigo. Ver `docs/08-escopo.md`.
- Não crie tela de configuração. O produto precisa funcionar sem configurar nada.
- Não adicione chat, CRM, ERP ou módulo fiscal.

## Onde olhar

| Preciso saber | Arquivo |
|---|---|
| O que é o produto e para quem | `docs/07-o-que-e-o-projeto.md` |
| O que entra e o que não entra | `docs/08-escopo.md` |
| As regras invioláveis | `docs/09-requisitos-imutaveis.md` |
| O cronograma e o que fazer esta semana | `docs/10-plano-desenvolvimento.md` |
| Por que uma decisão foi tomada | `docs/02-decisoes-consolidadas.md` e `docs/06-decisoes-tecnicas.md` |
| O inventário completo de funcionalidades | `docs/03-inventario-funcionalidades.md` |
