# Escopo do projeto

> Documento 2 de 4 · versão 1.0 · 07/08/2026
> Base: 188 funcionalidades levantadas da documentação oficial de Jira, Notion e Bitrix24, triadas uma a uma.

---

## 1. Resumo

| Fase | Itens | Duração | O que prova |
|---|---|---|---|
| **Fase 1 — MVP** | **38** | **14 semanas** | Que você substitui sua ferramenta atual pelo produto |
| **Fase 2** | 67 | 7 a 9 semanas | Que o produto serve a um escritório, não só a você |
| **Fase 3** | 47 | a definir | Escala, receita e diferenciação |
| **Fora de escopo** | 5 | — | Nunca |

O número de 14 semanas não é uma estimativa pessimista: é o resultado direto da regra que você mesmo escolheu em `A1` — **escopo fixo, marco desloca**. Você adicionou quatro capacidades no Bloco 4 e a data se moveu na proporção. O mecanismo funcionou como projetado.

---

## 2. Fase 1 — os 38 itens

### 2.1 Núcleo de dados (6)

| ID | Item | Dias |
|---|---|---|
| `F001` | Item de trabalho como registro tipado | 1,5 |
| `F003` | Hierarquia de dois níveis: item e subitem | 0,4 |
| `F009` | Identificador curto e legível por item | 0,4 |
| `F025` | Campos automáticos de auditoria | 0,4 |
| `F165` | Múltiplos workspaces por conta | 1,5 |
| `F186` | Separação arquitetural do contexto pessoal no schema | 1,0 |

`F186` não é tela: é disciplina de modelagem. As tabelas de dados pessoais nascem sem chave estrangeira para workspace, e nenhuma consulta é capaz de retornar os dois lados. Um dia agora, impossível depois.

### 2.2 Campos (7)

`F011` texto · `F013` seleção única · `F015` status agrupado em fases · `F016` data · `F018` data com hora e fuso · `F019` pessoa responsável · `F021` caixa de seleção — **5,0 dias**

`F018` entrou no Bloco 4 (`C5`): você respondeu que compromisso sem hora não serve.

### 2.3 Visões, ordem e agrupamento (7)

`F029` tabela · `F030` kanban com arrastar · `F033` lista compacta · `F040` filtro simples · `F044` ordenação · `F045` arrastar para priorizar · `F046` agrupamento por propriedade — **6,1 dias**

`F046` entrou no Bloco 4 (`C6`): agrupar por responsável e por cliente.

### 2.4 Planejamento temporal (4)

`F076` visão Hoje · `F077` visão da semana · `F078` prazo com sinalização de atraso · `F080` eventos com hora, distintos de tarefas — **4,9 dias**

`F080` entrou junto com `F018`: hora em tarefa sem evento com hora seria meia solução.

**É o bloco mais importante da Fase 1.** Se ele falhar, a tese do produto falhou.

### 2.5 Notas e conversa (3)

`F121` editor de texto rico · `F113` comentário no item · `F131` anexo em item — **2,3 dias**

### 2.6 Tempo e cobrança (3)

`F086` lançamento manual de horas · `F089` marcação de faturável · `F072m` duplicar item com um clique — **2,3 dias**

`F072m` é a versão mínima de recorrência aprovada em `C3`: duplicar com um clique custa 0,4 dia e cobre a maior parte do uso real; regra de repetição de verdade custa 1,5 dia e depende do agendamento que `B9` tirou da fase.

### 2.7 Equipe e acesso (3)

`F136` papéis (dono e membro) · `F137` permissão por projeto · `F166` convite por link — **4,5 dias**

Mantidos em `C10` mesmo com você sendo o único usuário até a semana 14, porque sem eles o convite não acontece e a fase inteira não prova nada.

### 2.8 Notificação, estrutura e portabilidade (3)

`F146` notificação no aplicativo · `F170` lixeira com restauração · `F161` exportação completa em formato aberto — **4,5 dias**

`F146` entrou no Bloco 4 (`C2`). `F161` é requisito imutável, não escolha.

### 2.9 Onboarding (2)

`F068` template de projeto · `F074` biblioteca inicial de templates — **3,0 dias**

Quais templates será decidido **depois das entrevistas de `K1`** na semana 3 (`I2`). Como `F074` só é construído na semana 12, não há conflito de cronograma.

---

## 3. A conta das 14 semanas

