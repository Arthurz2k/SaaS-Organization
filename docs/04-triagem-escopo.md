# Bloco 2 — Resultado da triagem e verificação de viabilidade

> 188 itens triados em 07/08/2026 · 45 divergências da sugestão
> **Status: MVP não cabe no prazo. Decisão necessária antes do Bloco 3.**

---

## 1. Distribuição final

| Escopo | Itens | Sugestão original | Delta |
|---|---|---|---|
| MVP | **69** | 50 | +19 |
| v2 | 67 | 81 | −14 |
| v3+ | 47 | 36 | +11 |
| Fora | 5 | 21 | −16 |

Composição do MVP por complexidade: **25 baixa · 39 média · 5 alta**.

---

## 2. A conta

Premissas: 1 pessoa (`R11`), 40h/semana (`G3`), 5 dias úteis por semana. Baixa = 0,4 dia · Média = 1,5 dia · Alta = 5 dias. São médias de desenvolvimento greenfield com Supabase, já contando integração e acabamento — não são chutes otimistas nem pessimistas.

| Bloco de esforço | Dias úteis |
|---|---|
| 69 funcionalidades do MVP | 93,5 |
| Scaffolding, autenticação, tenancy e políticas RLS | 4,0 |
| Camada de dados: schema, migrações, tipos, API | 5,0 |
| Construção da UI a partir da referência de front | 8,0 |
| Deploy, ambientes e monitoramento básico | 2,0 |
| i18n, LGPD básica, política e termos | 3,0 |
| Testes, correção e retrabalho (20%) | 18,7 |
| **Total** | **134,2 dias** |

**134 dias úteis ≈ 27 semanas ≈ 6 meses e meio.**

O orçamento de `G1` é de 8 semanas, ou 40 dias úteis. **O excedente é de 94 dias — quase 19 semanas.** O escopo triado é 3,4 vezes maior que o prazo.

Vale notar: **40 dos 134 dias são overhead que não aparece em nenhuma linha do inventário.** Autenticação, multi-tenancy, deploy, i18n, LGPD e retrabalho existem independentemente de quantas funcionalidades você escolher. Eles consomem sozinhos o orçamento inteiro das 8 semanas.

---

## 3. Duas inconsistências que impedem a construção

Não são questão de prioridade — são impossibilidades técnicas na ordem escolhida.

### 3.1 Relação bidirecional sem a relação

- `F051` **Relação bidirecional sincronizada** → MVP
- `F050` **Relação entre dois conjuntos de registros** → v2

`F051` é uma propriedade de `F050`, não uma funcionalidade separada. Sincronização bidirecional é o comportamento de um vínculo que já existe. Sem `F050` no MVP, não há o que sincronizar.

**Correção necessária:** ou `F050` sobe para o MVP junto (custo: +5 dias, é complexidade alta), ou `F051` desce para a v2.

### 3.2 Gatilhos de automação sem motor de automação

- `F095`, `F096`, `F097`, `F098`, `F102` (gatilhos e uma ação) → MVP
- `F094` **Modelo gatilho, condição e ação** → v2

`F094` não é uma funcionalidade ao lado das outras: é o motor que executa todas elas. Um gatilho sem motor não dispara nada. Os cinco itens promovidos ao MVP dependem inteiramente do item que ficou na v2.

**Correção necessária:** ou `F094` sobe para o MVP (custo: +5 dias, complexidade alta, e ele traz junto fila de execução, log de execução e tratamento de falha), ou os cinco descem para a v2 em bloco.

---

## 4. Onde o peso se concentra

| Grupo | Itens no MVP | Dias |
|---|---|---|
| Visões e apresentação | 5 | 8,8 |
| Conteúdo, blocos e documentos | 4 | 8,4 |
| Agenda e planejamento temporal | 7 | 8,3 |
| Campos e tipos de propriedade | 12 | 7,0 |
| Automação | 5 | 6,4 |
| Colaboração e comentários | 5 | 5,3 |
| Relações (só `F051`) | 1 | 5,0 |
| Integração com calendário externo (`F173`) | 1 | 5,0 |
| Fronteira do contexto pessoal (`F186`) | 1 | 5,0 |

Os cinco itens de complexidade alta somam **25 dias** — 62% do orçamento inteiro de 8 semanas, em cinco linhas:

| ID | Item | Por que é caro |
|---|---|---|
| `F032` | Visão em linha do tempo / Gantt | Layout temporal, colisão de barras, arrastar para reagendar, escala com zoom |
| `F051` | Relação bidirecional sincronizada | Consistência nos dois lados, ciclos, exclusão em cascata |
| `F130` | Histórico de versões e restauração | Versionar conteúdo, diferença entre versões, restauração parcial |
| `F173` | Integração com calendário externo | OAuth, renovação de token, mapeamento de fusos, tratamento de conflito |
| `F186` | Bloqueio arquitetural do contexto pessoal | Não é tela: é separação física de dados e prova de que nenhuma consulta cruza |

---

## 5. Avaliação das suas 45 divergências

**Onde você acertou contra a minha sugestão:**

- `F002` tipos de item no MVP — coerente com `H3` (registro tipado). Sem tipos, "registro tipado" é só nome.
- `F017` intervalo de datas e `F020` múltiplos responsáveis — baratos e o público espera.
- `F107` busca com filtros — para quem vem de planilha, filtrar é mais natural que buscar por texto.
- `F129` página aninhada e `F123` blocos estruturais — notas sem hierarquia viram uma pilha.
- `F161` exportação completa no MVP — é `RI-04`, requisito imutável. Estava certo desde o começo.
- `F142` de Fora para v2 — aceito: se o produto crescer para escritórios de 30 pessoas, departamento passa a fazer sentido.

**Onde eu discordo e recomendo reverter:**

| ID | Você pôs | Recomendo | Por quê |
|---|---|---|---|
| `F032` | MVP | v2 | Gantt é 5 dias, 12% do orçamento, e serve a projetos longos com dependências — que `F007` você mesmo mandou para a v3+. Gantt sem dependência é um gráfico bonito e inerte. |
| `F130` | MVP | v2 | Histórico de versões protege contra um problema que só aparece com volume e vários editores. Você terá nem um nem outro nas primeiras semanas. `F170` (lixeira) já cobre o desastre real. |
| `F173` | MVP | v2 | Você já pôs `F084` (.ics) no MVP, que entrega leitura da agenda sem OAuth. Ter os dois no MVP é pagar duas vezes pelo mesmo valor. |
| `F140`, `F141` | v3+ | v2 | Dar ao cliente do escritório uma janela para o andamento do próprio caso é o argumento de venda mais forte que esse nicho tem. Mandar para v3+ adia o que faz o produto ser mostrado a terceiros. |
| `F095`–`F098`, `F102` | MVP | v2 em bloco | Dependem de `F094`, que está na v2. Ver seção 3.2. |
| `F051` | MVP | v2 | Depende de `F050`, que está na v2. Ver seção 3.1. |

---

## 6. O que precisa ser decidido

O escopo triado é bom. O problema não é a qualidade das escolhas — é que `G1` (8 semanas) e `G2` (cobrar em 3 meses) foram respondidos antes de existir uma lista concreta do que construir. Agora ela existe, e os dois números não sobrevivem ao contato com ela.

Três variáveis, e pelo menos uma tem que ceder: **escopo**, **prazo**, ou **definição do que conta como "primeiro usuário"**.

A decisão está registrada no próximo passo do processo, e o Bloco 3 será dimensionado em cima do que for escolhido.
