# Bloco 3 — Decisões técnicas e de execução

> 95 respondidas · 9 divergências da sugestão · 07/08/2026
> **Três pendências bloqueiam o Bloco 4:** ver seção 4.

---

## 1. Arquitetura e modelo de dados

| # | Decisão |
|---|---|
| A1 | Identificador primário: **UUID v7** |
| A2 | Nomenclatura: **snake_case plural em inglês** (`work_items`, `time_entries`) |
| A3 | Campos customizados: **JSONB `custom_fields` + tabela `field_definitions`** |
| A4 | Três tipos da Fase 1 em **tabela única `work_items` com discriminador `type`** |
| A5 | Exclusão: **`deleted_at` com RLS filtrando por padrão** |
| A6 | Auditoria: **colunas nas próprias tabelas**, sem tabela de log |
| A7 | Ordenação manual: **índice fracionário** |
| A8 | Migrações: **SQL do Supabase versionado no repositório** |
| A9 | Lógica de negócio: **camada de serviço em TypeScript**, nunca em trigger |
| A10 | Frontend **nunca** fala com o banco direto — sempre pela API própria |
| A11 | Datas: **timestamptz em UTC**, conversão só na borda |
| A12 | Seed de desenvolvimento separado dos templates de produção |

## 2. Backend, frontend e segurança

| # | Decisão |
|---|---|
| B1 | **tRPC** — tipagem ponta a ponta, sem contrato escrito à mão |
| B2 | **Zod** em toda borda, schema compartilhado com o formulário |
| B3 | Erros de domínio nomeados, mapeados para HTTP numa camada só |
| B4 | **Sem paginação na Fase 1** |
| B5 | Idempotência só onde há risco real |
| B6 | Operações nomeadas `workItems.list`, `workItems.create` |
| B7 | Sem versionamento de API até a API pública existir |
| B8 | Log estruturado em JSON com id de requisição, tenant e usuário |
| B9 | **Nada assíncrono na Fase 1** |
| C1 | App Router com Server Components onde fizer sentido |
| C2 | **TanStack Query** para estado de servidor |
| C3 | **Zustand** para o pouco que for global |
| C4 | Estilo: **o que a referência de front usar** |
| C5 | **shadcn/ui** — código no próprio repositório |
| C6 | **React Hook Form** com o mesmo schema Zod da API |
| C7 | **dnd-kit** para arrastar e soltar |
| C8 | **TipTap** como editor de notas |
| C9 | Pastas organizadas **por funcionalidade** |
| C10 | Da referência de front: extrair tokens e padrões, reescrever os componentes |
| D1 | Supabase Auth: e-mail e senha + link mágico |
| D2 | Tenant ativo como **claim assinado no JWT** |
| D3 | **RLS obrigatória em toda tabela**, política por operação |
| D4 | **Suíte de testes que tenta vazar dados entre tenants** |
| D5 | **Dois papéis na Fase 1: dono e membro** |
| D6 | Segredos no gerenciador do provedor, `.env.example` versionado |
| D7 | **Beta fechado por convite** — ninguém se cadastra sozinho |
| D8 | Backup do provedor + exportação completa semanal guardada por você |
| D9 | LGPD pronta **antes do primeiro convite externo** |
| D10 | Log nunca contém conteúdo de item ou nota |

## 3. Qualidade, operação e ritmo

| # | Decisão |
|---|---|
| E1 | Poucos testes de integração cobrindo fluxos críticos |
| E2 | Primeiro alvo de teste: **isolamento entre tenants** |
| E3 | **Vitest** para lógica, **Playwright** para fluxos |
| E4 | Sem meta de percentual de cobertura |
| E5 | TypeScript estrito + ESLint + Prettier bloqueando o commit |
| E6 | **Revisão assistida por IA antes do merge** |
| E7 | Pronto = funciona, tem teste, está em produção e você usou |
| E8 | Dívida técnica registrada **dentro do próprio produto**, desde a semana 3 |
| E9 | Defeito que bloqueia, corrige na hora; o resto entra na fila |
| F1 | **Dois ambientes:** local e produção |
| F2 | Frontend no **Google Cloud** — ver seção 4.3 |
| F3 | Banco: **Supabase gerenciado, plano gratuito** |
| F4 | Deploy automático a cada merge na main |
| F5 | Migração automática no pipeline, falha bloqueia o deploy |
| F6 | **Sentry** no plano gratuito |
| F7 | Verificação externa de disponibilidade com alerta por e-mail |
| F8 | Domínio próprio desde o início, Resend quando o e-mail entrar |
| F9 | Reversão do deploy + **toda migração precisa ser reversível** |
| F10 | Teto de R$ 100/mês, alerta em R$ 70 |
| G1 | **Trunk-based:** branch curta por tarefa, integrada no mesmo dia |
| G2 | Commits em **português, texto livre** — ver seção 4.2 |
| G3 | Versionamento semântico a partir de 0.1.0 |
| G4 | Repositório **privado** no GitHub |
| G5 | Backlog **dentro do próprio produto** a partir da semana 3 |
| G6 | Ciclos de uma semana, entrega verificável toda sexta |
| G7 | **ADR curto em markdown** para cada decisão irreversível |
| H7 | README, ADRs, comentário onde não é óbvio, **mais uma pasta `docs/`** |

## 4. Onboarding, métricas e riscos

