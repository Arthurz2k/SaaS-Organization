# Bloco 1 — Respostas registradas

> Respondido em 07/08/2026 · 72 de 72 perguntas · Arthur de Oliveira

---

## A — Visão e propósito

| # | Decisão |
|---|---|
| A1 | Suíte de negócio para PMEs: tarefas + CRM + financeiro + comunicação, com espaço pessoal como complemento |
| A2 | *(múltipla)* Clareza de execução diária + automação de processos + memória organizacional |
| A3 | *(múltipla)* Gestão de projetos e times **e** planejamento unificado do dia/semana |
| A4 | North Star: dias ativos por semana por usuário (formação de hábito) |
| A5 | Ferramenta interna/uso próprio que eventualmente vira produto |
| A6 | Fracasso a evitar: ficar complexo demais e ninguém adotar |

## B — Público-alvo

| # | Decisão |
|---|---|
| B1 | Time pequeno de 2 a 10 pessoas |
| B2 | Serviços profissionais (advocacia, contabilidade, consultoria, arquitetura) |
| B3 | Comprador: gestor de área, PMO ou head de operações |
| B4 | Maturidade: vive em planilhas, WhatsApp e e-mail |
| B5 | Brasil, pt-BR apenas |
| B6 | Fundador solo com perfil técnico |
| B7 | Dogfooding total: uso pessoal e profissional diário |

## C — Problema

| # | Decisão |
|---|---|
| C1 | *(múltipla)* Fragmentação entre 5+ ferramentas + falta de visão consolidada do tempo |
| C2 | Automatizar: atualização de status e cobrança de andamento |
| C3 | Evidência: experiência própria e observação informal |
| C4 | Custo: horas perdidas por semana em coordenação e busca |
| C5 | Momento: insatisfação com preço e complexidade das suítes atuais |

## D — Diferencial

| # | Decisão |
|---|---|
| D1 | Simplicidade progressiva: começa trivial, cresce com o usuário |
| D2 | Sem IA no MVP (complemento futuro, fora de escopo agora) |
| D3 | Postura: substituto — o usuário abandona as outras ferramentas |
| D4 | Preço: freemium agressivo |
| D5 | Vantagem difícil de copiar: nenhuma clara ainda |
| D6 | Anti-escopo: nunca será um CRM completo de vendas |

## E — Contextos pessoal × profissional

| # | Decisão |
|---|---|
| E1 | Workspaces totalmente isolados, sem qualquer ponte |
| E2 | Identidades distintas: perfil pessoal e perfil de trabalho separados |
| E3 | Nada atravessa por padrão — opt-in explícito, item a item |
| E4 | Existe visão "Hoje" unificada, com marcação visual do contexto |
| E5 | Pessoais permanecem do usuário; do workspace ficam com a organização |
| E6 | Visibilidade do pessoal pelo empregador: configurável pelo administrador |
| E7 | Finanças fora do escopo do MVP |
| E8 | Contexto pessoal cobre tarefas + notas + agenda |

## F — Modelo de negócio

| # | Decisão |
|---|---|
| F1 | Cobrança por assento/usuário por mês |
| F2 | Trial de 30 dias |
| F3 | Gratuito × pago separados por número de membros e workspaces |
| F4 | Faixa de R$ 25 a R$ 50 por assento/mês |
| F5 | Canal misto: self-service na base, consultivo em contas maiores |
| F6 | IA não se aplica na precificação (sem IA agora) |
| F7 | Sem meta de receita — projeto de aprendizado/portfólio |

## G — Restrições

| # | Decisão |
|---|---|
| G1 | Primeiro usuário real em 4 a 8 semanas |
| G2 | Cobrando em 3 meses |
| G3 | 40 horas/semana ou mais (dedicação integral) |
| G4 | Time: você + 1 desenvolvedor |
| G5 | Orçamento de ferramentas livre, investimento financeiro zero |
| G6 | Infraestrutura: até R$ 100/mês |
| G7 | Recurso: do próprio bolso |
| G8 | Restrição que mais aperta: dinheiro |

## H — Filosofia de produto

| # | Decisão |
|---|---|
| H1 | Zero configuração: entra e já tem estrutura útil via template |
| H2 | Visual clean e minimalista — **design feito pelo próprio Arthur** |
| H3 | Modelo mental: tudo é registro em base de dados tipada, com múltiplas visões |
| H4 | Plataformas: web **e** aplicativo desktop dedicado |
| H5 | Offline: leitura do que já foi carregado |
| H6 | Colaboração: presença + edição simultânea estilo documento |
| H7 | pt-BR no MVP, i18n desde o primeiro commit |

## I — Dados e conformidade

| # | Decisão |
|---|---|
| I1 | LGPD desde o dia 1 |
| I2 | Hospedagem em qualquer região — prioridade custo-benefício e latência |
| I3 | Criptografia padrão: TLS em trânsito, disco/banco em repouso |
| I4 | Histórico básico de alterações por item |
| I5 | Exportação completa em formato aberto, sempre disponível |
| I6 | Retenção configurável por workspace |

## J — Direção técnica

| # | Decisão |
|---|---|
| J1 | Node.js com TypeScript |
| J2 | React com Next.js |
| J3 | PostgreSQL com JSONB para campos customizados (híbrido) |
| J4 | Um banco por tenant (isolamento máximo) |
| J5 | Google Cloud ou Oracle Cloud, aproveitando créditos gratuitos |
| J6 | Supabase ou similar, para ganhar meses |
| J7 | API pública e webhooks depois da v1 |

## K — Validação e governança

| # | Decisão |
|---|---|
| K1 | Entrevistas com 10 a 15 pessoas do público-alvo |
| K2 | Primeiros usuários: rede pessoal e indicações |
| K3 | Sucesso do MVP: 10 usuários semanais por 1 mês seguido |
| K4 | Sem critério de parada — vai até o fim |
| K5 | Decisão de escopo: você sozinho, com base nos requisitos imutáveis |

---

## Leitura do conjunto

**O que ficou sólido e não precisa ser revisitado:**

- Público e nicho (`B1`, `B2`, `B4`) formam um recorte coerente e defensável: times pequenos de serviços profissionais que hoje operam em planilhas e WhatsApp. É um público real, mal atendido, e que você consegue alcançar por indicação (`K2`).
- Modelo mental `H3` (registro tipado com múltiplas visões) combina perfeitamente com `J3` (Postgres + JSONB). Essa dupla é a decisão técnica mais acertada do conjunto — sustenta campos customizados sem virar NoSQL bagunçado.
- `D2` (sem IA no MVP) com `A6` (medo de complexidade) e `G8` (dinheiro é a restrição) é disciplina rara e correta. IA agora seria custo recorrente sem retorno de aprendizado.
- `H7` + `B5`: lançar só em pt-BR mas com i18n no código desde o início é o custo mais barato que existe. Retrofitar i18n depois custa 10x.
- `B7` (dogfooding diário) é a sua maior alavanca. Vale mais que qualquer entrevista.

**O que está em conflito:** ver `02-conflitos-bloco1.md` — 16 tensões que precisam de decisão antes do Bloco 2.
