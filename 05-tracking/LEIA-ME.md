# 05-tracking — Códigos de rastreamento e destino do lead

## Arquivos
- **head.txt** — código pra inserir dentro do `<head>` da página final.
- **body.txt** — código pra inserir logo APÓS a abertura do `<body>`.

Os dois vieram do brief preenchido no TRACKR. Se estiverem com o comentário
de "nenhum código fornecido", peça os códigos ao responsável pelo tracking.

## Onde cada ferramenta entra (regra geral)
| Ferramenta | `<head>` | após `<body>` |
| --- | --- | --- |
| **Meta Pixel** | ✅ script completo (só no head) | ❌ nada |
| **GTM (Google Tag Manager)** | ✅ script (parte 1) | ✅ `<noscript>` (parte 2) |
| **GA4 (gtag.js direto)** | ✅ script completo | ❌ nada |
| **TikTok Pixel** | ✅ script completo | ❌ nada |

- Meta Pixel: **só no head**. Eventos de conversão (Lead/Purchase) disparam
  no clique do CTA ou na página de obrigado — combinar com o gestor.
- GTM: **pede head E body** — as duas partes vêm juntas no painel do GTM.
- GA4 via GTM: só o GTM na página; o GA4 configura-se dentro do painel.

## Destino do lead deste cliente
**WhatsApp — o botão abre uma conversa direto no WhatsApp do cliente (sem formulário)**

Detalhe informado no brief: 5566992623735

Link pronto pro `href` de TODOS os CTAs:

```
https://wa.me/5566992623735?text=Ol%C3%A1!%20Vim%20pelo%20site%20e%20quero%20agendar.%20Pode%20me%20ajudar%3F
```

> Formato: `https://wa.me/{numero}?text={mensagem}` — número com DDI+DDD (só dígitos) e
> mensagem já codificada pra URL. Abrir em nova aba (`target="_blank" rel="noopener"`).
>
> Mensagem pré-preenchida: "Olá! Vim pelo site e quero agendar. Pode me ajudar?"

Todo botão de CTA da landing aponta pra este link do WhatsApp (já com a mensagem pré-preenchida).

A página NÃO precisa de formulário de captura: hero, meio e CTA final
usam o mesmo link acima. A conversão é medida no clique do CTA
(evento Lead/Purchase no pixel — combinar com o gestor).
