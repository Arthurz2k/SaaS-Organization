# Processo de Descoberta e Definição — SaaS Organizacional

> Documento de controle do processo. Atualizado a cada bloco concluído.
> Início: 07/08/2026 · Responsável pelas decisões: Arthur de Oliveira

---

## Parâmetros acordados

| Item | Decisão |
|---|---|
| Formato das perguntas | Formulário HTML interativo, gera texto para colar no chat |
| Granularidade do Bloco 2 | Detalhada — 150 a 200 funcionalidades |
| Restrições travadas | Prazo e orçamento definidos (a informar no Bloco 1, seção G) |
| Demais decisões | Todas em aberto — stack, arquitetura, time, escopo |
| Entregáveis | Arquivos `.md` versionáveis na pasta do projeto |
| Idioma | Conversa e documentos em pt-BR · código e nomenclatura técnica em inglês |

---

## Mapa dos 4 blocos

| Bloco | Objetivo | Perguntas | Status |
|---|---|---|---|
| **1 — Descoberta** | Entender a ideia: visão, público, problema, diferencial, contextos, negócio, restrições, filosofia, privacidade, direção técnica, validação | **72** | 🟡 Aguardando respostas |
| **2 — Triagem de escopo** | Inventário de funcionalidades de Jira, Notion e Bitrix24; cada uma vira uma decisão MVP / v2 / futuro / fora | **~180** | ⚪ Não iniciado |
| **3 — Plano e fases** | Arquitetura, modelo de dados, sequenciamento, marcos, qualidade, release, operação e custos | **~90** | ⚪ Não iniciado |
| **4 — Validação cruzada** | Confirmar tudo, expor contradições entre blocos, travar decisões | **~60** | ⚪ Não iniciado |
| | **Total estimado** | **~400** | |

Depois dos quatro blocos, os entregáveis finais:

1. `01-o-que-e-o-projeto.md` — definição do produto, visão, persona, posicionamento
2. `02-escopo.md` — dentro do escopo, fora do escopo, escopo diferido por versão
3. `03-requisitos-imutaveis.md` — as regras que nenhuma decisão futura pode violar
4. `04-plano-desenvolvimento.md` — fases, marcos, entregas, riscos, estimativas

---

## Bloco 1 — Estrutura das 72 perguntas

| Seção | Tema | Perguntas | Por que importa |
|---|---|---|---|
| A | Visão e propósito | 6 | Define o enquadramento do produto e o que é sucesso |
| B | Público-alvo e persona | 7 | Determina quase todo o resto: escopo, preço, UX |
| C | Problema e evidência | 5 | Separa dor real de suposição |
| D | Diferencial e posicionamento | 6 | Razão para existir frente a Notion/Jira/Bitrix24 |
| E | Contextos pessoal × profissional | 8 | **Núcleo do produto** — é o diferencial estrutural |
| F | Modelo de negócio | 7 | Preço e plano gratuito moldam a arquitetura (limites, tenancy) |
| G | Restrições reais: prazo, dinheiro, time | 8 | Calibra o tamanho do MVP ao que é executável |
| H | Filosofia de produto e experiência | 7 | Densidade, modelo mental, plataforma, offline, colaboração |
| I | Dados, privacidade e conformidade | 6 | LGPD e fronteira de privacidade são requisito, não recurso |
| J | Direção técnica de alto nível | 7 | Stack, banco, multi-tenancy, hospedagem, API |
| K | Validação, lançamento e governança | 5 | Como saber que deu certo e quem decide em caso de conflito |

**Perguntas críticas** (as que, mudando, mudam a arquitetura inteira):
`A1`, `B1`, `E1`, `E3`, `E6`, `H3`, `J3`, `J4`, `G1`, `G4`.

---

## Regras que valem para todo o processo

1. Não invento APIs, limites ou nomes de recursos de Jira, Notion ou Bitrix24. Quando não tiver certeza, digo que não tenho.
2. Inspiração é em **padrão funcional**, nunca em texto, marca ou identidade visual dessas plataformas.
3. Toda recomendação vem com o trade-off explícito — inclusive quando o padrão da referência **não** serve aqui.
4. Nenhuma pergunta é retórica: cada uma existe porque a resposta muda uma decisão de escopo, arquitetura ou plano.
