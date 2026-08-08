# [nome a definir]

Sistema de organizacao de trabalho para escritorios de servicos profissionais de 2 a 10 pessoas.

> **Promessa central:** voce abre uma tela e sabe o que fazer hoje.

## Estado

**Fase 1 — MVP.** 38 itens, 14 semanas, um desenvolvedor.
Cronograma e itens da semana atual em [`docs/10-plano-desenvolvimento.md`](docs/10-plano-desenvolvimento.md).

## Comecar

```bash
pnpm install
cp .env.example .env.local   # preencha as chaves
pnpm dev
```

## Comandos

| Comando | O que faz |
|---|---|
| `pnpm dev` | Servidor de desenvolvimento |
| `pnpm build` | Build de producao |
| `pnpm lint` | ESLint |
| `pnpm test` | Vitest |
| `pnpm test:e2e` | Playwright |
| `supabase migration new <nome>` | Nova migracao |
| `supabase db push` | Aplica migracoes no projeto remoto |
| `supabase gen types typescript --linked > src/types/database.ts` | Regenera os tipos do banco |

## Pilha

Next.js App Router · TypeScript estrito · tRPC · Zod · TanStack Query · Zustand · Tailwind · shadcn/ui · TipTap · dnd-kit · PostgreSQL no Supabase · Vercel

## Regras que nao se negociam

Resumo em [`CLAUDE.md`](CLAUDE.md). Detalhe em [`docs/09-requisitos-imutaveis.md`](docs/09-requisitos-imutaveis.md).

As tres que mais aparecem no dia a dia:

1. **RLS em toda tabela.** Tabela nova sem politica escrita nao entra.
2. **O tenant vem do JWT**, nunca do cliente.
3. **Nenhum texto literal em componente.** Tudo pela camada de i18n, mesmo uma palavra.

## Documentacao

| Arquivo | Conteudo |
|---|---|
| `docs/07-o-que-e-o-projeto.md` | O que e o produto e para quem |
| `docs/08-escopo.md` | O que entra em cada fase e o que nunca entra |
| `docs/09-requisitos-imutaveis.md` | Regras invioláveis |
| `docs/10-plano-desenvolvimento.md` | Cronograma de 14 semanas |
| `docs/adr/` | Decisoes de arquitetura, uma por arquivo |

## Convencoes

- Commits em portugues, texto livre.
- Codigo, tabelas, colunas e endpoints em ingles.
- Trunk-based: branch curta por tarefa, integrada na main no mesmo dia.
- Pronto = funciona, tem teste do caminho feliz, esta em producao e foi usado de verdade.
