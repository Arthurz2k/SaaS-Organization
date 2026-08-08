# Bloco 2 - Inventario de funcionalidades e triagem de escopo
> 188 capacidades funcionais levantadas da documentacao oficial de Jira, Notion e Bitrix24, em 22 dominios.
> Levantado em 07/08/2026. Fonte: 26 paginas oficiais lidas (lista no fim do documento).

## Como ler
- **Origem**: J = Jira, N = Notion, B = Bitrix24, P = proprio do projeto (nao vem das referencias).
- **Complexidade**: esforco estimado para reimplementar do zero, nao o esforco de usar.
- **Escopo**: preenchido por voce no formulario `bloco2-escopo.html`.

### Regras de honestidade aplicadas
Nenhum nome de recurso de marca, limite numerico, nome de plano ou endpoint das tres plataformas foi reproduzido. As capacidades estao descritas como **padrao funcional generico** - o que a capacidade faz conceitualmente - que e o que interessa como repertorio de projeto e o que nao esta sujeito a protecao.

---

## 1. Itens de trabalho e hierarquia

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F001 | Item de trabalho como registro tipado | Unidade basica do sistema: registro com tipo, campos proprios e ciclo de vida | Jira, Notion, Bitrix24 | Media | _a definir_ |
| F002 | Tipos de item configuraveis | Definir tipos distintos (tarefa, entrega, prazo, chamado) com conjuntos de campos diferentes | Jira | Media | _a definir_ |
| F003 | Hierarquia de dois niveis: item e subitem | Decompor um item em subitens diretos | Jira, Notion, Bitrix24 | Baixa | _a definir_ |
| F004 | Hierarquia de tres niveis | Camada superior agrupando itens de varios projetos (padrao epico) | Jira | Media | _a definir_ |
| F005 | Hierarquia de profundidade livre | Subitens aninhados sem limite de nivel | Notion | Media | _a definir_ |
| F006 | Vinculos tipados entre itens | Relacoes como bloqueia, e bloqueado por, duplica, relaciona-se com | Jira | Media | _a definir_ |
| F007 | Dependencias com impacto em datas | Atraso no antecessor empurra automaticamente a data do dependente | Jira, Bitrix24 | Alta | _a definir_ |
| F008 | Item pertencente a mais de um projeto | O mesmo registro aparece em varios projetos sem duplicacao | Notion, Bitrix24 | Media | _a definir_ |
| F009 | Identificador curto e legivel por item | Codigo unico e citavel para referenciar o item em conversas | Jira | Baixa | _a definir_ |
| F010 | Conversao entre tipos de item | Transformar tarefa em subitem, subitem em item independente, etc. | Jira | Media | _a definir_ |

## 2. Campos e tipos de propriedade

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F011 | Texto curto e texto longo formatado | Campo textual com ou sem formatacao | Notion | Baixa | _a definir_ |
| F012 | Numero com formatacao | Valor numerico exibido como moeda, percentual ou barra de progresso | Notion | Baixa | _a definir_ |
| F013 | Selecao unica | Escolher uma opcao de uma lista controlada | Notion | Baixa | _a definir_ |
| F014 | Selecao multipla | Escolher varias opcoes de uma lista controlada | Notion | Baixa | _a definir_ |
| F015 | Status agrupado em fases | Estados agrupados em a fazer / em andamento / concluido | Notion | Media | _a definir_ |
| F016 | Data simples | Campo de data sem hora | Notion | Baixa | _a definir_ |
| F017 | Intervalo de datas | Data de inicio e data de fim no mesmo campo | Notion | Baixa | _a definir_ |
| F018 | Data com hora e fuso horario | Necessario para agenda e para equipes distribuidas | Notion, Bitrix24 | Media | _a definir_ |
| F019 | Pessoa responsavel | Vincular um membro do workspace ao registro | Jira, Notion, Bitrix24 | Baixa | _a definir_ |
| F020 | Multiplos responsaveis | Mais de uma pessoa atribuida ao mesmo item | Notion, Bitrix24 | Baixa | _a definir_ |
| F021 | Caixa de selecao | Campo booleano verdadeiro/falso | Notion | Baixa | _a definir_ |
| F022 | URL, e-mail e telefone acionaveis | Campos que abrem link, cliente de e-mail ou discagem | Notion | Baixa | _a definir_ |
| F023 | Arquivo ou imagem como campo | Anexar arquivo diretamente numa propriedade do registro | Notion | Media | _a definir_ |
| F024 | Campo de formula calculada | Valor derivado de outras propriedades por expressao | Notion | Alta | _a definir_ |
| F025 | Campos automaticos de auditoria | Criado em, criado por, editado em, editado por, preenchidos pelo sistema | Notion | Baixa | _a definir_ |
| F026 | Identificador numerico automatico | Contador unico gerado por registro | Notion | Baixa | _a definir_ |
| F027 | Localizacao ou endereco | Campo de lugar, por nome ou endereco | Notion | Media | _a definir_ |
| F028 | Esquema de campos por tipo de item | Cada tipo de item tem seu proprio conjunto de campos customizados | Jira, Bitrix24 | Alta | _a definir_ |