| Bloco | Dias úteis |
|---|---|
| 38 funcionalidades | 37,8 |
| Fundação: scaffolding, autenticação, multi-tenancy, RLS | 4,0 |
| Camada de dados: schema, migrações, tipos, acesso | 5,0 |
| Construção da UI a partir da referência de front | 6,0 |
| Deploy, ambientes, monitoramento | 2,0 |
| i18n, LGPD, política e termos | 3,0 |
| Retrabalho e correção (15%) | 5,7 |
| **Subtotal de trabalho** | **63,5** |
| Folga de meio dia por semana (`A4`) | 7,0 |
| **Total** | **70,5 dias ≈ 14 semanas** |

**Vinte dos 63,5 dias são fundação e conformidade** — eles existiriam mesmo com 3 itens de escopo. É por isso que o prazo original de 8 semanas nunca foi viável, independentemente do corte.

A volta para a Vercel (`A3`) devolveu os 2 dias que o Google Cloud custaria. Os créditos de nuvem ficam reservados para quando o produto justificar a migração.

---

## 4. Fase 2 — 67 itens

Ordenada por dependência e retorno, não por preferência.

| Ordem | Bloco | O que entra |
|---|---|---|
| 1 | **Motor de automação** | `F094` a `F103` — ataca `C2` do Bloco 1, a dor declarada como principal |
| 2 | **Relações entre registros** | `F050` `F051` `F052` `F053` — base do modelo; quanto mais tarde, mais caro |
| 3 | **Importação de planilha** | `F159` — obrigatório **antes do primeiro convite externo**, conforme `B4` |
| 4 | **Agenda completa** | `F031` `F081` `F082` `F084` `F173` |
| 5 | **Campos e visões restantes** | `F002` `F012` `F014` `F017` `F020` `F032` inclui Gantt |
| 6 | **Colaboração e notificação** | `F115` a `F119`, `F147` a `F149` |
| 7 | **Busca e relatórios** | `F106` `F107` `F154` `F162` |
| 8 | **Contexto pessoal** | `F182` a `F185` — o schema já estará pronto desde a semana 2 |
| 9 | **Histórico de versões** | `F130` |
| 10 | **Faturamento por assento** | `F167` — habilita a cobrança simbólica de `R8` |

> ⚠️ **`F159` é pré-requisito de convite, não item de fase.** Em `B4` você aceitou tirar a importação de planilha da Fase 1 com o argumento de que, na Fase 1, só você usa. O argumento é válido — e cria uma obrigação: nenhum convite externo acontece antes de `F159` existir. Sem migração, ninguém larga a planilha.

---

## 5. Fase 3 — 47 itens

Depende de escala ou de receita que ainda não existe. Inclui CRM leve (`F176` a `F181`), permissões finas (`F138` a `F141`), SSO e provisionamento, relatórios avançados, API pública, dependências com impacto em datas, e o restante das capacidades de relação e fórmula.

---

## 6. Fora de escopo — 5 itens

| ID | Item | Motivo |
|---|---|---|
| `F005` | Hierarquia de profundidade livre | Vira labirinto num time de 2 a 10; dois níveis bastam |
| `F008` | Item pertencente a mais de um projeto | Confunde quem está saindo da planilha |
| `F062` | Condições que bloqueiam uma transição | Fricção pura num escritório de cinco pessoas |
| `F135` | Edição colaborativa de documento de escritório | Projeto de anos; integrar com o que o cliente já usa |
| `F160` | Importação a partir de outras ferramentas | O público não vem de outras ferramentas, vem de planilha |

---

## 7. Registro: o controle de escopo foi desligado

Isto não é uma crítica, é um registro necessário para quando o assunto voltar.

No Bloco 4 três respostas, juntas, removeram o mecanismo que continha o crescimento de escopo:

- **`C9` = "nenhuma troca, os 33 estão certos"** — mas `C2`, `C3`, `C5` e `C6` pediram quatro adições logo antes, sem indicar o que sairia.
- **`D10` removido** — a regra "nada entra sem que algo equivalente saia" deixou de ser requisito imutável.
- **`A1` = escopo fixo, marco desloca** — a data virou a variável de ajuste.

O resultado é coerente e legítimo: **o escopo cresce e o prazo acompanha.** Foi assim que 33 itens em 10,5 semanas viraram 38 itens em 14 semanas, e o mecanismo funcionou exatamente como você o desenhou.

O que precisa ficar consciente é que, sem `D10`, **nada impede que isso se repita.** Se na semana 6 surgirem mais quatro itens "que eu preciso", o plano vai para 17 semanas pelo mesmo caminho, sem que nenhuma regra seja violada. Em `K2` você identificou o crescimento de escopo como o maior risco de execução — e este documento registra que a defesa contra esse risco foi removida por escolha, não por descuido.

**Sugestão, não regra:** reintroduzir a troca apenas para a Fase 1, e apenas depois da semana 6. Até lá, adicionar é aprender; depois disso, adicionar é adiar.
