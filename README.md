# Horizonte de Glifos

Um buraco negro de Schwarzschild em 3D, desenhado com cerca de 300 mil símbolos matemáticos (∫ ∑ ∂ ∇ ∞ α β γ Ω …) que orbitam de acordo com a Relatividade Geral.

De longe, os símbolos aparecem como poeira luminosa. Quando você aproxima a câmera, ou usa a lupa, eles ficam legíveis.

**Demo:** https://brunosakamoto.github.io/horizonte-de-glifos/

## Controles

| Ação | Comando |
|---|---|
| Girar a câmera | arrastar |
| Aproximar / afastar | roda do mouse ou pinça |
| Lupa (teleobjetiva) | `Shift` + roda, ou o controle "lupa" |
| Pausar o tempo | `Espaço` |
| Esconder a interface | `H` |
| Vistas prontas | borda (i=84°), inclinado (i=60°), polar (i=17°), mergulho |

## Física simulada

Unidades: G = c = 1 e r<sub>s</sub> = 2GM/c² = 1.

- **Métrica de Schwarzschild**: horizonte de eventos em r = r<sub>s</sub>.
- **Disco de acreção** de 3 a 20 r<sub>s</sub>, com rotação kepleriana diferencial: Ω(r) = √(GM/r³).
- **ISCO** (última órbita circular estável) em 3 r<sub>s</sub>. Dentro dela, o gás mergulha em espiral até o horizonte.
- **Temperatura do disco** (modelo Novikov–Thorne simplificado): T(r) ∝ r<sup>−3/4</sup> (1 − √(r<sub>ISCO</sub>/r))<sup>1/4</sup>, convertida em cor de corpo negro.
- **Doppler relativístico + redshift gravitacional**: g = √(1 − 3M/r) / (1 − **v**·**n**). O brilho escala com g³ e a cor com g·T.
- **Lente gravitacional** (equação da lente pontual): θ<sub>±</sub> = ½(β ± √(β² + 4θ<sub>E</sub>²)), com θ<sub>E</sub>² = 2 r<sub>s</sub> D<sub>LS</sub> / (D<sub>L</sub> D<sub>S</sub>). A imagem primária forma o arco sobre a sombra; a secundária forma o anel interno.
- **Sombra** com parâmetro de impacto crítico b<sub>c</sub> = (3√3/2) r<sub>s</sub> ≈ 2,6 r<sub>s</sub>.
- **Anel de fótons**, mais brilhante do lado que se aproxima do observador.
- **Jatos relativísticos** opcionais.

A lente usa a aproximação de campo fraco, ajustada perto da sombra. Não é um ray-tracing completo de geodésicas.

## Como funciona

- O projeto é um único `index.html`, com [Three.js](https://threejs.org/) r128 carregado por CDN.
- Cada símbolo é uma partícula `THREE.Points`. As órbitas, a lente e o Doppler são calculados no vertex shader, inteiramente na GPU.
- Os símbolos vêm de um atlas de textura gerado em canvas com as fontes STIX Two Text e Noto Sans Math.
- O tamanho de cada partícula na tela decide como ela aparece: abaixo de ~4 px vira um ponto gaussiano, acima de ~13 px vira o glifo inteiro.

Para rodar localmente, basta abrir o `index.html` no navegador. Não há build.

## Licença

MIT
