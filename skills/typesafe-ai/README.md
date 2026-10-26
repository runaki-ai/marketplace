# typesafe-ai (skill)

Espelho da skill oficial da TypeSafe AI para o marketplace do Runaki.

- Origem: https://github.com/typesafe-ai/skills (`skills/typesafe-ai/SKILL.md`), licença MIT.
- Conteúdo do `SKILL.md` preservado. O frontmatter ganhou `version` (exigido pelo
  `cmd/sync` do ms-naki-marketplace) e `description` em PT-BR.

## Atualizar

1. Copie o `SKILL.md` novo do upstream para a raiz deste repo.
2. Reaplique no frontmatter: `version` (bump semver) e a `description` em PT-BR.
3. Faça push na `main`. O `cmd/sync` do ms-naki-marketplace detecta a versão nova e publica.