| # | Decisão |
|---|---|
| I1 | Primeiro acesso: workspace já criado com template aplicado |
| I2 | **Templates definidos depois das entrevistas de K1** |
| I3 | Templates trazem itens de exemplo apagáveis de uma vez |
| I4 | Momento de valor: ver a visão Hoje com trabalho real |
| I5 | Aprende usando; dica contextual só onde travar |
| I6 | Convite por link com papel definido e prazo de validade |
| J1 | Telemetria: eventos próprios em tabela do Postgres |
| J2 | Número semanal: **dias ativos por semana** |
| J3 | Feedback por **formulário dentro do produto** |
| J4 | Funcionalidade morta = ninguém usa por duas semanas sabendo que existe |
| J5 | Funcionalidade morta é **removida**, não escondida |
| J6 | Toda mudança de decisão atualiza o documento de decisões consolidadas |
| J7 | Escopo das fases seguintes revisto ao fim de cada fase |
| K1 | Maior risco técnico: **RLS vazando dados entre tenants** |
| K2 | Maior risco de execução: **escopo crescer durante a construção** |
| K3 | Regra escrita: **nada entra na Fase 1 sem que algo equivalente saia** |
| K4 | Supabase apertado → migrar para os créditos de nuvem |
| K5 | Visão Hoje não se provando na semana 6 → **parar e repensar** |
| K6 | Pausa de um mês → tudo em produção com README de retomada |

---

## 5. Pendências

### 5.1 A seção H desligou o controle de cronograma

Quatro respostas que, isoladas, são defensáveis. Juntas, removem todo mecanismo que impede o plano de escorregar indefinidamente.

| # | Você escolheu | Efeito |
|---|---|---|
| `H1` | Medir progresso por **horas trabalhadas** | Horas medem esforço, não avanço. Uma semana de 40 horas presa num problema pontua igual a uma semana que entregou cinco itens. |
| `H2` | Quando atrasa, **empurrar tudo uma semana** | Remove a pressão sobre o escopo e a transfere para a data. |
| `H5` | **Sem folga nenhuma** | Toda estimativa vira o melhor caso possível. |
| `H6` | Se perder uma semana, **o marco desloca** | Mesmo mecanismo de `H2`, aplicado a imprevisto. |

O problema não é nenhuma delas. É que **`H2` e `H6` juntos definem que a data sempre cede, `H5` garante que ela vai ceder, e `H1` esconde que está cedendo.** Não sobra nenhum ponto em que alguém é obrigado a decidir o que sai.

Isso também contradiz o que você mesmo respondeu logo depois: `K2` diz que o maior risco de execução é o escopo crescer, e `K3` cria uma regra escrita para conter escopo. Mas escopo só cresce contra alguma coisa — e a única coisa contra a qual ele podia crescer era o tempo, que `H2` acabou de tornar elástico.

Existe uma combinação coerente e existe outra, também coerente:

- **Data fixa:** o marco não se move, o escopo da semana cede. Exige `H2 = A`.
- **Escopo fixo:** o escopo não se move, o marco cede — mas então `H1` precisa medir itens, não horas, senão você não enxerga o deslocamento acontecendo.

O que não funciona é escopo elástico **e** data elástica **e** medição por esforço. Levado para o Bloco 4.

### 5.2 Commits em português contradizem as regras do projeto

`G2` escolheu mensagens de commit em português, texto livre. As instruções do projeto dizem, textualmente: *"Código, nomes de tabelas/colunas/variáveis, endpoints, chaves de i18n e mensagens de commit em inglês."*

Não vou mudar uma regra que você escreveu com base numa resposta de formulário. Levado para o Bloco 4 como confirmação explícita: ou `G2` muda, ou a regra do projeto muda.

### 5.3 Google Cloud no lugar da Vercel custa dias

`F2` trocou Vercel por Google Cloud. Coerente com `J5`, que reservou os créditos — mas Next.js com App Router no Google Cloud significa Cloud Run com container: Dockerfile, pipeline de build, configuração de domínio e certificado, e ajuste de build para modo `standalone`.

**Custo estimado: 2 dias a mais na semana 1.** O plano vai de 52,7 para 54,7 dias, ou seja **de 10,5 para 11 semanas**. Com `H5` sem folga nenhuma, esses 2 dias não têm de onde sair.

### 5.4 `B10` ficou ambíguo

Você respondeu "Sim." em texto livre para "precisa de limite de requisições?". Vou assumir **configuração na borda do provedor, sem código próprio** — a opção mais barata, já que `D7` fechou o cadastro por convite. Se você quis outra coisa, corrija no Bloco 4.

---

## 6. O que essas decisões travam

Sete decisões desta lista são **irreversíveis na prática** — mudar depois significa migração de dados ou reescrita. Elas entram no documento de requisitos imutáveis:

- `A1` UUID v7 como identificador — trocar depois reescreve toda chave estrangeira
- `A3` JSONB + tabela de definição — trocar para EAV migra todo dado customizado
- `A4` Tabela única com discriminador — separar depois quebra toda consulta da visão Hoje
- `A11` UTC no banco — trocar depois corrompe silenciosamente todo dado histórico de data
- `D2` Tenant como claim no JWT — mudar a origem do tenant reescreve toda política de RLS
- `D3` RLS obrigatória em toda tabela — abandonar depois exige auditar cada consulta existente
- `C8` TipTap como editor — trocar de editor migra todo conteúdo já escrito
