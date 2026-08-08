# O que é o projeto

> Documento 1 de 4 · Definição do produto · versão 1.0 · 07/08/2026
> Derivado de 413 decisões registradas nos Blocos 1, 1.5, 2, 3 e 4.

---

## 1. Em uma frase

> **O sistema que organiza o trabalho do seu escritório sem virar um projeto à parte.**

A frase foi escolhida em `B1` porque fala do medo real do público: eles já tentaram adotar uma ferramenta antes e desistiram na configuração. A promessa não é poder — é o produto não cobrar nada de você para começar a servir.

## 2. A promessa que precisa ser verdadeira todo dia

> **Você abre uma tela e sabe o que fazer hoje.**

Tudo no MVP existe para que essa frase seja verdadeira. Se um item do escopo não contribui para ela, ele está no lugar errado.

## 3. Para quem

**Sócio ou dono de escritório de serviços profissionais, com 2 a 10 pessoas.** Advocacia, contabilidade, consultoria, arquitetura.

Três características que definem tudo o mais:

1. **Hoje vive em planilha, WhatsApp e e-mail.** Nunca padronizou nada, e já desistiu de pelo menos uma ferramenta por complexidade.
2. **Quem compra é quem usa.** Não há PMO, não há TI, não há comitê. A decisão acontece em minutos ou não acontece.
3. **Cobra por hora ou por entrega.** Saber quanto tempo cada cliente consome não é um relatório bonito — é a conta do mês.

O primeiro cliente é o próprio Arthur. Os seguintes vêm por indicação direta.

## 4. Contra o que o produto compete

**Contra a planilha e a agenda solta.** Não contra Jira, Notion ou Bitrix24.

Essa é uma das decisões mais importantes do projeto, tomada em `R7`. As três suítes foram estudadas em detalhe — 188 capacidades levantadas da documentação oficial delas — mas como **repertório de padrões funcionais**, nunca como alvo de paridade. O público-alvo não usa nenhuma das três. Vencer a planilha é um problema completamente diferente, e muito mais alcançável, do que vencer o Jira.

## 5. Como o produto se descreve em dez segundos

> "É onde seu escritório vê os prazos, quem está fazendo o quê, e quantas horas foram para cada cliente. Um gerenciador de projetos simples."

## 6. O tom

**Direto e sóbrio.** Sem simpatia forçada, sem jargão de produtividade, sem gamificação. O público é composto de profissionais que cobram pelo próprio tempo — eles reconhecem quando um produto está tentando ser divertido em vez de útil.

## 7. Modelo mental do produto

**Tudo é um registro tipado, exibido por múltiplas visões.**

Não é "tudo é um bloco" (que seria copiar o Notion e virar um Notion pior). Não é "tudo é um item de trabalho" (que seria copiar o Jira e herdar sua rigidez). É um registro com tipo, campos tipados e ciclo de vida, que a interface apresenta como tabela, quadro ou lista conforme a pergunta que o usuário está fazendo.

Na Fase 1 existem três tipos: **tarefa, nota e evento**. Eles vivem na mesma tabela, com um discriminador — decisão `A4` do Bloco 3, tomada precisamente para que a visão Hoje consiga uni-los numa consulta só.

## 8. A fronteira pessoal e profissional

O produto nasceu da ideia de unir vida pessoal e profissional num só sistema. Ao longo da descoberta, essa ideia foi **redimensionada, não abandonada**:

- O contexto **profissional é o escopo principal**.
- O contexto **pessoal é um módulo opcional**, que entra na Fase 2 e que o usuário liga ou desliga.
- Os dois **nunca se cruzam no servidor**. A junção, quando existir, acontece no cliente.
- O administrador de um workspace **nunca** alcança o espaço pessoal de ninguém. Não é permissão, é arquitetura.

Mesmo com o módulo pessoal fora da Fase 1, o schema nasce preparado para ele desde a semana 2. Fazer isso agora custa um dia; descobrir depois que o modelo de dados não permite custa a reescrita inteira.

## 9. O que o produto não será

| Nunca | Por quê |
|---|---|
| **ERP ou módulo fiscal** | Domínio regulado, altíssimo custo de conformidade, e existe quem faça bem |
| **Ferramenta de engenharia** (repositório, CI/CD, deploy) | Público errado, problema errado |

Duas exclusões que existiam em rascunhos anteriores foram **removidas conscientemente** em `B6` e `D6`: chat interno e CRM completo de vendas deixaram de ser "nunca" e passaram a ser "não agora". O CRM leve, aliás, está planejado para a Fase 3.

## 10. Estágio e ambição

**Estágio:** ideação concluída, construção não iniciada.

**Ambição declarada:** projeto de aprendizado com uso real, sem meta de receita. O valor está no produto existir e ser usado — primeiro por você, depois por escritórios conhecidos. Cobrança simbólica entra na Fase 3, junto com o faturamento por assento, e existe para testar a mecânica, não para gerar receita.

Em `G7` isso foi confirmado de olhos abertos: cinco usuários pagando R$ 19 depois de seis meses de trabalho em tempo integral **é considerado sucesso** neste projeto, porque a régua é aprendizado e uso próprio, não retorno financeiro.

## 11. O número que importa

| Fase | Métrica |
|---|---|
| **Fase 1** (só você) | Dias em que você **não voltou à ferramenta antiga** |
| **Fase 2 em diante** | Dias ativos por semana por usuário |

A troca foi decidida em `G2` e é mais inteligente do que parece: durante a Fase 1 você vai abrir o produto todo dia de qualquer jeito, porque está construindo. "Dias ativos" mediria sua disciplina de desenvolvedor, não a qualidade do produto. "Dias em que não voltei à planilha" mede substituição, que é a única coisa que importa quando o concorrente é a planilha.

## 12. O ponto cego assumido

Você vai passar cerca de catorze semanas construindo e usando o produto sozinho, e o seu trabalho — laboratório de projetos — não é o trabalho de um escritório de advocacia ou contabilidade.

Em `G6` você respondeu que isso não invalida o dogfooding porque o produto não é só para advocacia. É uma resposta razoável, mas ela transfere peso para outro lugar: **as entrevistas de `K1`, na semana 3, deixam de ser opcionais.** Elas são o único contrapeso ao risco de otimizar o produto para o seu próprio jeito de trabalhar durante três meses seguidos.

---

**Próximos documentos:** `08-escopo.md` · `09-requisitos-imutaveis.md` · `10-plano-desenvolvimento.md`
