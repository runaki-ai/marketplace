# Runaki Marketplace (conteúdo)

Fonte única de tudo que o marketplace do Runaki publica: skills, MCPs e plugins.
Um diretório por item. O serviço que assina e serve o catálogo é o
[`ms-naki-marketplace`](https://github.com/runaki-ai/ms-naki-marketplace); este
repositório é só o conteúdo que ele sincroniza.

```
skills/<slug>/SKILL.md     skill (frontmatter com name, version, description)
mcps/<slug>/               servidores MCP (em breve)
plugins/<slug>/            plugins (em breve)
```

## Como uma skill chega no app

1. `ms-naki-marketplace/sync/skills.json` lista cada item com `repo`
   (`runaki-ai/marketplace`) e `path` (`skills/<slug>`).
2. `go run ./cmd/sync` baixa o tarball da `main`, lê `version` do frontmatter do
   `SKILL.md` em `path`, compara com a versão publicada e, se mudou, empacota só
   aquela pasta e publica uma versão nova (assinada Ed25519).
3. O app detecta a versão nova e oferece **Atualizar**.

Só o conteúdo de `skills/<slug>/` entra no artefato. README deste repo, outras
skills e `mcps/` nunca vazam para o zip.

## Adicionar ou atualizar uma skill

- Crie `skills/<slug>/SKILL.md` com `version:` no frontmatter. Para mirror de
  skill de terceiros, preserve o conteúdo original e traga a `LICENSE` (e
  `NOTICE` quando houver). A `description` pode ser em PT-BR; o item no catálogo
  também aceita curadoria via `PATCH /v1/items/<slug>`.
- Atualização = bump de `version` + push na `main`. Sem bump, o sync ignora.
- Skill nova também precisa da entrada em `sync/skills.json` no
  `ms-naki-marketplace`.

## Licenças

Cada skill mantém a licença de origem dentro da própria pasta. Os wrappers
foram criados a partir dos repositórios individuais `runaki-ai/<skill>`
(migrados para cá em 2026-10-26).