## 3. Visoes e apresentacao

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F029 | Visao em tabela | Registros em linhas e colunas, edicao em linha | Jira, Notion, Bitrix24 | Baixa | _a definir_ |
| F030 | Visao em quadro kanban | Colunas por propriedade, com arrastar e soltar | Jira, Notion, Bitrix24 | Media | _a definir_ |
| F031 | Visao em calendario | Registros posicionados por uma propriedade de data | Notion, Bitrix24 | Media | _a definir_ |
| F032 | Visao em linha do tempo / Gantt | Barras temporais com dependencias visiveis | Notion, Bitrix24 | Alta | _a definir_ |
| F033 | Visao em lista compacta | Layout minimalista de leitura rapida | Notion | Baixa | _a definir_ |
| F034 | Visao em galeria | Cartoes com imagem em destaque | Notion | Media | _a definir_ |
| F035 | Visao em grafico | Barras, linhas ou rosca sobre os proprios dados | Notion | Alta | _a definir_ |
| F036 | Visao em formulario de coleta | Formulario publico que grava registros no conjunto | Notion | Media | _a definir_ |
| F037 | Multiplas visoes salvas sobre os mesmos dados | Varias configuracoes de visualizacao para o mesmo conjunto | Notion | Media | _a definir_ |
| F038 | Visoes pessoais versus compartilhadas | Uma alteracao de visao pode valer so para mim ou para todos | Notion | Media | _a definir_ |
| F039 | Raias no quadro | Segunda dimensao de agrupamento dentro do kanban | Jira | Media | _a definir_ |

## 4. Filtros, ordenacao e agrupamento

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F040 | Filtro simples por valor de propriedade | Uma condicao sobre um campo | Jira, Notion, Bitrix24 | Baixa | _a definir_ |
| F041 | Filtro avancado com E/OU aninhado | Grupos logicos combinados em multiplas camadas | Notion | Alta | _a definir_ |
| F042 | Filtro salvo e reutilizavel | Guardar uma combinacao de criterios com nome | Jira | Media | _a definir_ |
| F043 | Filtro pessoal que nao afeta os outros | Aplicar um recorte so para mim numa visao compartilhada | Notion | Media | _a definir_ |
| F044 | Ordenacao por uma ou varias propriedades | Prioridade de ordenacao configuravel | Notion | Baixa | _a definir_ |
| F045 | Ordenacao manual arrastando | Ordem definida pelo usuario, persistida | Notion | Media | _a definir_ |
| F046 | Agrupamento por propriedade | Registros agrupados por valor de um campo | Notion | Media | _a definir_ |
| F047 | Subagrupamento | Segunda camada de agrupamento dentro da primeira | Notion | Alta | _a definir_ |
| F048 | Ocultar grupos vazios e ordenar grupos | Controle da apresentacao dos grupos | Notion | Baixa | _a definir_ |
| F049 | Agregacoes de coluna | Soma, media, contagem e percentual no rodape da coluna | Notion | Media | _a definir_ |

