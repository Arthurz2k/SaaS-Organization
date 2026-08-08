# Plano de desenvolvimento

> Documento 4 de 4 · versão 1.0 · 07/08/2026
> Fase 1: 38 itens · 14 semanas · uma pessoa · 40h por semana · orçamento de infraestrutura R$ 0

---

## 1. Regras de operação do plano

| Regra | Definição | Origem |
|---|---|---|
| **Escopo fixo, marco desloca** | Os 38 itens são inegociáveis. Quando uma semana atrasa, a data se move — não o escopo | `A1` |
| **Medição dupla** | Itens concluídos medem avanço; horas medem esforço. Quando os dois divergem, é o sinal de alerta | `A2` |
| **Folga visível** | Meio dia por semana reservado no cronograma, não diluído na estimativa | `A4` |
| **Ciclo semanal** | Toda sexta: revisar o que saiu, replanejar a semana seguinte | `G6` |
| **Pronto** | Funciona + tem teste do caminho feliz + está em produção + você já usou | `E7` do Bloco 3 |
| **Deploy** | Automático a cada merge na main; migração aplicada no pipeline com verificação prévia | `F4`, `F5` |

---

## 2. Pilha técnica confirmada

| Camada | Escolha |
|---|---|
| Frontend | Next.js App Router · React · TypeScript estrito |
| Estado | TanStack Query (servidor) · Zustand (interface) |
| Estilo | Definido pela referência de front do Arthur · shadcn/ui como base de componentes |
| Editor | TipTap · **dnd-kit** para arrastar e soltar |
| API | tRPC · Zod na borda, schema compartilhado com o formulário |
| Lógica | Camada de serviço em TypeScript. Nunca em trigger de banco |
| Banco | PostgreSQL no Supabase gerenciado, plano gratuito |
| Multi-tenancy | Schema compartilhado · `tenant_id` · RLS obrigatória · tenant como claim no JWT |
| Identificadores | UUID v7 · ordenação manual por índice fracionário |
| Hospedagem | **Vercel** na Fase 1; créditos de Google Cloud reservados para depois |
| Erro e log | Sentry no gratuito · log estruturado em JSON com id de requisição |
| Testes | Vitest para lógica · Playwright para fluxos críticos |
| Repositório | Privado no GitHub · trunk-based · commits em **português** |
| Revisão | Assistida por IA antes do merge |

> **Nota sobre commits:** em `A5` você decidiu que a regra do projeto muda — tudo em português, inclusive mensagens de commit. As instruções do projeto (`Projeto SaaS Organizacional`) ainda dizem o contrário e precisam ser atualizadas por você, já que eu não tenho acesso de escrita a elas.

---

## 3. Cronograma semana a semana

### Semana 1 — Fundação
Repositório, Next.js com TypeScript estrito, Supabase, autenticação funcionando, `tenant_id` com RLS ativa, pipeline de deploy na Vercel, i18n configurada no primeiro commit, ESLint e Prettier bloqueando o commit.

**Entrega verificável:** uma página autenticada em produção, com um registro lido do banco através de política RLS.

### Semana 2 — Núcleo de dados
`F001` `F003` `F009` `F025` `F165` `F186`

Schema desenhado com a separação do contexto pessoal prevista. Criar workspace, criar item, criar subitem, código curto legível, auditoria automática.

**Entrega verificável:** criar e listar itens em dois workspaces distintos, sem vazamento entre eles.

### Semana 3 — Campos
`F011` `F013` `F015` `F016` `F018` `F019` `F021`

**Em paralelo: começam as entrevistas de `K1`.** Dez a quinze conversas com donos de escritório, mostrando o que já existe. Não é opcional — é o contrapeso ao ponto cego de `G6`.

**Entrega verificável:** um item com todos os campos preenchidos, incluindo hora e fuso.

### Semana 4 — Visões
`F029` `F030` `F033` `F040` `F044`

Tabela, kanban com arrastar e soltar, lista compacta, filtro e ordenação.

**Entrega verificável:** o mesmo conjunto de itens visto nas três formas.

### Semana 5 — Prioridade e agrupamento
`F045` `F046`

Arrastar para priorizar com índice fracionário, agrupamento por responsável e por cliente.

**Entrega verificável:** reordenar manualmente uma lista e a ordem persistir após recarregar.

### Semana 6 — Planejamento, parte 1
`F076` `F078`

A visão Hoje e a sinalização de atraso. **O bloco mais importante do plano.**

### Semana 7 — Planejamento, parte 2 · 🚩 MARCO
`F077` `F080`

Visão da semana e eventos com hora.

> **🚩 Marco de verdade — fim da semana 7.**
> A partir daqui você **usa o produto no seu próprio trabalho**, mesmo incompleto. Se na semana 7 você não conseguir usar, o problema não é o cronograma: é que algo essencial ficou fora do corte, e vale parar para descobrir o quê antes de seguir. Isso é o que `K5` chamou de "parar e repensar".

### Semana 8 — Notas e conversa
`F121` `F113` `F131`

Editor TipTap, comentário no item, anexo.

### Semana 9 — Tempo e cobrança
`F086` `F089` `F072m`

Lançamento de horas, marcação de faturável, duplicar item com um clique.

**Entrega verificável:** um mês simulado de horas lançadas, separadas entre faturáveis e não faturáveis.

### Semana 10 — Equipe
`F136` `F137`

Papéis (dono e membro) e permissão por projeto.

