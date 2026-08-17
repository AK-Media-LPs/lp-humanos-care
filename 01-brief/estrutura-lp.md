# Estrutura da landing page — Humanos Care

> Ordem das seções, elemento-assinatura e o que anima em cada momento.
> É o roteiro de construção — o Claude Design segue esta ordem.

## Regras estruturais (inegociáveis)
- Uma página, um objetivo: captura de lead (formulário/WhatsApp).
- 3 CTAs com a mesma ação (hero, meio, final) — textos em `01-brief/copy.md`, nunca repetir a mesma frase.
- Sem menu de navegação, sem links de fuga que compitam com o CTA.
- Mobile-first, tipografia fluida, touch targets ≥ 48px.

## Para onde os CTAs apontam
Todo botão de CTA da landing aponta pra este link do WhatsApp (já com a mensagem pré-preenchida).

```
https://wa.me/5566992623735?text=Ol%C3%A1!%20Vim%20pelo%20site%20e%20quero%20agendar.%20Pode%20me%20ajudar%3F
```

(abrir em nova aba: `target="_blank" rel="noopener"`)
Detalhes e checagem final em `05-tracking/LEIA-ME.md`.

## Elemento-assinatura (o personagem visual recorrente)
A caderneta de vacinação, tratada como ícone gráfico linear (nunca foto de frasco/agulha/rótulo) — um pequeno cartão com linhas de checklist que funciona como o 'personagem' da página, já que não há logo ou mascote. Arco: no hero, aparece pequeno, próximo ao CTA, com 2 caixinhas de checklist vazias e uma marcada com '?' — sinaliza a dúvida da mãe, com um movimento próprio contínuo e discreto (leve pulsar/oscilação em spring calma, nunca giro ou bounce). Na seção Problema, o mesmo ícone aparece fragmentado/disperso ao lado de cada dor-card (uma caixinha vazia por dor). Na seção Solução — momento de maior orquestração de movimento da página — as 3 caixinhas se preenchem em sequência com check em spring suave, sincronizadas ao scroll dos 3 passos, formando uma linha de checklist completa ao final da seção. Na Prova Social, o ícone aparece no fundo escuro, já totalmente check, em baixa opacidade, como marca de fundo. No CTA final, resolve-se: a caderneta aparece com um selo/stamp circular 'resolvido' sobreposto, na cor #4361EE, coroando a promessa da página. No mobile, o ícone simplifica para uma versão de 1 linha (3 caixinhas em fileira) sem perder o arco de estado.

## Ordem das seções

### 1. Hero
Layout assimétrico full-bleed 55/45: painel de texto à esquerda sobre fundo #FAF8F4 (headline de 2 linhas com contraste de peso, subheadline, CTA principal + hint) e a foto real do atendimento ocupando a coluna direita até a borda da viewport, com leve overlay #14193A apenas na área de sobreposição do texto se necessário para legibilidade. O ícone-assinatura da caderneta (estado incompleto, com '?') fica ancorado próximo ao CTA. Headline, subheadline e CTA são estáticos no HTML, sem dependência de JS.

**O que anima:** Ícone-assinatura entra em spring calma e mantém oscilação contínua discreta; headline/CTA aparecem imediatamente sem animação bloqueante; foto recebe fade curto de entrada.

### 2. Problema
Fundo #EEF1FC. Kicker + título centralizados, seguidos de 3 dor-cards em grid (desktop) ou scroll horizontal com snap (mobile), cada um com borda-topo #4361EE e um fragmento do ícone-assinatura (caixinha vazia) ao lado do título do card.

**O que anima:** Cards entram em stagger (0,04-0,08s) com fade + deslocamento 16-24px; cada card anima uma única vez.

### 3. Solução
Fundo #FAF8F4. Título 'Chega com a caderneta, sai sabendo o que fazer' seguido de 3 passos numerados (01/02/03 no tratamento tipográfico de stat), dispostos em linha de timeline horizontal conectada visualmente pela linha de checklist do elemento-assinatura. CTA de meio de página ao final da seção. Momento de maior ousadia de movimento da página.

**O que anima:** As 3 caixinhas do elemento-assinatura preenchem em spring physics sincronizadas ao stagger de entrada dos 3 cards de passo — o clímax visual da página.

### 4. Prova Social
Seção full-bleed de fundo escuro #2B3F8C/#14193A, quebrando a leitura clara da página (contraste emocional proposital). Bloco de stats em destaque editorial tipográfico ('09' grande), abaixo depoimentos em cards com iniciais + cidade de origem (scroll horizontal com snap em mobile, card cortado indicando continuação), e fileira de selos com ícone incluindo identificação do responsável técnico habilitado, sempre visível. Ícone-assinatura aparece de fundo, já totalmente check, em baixa opacidade.

**O que anima:** Fundo com parallax leve na entrada; stats e selos entram em stagger curto; depoimentos apenas fade curto com deslocamento pequeno (movimento discreto, registro de credibilidade).

### 5. CTA final
Retorno ao fundo #FAF8F4 com um cartão central #FFFFFF elevado por borda-topo #4361EE, contendo título, texto, CTA final e risk reversal. O elemento-assinatura aparece resolvido: caderneta com selo circular 'resolvido' em #4361EE sobreposto, coroando a página. Disclaimer 'atendimento particular, complementar ao SUS' visível junto ao CTA.

**O que anima:** Fade curto com deslocamento pequeno no cartão; selo do elemento-assinatura entra em spring suave uma única vez.

### 6. Rodapé
Fundo #14193A, texto claro. Marca tipográfica 'Humanos Care', identificação do responsável técnico habilitado, endereço em Barra do Garças, reforço de 'atendimento particular' e canais de contato — sem navegação, sem links de fuga.

**O que anima:** Apenas fade curto estático, sem stagger elaborado.

## Direção geral de motion
Baseline scroll-driven com scroll() nativo do Motion: cada seção revela seu conteúdo uma única vez com fade curto (200-300ms) + deslocamento de 16-24px em transform/opacity apenas, curva de saída suave, respeitando prefers-reduced-motion (tudo estático se ativado). Hero: headline, subheadline e CTA renderizam imediatamente no HTML (sem aguardar JS, protegendo LCP); a entrada em spring calma (sem repique) se aplica apenas ao ícone-assinatura da caderneta, que ganha depois um movimento contínuo e discreto (leve respiração/oscilação vertical de 2-3px em loop suave) fazendo o papel do 'mascote' que a marca não tem. Momento de maior ousadia da página (o único orçamento de movimento elaborado): a seção Solução, onde as 3 caixinhas de checklist do elemento-assinatura preenchem em spring physics sincronizadas ao stagger de entrada dos 3 cards de passo (intervalo ~0,06s entre eles) — é o clímax visual antes da prova social. Stagger com timeline é usado nos cards de dor, nos selos e nos cards de depoimento (cascata curta 0,04-0,08s). Parallax leve (sem exagero) apenas no bloco de fundo da seção Prova Social ao entrar (deslocamento do painel escuro levemente mais lento que o conteúdo). FAQ/rodapé/prova social recebem apenas fade curto com deslocamento pequeno, sem stagger elaborado. Scroll horizontal com CSS scroll-snap (sem JS extra) nos depoimentos em mobile, com card cortado na borda direita indicando continuação. Nenhuma animação usa hover, drag, exit ou layout animation; nada anima mais de uma vez por scroll; nada atrasa a leitura da headline, oferta ou botão.