## 5. Relacoes entre registros e valores derivados

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F050 | Relacao entre dois conjuntos de registros | Ligar registros de bases diferentes | Notion | Alta | _a definir_ |
| F051 | Relacao bidirecional sincronizada | O vinculo aparece automaticamente nos dois lados | Notion | Alta | _a definir_ |
| F052 | Auto-relacao | Relacionar registros do mesmo conjunto entre si | Notion | Media | _a definir_ |
| F053 | Limite de cardinalidade | Restringir a relacao a um ou permitir varios | Notion | Media | _a definir_ |
| F054 | Valor derivado por agregacao sobre relacao | Trazer e resumir dados dos registros relacionados | Notion | Alta | _a definir_ |
| F055 | Agregacoes numericas derivadas | Soma, media, mediana, minimo, maximo, amplitude | Notion | Media | _a definir_ |
| F056 | Agregacoes de data derivadas | Data mais antiga, mais recente e intervalo entre elas | Notion | Media | _a definir_ |
| F057 | Contagem de preenchidos e vazios | Quantidade e percentual de valores presentes ou ausentes | Notion | Baixa | _a definir_ |
| F058 | Formulas referenciando outras propriedades | Expressoes calculadas dentro do registro | Notion | Alta | _a definir_ |
| F059 | Propagacao automatica ao alterar relacionado | Mudar um registro atualiza os valores derivados dos outros | Notion | Alta | _a definir_ |

## 6. Workflows, estados e transicoes

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F060 | Estados configuraveis por tipo de item | Cada tipo tem seu proprio conjunto de estados | Jira | Media | _a definir_ |
| F061 | Grafo de transicoes permitidas | Definir de qual estado se pode ir para qual | Jira | Alta | _a definir_ |
| F062 | Condicoes que bloqueiam uma transicao | Regras que impedem avancar sem criterios atendidos | Jira | Alta | _a definir_ |
| F063 | Campos obrigatorios em uma transicao | Exigir preenchimento ao mudar de estado | Jira | Media | _a definir_ |
| F064 | Resolucao ou desfecho ao encerrar | Registrar como o item terminou, nao apenas que terminou | Jira | Baixa | _a definir_ |
| F065 | Editor visual de fluxo | Desenhar o fluxo graficamente em vez de configurar em lista | Jira | Alta | _a definir_ |
| F066 | Esquema de fluxo reutilizavel | Um mesmo fluxo aplicado a varios projetos | Jira | Alta | _a definir_ |
| F067 | Mapeamento de colunas do quadro para estados | A coluna do kanban representa um estado do fluxo | Jira | Media | _a definir_ |

## 7. Templates e recorrencia

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F068 | Template de projeto completo | Estrutura inteira de projeto criada de uma vez | Jira, Notion, Bitrix24 | Media | _a definir_ |
| F069 | Template de item com campos pre-preenchidos | Novo registro ja nasce com valores padrao | Notion | Media | _a definir_ |
| F070 | Template com conteudo e checklist embutido | O corpo do item ja vem com o roteiro de execucao | Notion | Media | _a definir_ |
| F071 | Templates aninhados | Template que contem outros templates | Notion | Media | _a definir_ |
| F072 | Item recorrente | Repeticao diaria, semanal, mensal ou customizada | Notion, Bitrix24 | Media | _a definir_ |
| F073 | Template recorrente que gera registro sozinho | O sistema cria a instancia na data prevista | Notion | Media | _a definir_ |
| F074 | Biblioteca de templates por profissao | Modelos prontos para advocacia, contabilidade, consultoria | Jira, Bitrix24 | Media | _a definir_ |
| F075 | Duplicacao de projeto existente | Copiar um projeto que ja deu certo como ponto de partida | Bitrix24 | Baixa | _a definir_ |

## 8. Agenda e planejamento temporal

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F076 | Visao Hoje | Tudo que tem data para hoje, de todas as origens, em uma tela | Notion, Bitrix24 | Media | _a definir_ |
| F077 | Visao da semana | Planejamento semanal com distribuicao de carga | Notion, Bitrix24 | Media | _a definir_ |
| F078 | Prazo com sinalizacao de atraso | Destaque visual e ordenacao por urgencia | Jira, Notion, Bitrix24 | Baixa | _a definir_ |
| F079 | Data de inicio separada da data de termino | Permite planejar duracao, nao so vencimento | Notion | Baixa | _a definir_ |
| F080 | Eventos de agenda distintos de tarefas | Compromisso com hora marcada, diferente de item de trabalho | Bitrix24 | Media | _a definir_ |
| F081 | Eventos recorrentes | Repeticao com regra e excecoes | Bitrix24 | Media | _a definir_ |
| F082 | Calendarios paralelos | Calendario pessoal, de equipe e de projeto sobrepostos | Bitrix24 | Media | _a definir_ |
| F083 | Sincronizacao bidirecional com calendario externo | Espelhar Google, Microsoft ou Apple nos dois sentidos | Bitrix24 | Alta | _a definir_ |
| F084 | Assinatura ou exportacao em formato .ics | Consumir a agenda em qualquer cliente de calendario | Bitrix24 | Media | _a definir_ |
| F085 | Disponibilidade e busca de horario livre | Encontrar janela comum sem trocar mensagens | Bitrix24 | Alta | _a definir_ |

