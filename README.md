# Meus Gastos 💸 (PWA)

Telinha do assistente financeiro pessoal. Página estática (PWA) que roda no
GitHub Pages e grava numa planilha do Google Sheets através de um Apps
Script (o "porteiro").

## Arquitetura

```
[iPhone: PWA no GitHub Pages] --POST + token--> [Apps Script doPost] --> [Planilha]
```

- O app abre instantâneo (cache local via service worker) e tem ícone nativo.
- A URL do Apps Script e o token **não ficam neste repositório**: são
  digitados uma vez na tela de configuração (⚙️) e salvos só no aparelho.
- Sem o token, ninguém grava nada na planilha, mesmo conhecendo a URL.

## Arquivos

- `index.html` — o app inteiro (tela, estilos e lógica)
- `manifest.webmanifest` — nome/ícone/cores do PWA
- `sw.js` — service worker (cache da casca do app; suba `gastos-v1` → `v2`
  ao publicar mudanças)
- `icon-*.png`, `apple-touch-icon.png` — ícones

## Backend

O código do Apps Script (com o `doPost` e o token) vive em
`../assistente-gastos/Code.gs`, colado num projeto Apps Script vinculado à
planilha, publicado como App da Web com acesso "Qualquer pessoa".
