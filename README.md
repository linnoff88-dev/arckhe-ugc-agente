ï»¿# ê°Å¸Å½Â¬ UGC com agente ê¢â¬â vêÂ­deo promocional feito por um agente de IA

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


[![VêÂ­deo UGC com agente](guia/assets/banner.jpg)](https://inematds.github.io/ugc-agente/guia/)

**ê°Å¸â¡Â§ê°Å¸â¡Â· [PortuguêÂªs](README.md) êÂ· ê°Å¸â¡Âºê°Å¸â¡Â¸ [English](README.en.md) êÂ· ê°Å¸â¡Âªê°Å¸â¡Â¸ [EspaêÂ±ol](README.es.md)**

## O que êÂ©

Este projeto conta como um agente de IA (o Claude Code) produziu um vêÂ­deo promocional de 15 segundos do INEMA.CLUB no estilo UGC, aquele vêÂ­deo "de gente real falando com a cêÂ¢mera" das redes sociais. Serve para quem cria conteêÂºdo e quer delegar a produêÂ§êÂ£o a um agente. Mostra a ideia, os passos com os comandos usados, as dicas que fizeram diferenêÂ§a e os problemas que apareceram no caminho. Para repetir, vocêÂª precisa de assinatura do Kling AI, uma conta ElevenLabs, ffmpeg, Python e um navegador logado no Kling.

## ê°Å¸ââ Guia de uso

Guia completo (ideia, dicas, problemas e passo a passo): **https://inematds.github.io/ugc-agente/guia/**

## A dica principal

**Use a sua assinatura e dêÂª ao agente a capacidade de operar o site.**

- As cenas saêÂ­ram da assinatura Pro do Kling pela CLI oficial (`kling`): 120 crêÂ©ditos, sem chave de API.
- O Lip Sync do Kling sêÂ³ existe no site. O agente abriu um Chromium jêÂ¡ logado (`--remote-debugging-port`) e, pelo Playwright, enviou as cenas, conferiu o custo no botêÂ£o e baixou o resultado: mais 10 crêÂ©ditos.

## Como foi feito

| Etapa | Ferramenta | Resultado |
|---|---|---|
| Cenas | `kling omni_ref_video` (v3.0 Omni, 15 s, 9:16, 1080p, sem êÂ¡udio) | 3 tomadas a partir da arte de referêÂªncia |
| Voz | ElevenLabs `eleven_multilingual_v2`, voz Amanda Kelly, velocidade 1,12 | 13,3 s, conferida pelo Whisper |
| Textos | `scripts/overlay.py` (Pillow) | 450 quadros PNG sincronizados com a fala |
| Lipsync | site do Kling + `scripts/kling_lipsync_*.mjs` | cenas 1 e 3 com a boca sincronizada |
| Montagem | `scripts/montar.sh` (ffmpeg) | 15,000 s, sem marca d'êÂ¡gua, ê¢Ëâ14 LUFS |
| PublicaêÂ§êÂ£o | [yt-pubx](https://github.com/inematds/yt-pubx) | [Short no YouTube](https://www.youtube.com/watch?v=XOyI6dT6ioQ) |

## Arquivos

```
scripts/
  tts_elevenlabs.py          narraêÂ§êÂ£o (chave em ELEVENLABS_API_KEY)
  overlay.py                 camada de textos 1080x1920, 30 fps
  kling_lipsync_enviar.mjs   envia vêÂ­deo + êÂ¡udio ao Lip Sync do site (confere o custo antes)
  kling_lipsync_baixar.mjs   baixa sêÂ³ os resultados pedidos
  montar.sh                  cortes, troca pelas cenas com lipsync e montagem final
guia/                        pêÂ¡gina do guia (PT, EN, ES)
```

## Problemas que apareceram

Lipsync esquecido na 1êÂª versêÂ£o, CLI do Kling sem êÂ¡udio, envio "sem confirmaêÂ§êÂ£o" que tinha entrado, download de trabalhos antigos, marca d'êÂ¡gua, formato de êÂ¡udio recusado (403), mp3 vazio, narraêÂ§êÂ£o longa, quadro 0 vazio, texto sem contraste e folha de quadros fora de ordem. A correêÂ§êÂ£o de cada um estêÂ¡ no [guia](https://inematds.github.io/ugc-agente/guia/#problemas).

---

[INEMA.CLUB](https://inema.club) êÂ· conteêÂºdo aberto e gratuito

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>