## 9. Controle de tempo e carga de trabalho

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F086 | Registro manual de horas por item | Lancar tempo gasto depois do fato | Bitrix24 | Baixa | _a definir_ |
| F087 | Cronometro iniciar, pausar e parar | Medir tempo em tempo real, com pausas | Bitrix24 | Media | _a definir_ |
| F088 | Estimativa versus tempo real | Comparar duracao planejada com a executada | Bitrix24 | Media | _a definir_ |
| F089 | Horas faturaveis e nao faturaveis | Separar o que vira fatura do que e custo interno | Bitrix24 | Media | _a definir_ |
| F090 | Folha de horas por periodo e por pessoa | Consolidado de tempo para fechamento | Bitrix24 | Media | _a definir_ |
| F091 | Visao de carga de trabalho por pessoa | Quanto cada um tem alocado no periodo | Bitrix24 | Alta | _a definir_ |
| F092 | Alerta de sobrecarga | Aviso quando alguem passa da capacidade | Bitrix24 | Media | _a definir_ |
| F093 | Jornada e horario de trabalho configuravel | Define o que conta como dia util e horario comercial | Bitrix24 | Media | _a definir_ |

## 10. Automacao

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F094 | Modelo gatilho, condicao e acao | Estrutura geral de regras automaticas | Jira, Notion, Bitrix24 | Alta | _a definir_ |
| F095 | Gatilho: registro criado | Disparar quando um item nasce | Notion | Media | _a definir_ |
| F096 | Gatilho: propriedade alterada | Disparar quando um campo especifico muda | Jira, Notion | Media | _a definir_ |
| F097 | Gatilho: data atingida ou agendamento | Disparar em uma data ou em intervalo recorrente | Jira, Notion | Media | _a definir_ |
| F098 | Gatilho manual por botao | O usuario dispara a automacao quando quiser | Jira, Notion | Baixa | _a definir_ |
| F099 | Acao: alterar propriedade do proprio registro | Atualizar campos automaticamente | Jira, Notion | Media | _a definir_ |
| F100 | Acao: criar registro em outro conjunto | Gerar itens derivados automaticamente | Jira, Notion | Media | _a definir_ |
| F101 | Acao: alterar registros relacionados | Propagar mudancas para itens vinculados | Jira, Notion | Alta | _a definir_ |
| F102 | Acao: notificar pessoa ou canal | Avisar alguem sem intervencao humana | Jira, Notion, Bitrix24 | Media | _a definir_ |
| F103 | Acao: enviar e-mail | Disparo de e-mail a partir da regra | Notion, Bitrix24 | Media | _a definir_ |
| F104 | Acao: chamar webhook externo | Integrar com qualquer sistema que aceite HTTP | Notion | Media | _a definir_ |
| F105 | Ramificacao sobre itens relacionados | A regra percorre subitens ou itens vinculados | Jira | Alta | _a definir_ |

## 11. Busca e consulta

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F106 | Busca textual global | Encontrar por palavra em todo o workspace | Jira, Notion, Bitrix24 | Media | _a definir_ |
| F107 | Busca com filtros estruturados | Restringir por tipo, projeto, responsavel e data | Jira | Media | _a definir_ |
| F108 | Linguagem de consulta estruturada | Consulta escrita com campo, operador e valor | Jira | Alta | _a definir_ |
| F109 | Funcoes de consulta | Expressoes como itens do usuario atual ou prazo nesta semana | Jira | Alta | _a definir_ |
| F110 | Consultas salvas e compartilhaveis | Guardar e distribuir uma consulta com nome | Jira | Media | _a definir_ |
| F111 | Busca dentro de anexos e documentos | Indexar conteudo de arquivos, nao so metadados | Bitrix24 | Alta | _a definir_ |
| F112 | Paleta de comandos por teclado | Navegar e agir sem tirar as maos do teclado | Notion | Media | _a definir_ |

