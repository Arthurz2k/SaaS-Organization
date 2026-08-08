# ADR 0001 — Registro tipado em tabela unica

**Data:** 2026-08-07 · **Status:** aceito

## Contexto

O produto precisa de tres tipos na Fase 1: tarefa, nota e evento. A visao Hoje, que e a tela
mais importante do produto, precisa uni-los numa consulta unica e ordena-los por data.

Alternativas consideradas: tres tabelas separadas, tabela base com tabelas de extensao,
e tabela generica com todo o conteudo em JSONB.

## Decisao

Tabela unica `work_items` com coluna discriminadora `type` e colunas anulaveis por tipo.
Campos customizados em coluna JSONB `custom_fields`, descritos por uma tabela `field_definitions`.

## Consequencias

**Positivas:** a visao Hoje e um SELECT com WHERE, sem UNION. Adicionar um tipo novo nao cria tabela.
Filtro, ordenacao e agrupamento funcionam igual para os tres tipos, sem codigo duplicado.

**Negativas:** colunas anulaveis que so fazem sentido para um tipo. A integridade por tipo
precisa ser garantida na camada de servico ou por CHECK constraint, nao pelo schema sozinho.

**Irreversivel na pratica:** separar em tabelas depois quebra toda consulta da visao Hoje.
Registrado como RI-10.
