# Requisitos imutáveis

> Documento 3 de 4 · versão 1.0 · 07/08/2026
> Estas são as regras que nenhuma decisão futura pode violar sem passar por aqui primeiro.

---

## Como este documento funciona

Um requisito imutável não é um requisito importante. É um requisito cuja violação **custa mais do que o benefício de violá-lo**, sempre — seja porque quebra a confiança do usuário, seja porque a correção posterior exige reescrita.

Em `F1` você decidiu que **pode alterar qualquer um deles livremente, sem registro**. Isso está registrado e respeitado. Consequência prática, para ficar dita uma vez: sem registro, daqui a seis meses não haverá como distinguir uma regra que você reavaliou de uma regra que você esqueceu. A leitura deste documento em janeiro dirá que ele é a verdade, mesmo que já não seja.

Se em algum momento você quiser retomar o rastro, basta anotar data e motivo ao lado da regra alterada. Uma linha.

---

## Parte I — Privacidade e fronteira de contexto

### RI-01 — O administrador nunca alcança o contexto pessoal
O administrador de um workspace nunca acessa dados do contexto pessoal de nenhum membro, **sob nenhuma configuração**. Não é uma permissão desligada por padrão: é uma impossibilidade arquitetural.

*Verificação:* teste automatizado que autentica como administrador e tenta ler tabelas do espaço pessoal de outro usuário. Falha do teste bloqueia o deploy.

### RI-02 — Nenhuma consulta cruza os dois contextos
Nenhuma consulta no servidor pode retornar dados dos contextos pessoal e profissional na mesma resposta. Quando a visão unificada existir, a junção acontece no cliente, autenticado nos dois lados.

*Verificação:* revisão obrigatória de qualquer consulta que toque tabelas de ambos os domínios. Na prática, o schema de `F186` torna isso impossível de escrever por acidente.

---

## Parte II — Isolamento e segurança

### RI-03 — Row Level Security em toda tabela
Todo dado de um tenant é isolado por RLS no banco. Nenhuma consulta de aplicação depende apenas de filtro em código. Toda tabela nova exige política escrita, sem exceção.

*Verificação:* suíte de testes que tenta ativamente ler dados de outro tenant e falha se conseguir (`D4` do Bloco 3). É o único teste que existiria mesmo se não houvesse nenhum outro — vazamento entre tenants não é defeito, é fim de produto.

### RI-04 — Log nunca contém conteúdo
Nenhum log — de aplicação, de erro ou de auditoria — contém conteúdo de item, nota ou comentário. Apenas identificadores, tenant, usuário e tipo de operação.

*Verificação:* revisão do formato de log estruturado; campos de conteúdo nunca são passados ao logger.

### RI-05 — Toda migração de banco é reversível
Nenhuma migração vai para produção sem o caminho de volta escrito e testado. Isso é o que torna o plano de reversão de `F9` executável de fato.

*Verificação:* o pipeline recusa migração sem script de reversão.

---

## Parte III — Direitos do usuário

### RI-06 — Exportação completa, sempre, para todos
Exportação completa dos dados em formato aberto disponível a todo usuário, em todos os planos, a qualquer momento. Não é funcionalidade de plano pago, não é atendida sob solicitação, não é adiável.

*Verificação:* `F161` está na Fase 1 por causa desta regra, não por prioridade de produto.

### RI-07 — Internacionalização desde o primeiro commit
Nenhuma cadeia de texto vai codificada na interface. Tudo passa pela camada de i18n desde o início, mesmo com o produto lançando apenas em pt-BR.

*Verificação:* regra de lint que rejeita texto literal em componente. Retrofitar i18n depois custa dez vezes mais que fazer certo agora.

---

## Parte IV — Decisões técnicas irreversíveis

Estas não foram declaradas imutáveis por princípio. São imutáveis por **custo de reversão**: mudá-las depois significa migração de dados ou reescrita.

| ID | Decisão | O que custa mudar depois |
|---|---|---|
| **RI-08** | Identificador primário é UUID v7 | Reescreve toda chave estrangeira do banco |
| **RI-09** | Campos customizados em JSONB + tabela de definição | Migra todo dado customizado já gravado |
| **RI-10** | Tipos na mesma tabela, com discriminador | Quebra toda consulta da visão Hoje |
| **RI-11** | Datas em UTC no banco, conversão só na borda | Corrompe silenciosamente todo histórico de datas |
| **RI-12** | Tenant como claim assinado no JWT | Reescreve toda política de RLS |
| **RI-13** | Editor de notas é TipTap | Migra todo conteúdo já escrito pelos usuários |
| **RI-14** | Frontend nunca fala com o banco direto | Reescreve a camada de acesso inteira |

---

## Parte V — Diretriz forte, não imutável

### DF-01 — Uma pessoa nova usa o produto sem configurar nada
Rebaixada de imutável para diretriz em `D7`, e a decisão está correta: é o único item da lista que **não é verificável por teste automático**. Requisito imutável sem forma de verificar vira slogan.

Continua sendo o critério de projeto para toda tela nova, mas não bloqueia deploy.

---

## O que deixou de ser imutável

Registrado para que a mudança seja rastreável.

| Regra | Status anterior | Decisão | Onde |
|---|---|---|---|
| O produto nunca terá chat interno | Candidata a imutável | **Removida.** Passa de "nunca" a "não agora" | `D6`, `B6` |
| Nada entra numa fase sem que algo equivalente saia | Candidata a imutável | **Removida.** O escopo cresce e o prazo acompanha | `D10`, `A1` |
| Uma pessoa nova usa sem configurar nada | Candidata a imutável | **Rebaixada** a diretriz forte | `D7` |

A remoção do chat interno da lista de "nunca" tem uma consequência que vale notar: em `R1` você havia decidido que comunicação nunca entraria e que o produto integraria com o que o time já usa. As duas decisões agora convivem em tensão. Não é urgente — nenhuma das três fases planejadas inclui chat — mas quando o assunto voltar, `R1` e `B6` vão discordar.

---

## Governança

| Pergunta | Resposta |
|---|---|
| Quem pode alterar um requisito imutável? | Você, livremente, sem exigência de registro (`F1`) |
| Com que frequência revisar? | Ao fim de cada fase, e sempre que uma decisão individual mudar (`F2`) |
| Onde fica a fonte da verdade? | Arquivos `.md` para decisão e requisito; dentro do produto para backlog e dívida técnica (`F3`) |
| Quem lê isto primeiro ao entrar no projeto? | Este documento, depois o escopo da fase (`F5`) |
| O que acontece com estes arquivos no fim da Fase 1? | Viram a documentação inicial do repositório, na pasta `docs/` (`F4`) |
