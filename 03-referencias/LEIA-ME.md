# 03-referencias — Referências de EXECUÇÃO (o gestor preenche)

Esta pasta começa **vazia de propósito**: é você, gestor, quem cura as
referências antes de levar o pacote ao Claude Design.

## O que é referência de EXECUÇÃO (importante)
Referência de execução significa **"quero esse NÍVEL de motion/qualidade"** —
NÃO "quero essa cor/estética". A estética da página já está decidida em
`04-direcao-visual/` (cores da marca, tipografia, personalidade). O que você
cola aqui são exemplos do padrão de EXECUÇÃO: como um site premiado anima o
scroll, como uma transição de seção se comporta, o peso de um reveal.

## O que colocar aqui
- Prints de sites/LPs com execução do nível que você quer
- Frames extraídos de vídeos de referência (ver abaixo)
- Um `notas.md` seu apontando O QUE observar em cada referência
  (ex.: "ref-parallax-01.png: olhar a diferença de velocidade entre camadas")

## Como extrair frames de um vídeo de referência (ffmpeg)
Tem um screen-recording de um site com motion do nível desejado? Extraia
frames dos momentos-chave:

```bash
# 1 frame por segundo do vídeo inteiro (visão geral):
ffmpeg -i referencia.mp4 -vf fps=1 frame-%03d.png

# Frames de um trecho específico (ex.: transição aos 12s, 3s de duração, 4 fps):
ffmpeg -ss 00:00:12 -t 3 -i referencia.mp4 -vf fps=4 transicao-%02d.png
```

**Quais momentos capturar** (3 frames por padrão de motion bastam):
1. Estado INICIAL (antes da animação começar)
2. MEIO da transição (o movimento acontecendo)
3. Estado FINAL (animação resolvida)

**Como nomear** — pelo padrão de motion, não por número solto:
- `ref-hero-load-01.png` … `03.png` — sequência de entrada do hero
- `ref-parallax-01.png` … — parallax multicamada
- `ref-pin-01.png` … — seção pinada (tela trava e a transformação roda)
- `ref-wipe-01.png` … — transição de seção (panel wipe)
- `ref-marquee-01.png` … — marquee horizontal no scroll

No Claude Design, anexe os frames em sequência e diga: "isto é referência de
EXECUÇÃO do padrão X — reproduza o nível/técnica, não as cores".
