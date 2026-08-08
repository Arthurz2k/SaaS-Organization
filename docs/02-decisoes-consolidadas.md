# Decisões consolidadas — pós Bloco 1 + Bloco 1.5

> Estado: **travado para o Bloco 2** · 07/08/2026
> Substitui as respostas do Bloco 1 onde houver divergência. Só muda com decisão explícita registrada aqui.

---

## 1. O que é o produto

**Visão de 3 anos:** suíte de organização profissional para PMEs — trabalho, relacionamento com clientes e finanças no mesmo motor.

**O que é o MVP:** núcleo de trabalho — **projetos, tarefas, notas e agenda**. Nada além disso.

| Módulo | Quando |
|---|---|
| Projetos, tarefas, notas, agenda | **MVP** |
| CRM leve (contatos, funil simples) | v2 |
| Financeiro (contas a receber por projeto) | v3 |
| Comunicação/chat interno | **Nunca** — integra com o que o time já usa |
| IA | Futuro, fora de discussão agora |

**A coisa que precisa ser excepcional:** o planejamento unificado do dia e da semana. Projetos são a estrutura que alimenta essa visão, não o produto em si. *(R10)*

**Concorrente real:** planilha e agenda solta. Jira, Notion e Bitrix24 são repertório de padrões, não alvos de paridade. *(R7)*

---

## 2. Contextos pessoal × profissional

O contexto **profissional é o escopo principal**. O contexto pessoal é um **módulo que pode ser ligado ou desligado**. *(R2 obs)*

| Regra | Definição |
|---|---|
| Isolamento | Os dados dos dois contextos **nunca se cruzam no servidor**. Bancos/linhas separados, consultas separadas. |
| Junção | A visão "Hoje" é montada **no cliente**, pelo aplicativo autenticado nos dois lados. Nenhuma junção acontece no backend. *(R2)* |
| Travessia | Nada atravessa por padrão. Opt-in explícito, item a item, sempre iniciado pelo usuário. |
| Administrador | **Nunca** acessa o espaço pessoal. Não é configurável, não é uma permissão — é impedido por arquitetura. O admin governa apenas o workspace. *(R3)* |
| Saída da empresa | Dados pessoais permanecem do usuário; dados do workspace ficam com a organização. |
| Escopo do pessoal | Tarefas, notas e agenda. Sem finanças. |

> ⚠️ **Tensão em aberto:** se o pessoal é opcional e o profissional é o escopo principal, "planejamento unificado" (R10) passa a significar *unificado entre projetos e compromissos de trabalho*, não *entre pessoal e profissional*. Vou trabalhar com essa leitura. Se estiver errada, me corrija — muda a tela mais importante do produto.

---

## 3. Público e comercial

| Item | Decisão |
|---|---|
| Público | Times de 2 a 10 pessoas, serviços profissionais (advocacia, contabilidade, consultoria, arquitetura) |
| Maturidade | Vive em planilhas, WhatsApp e e-mail |
| Primeiro cliente | **Você mesmo.** Os próximos vêm por indicação direta *(R13)* |
| Comprador | O sócio/dono do escritório — a mesma pessoa que usa |
| Mercado | Brasil, pt-BR, com i18n no código desde o primeiro commit |
| Modelo | **Beta fechado.** Conta do administrador gratuita; **assentos adicionais são licença paga** *(R5 + obs)* |
| Preço | Simbólico: R$ 9 a R$ 19 por assento/mês, para testar a mecânica de cobrança, sem pretensão de receita *(R8)* |
| Meta de receita | Nenhuma. É projeto de aprendizado com uso real |
| North Star | Dias ativos por semana por usuário |
| Sucesso do MVP | 10 usuários usando semanalmente por 1 mês seguido |

---

## 4. Restrições de execução

| Item | Decisão |
|---|---|
| Time | **1 pessoa: você** *(R11)* |
| Disponibilidade | 40h/semana |
| Primeiro usuário real | 4 a 8 semanas |
| Investimento | R$ 0. Infraestrutura no gratuito, teto de R$ 100/mês |
| Restrição dominante | Dinheiro |
| Design visual | Feito por você, a partir de um projeto de referência que você vai trazer *(R15)* |
| Decisão de escopo | Você sozinho, com base nos requisitos imutáveis |

---

## 5. Arquitetura

| Item | Decisão |
|---|---|
| Backend | Node.js + TypeScript |
| Frontend | React + Next.js |
| Banco | PostgreSQL, com JSONB para campos customizados |
| Multi-tenancy | **Schema compartilhado + `tenant_id` + Row Level Security** *(R4)* |
| Modelo mental | Tudo é registro tipado, exibido por múltiplas visões |
| Infra | Supabase gerenciado no plano gratuito; créditos de nuvem reservados para migração futura *(R9)* |
| Região | A mais barata disponível; migrar se um cliente exigir Brasil *(R12)* |
| API pública | Depois da v1, quando o modelo de dados estabilizar |
| Plataformas | Web no MVP · tempo real e leitura offline na v2 · desktop na v3 *(R6)* |
| Colaboração no MVP | Salvamento automático, aviso de edição concorrente, comentários assíncronos |

---

## 6. Dados e conformidade

| Item | Decisão |
|---|---|
| LGPD | Conformidade desde o dia 1 |
| Criptografia | TLS em trânsito, criptografia de disco/banco em repouso |
| Auditoria | Histórico básico por item: quem mudou o quê e quando |
| Exportação | Completa, formato aberto, sempre disponível a todos |
| Retenção | Configurável por workspace |

---

## 7. Riscos aceitos conscientemente

Registrados porque foram escolhas suas, não descuidos. Se um deles doer no futuro, esta seção explica quando foi decidido.

1. **Sem critério de parada ou revisão** *(R14)*. O projeto continua independentemente de tração. Aceitável porque você é o primeiro usuário e o valor de uso próprio é real mesmo sem terceiros.
2. **Dados fora do Brasil no início** *(R12)*. Advogados e contadores costumam perguntar isso na primeira conversa. A migração de região depois exige janela de indisponibilidade e replanejamento de backup.
3. **Nenhuma vantagem difícil de copiar ainda** *(D5)*. Não é um problema no estágio atual, mas precisa virar uma decisão consciente antes de existir concorrência.
4. **Evidência do problema é experiência própria** *(C3)*. Mitigado por: você é o primeiro cliente e as 10-15 entrevistas de `K1` continuam no plano.
5. **Cobrar cedo, mesmo que simbólico** *(R8)*. Traz obrigações fiscais e de suporte antes da validação. Simbólico reduz, mas não elimina.

---

## 8. Requisitos que já nascem imutáveis

Estes saíram tão firmes da reconciliação que já entram como candidatos ao documento de requisitos imutáveis:

- **RI-01** — O administrador de um workspace nunca acessa dados do contexto pessoal de nenhum membro, sob nenhuma configuração.
- **RI-02** — Nenhuma consulta no servidor pode retornar dados dos dois contextos na mesma resposta.
- **RI-03** — Todo dado de um tenant é isolado por Row Level Security no banco; nenhuma consulta de aplicação depende apenas de filtro em código.
- **RI-04** — Exportação completa em formato aberto está disponível a todo usuário, em todos os planos, sempre.
- **RI-05** — Nenhuma cadeia de texto vai codificada na interface; tudo passa pela camada de i18n desde o primeiro commit.
- **RI-06** — O produto nunca terá chat interno próprio.
- **RI-07** — Uma pessoa nova precisa conseguir usar o produto sem configurar nada.
