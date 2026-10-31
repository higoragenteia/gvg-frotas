# GVG & ARTEFAL — PWA de Frotas

Shell instalável que abre o **Controle de Frota** dentro do próprio app, sem redirecionar para
`script.google.com` e sem exibir a faixa azul do Google Apps Script.

## Arquitetura

```
GitHub Pages (shell + manifest + service worker + ícones)
        └── iframe em tela cheia → Apps Script /exec (app real)
```

O sistema, a planilha e os dados da frota continuam no Google Apps Script da empresa.

## Links

- PWA: `https://higoragenteia.github.io/gvg-frotas/`
- App (Apps Script): `https://script.google.com/macros/s/AKfycby3W5KlwLYtX7j3_lvi6Zcf6d67k2fKnsg7K0MOmIK-b2X3xY7y57Al-uEPBdzxBaLB/exec`
- Planilha: `https://docs.google.com/spreadsheets/d/1ck1lDtk_W9vjyQEnhV2Ze5secbayGLFfZi4Z0NuX-GY/edit`

## Arquivos

- `index.html` — shell em tela cheia + iframe + instalação + instruções iOS/Android.
- `manifest.webmanifest` — nome, ícones, cores, `standalone`, `start_url` e `scope`.
- `sw.js` — service worker com versionamento de cache.
- `icone-180.png`, `icone-192.png`, `icone-512.png` — ícones.
- `.nojekyll` — necessário para GitHub Pages.

## Instalação

### Android

Abra a URL do GitHub Pages no Chrome e use **📲 Instalar** no canto inferior direito.

### iPhone

No Safari, abra a URL do GitHub Pages e use **Compartilhar → Adicionar à Tela de Início**.

> Se o Safari bloquear o app dentro do iframe, use o link
> **Problemas para abrir? Toque aqui** no canto inferior esquerdo.

## Atualizações

O service worker usa `CACHE = 'gvg-frotas-pwa-v1'`. Ao publicar uma nova versão do shell,
incremente esse valor. O conteúdo do Apps Script é atualizado pelo próprio Apps Script; os
funcionários não precisam reinstalar o PWA.
