# One-Shot — LC 214/2025 (IBS/CBS/IS) — Orquestração Sequencial
## Objetivo
Executar uma única corrida de pesquisa profunda (multiagentes + sequential thinking) para mapear LC 214/2025 com evidências **ipsis litteris (≤25 palavras)** + **URL completa**, gerando:
- `/outputs/relatorios/lc214-dossie.md` (+PDF)
- `/outputs/planilhas/lc214-evidencias.csv`
- Commits por etapa

## Ferramentas MCP esperadas
- fetch.get(url) → captura + conversão
- filesystem.write(path, content)
- git.commit(message)
- (opcional) everything.complete()

## Sequência (executar em ordem)
1. Rodar **A-Fontes Oficiais** (`prompts/01-agente-fontes-oficiais.md`) usando **configs/queries-pack.yaml::A1_oficiais** → salve em `/outputs/evidencias/01-oficiais.md` + CSV.
2. Rodar **A-Rastreio Legislativo** (`prompts/02-agente-rastreio-legislativo.md`) → `/outputs/evidencias/02-linhadotempo.md` + CSV.
3. Rodar **A-Conteúdo Técnico** (cruzar IBS/CBS/IS, Comitê Gestor, regimes) → `/outputs/evidencias/03-conteudo-tecnico.md` + CSV.
4. Rodar **A-Cronograma & Transição** (DF-e, notas técnicas) → `/outputs/evidencias/04-cronograma.md` + CSV.
5. Rodar **A-Edge Cases/Benefícios** (isenções/reduções) → `/outputs/evidencias/05-especificos.md` + CSV.
6. Rodar **Orquestrador-Síntese** (`prompts/00-orquestrador-oneshot.md`) → consolida tudo em `/outputs/relatorios/lc214-dossie.md` (+ PDF) e faz o commit final.

## Política de Citação (obrigatória)
- Máx. 25 palavras por citação literal; sempre URL completa; diferenciar norma (DOU/lei) de doutrina (análises).
