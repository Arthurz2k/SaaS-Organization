# Escopo cortado — Fase 1 e mapa de fases

> Decidido em 07/08/2026: cortar o escopo, manter o prazo curto.
> **Resultado honesto do corte: 10 semanas, não 8.** Justificativa na seção 2.

---

## 1. O corte

De **69 itens** para **33 itens**. O critério não foi "o que é mais legal" — foi **o menor conjunto que fecha um ciclo de uso completo**: entrar, criar um projeto, cadastrar trabalho, ver o que fazer hoje, executar, registrar tempo, comentar e tirar os dados de volta.

Qualquer item que não estivesse nesse caminho saiu, por mais barato que fosse.

### Os 33 da Fase 1

| Grupo | IDs | O que entrega |
|---|---|---|
| Núcleo de dados | `F001` `F003` `F009` `F025` | Item de trabalho tipado, subitens, código curto citável, auditoria automática |
| Campos | `F011` `F013` `F015` `F016` `F019` `F021` | Texto, seleção, status em fases, data, responsável, caixa de seleção |
| Visões | `F029` `F030` `F033` | Tabela, kanban, lista |
| Ordem e filtro | `F040` `F044` `F045` | Filtro simples, ordenação, arrastar para priorizar |
| Planejamento | `F076` `F077` `F078` | Visão Hoje, visão da semana, prazo com sinalização de atraso |
| Notas e conversa | `F121` `F113` `F131` | Editor de notas, comentário no item, anexo |
| Tempo | `F086` `F089` | Lançamento de horas, marcação de faturável |
| Equipe | `F136` `F137` `F166` | Papéis, permissão por projeto, convite de membros |
| Estrutura | `F165` `F170` | Múltiplos workspaces, lixeira com restauração |
| Portabilidade | `F161` | Exportação completa em formato aberto — `RI-04` |
| Onboarding | `F068` `F074` | Template de projeto e biblioteca inicial de três templates |
| Fronteira | `F186` | Restrição de schema, não tela — ver nota abaixo |

### O que saiu do seu MVP e para onde foi

| Saiu | Vai para | Motivo |
|---|---|---|
| `F032` Gantt | Fase 2 | 5 dias, e serve a projetos com dependências que você mandou para v3+ |
| `F050` `F051` Relações | Fase 2 | Dependência quebrada resolvida: os dois juntos, ou nenhum |
| `F094`–`F102` Automação | Fase 2 | Dependência quebrada resolvida: o motor vai junto com os gatilhos |
| `F130` Histórico de versões | Fase 2 | Resolve problema de volume e de vários editores; você não terá nenhum dos dois |
| `F173` Calendário externo | Fase 2 | OAuth e conflito de fuso; `F084` já entregaria leitura mais barato |
| `F002` Tipos configuráveis | Fase 2 | Fase 1 tem três tipos fixos: tarefa, nota e evento |
| `F031` Calendário, `F080` `F082` `F084` Agenda | Fase 2 | Hoje e Semana cobrem a necessidade real das primeiras semanas |
| `F012` `F014` `F017` `F018` `F020` Campos extras | Fase 2 | Baratos individualmente, mas somam e nenhum é bloqueante |
| `F046` Agrupamento, `F107` Busca filtrada, `F106` Busca | Fase 2 | Com poucos itens no sistema, buscar ainda não é um problema |
| `F115` `F116` `F117` Menções e resolução | Fase 2 | Time de 2 a 5 pessoas conversa por outro canal nas primeiras semanas |
| `F120` Aviso de edição concorrente | Fase 2 | Só importa quando duas pessoas editam o mesmo item, o que exige adoção |
| `F123` `F129` Blocos e páginas aninhadas | Fase 2 | O editor básico de `F121` já serve para nota |
| `F146` `F147` Notificações | Fase 2 | O produto ainda não gera evento suficiente para valer notificar |
| `F154` Relatório de tempo | Fase 2 | Depende de haver meses de lançamento acumulado |
| `F159` `F162` Importação e exportação de visão | Fase 2 | `F161` já garante a portabilidade que é requisito imutável |
| `F067` Mapeamento coluna–estado | Fase 2 | O kanban da Fase 1 usa o status direto, sem camada de fluxo |
| `F072` Item recorrente | Fase 2 | Doloroso para o nicho, mas não impede o primeiro mês de uso |

**Sobre `F186`:** na Fase 1 ele não é uma funcionalidade de 5 dias — é **1 dia de disciplina de schema**. O contexto pessoal só existe na Fase 2, mas o modelo de dados precisa nascer com a separação física prevista: tabelas de dados pessoais sem chave estrangeira para workspace, e nenhuma consulta capaz de retornar os dois lados. Fazer isso agora custa um dia. Descobrir na Fase 2 que o schema não permite custa a reescrita inteira.

---

## 2. Por que 10 semanas e não 8

| Bloco | Dias úteis |
|---|---|
| 33 funcionalidades da Fase 1 | 28,4 |
| Fundação: scaffolding, autenticação, multi-tenancy, RLS | 4,0 |
| Camada de dados: schema, migrações, tipos, acesso | 5,0 |
| Construção da UI a partir da sua referência de front | 6,0 |
| Deploy, ambientes, monitoramento básico | 2,0 |
| i18n, LGPD básica, política e termos | 3,0 |
| Testes, correção e retrabalho (15%) | 4,3 |
| **Total** | **52,7 dias ≈ 10,5 semanas** |

