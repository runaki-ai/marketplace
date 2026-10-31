---
version: 0.14.1
name: higgsfield-video-explainer
description: |
  Entrada de compatibilidade para a antiga skill de vídeo explicativo. Use quando: o usuário invoca explicitamente higgsfield-video-explainer ou continua um fluxo já existente dela. NÃO para: novos pedidos genéricos de explicativo, anúncios, clipes avulsos ou edições de vídeo não relacionadas.
argument-hint: "[topic or source files] [duration] [language] [aspect ratio]"
allowed-tools: Bash
---

# Video explainer

Use the `higgsfield-faceless-video` skill for this request and select its illustrated explainer workflow. Preserve the user's inputs and choices. If that skill is not installed, ask the user to update or install the current Higgsfield skills package before generating any assets. Do not use `explainer_video` or `video_explainer`.
