# Modelo de pastas do marketplace

Este é o **modelo oficial** de organização do conteúdo do marketplace do Runaki.
Vale para skills, MCPs e plugins. Toda adição futura segue este modelo.

## Dois casos

### 1. Item avulso (marca com um único item)
Fica no topo, dentro da pasta do tipo:

```
skills/<slug>/        uma skill avulsa
mcps/<slug>/          um MCP avulso
plugins/<slug>/       um plugin avulso
```

Exemplos atuais: `skills/humanizer`, `skills/impeccable`, `skills/typesafe-ai`,
`skills/watch`. (impeccable tem muitos arquivos de `reference/` e `scripts/`,
mas é **uma** skill só — um `SKILL.md` — então é avulso, não família.)

### 2. Família (marca com dois ou mais itens)
A marca ganha **uma pasta única no topo** e, dentro dela, os itens agrupados
por tipo:

```
<marca>/
  skills/<slug>/      cada skill da marca
  mcps/<slug>/        cada MCP da marca (quando houver)
  plugins/<slug>/     cada plugin da marca (quando houver)
```

Exemplo atual: **ponytail** — família de 6 skills.

```
ponytail/
  skills/
    ponytail/
    ponytail-audit/
    ponytail-debt/
    ponytail-gain/
    ponytail-help/
    ponytail-review/
```

## Regras

- **Nomes reservados no topo:** `skills/`, `mcps/`, `plugins/` são pastas de
  tipo (itens avulsos). Qualquer **outra** pasta no topo é uma família.
- **Slug continua único e global.** Agrupar numa família é só organização de
  diretório — NÃO funde itens. `ponytail-audit` continua sendo uma skill
  instalável com slug próprio e entrada própria no catálogo.
- **Cada item = uma entrada** em `ms-naki-marketplace/sync/skills.json`, com
  `path` apontando para a pasta folha (a que contém o `SKILL.md`):
  - avulso: `"path": "skills/<slug>"`
  - família: `"path": "<marca>/skills/<slug>"`
- **Quando promover a família:** se uma marca que era avulsa ganha um segundo
  item, mova o primeiro de `skills/<slug>` para `<marca>/skills/<slug>` (com
  `git mv`, preservando histórico) e ajuste o `path` no `skills.json`. Como a
  versão não muda, o sync marca "up to date" e nada é republicado.
- **Um `SKILL.md` por pasta folha.** Material de apoio (reference/, scripts/,
  assets/) fica dentro da pasta do próprio item.

## Por que assim

Um repo por skill virava dezenas de reppositórios soltos. O monorepo já
resolveu isso; o modelo de família resolve o nível seguinte: manter juntas as
peças de uma mesma marca (ex.: a linha ponytail) sem perder que cada uma é
instalável de forma independente. O `cmd/sync` empacota só a pasta-folha de
cada `path`, então nada de uma família vaza para o artefato de outra.
