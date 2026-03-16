# WARP.md

Este arquivo orienta o WARP (warp.dev) ao trabalhar com código neste repositório.

## O que é este repositório

Este repositório é uma skill para Claude Code implementada inteiramente em Markdown. É uma adaptação para português da skill [humanizer](https://github.com/blader/humanizer).

O artefato "executável" é o `SKILL.md`: o Claude Code lê o frontmatter YAML (metadados + ferramentas permitidas) e as instruções/prompt que seguem.

O `README.md` é para humanos: instalação, uso e uma visão geral compacta dos padrões.

## Arquivos principais (e como se relacionam)

- **`SKILL.md`**
  - A definição da skill propriamente dita.
  - Começa com frontmatter YAML (`---` ... `---`) contendo `name`, `version`, `description` e `allowed-tools`.
  - Após o frontmatter está o prompt do editor: a lista canônica e detalhada de padrões com exemplos adaptados para português.

- **`README.md`**
  - Instruções de instalação e uso.
  - Contém a tabela resumida dos "24 padrões" e um breve histórico de versões.

Ao alterar comportamento/conteúdo, trate o `SKILL.md` como fonte da verdade e atualize o `README.md` para mantê-lo consistente.

## Comandos comuns

### Instalar a skill no Claude Code

**Recomendado** (clonar direto no diretório de skills):

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/argentoni/humanizador.git ~/.claude/skills/humanizador
```

**Instalação/atualização manual** (somente o arquivo da skill):

```bash
mkdir -p ~/.claude/skills/humanizador
cp SKILL.md ~/.claude/skills/humanizador/
```

### Como "executar" (Claude Code)

Invocar a skill:

- `/humanizador` e colar o texto
- Ou pedir diretamente: "humanize este texto", "tire a cara de IA desse texto"

## Fazendo alterações com segurança

### Versionamento (manter em sincronia)

- `SKILL.md` tem um campo `version:` no frontmatter YAML.
- `README.md` tem uma seção "Histórico de versões".

Se você alterar a versão, atualize ambos.

### Editando o `SKILL.md`

- Preserve a formatação e indentação válidas do frontmatter YAML.
- Mantenha a numeração dos padrões estável, a menos que esteja renumerando intencionalmente (já que a tabela e os exemplos do README referenciam a mesma numeração).

### Documentando correções não óbvias

Se você alterar o prompt para lidar com um modo de falha complicado (por exemplo, uma edição incorreta recorrente ou uma mudança inesperada de tom), adicione uma nota curta na seção "Histórico de versões" do `README.md` descrevendo o que foi corrigido e por quê.
