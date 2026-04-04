# Builder Landing Pages Squad

## O que é?

Um squad de **7 agentes especializados** que criam landing pages e websites **end-to-end**, pronto para deploy em GitHub Pages.

## Dois Modos de Operação

### 🎨 Modo B — Hybrid (Padrão)

Você cria o design no **Stitch** (Google AI Design), e Claude Code traduz para código.

```
Stitch Design → Diana extrai tokens → Henrique constrói HTML → Ana integra animações → Deploy GitHub Pages
```

**Quando usar:** Você quer design visual customizado + código profissional.

### 💎 Modo A — Pure Claude

Claude cria **tudo do zero** — brief, copy, design, HTML, animações. 100% IA.

```
Brief → Copy → Design System → HTML → GSAP Animations → QA → Deploy
```

**Quando usar:** Comparar Pure AI vs. Hybrid, ou experimentar sem design importado.

---

## Quick Start

```bash
/opensquad run builder-landing-page
```

Siga os passos:

1. **Step 01:** Forneça info do produto (nome, objetivo, público, [Modo B] design Stitch)
2. **Step 02-14:** Agentes trabalham automaticamente com checkpoints para você aprovar

---

## Os 7 Agentes

| # | Agente | Papel | Output |
|---|--------|-------|--------|
| 1 | **Beatriz Briefing** | Estrategista | `structured-brief.md` |
| 2 | **Carlos Copy** | Redator | `copy-deck.md` (3 variantes) |
| 3 | **Diana Design** | Arquiteta | `design-system.md` |
| 4 | **Henrique HTML** | Desenvolvedor | `index.html` (sem animações) |
| 5 | **Ana Animação** | Integradora | `index-animated.html` |
| 6 | **Rodrigo Revisão** | QA | `auditoria.md` (Conversão/Acessibilidade/SEO/Performance) |
| 7 | **Pedro Publicação** | DevOps | `/dist` + deploy instructions + screenshots |

---

## Pipeline — 14 Steps

```
Step 01 ────  [✓ Checkpoint] Coleta de Briefing
Step 02 ────  [Agent] Beatriz Briefing
Step 03 ────  [✓ Checkpoint] Aprovação do Brief
Step 04 ────  [Agent] Carlos Copy
Step 05 ────  [✓ Checkpoint] Aprovação do Copy
Step 06 ────  [Agent] Diana Design
Step 07 ────  [✓ Checkpoint] Aprovação do Design System
Step 08 ────  [Agent] Henrique HTML
Step 09 ────  [✓ Checkpoint] Aprovação da Estrutura (screenshot)
Step 10 ────  [Agent] Ana Animação
Step 11 ────  [Agent] Rodrigo Revisão
Step 12 ────  [✓ Checkpoint] Aprovação QA
Step 13 ────  [Agent] Pedro Publicação
Step 14 ────  [✓ Checkpoint] Entrega Final
```

**Tempo total:** ~2-3 horas (agentes rodam, você aprova).

---

## Input Esperado (Step 01)

Forneça:
- ✅ Nome do produto
- ✅ Descrição curta (1-2 parágrafos)
- ✅ Diferencial principal (o que torna único?)
- ✅ Público-alvo (pode ser vago, Beatriz refina)
- ✅ Objetivo (conversão? educação? waitlist?)
- ✅ **[Modo B Apenas]** URL/arquivo do design Stitch exportado

---

## Output Final

Você recebe em `squads/builder-landing-page/output/`:

- ✅ `index-animated.html` — Landing page completa, responsiva, pronta
- ✅ `/dist/` — Pasta para deploy no GitHub Pages
- ✅ `/screenshots/` — Previews em 3 viewports (desktop, tablet, mobile)
- ✅ `deploy-github-pages.md` — Instruções passo-a-passo (não-técnicas)
- ✅ `auditoria.md` — Relatório QA (scores 0-10 por eixo)
- ✅ Todos os arquivos intermediários (brief, copy, design system)

---

## Deploy em 2 Minutos

### GitHub Pages (Recomendado)

```bash
# No terminal, na raiz do repo
git add dist/
git commit -m "deploy: landing page"
git subtree push --prefix dist origin gh-pages
```

Seu site estará em: `https://[seu-usuario].github.io/[repo-name]/`

### Netlify (Alternativa)

1. Vá a Netlify.com
2. Drag-and-drop a pasta `/dist`
3. Pronto. URL gerada automaticamente.

---

## Qualidade Garantida

Cada landing page é auditada em **4 eixos**, score mínimo **7/10**:

- ✅ **Conversão** — CTA clara? Copy assertiva?
- ✅ **Acessibilidade** — WCAG AA? Contraste 4.5:1?
- ✅ **SEO** — Title, meta, H1, mobile responsivo?
- ✅ **Performance** — Lighthouse > 80?

Se algum score ficar abaixo de 7/10, há **fix loop** automático (step-12) antes de deploy.

---

## 📈 Loop de Melhoria Pós-Deploy (Essencial!)

Uma landing page **V1 é só o começo**. Após deploy:

1. **Instrumentar:** Google Analytics 4 + Hotjar (heatmaps) para coletar dados reais
2. **Diagnosticar:** Identificar gargalos (bounce rate alta em hero? Conversão cai antes de social proof?)
3. **Hipótese:** "Se remover 1 campo do form, conversão sobe 20%"
4. **Iterar:** Re-rodar squad apenas com agentes relevantes (Carlos Copy + Henrique HTML = 1-2h)
5. **Medir:** Comparar V1 vs V2 em GA4

**Roadmap típico:**
- Semanas 1-2: V1 → 0.8% conversion rate
- Semanas 3-4: V2 (adicionar social proof) → 1.8%
- Semanas 5-6: V3 (reduzir form) → 2.5%
- Semanas 7-12: V4-V8 → 3.5%+ (alvo SaaS)

Veja `pipeline/data/iteration-loop.md` para full framework (GA4 setup, diagnóstico, A/B testing, templates).

---

## Customizações

Cada agente tem **princípios claros** e **anti-patterns documentados**. Você pode:

- Editar `.agent.md` files se quiser ajustar persona/princípios
- Adicionar dados em `/pipeline/data/` (referências, templates)
- Criar novos steps se quiser workflow diferente

**Não altere:** Squad.yaml, pipeline.yaml, squad-party.csv (use `/opensquad edit` em vez disso).

---

## Referências

- **Como Beatriz funciona:** `agents/beatriz-briefing.agent.md` (vai muito além de um simples prompt)
- **Princípios de copy:** `pipeline/data/conversion-principles.md`
- **🆕 Arquitetura de conversão:** `pipeline/data/conversion-architecture.md` — Estrutura obrigatória (Hero → Value → Social Proof → FAQ → CTA), gatilhos mentais, padrões de copy vencedor
- **🆕 Loop de melhoria:** `pipeline/data/iteration-loop.md` — GA4 setup, diagnóstico pós-deploy, A/B testing, roadmap de iterações (essencial para escalar conversão)
- **Design system anatomy:** `agents/diana-design.agent.md`
- **HTML semântico:** `agents/henrique-html.agent.md`
- **QA rubric:** `agents/rodrigo-revisao.agent.md`

---

## Troubleshooting

**"Conversão score baixo em step-12"**
→ Volta para step-05 (Carlos Copy), refina CTA ou headlines. Henrique reconstrói HTML.

**"Acessibilidade falha (contraste < 4.5:1)"**
→ Volta para step-07 (Diana Design), ajusta paleta. Henrique atualiza CSS.

**"GitHub Pages não mostra site"**
→ Aguarde 2-5 minutos. GitHub processa. Verifique Settings > Pages se `gh-pages` branch está selecionado.

**"Performance < 80"**
→ Pedro reotimiza imagens em `index-animated.html`. Reexecuta step-13.

---

## Modo B vs Modo A — Qual Escolher?

| Critério | Modo B (Hybrid) | Modo A (Pure Claude) |
|----------|-----------------|----------------------|
| Design visual | Seu Stitch + customizado | IA gera do zero |
| Tempo | Rápido (~30 min design + 2h squad) | ~3h (tudo no squad) |
| Controle criativo | Alto (você traz design) | Médio (IA sugere) |
| Resultado | Design-driven, pessoal | IA-coeso, genérico |
| Custo design | Gratuito (Stitch) | Gratuito (IA) |
| **Recomendação** | ✅ Use para projetos reais | Compare com A depois |

---

## Próximos Passos Após Deploy

1. **Monitor conversão:** Configure Google Analytics
2. **A/B test:** Teste 2 headlines, 2 cores de CTA
3. **Coletar feedback:** Pergunte a usuarios por email
4. **Iterar:** Se conversão cair, re-rode squad com adjustments

---

## Contato / Troubleshooting

Veja `pipeline/steps/step-14-entrega-final.md` para checklist final.

Se algo não funcionar como esperado, abra uma issue em `/opensquad help`.

---

**Pronto? Vamos lançar landing pages!**

```bash
/opensquad run builder-landing-page
```