## 12. Colaboracao e comentarios

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F113 | Comentario no nivel do item | Discussao vinculada ao registro | Jira, Notion, Bitrix24 | Baixa | _a definir_ |
| F114 | Comentario ancorado em trecho de texto | Comentar um pedaco especifico do conteudo | Notion | Alta | _a definir_ |
| F115 | Resolver e reabrir comentario | Marcar discussoes como encerradas | Notion | Baixa | _a definir_ |
| F116 | Mencao a pessoa com notificacao | Chamar alguem para a conversa | Jira, Notion, Bitrix24 | Media | _a definir_ |
| F117 | Mencao a item ou projeto criando link | Referenciar outro registro dentro do texto | Notion | Media | _a definir_ |
| F118 | Reacoes rapidas | Concordar ou sinalizar sem escrever comentario | Notion | Baixa | _a definir_ |
| F119 | Caixa de entrada unificada | Um lugar so com mencoes, atribuicoes e respostas | Notion | Media | _a definir_ |
| F120 | Aviso de edicao concorrente | Alertar que outra pessoa esta editando agora | Proprio | Media | _a definir_ |

## 13. Conteudo, blocos e documentos

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F121 | Editor de texto rico | Formatacao basica de texto | Notion | Media | _a definir_ |
| F122 | Modelo de blocos componiveis | Todo conteudo e um bloco movivel e transformavel | Notion | Alta | _a definir_ |
| F123 | Titulos, listas, citacoes, divisores e destaques | Conjunto basico de blocos estruturais | Notion | Baixa | _a definir_ |
| F124 | Lista de tarefas dentro do documento | Checklist no corpo do texto | Notion | Media | _a definir_ |
| F125 | Bloco de codigo com destaque de sintaxe | Util para documentacao tecnica | Notion | Baixa | _a definir_ |
| F126 | Tabela simples dentro do documento | Tabela estatica, sem virar base de dados | Notion | Media | _a definir_ |
| F127 | Incorporacao de conteudo externo | Embutir arquivo ou pagina de outro servico | Notion | Media | _a definir_ |
| F128 | Menu de comando por barra | Inserir qualquer bloco digitando / | Notion | Media | _a definir_ |
| F129 | Pagina aninhada dentro de pagina | Hierarquia de documentos | Notion | Media | _a definir_ |
| F130 | Historico de versoes e restauracao | Voltar a um estado anterior do conteudo | Notion | Alta | _a definir_ |

## 14. Arquivos e anexos

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F131 | Anexo em item | Arquivos vinculados a um registro | Jira, Notion, Bitrix24 | Baixa | _a definir_ |
| F132 | Repositorio de arquivos por projeto | Area de arquivos organizada por projeto | Bitrix24 | Media | _a definir_ |
| F133 | Pre-visualizacao de imagem e PDF | Ver sem baixar | Bitrix24 | Media | _a definir_ |
| F134 | Versionamento de arquivo | Guardar versoes anteriores do mesmo documento | Bitrix24 | Alta | _a definir_ |
| F135 | Edicao colaborativa de documento de escritorio | Editar planilha ou texto dentro do produto | Bitrix24 | Muito alta | _a definir_ |

## 15. Permissoes, papeis e estrutura

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F136 | Papeis pre-definidos | Administrador, membro, convidado e leitor | Jira, Notion, Bitrix24 | Media | _a definir_ |
| F137 | Permissao por projeto | Quem ve e quem edita cada projeto | Jira, Notion, Bitrix24 | Media | _a definir_ |
| F138 | Permissao por item individual | Controle no nivel do registro | Notion | Alta | _a definir_ |
| F139 | Heranca de permissao | Subitens e subpaginas herdam do pai | Notion | Alta | _a definir_ |
| F140 | Convidado externo com acesso restrito | Cliente entra so no que lhe diz respeito | Notion, Bitrix24 | Media | _a definir_ |
| F141 | Compartilhamento por link publico somente leitura | Mostrar algo sem exigir cadastro | Notion | Media | _a definir_ |
| F142 | Estrutura organizacional com departamentos | Hierarquia de subordinacao e supervisores | Bitrix24 | Alta | _a definir_ |
| F143 | Esquema de permissao reutilizavel | Conjunto de regras aplicado a varios projetos | Jira | Alta | _a definir_ |
| F144 | Login unico corporativo | Autenticacao pelo provedor de identidade da empresa | Bitrix24 | Alta | _a definir_ |
| F145 | Provisionamento automatico de usuarios | Criar e desativar contas a partir do diretorio corporativo | Bitrix24 | Muito alta | _a definir_ |