O que empurra para além das 8 semanas **não são as funcionalidades** — são os 20 dias de fundação e conformidade, que existem independentemente de você escolher 33 ou 3 itens. Autenticação, multi-tenancy com RLS, deploy, i18n e LGPD consomem metade do orçamento original antes de a primeira tela existir.

### Como chegar às 8 semanas, se você quiser forçar

Três alavancas, em ordem de dano crescente:

1. **Cortar equipe da Fase 1** — tirar `F136`, `F137` e `F166` (papéis, permissão por projeto, convite). O produto vira monousuário na Fase 1, você usa sozinho, e multiusuário entra na Fase 2. **Economia: 4,5 dias.** Coerente com `A5` e `R13`, onde você é o primeiro cliente.
2. **Cortar tempo da Fase 1** — tirar `F086` e `F089` (lançamento de horas e faturável). **Economia: 1,9 dia.** Custo alto: é o que amarra o produto ao nicho de `B2`.
3. **Adiar LGPD e termos para antes do primeiro usuário externo** — se na Fase 1 só você usa, não há titular de dados de terceiros. **Economia: 3 dias.** Risco: vira dívida que precisa ser paga antes de qualquer convite.

Aplicando 1 e 3: **44,3 dias ≈ 8,9 semanas.** Aplicando as três: **42,4 dias ≈ 8,5 semanas.** Mesmo cortando tudo isso, 8 semanas cravadas continua otimista para uma pessoa. Meu conselho é assumir 10 e entregar em 9.

---

## 3. Plano semana a semana

| Semana | Foco | Entrega verificável |
|---|---|---|
| **1** | Fundação | Repositório, Next.js + TypeScript, Supabase, autenticação funcionando, `tenant_id` com RLS ativo, deploy automático, i18n no primeiro commit, schema desenhado com a separação de `F186` |
| **2** | Núcleo de dados | `F001` `F003` `F009` `F025` `F165` — criar workspace, criar item, criar subitem, código curto, auditoria |
| **3** | Campos e projetos | `F011` `F013` `F015` `F016` `F019` `F021` — item com campos reais e status em fases |
| **4** | Visões | `F029` `F030` `F033` — tabela, kanban com arrastar, lista |
| **5** | Ordem e filtro | `F040` `F044` `F045` — o trabalho fica navegável e priorizável |
| **6** | Planejamento | `F076` `F077` `F078` — **a semana mais importante.** Hoje, Semana e atraso. É o que `R10` definiu como a coisa excepcional |
| **7** | Notas e conversa | `F121` `F113` `F131` — o produto para de ser só um gestor de tarefas |
| **8** | Tempo e equipe | `F086` `F089` `F136` `F137` `F166` — vira utilizável por um escritório, não só por você |
| **9** | Portabilidade e recuperação | `F161` `F170` — requisito imutável cumprido e desastre evitável |
| **10** | Onboarding e estabilização | `F068` `F074`, correção de defeitos, primeiro uso real seu de ponta a ponta |

**Marco de verdade:** ao fim da semana 6 você deve conseguir usar o produto no seu próprio trabalho, mesmo incompleto. Se na semana 6 você não estiver usando, o plano falhou e o problema não é o cronograma — é que algo essencial ficou de fora.

---

## 4. Fase 2 — o que você marcou como MVP e não coube

Estimativa: **7 a 9 semanas** depois da Fase 1.

Ordem sugerida, por dependência e por retorno:

1. **Motor de automação completo** (`F094` a `F103`) — ataca `C2`, a dor que você mesmo apontou: atualização de status e cobrança de andamento. Maior retorno de toda a Fase 2.
2. **Relações entre registros** (`F050` `F051` `F052` `F053`) — base do modelo. Quanto mais tarde, mais caro.
3. **Agenda completa** (`F031` `F080` `F082` `F084` `F173`) — eventos, calendários paralelos, `.ics` e sincronização externa.
4. **Campos e visões restantes** (`F002` `F012` `F014` `F017` `F018` `F020` `F032` `F046`) — inclui Gantt.
5. **Colaboração e notificações** (`F115`–`F120`, `F146`–`F149`) — passa a importar quando houver mais de duas pessoas.
6. **Busca, relatórios e importação** (`F106` `F107` `F154` `F159` `F162`).
7. **Contexto pessoal** (`F182`–`F185`) — o schema já estará pronto desde a semana 1.
8. **Histórico de versões** (`F130`).

---

## 5. Cláusula de reajuste

Você autorizou reajustar o prazo se ele estourar. Para que isso seja uma decisão e não uma deriva, fica registrado o gatilho:

> **Ao fim da semana 5, se menos de 15 dos 33 itens estiverem prontos, o prazo é reajustado formalmente para 14 semanas e a Fase 1 é recortada** — a primeira coisa a sair é o bloco "equipe" (`F136` `F137` `F166`), transformando a Fase 1 em produto monousuário.

Sem esse gatilho, o que acontece na prática é chegar na semana 8 com tudo pela metade e nada utilizável.
