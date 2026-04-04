# Animações Recomendadas para Landing Pages

## Fade In (Entrada)
- Duration: 0.3-0.6s
- Easing: cubic-bezier(0.25, 0.46, 0.45, 0.94)
- Trigger: Elemento entra no viewport

## Slide In (Lateral)
- Duration: 0.4-0.7s
- Easing: cubic-bezier(0.25, 0.46, 0.45, 0.94)
- Quando: Features cards, testimoniais

## Scale In (Crescimento)
- Duration: 0.3-0.5s
- Easing: cubic-bezier(0.25, 0.46, 0.45, 0.94)
- Quando: Icons, badges

## Stagger (Sequência)
- Entre elementos: 0.1s delay cada
- Criar ritmo visual
- Quando: Card lists, testimonial grid

## Parallax (Profundidade)
- Imagem se move mais lento que scroll
- Factor: 0.5 (metade da velocidade)
- Quando: Hero section

## Hover States
- Button: darken on hover (0.2s)
- Links: underline or color change (0.2s)
- Cards: lift (transform: translateY -4px) on hover (0.2s)

## Scroll Trigger Library
```javascript
// GSAP ScrollTrigger
gsap.to(".element", {
  scrollTrigger: {
    trigger: ".element",
    start: "top 80%",
    end: "top 50%",
    markers: false
  },
  opacity: 1,
  duration: 0.6
});
```

## Animate.css Classes
- `.fade-in` / `.fade-out`
- `.slide-in-left` / `.slide-in-right`
- `.bounce-in`
- `.flip-in`

**Important:** Use sparingly. Menos é mais.