## 16. Notificacoes

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F146 | Notificacao dentro do aplicativo | Central de avisos no proprio produto | Jira, Notion, Bitrix24 | Media | _a definir_ |
| F147 | Notificacao por e-mail | Aviso fora do produto | Jira, Notion, Bitrix24 | Media | _a definir_ |
| F148 | Resumo diario ou semanal por e-mail | Digest em vez de aviso a cada evento | Bitrix24 | Media | _a definir_ |
| F149 | Preferencias por tipo de evento | O usuario escolhe o que quer receber | Jira | Media | _a definir_ |
| F150 | Esquema de notificacao por projeto | Politica de avisos definida no nivel do projeto | Jira | Alta | _a definir_ |
| F151 | Notificacao push no celular | Requer aplicativo instalado ou PWA | Bitrix24 | Alta | _a definir_ |

## 17. Relatorios e metricas

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F152 | Painel com indicadores configuraveis | Conjunto de metricas escolhido pelo usuario | Jira, Bitrix24 | Alta | _a definir_ |
| F153 | Relatorio de itens concluidos por periodo | Producao da equipe ao longo do tempo | Jira, Bitrix24 | Media | _a definir_ |
| F154 | Relatorio de tempo por projeto e por pessoa | Base para faturamento e para custo | Bitrix24 | Media | _a definir_ |
| F155 | Grafico de progresso de ciclo | Evolucao do trabalho restante dentro de um periodo | Jira | Alta | _a definir_ |
| F156 | Metricas de tempo de ciclo e de espera | Quanto tempo um item leva e onde ele para | Jira | Alta | _a definir_ |
| F157 | Relatorio agendado enviado por e-mail | Chega sozinho, sem alguem lembrar de gerar | Bitrix24 | Media | _a definir_ |
| F158 | Exportacao de relatorio em CSV ou PDF | Levar o dado para fora | Jira, Bitrix24 | Media | _a definir_ |

## 18. Importacao, exportacao e portabilidade

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F159 | Importacao de planilha com mapeamento de colunas | Trazer o que o cliente ja tem em Excel | Notion | Media | _a definir_ |
| F160 | Importacao a partir de outras ferramentas | Migrar de Trello, Notion, Asana e afins | Notion | Alta | _a definir_ |
| F161 | Exportacao completa do workspace em formato aberto | Requisito imutavel do projeto | Notion | Media | _a definir_ |
| F162 | Exportacao de uma visao especifica | Baixar so o recorte que interessa | Notion | Baixa | _a definir_ |
| F163 | Exportacao de documento em Markdown ou PDF | Levar o conteudo textual para fora | Notion | Media | _a definir_ |
| F164 | Copia de seguranca agendada | Backup automatico e recuperavel | Bitrix24 | Media | _a definir_ |

## 19. Administracao de workspace e conta

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F165 | Multiplos workspaces por conta | Uma pessoa participa de varias organizacoes | Jira, Notion, Bitrix24 | Media | _a definir_ |
| F166 | Convite e gestao de membros | Adicionar, remover e trocar papel | Jira, Notion, Bitrix24 | Media | _a definir_ |
| F167 | Faturamento e assinatura por assento | Cobranca proporcional ao numero de licencas | Jira, Notion, Bitrix24 | Alta | _a definir_ |
| F168 | Trilha de auditoria de acoes administrativas | Registro do que os administradores fizeram | Jira, Bitrix24 | Alta | _a definir_ |
| F169 | Politica de retencao configuravel | Quanto tempo cada tipo de dado permanece | Notion | Media | _a definir_ |
| F170 | Lixeira com restauracao | Desfazer exclusoes dentro de um prazo | Notion | Media | _a definir_ |

## 20. Integracoes e extensibilidade

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F171 | API publica REST | Terceiros leem e escrevem dados do produto | Jira, Notion, Bitrix24 | Alta | _a definir_ |
| F172 | Webhooks de saida | O produto avisa outros sistemas quando algo muda | Jira, Notion | Media | _a definir_ |
| F173 | Integracao com calendario externo | Google, Microsoft ou Apple | Bitrix24 | Alta | _a definir_ |
| F174 | Criar item a partir de e-mail | Encaminhar mensagem e virar tarefa | Bitrix24 | Alta | _a definir_ |
| F175 | Loja de aplicativos de terceiros | Ecossistema de extensoes instalaveis | Jira, Bitrix24 | Muito alta | _a definir_ |

