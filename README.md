# ðŸŽ¬ UGC com agente â€” vÃ­deo promocional feito por um agente de IA

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


[![VÃ­deo UGC com agente](guia/assets/banner.jpg)](https://inematds.github.io/ugc-agente/guia/)

**ðŸ‡§ðŸ‡· [PortuguÃªs](README.md) Â· ðŸ‡ºðŸ‡¸ [English](README.en.md) Â· ðŸ‡ªðŸ‡¸ [EspaÃ±ol](README.es.md)**

## O que Ã©

Este projeto conta como um agente de IA (o Claude Code) produziu um vÃ­deo promocional de 15 segundos do INEMA.CLUB no estilo UGC, aquele vÃ­deo "de gente real falando com a cÃ¢mera" das redes sociais. Serve para quem cria conteÃºdo e quer delegar a produÃ§Ã£o a um agente. Mostra a ideia, os passos com os comandos usados, as dicas que fizeram diferenÃ§a e os problemas que apareceram no caminho. Para repetir, vocÃª precisa de assinatura do Kling AI, uma conta ElevenLabs, ffmpeg, Python e um navegador logado no Kling.

## ðŸ“– Guia de uso

Guia completo (ideia, dicas, problemas e passo a passo): **https://inematds.github.io/ugc-agente/guia/**

## A dica principal

**Use a sua assinatura e dÃª ao agente a capacidade de operar o site.**

- As cenas saÃ­ram da assinatura Pro do Kling pela CLI oficial (`kling`): 120 crÃ©ditos, sem chave de API.
- O Lip Sync do Kling sÃ³ existe no site. O agente abriu um Chromium jÃ¡ logado (`--remote-debugging-port`) e, pelo Playwright, enviou as cenas, conferiu o custo no botÃ£o e baixou o resultado: mais 10 crÃ©ditos.

## Como foi feito

| Etapa | Ferramenta | Resultado |
|---|---|---|
| Cenas | `kling omni_ref_video` (v3.0 Omni, 15 s, 9:16, 1080p, sem Ã¡udio) | 3 tomadas a partir da arte de referÃªncia |
| Voz | ElevenLabs `eleven_multilingual_v2`, voz Amanda Kelly, velocidade 1,12 | 13,3 s, conferida pelo Whisper |
| Textos | `scripts/overlay.py` (Pillow) | 450 quadros PNG sincronizados com a fala |
| Lipsync | site do Kling + `scripts/kling_lipsync_*.mjs` | cenas 1 e 3 com a boca sincronizada |
| Montagem | `scripts/montar.sh` (ffmpeg) | 15,000 s, sem marca d'Ã¡gua, âˆ’14 LUFS |
| PublicaÃ§Ã£o | [yt-pubx](https://github.com/inematds/yt-pubx) | [Short no YouTube](https://www.youtube.com/watch?v=XOyI6dT6ioQ) |

## Arquivos

```
scripts/
  tts_elevenlabs.py          narraÃ§Ã£o (chave em ELEVENLABS_API_KEY)
  overlay.py                 camada de textos 1080x1920, 30 fps
  kling_lipsync_enviar.mjs   envia vÃ­deo + Ã¡udio ao Lip Sync do site (confere o custo antes)
  kling_lipsync_baixar.mjs   baixa sÃ³ os resultados pedidos
  montar.sh                  cortes, troca pelas cenas com lipsync e montagem final
guia/                        pÃ¡gina do guia (PT, EN, ES)
```

## Problemas que apareceram

Lipsync esquecido na 1Âª versÃ£o, CLI do Kling sem Ã¡udio, envio "sem confirmaÃ§Ã£o" que tinha entrado, download de trabalhos antigos, marca d'Ã¡gua, formato de Ã¡udio recusado (403), mp3 vazio, narraÃ§Ã£o longa, quadro 0 vazio, texto sem contraste e folha de quadros fora de ordem. A correÃ§Ã£o de cada um estÃ¡ no [guia](https://inematds.github.io/ugc-agente/guia/#problemas).

---

[INEMA.CLUB](https://inema.club) Â· conteÃºdo aberto e gratuito

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>