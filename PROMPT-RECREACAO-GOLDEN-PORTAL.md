# Prompt de Recreação — "Golden Portal" (hero Apogee)

> Recriação independente a partir do preview público (vídeo de 6.5s). Nenhum prompt licenciado foi extraído — o design foi decodificado dos frames.

## Decodificação visual (o que o preview mostra)

- **Cena 3D (WebGL/three.js):** campo de flores estilizadas (papoula/anêmona) visto de BAIXO, câmera rente ao solo. Pétalas em vermelho, magenta, rosa, azul e violeta; centros emissivos amarelo-alaranjados com bloom forte. Caules finos escuros. Céu quase preto com brilho quente avermelhado difuso no canto superior esquerdo (fonte de luz distante).
- **Câmera:** push-in lento e sutil (dolly para dentro do campo), com micro-órbita/parallax. Borda das flores em primeiro plano grandes e suavemente desfocadas (profundidade de campo).
- **Movimento idle:** flores balançam com vento suave; partículas de pólen/faíscas derivam para cima ao redor dos centros brilhantes.
- **UI sobreposta:**
  - Header: logo serifada "Apogee" com glifo abstrato; centro: "Menu" + ícone hambúrguer + pill claro "Book a demo"; direita: pill outline "Find out more".
  - Hero central: headline serifada em 3 linhas "Ascend beyond limits with intelligent predictive infrastructure"; subheadline sans 2 linhas cinza-clara "Advanced reasoning systems and predictive models built for the unknown"; CTA pill claro "Discover the Core →".
  - Canto inferior direito: microtexto estilo HUD (timestamp/coordenadas).
- **Paleta:** fundo #050308/#0a0508, branco cru #f5f1ea para texto, acentos das flores (#ff3b3b, #e0409a, #ff7ab8, #4a5cff, #8b5cf6) e centros #ffb347/#ffd166.
- **Tipografia:** display serif (estilo Cormorant/Playfair), texto sans neutro.

## Prompt de recriação (colo no Claude Code / Codex)

```
Crie uma landing page hero-only em HTML único (CDN three.js + GSAP) que recrie a estética "golden portal": um campo de flores bioluminescentes 3D visto de baixo em cena noturna.

CENA 3D (three.js, módulos via importmap, EffectComposer + UnrealBloomPass):
- 350–500 flores instanciadas espalhadas no plano, densas perto da câmera, mais esparsas ao fundo; fog escuro para profundidade.
- Cada flor: 5–7 pétalas (esferas achatadas escala 1×0.15×1.6) arranjadas radialmente com leve rotação e variação de cor entre #ff3b3b, #e0409a, #ff7ab8, #4a5cff, #8b5cf6 (roughness alto); caule cilíndrico fino escuro; centro esfera emissiva amarelo-alaranjado (#ffb347, emissiveIntensity alto) + sprite glow radial.
- Bloom: strength ~0.9, radius ~0.6, threshold ~0.15 — os centros devem brilhar de verdade.
- Céu: fundo #050308; um glow quente avermelhado radial no canto superior esquerdo (sprite grande, additive, opacity baixa).
- Animação idle: cada flor balança rotation.z = sin(t·speed + phase) · 0.06; partículas de pólen (200 pontos, additive, cor quente) derivam lentamente para cima e resetam.
- Entrada: flores "florescem" — pétalas escalam de 0.01 → 1 com stagger por distância da câmera (as de trás primeiro), ease expo.out, ao longo de ~3.5s; câmera faz push-in sutil (dolly de 8% para frente) nos primeiros 6s e depois micro-drift; parallax de mouse leve (±0.3 rad máx) apenas em (pointer:fine).
- Preferências: DPR máx 1.5; se prefers-reduced-motion, cena estática com flores abertas e sem partículas.

UI (sobreposta, pointer-events none exceto interativos):
- Header fixo: esquerda glifo SVG abstrato + "Apogee" em serif; centro "Menu" com ícone hambúrguer e pill claro "Book a demo"; direita pill outline "Find out more". Pills: border-radius 999px, fundo rgba(245,241,234,0.12) backdrop-blur.
- Hero central: headline serifada (Cormorant Garamond 500) em 3 linhas manuais "Ascend beyond limits / with intelligent / predictive infrastructure", clamp(2.5rem, 7vw, 6.5rem), line-height 1.02, cor #f5f1ea; subheadline sans 15–17px cinza #b8b2a8 máx 2 linhas; CTA pill claro "Discover the Core" com seta →, hover 0.35s.
- Canto inferior direito: microtexto mono 10px uppercase tracking 0.2em, opacity 0.5 ("51.9245° N — APOGEE.CORE / v2.4.1").
- Entrada do texto com GSAP: máscara overflow-hidden por linha, yPercent 110 → 0, power4.out, 1.1s, stagger 0.09s, começando 1.2s após o load; depois subheadline e CTA fade-up.
```