## 21. CRM leve (candidato a v2)

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F176 | Cadastro de contatos e empresas | Base de clientes com dados de contato | Bitrix24 | Media | _a definir_ |
| F177 | Vinculo de contato a projeto | Saber de quem e cada projeto | Bitrix24 | Baixa | _a definir_ |
| F178 | Funil de negocios com estagios | Acompanhar oportunidades ate o fechamento | Bitrix24 | Media | _a definir_ |
| F179 | Historico de interacoes por cliente | Linha do tempo do relacionamento | Bitrix24 | Media | _a definir_ |
| F180 | Orcamento ou proposta a partir de um negocio | Gerar documento comercial do proprio registro | Bitrix24 | Alta | _a definir_ |
| F181 | Formulario publico que gera registro | Captar solicitacao de cliente sem e-mail | Notion, Bitrix24 | Media | _a definir_ |

## 22. Contexto pessoal e fronteira de privacidade

| ID | Capacidade | O que faz | Origem | Complexidade | Escopo |
|---|---|---|---|---|---|
| F182 | Espaco pessoal separado do workspace | Dados pessoais em isolamento total no servidor | Proprio | Alta | _a definir_ |
| F183 | Modulo pessoal ativavel ou desativavel | O usuario liga ou desliga a parte pessoal | Proprio | Media | _a definir_ |
| F184 | Visao Hoje montada no cliente | Juncao dos dois contextos acontece no aplicativo, nunca no banco | Proprio | Alta | _a definir_ |
| F185 | Promover item pessoal para o workspace | Travessia explicita, item a item, iniciada pelo usuario | Proprio | Media | _a definir_ |
| F186 | Bloqueio arquitetural de acesso do administrador | O admin nao alcanca o espaco pessoal nem por configuracao | Proprio | Alta | _a definir_ |
| F187 | Exportacao separada dos dados pessoais | O usuario leva o que e dele ao sair da empresa | Proprio | Media | _a definir_ |
| F188 | Habitos e rotinas pessoais | Acompanhamento de repeticao no contexto pessoal | Proprio | Media | _a definir_ |

---

## Fontes lidas

- https://www.notion.com/help/category/databases
- https://www.notion.com/help/database-properties
- https://www.notion.com/help/views-filters-and-sorts
- https://www.notion.com/help/relations-and-rollups
- https://www.notion.com/help/database-automations
- https://www.notion.com/help/database-templates
- https://www.notion.com/help/comments-mentions-and-reminders
- https://www.notion.com/help/sharing-and-permissions
- https://www.notion.com/help/writing-and-editing-basics
- https://www.notion.com/help/import-data-into-notion
- https://www.notion.com/help/forms
- https://www.atlassian.com/software/jira/features
- https://www.atlassian.com/software/jira/guides/automation/overview
- https://www.atlassian.com/software/jira/guides/workflows/overview
- https://www.atlassian.com/software/jira/guides/boards/overview
- https://www.atlassian.com/software/jira/guides/jql/overview
- https://www.atlassian.com/software/jira/guides/issues/overview
- https://www.bitrix24.com/features/
- https://www.bitrix24.com/tools/tasks_and_projects/task-management.php
- https://www.bitrix24.com/tools/tasks_and_projects/task-tracking.php
- https://www.bitrix24.com/tools/tasks_and_projects/automation.php
- https://www.bitrix24.com/tools/crm/sales-management.php
- https://www.bitrix24.com/tools/communications/shared-calendars.php
- https://www.bitrix24.com/tools/communications/online-documents-and-cloud-file-storage.php
- https://www.bitrix24.com/tools/hr_automation/employee-management.php
- https://www.bitrix24.com/tools/hr_automation/work-management.php

## Lacunas conhecidas

Tres paginas retornaram erro 404 e nao puderam ser lidas: historico de versoes do Notion, subitens e dependencias do Notion, e relatorios do Jira. As capacidades desses temas que aparecem no inventario vieram de outras paginas que as mencionam, e por isso estao descritas em nivel mais generico.