> **Decisão pendente até aqui:** o nome do produto (`B2`). Ele trava domínio, e-mail de convite e identidade visual — e a semana 11 já precisa dele.

### Semana 11 — Convite e notificação
`F166` `F146`

Convite por link com papel definido, notificação dentro do aplicativo.

### Semana 12 — Estrutura e portabilidade
`F170` `F161`

Lixeira com restauração e exportação completa em formato aberto (`RI-06`).

### Semana 13 — Onboarding
`F068` `F074`

Template de projeto e a biblioteca inicial — **definida com base no que as entrevistas da semana 3 revelaram**, não no que imaginamos hoje.

### Semana 14 — Estabilização
Suíte de testes de isolamento entre tenants rodando e passando. Documentos de LGPD prontos. Correção de defeitos. Verificação de disponibilidade configurada. Início da contagem dos 10 dias úteis de uso próprio.

---

## 4. Critérios de aceite

| Critério | Definição | Origem |
|---|---|---|
| **MVP aceito** | Todos os testes passam e não há defeito conhecido | `E1` |
| **Barra para convidar** | Nenhum defeito conhecido que faça perder dado ou vazar entre tenants | `E5` |
| **Uso próprio comprovado** | 10 dias úteis seguidos usando no trabalho real | `E2` |
| **Primeiro convite** | Ao fim da Fase 1, com os documentos de LGPD prontos | `E3` |
| **Primeiro grupo** | 3 a 5 pessoas, todas conhecidas suas | `E4` |
| **Itens faltando na semana 14** | Decisão caso a caso, conforme quais itens forem | `E6` |
| **Início da Fase 2** | Quando você decidir | `E8` |

### Duas tensões dentro desta tabela

**`E1` × `E5`.** O critério de aceite é mais rígido que a barra de convite: `E1` exige nenhum defeito conhecido de qualquer gravidade, `E5` exige apenas nenhum defeito que perca dado. Na prática, `E1` é a barra mais alta e será ela a valer. Se em algum momento isso travar o convite por um defeito cosmético, `E5` é a régua correta.

**`E2` × `E3`.** Você definiu 10 dias úteis de uso próprio como comprovação, mas escolheu convidar assim que a Fase 1 terminar. Os dois só cabem juntos se os 10 dias começarem **durante** a semana 14 e o convite sair no fim dela. É assim que o cronograma acima está montado. Se preferir convidar antes de completar os 10 dias, `E2` deixa de ter função.

### Sobre o critério de falha

Em `E7` você respondeu que **não existe critério de falha**, e em `E8` que a Fase 2 começa quando você decidir. Está registrado e respeitado.

Vale dizer uma vez, e não repito: `K5` do Bloco 3 diz "parar e repensar se a visão Hoje não se provar". Sem critério de falha, essa regra não tem gatilho — nada dispara a parada. O marco da semana 7 acima é a única coisa no plano que se aproxima disso, e ele é uma sugestão, não uma trava.

Se um dia você quiser um gatilho objetivo, o mais barato é este: **uma semana inteira sem abrir o produto, tendo ele disponível e funcionando.** Uma linha, verificável, e você mesmo é quem observa.

---

## 5. Riscos e resposta

| # | Risco | Resposta planejada |
|---|---|---|
| 1 | **RLS mal configurada vazando entre tenants** (`K1`) | Suíte de testes adversarial rodando desde a semana 2; falha bloqueia o deploy |
| 2 | **Escopo crescer durante a construção** (`K2`) | O prazo absorve, por decisão de `A1`. Sem trava — ver seção 7 do documento de escopo |
| 3 | **Supabase gratuito não aguentar** (`K4`) | Migrar para os créditos de Google Cloud, caminho já previsto |
| 4 | **Perder uma semana por imprevisto** (`H6`) | O marco desloca, o escopo não muda |
| 5 | **Pausa longa no projeto** (`K6`) | Tudo permanece em produção, com README de retomada atualizado |
| 6 | **Otimizar o produto só para o seu jeito de trabalhar** (`G6`) | Entrevistas de `K1` na semana 3, tratadas como obrigatórias |
| 7 | **Custo passar de R$ 100/mês** (`F10`) | Alerta configurado em R$ 70; ação antes do teto |

---

## 6. Depois da Fase 1

A Fase 2 tem 67 itens e 7 a 9 semanas, e a ordem está no documento de escopo. Três coisas dela merecem estar aqui:

1. **`F159`, importação de planilha, é pré-requisito de convite externo em escala.** O primeiro grupo de 3 a 5 conhecidos pode entrar sem ela; qualquer coisa além disso, não.
2. **O motor de automação é o item de maior retorno de toda a Fase 2.** Ele ataca `C2` do Bloco 1, a dor que você declarou como principal e que a Fase 1 conscientemente não resolve (`G5`).
3. **`F167`, faturamento por assento, é o que habilita a cobrança simbólica** decidida em `R8`. Antes dele não há como cobrar, nem se quisesse (`G3`).

---

## 7. Cadência de acompanhamento

**Toda sexta**, ao fim do ciclo (`F6`): revisar o que saiu, comparar itens concluídos com horas gastas, replanejar a semana seguinte e atualizar o painel.

O painel de acompanhamento (`painel-plano.html`) tem as 14 semanas com seus itens. Marque o que concluiu; ele calcula o avanço, projeta a data de término com base no ritmo real e avisa quando a projeção diverge do plano.
