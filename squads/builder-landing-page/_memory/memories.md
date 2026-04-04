# Squad Builder Landing Pages — Shared Memory

## Modo B (Hybrid — Padrão)

- **Design:** User cria no Stitch (Google AI Design) e conecta via MCP
- **Diana Design:** Extrai tokens do design (cores, tipografia, espaçamento)
- **Henrique HTML:** Traduz fiel ao design Stitch em HTML/CSS
- **Ana Animação:** Integra animações/componentes externos fornecidos pelo user
- **Result:** Design + Claude Code hybrid landing page

## Modo A (Pure Claude — Comparação Opcional)

- **Todos agentes criam do zero:** Beatriz gera brief, Carlos copy, Diana design system, Henrique HTML, Ana GSAP
- **Usado para:** Comparar Pure AI vs Hybrid approach
- **Result:** 100% AI landing page

## Checklist de Qualidade

**Conversão:** CTA clara? Copy assertiva? Score >= 7/10

**Acessibilidade:** Contraste WCAG AA? Alt text? Score >= 7/10

**SEO:** Title, meta, H1, mobile? Score >= 7/10

**Performance:** Lighthouse > 80? Core Web Vitals green? Score >= 7/10

## Deployment Padrão

**GitHub Pages** com git subtree push. Alternativa: Netlify drag-and-drop.

## Próximas Iterações

- [ ] Instalar skills: frontend-design, ui-ux-pro-max, nano-banana-2
- [ ] Verificar se MCP do Stitch já existe ou criar conector
- [ ] Criar best-practices/landing-page.md
- [ ] Criar tools/landing-page/ (screenshot-multiviewport.js, deploy-package.js)
- [ ] Testar squad com brief de teste (HUB R.E.C., por exemplo)
