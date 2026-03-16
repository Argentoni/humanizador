# Humanizador

Uma skill para Claude Code que remove sinais de escrita gerada por IA de textos em português, tornando-os mais naturais e com som de escrita humana.

Adaptação para português da skill [humanizer](https://github.com/blader/humanizer) (v2.2.0), originalmente escrita em inglês.

## Instalação

**Recomendado** (clonar direto no diretório de skills do Claude Code):

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/argentoni/humanizador.git ~/.claude/skills/humanizador
```

**Instalação/atualização manual** (somente o arquivo da skill):

```bash
mkdir -p ~/.claude/skills/humanizador
cp SKILL.md ~/.claude/skills/humanizador/
```

## Uso

No Claude Code, invoque a skill:

```
/humanizador

[cole seu texto aqui]
```

Ou peça ao Claude para humanizar o texto diretamente:

```
Humanize este texto: [seu texto]
```

```
Tire a cara de IA desse texto: [seu texto]
```

## Visão geral

Baseado no guia [Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) da Wikipédia, mantido pelo WikiProject AI Cleanup, com padrões e exemplos adaptados para o português brasileiro.

A skill inclui uma passada final de auditoria ("o que torna isso obviamente gerado por IA?") seguida de uma segunda reescrita, para capturar IAísmos remanescentes no primeiro rascunho.

### Insight central da Wikipédia

"LLMs usam algoritmos estatísticos para adivinhar o que deveria vir a seguir. O resultado tende ao resultado estatisticamente mais provável que se aplica à maior variedade de casos."

## 24 Padrões detectados (com exemplos Antes/Depois)

### Padrões de conteúdo

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 1 | Inflação de importância | "marcando um momento fundamental na evolução..." | "foi criado em 1934 para centralizar a coleta de dados" |
| 2 | Name-dropping de notabilidade | "citada na Folha, no O Globo, na BBC Brasil" | "Em entrevista à Folha em 2024, ela argumentou..." |
| 3 | Análises superficiais com gerúndio | "simbolizando... refletindo... evidenciando..." | Remover ou expandir com fontes reais |
| 4 | Linguagem promocional | "aninhada na deslumbrante região" | "é uma cidade no litoral do Rio de Janeiro" |
| 5 | Atribuições vagas | "Especialistas acreditam que desempenha um papel crucial" | "segundo levantamento de 2019 da Embrapa" |
| 6 | Desafios formulaicos | "Apesar dos desafios... continua prosperando" | Fatos específicos sobre desafios reais |

### Padrões de linguagem

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 7 | Vocabulário de IA | "Além disso... testemunho... cenário... evidenciando" | "também... continua sendo" |
| 8 | Verbos inflados | "serve como... apresenta... oferece" | "é... tem" |
| 9 | Paralelismos negativos | "Não se trata apenas de X; trata-se de Y" | Afirmar o ponto diretamente |
| 10 | Regra de três | "inovação, inspiração e insights" | Usar número natural de itens |
| 11 | Rodízio de sinônimos | "protagonista... personagem principal... figura central... herói" | "protagonista" (repetir quando mais claro) |
| 12 | Faixas falsas | "do Big Bang à matéria escura" | Listar tópicos diretamente |

### Padrões de estilo

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 13 | Excesso de travessão | "instituições — não o povo — no entanto continua —" | Usar vírgulas ou pontos |
| 14 | Excesso de negrito | "**OKRs**, **KPIs**, **BMC**" | "OKRs, KPIs, BMC" |
| 15 | Listas com cabeçalhos em linha | "**Performance:** Performance melhorou" | Converter em prosa |
| 16 | Title Case nos títulos | "Negociações Estratégicas E Parcerias" | "Negociações estratégicas e parcerias" |
| 17 | Emojis | "🚀 Fase de Lançamento: 💡 Insight:" | Remover emojis |
| 18 | Aspas tipográficas | \u201cdisse 'o projeto'\u201d | disse "o projeto" |

### Padrões de comunicação

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 19 | Artefatos de chatbot | "Espero que isso ajude! Me avise se..." | Remover completamente |
| 20 | Disclaimers de data de corte | "Embora detalhes sejam limitados nas fontes disponíveis..." | Encontrar fontes ou remover |
| 21 | Tom bajulador | "Ótima pergunta! Você está absolutamente certo!" | Responder diretamente |

### Preenchimento e atenuação

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 22 | Frases de preenchimento | "A fim de", "Devido ao fato de que" | "Para", "Porque" |
| 23 | Atenuação excessiva | "poder-se-ia potencialmente" | "pode" |
| 24 | Conclusões genéricas | "O futuro parece brilhante" | Planos ou fatos específicos |

## Exemplo completo

**Antes (cara de IA):**

> Ótima pergunta! Aqui está um ensaio sobre este tópico. Espero que isso ajude!
>
> A programação assistida por IA serve como um testemunho duradouro do potencial transformador dos grandes modelos de linguagem, marcando um momento fundamental na evolução do desenvolvimento de software. No cenário tecnológico em rápida evolução de hoje, essas ferramentas revolucionárias — aninhadas na interseção entre pesquisa e prática — estão remodelando como engenheiros ideiam, iteram e entregam, ressaltando seu papel vital nos fluxos de trabalho modernos.

**Depois (humanizado):**

> Assistentes de código com IA podem te deixar mais rápido nas partes chatas. Não em tudo. Definitivamente não em arquitetura.
>
> São ótimos em boilerplate: configs, scaffolding de testes, refatorações repetitivas. Também são ótimos em parecer certos estando errados. Já aceitei sugestões que compilaram, passaram no lint e ainda assim erraram o ponto, porque eu parei de prestar atenção.
>
> Se você trata como autocomplete e revisa cada linha, é útil. Se usa pra evitar pensar, vai te ajudar a subir bugs mais rápido.

## Referências

- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) - Fonte primária
- [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup) - Organização mantenedora
- [humanizer](https://github.com/blader/humanizer) - Skill original em inglês

## Histórico de versões

- 2.2.0 - Versão inicial da adaptação para português, baseada na v2.2.0 do humanizer original

## Licença

MIT
