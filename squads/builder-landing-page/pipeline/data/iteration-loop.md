# Loop de Melhoria Iterativa — Landing Page Optimization

## 🎯 Filosofia

Uma landing page não é **lançada e esquecida**. É um **experimento vivo**. Após deploy:

1. Medir performance real
2. Identificar gargalos
3. Hipótese de melhoria
4. Re-rodar squad com ajustes
5. Comparar métricas

Ciclo: **V1 → Dados → Hipótese → V2 → Dados → ...**

---

## 📈 Fase 1: Instrumentação (Imediatamente após deploy)

### Google Analytics 4 (GA4) — Essencial

```
1. Crie property GA4 nova para landing page
2. Coloque tag no <head> do index-animated.html:

<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX', {
    'page_path': window.location.pathname,
    'page_title': document.title
  });
</script>

3. Events importantes a rastrear:
   - view_page (automático)
   - click_cta_hero (click no botão principal)
   - click_cta_final (click na CTA de footer)
   - scroll_to_faq (usuário chegou em FAQ)
   - view_social_proof (viu depoimentos)
   - form_start (iniciou preenchimento)
   - form_submit (completou conversão)
```

**Esperar:** 48h mínimo de dados antes de analisar

---

### Hotjar / Microsoft Clarity (Heatmaps — Opcional mas Valiosa)

```
Mostram:
- Onde usuários clicam
- Onde scrollam (e desistem)
- Movimentos de mouse
- Rage clicks (cliques repetidos no mesmo lugar)

Se conversão cai ou há estranha drop de scroll:
→ Heatmap revela o culpado
```

**Setup rápido:**
- Hotjar: Insira snippet no <head>
- Clarity: Microsoft account + snippet
- Ambas têm tier gratuito

---

### Formulário de Feedback (Se não há conversão automática)

```html
<!-- Coloque em rodapé ou float à direita -->
<button class="feedback-trigger">Feedback?</button>
<form class="feedback-modal" style="display:none">
  <textarea placeholder="O que faltou?"></textarea>
  <select name="reason">
    <option>Preço alto</option>
    <option>Funcionalidade não existe</option>
    <option>Pouco claro</option>
    <option>Desconfiança / Social proof</option>
    <option>Outro</option>
  </select>
  <button type="submit">Enviar</button>
</form>
```

Colha feedback qualitativo de visitantes que **NÃO** converteram.

---

## 📊 Fase 2: Análise (Semana 1-2)

### Métricas Chave

| Métrica | Alvo | Red Flag |
|---------|------|----------|
| **Conversion Rate (CR)** | SaaS: 3%+ / E-comm: 5%+ / B2B: 2%+ | < 1% |
| **Bounce Rate** | < 50% (hero) | > 70% |
| **Avg Session Duration** | > 2 min | < 30s |
| **Click-Through Rate (Hero CTA)** | > 15% dos visitantes | < 5% |
| **Scroll Depth** | > 70% chegar a FAQ | > 50% saem antes de social proof |
| **Traffic Quality** | Baixo bounce em pagas, alto em organic esperado | Bounce 95%+ em pagas |

### Ferramenta: Google Analytics Dashboard

```
Setup em 10 min:

1. GA4 > Home
2. Create new Dashboard
3. Add cards:
   - Conversion Rate (Goal Completions / Sessions)
   - Users → Engagement Summary
   - Engagement > Event Count (track custom events)
   - Behavior > Scroll depth (% usuarios que scrollaram X%)
   - Traffic source breakdown (Organic vs Paid)
4. Set date range: Last 7 days
```

---

## 🔍 Fase 3: Diagnóstico (Semana 1-2)

### Quadrante de Problemas

```
        Alta Bounce    Baixa Bounce
        (< 30s)        (> 2min)
        
Baixa   🔴 Hero falha    🟡 Copy/Value
Conv    (Não resolvem)   (Resolvem mas
        - Headline       preço/trust)
          confuso        - Need social
        - Falta urgência   proof
        - Wrong audience - Precisa FAQ
        
Alta    🟢 Tudo certo    🟢 Otimizar
Conv    (Raro)           (Melhor CR)
        - Parabéns!      - Keep iterating
                         - A/B testing
```

### Debug por Métrica

#### 🔴 Bounce Rate > 70% em 30 segundos
**Problema:** Hero não convence

**Soluções:**
1. Headline confuso? → Carlos volta em Step 04 (copy refinement)
2. Imagem genérica? → Diana volta em Step 06 (design)
3. Wrong audience chegando? → Beatriz volta em Step 02 (briefing, refine SEO keywords)
4. Mobile layout quebrado? → Henrique volta em Step 08 (HTML responsiveness)

#### 🟡 Bounce Rate Baixa, CR < 1%
**Problema:** Gostam, mas não convertam

**Soluções:**
1. Escaneie FAQ → respostas incompletas?
2. Falta social proof? (logos, depoimentos) → Beatriz volta
3. Preço muito alto/invisível? → Carlos volta (CTA de preço)
4. Medo de spam após signup? → FAQ deve tranquilizar
5. CTA button confuso? → Henrique volta (design do botão)

#### 🟡 Scroll Depth cai 70% após Hero
**Problema:** Hero venceu, mas Value Prop não convence seguir

**Solução:**
- Volta Carlos (copy) + Diana (design de seção 2)
- Value props parecem genéricas?
- "Incríveis" em vez de números?

---

## 💡 Fase 4: Hipótese e Prioritização

**Padrão:**

```
Métrica: CR = 0.8%
Hipótese: "Falta social proof. Se adicionar 5 depoimentos + logos, → 2%+"
Impacto: +150% conversion (realista para social proof)
Esforço: Beatriz refina brief + Carlos re-gera copy + Henrique + QA + deploy = 1-2h
ROI: Alto

✅ PRIORIDADE 1
```

```
Métrica: Form abandonment = 50% (3 campos)
Hipótese: "Se reduzir para 1 campo (email) + CTA 'Agendar Demo', → 80%+ completion"
Impacto: +60% form completions
Esforço: Carlos (copy CTA) + Henrique (form) = 30 min
ROI: Alto

✅ PRIORIDADE 2
```

```
Métrica: CTA button azul, CR = 1%
Hipótese: "Se trocar para laranja, → 1.5%"
Impacto: +50% conversion (teste comum)
Esforço: Henrique (1 mudança CSS) = 5 min
ROI: Médio (mas rápido)

⏳ PRIORIDADE 3 (para A/B test simultâneamente)
```

---

## 🚀 Fase 5: Re-rodar Squad com Ajustes

### Modo Iterativo (Novo)

```bash
/opensquad run builder-landing-page --mode iterate

Step 00: [Checkpoint] Selecione o que mudou
         - "Refinar copy (Carlos)"
         - "Ajustar design (Diana)"
         - "Mudar estrutura HTML (Henrique)"
         - "Integrar nova seção (Ana)"

Step 01: Rodar APENAS agentes selecionados
         - Se só copy → roda Carlos + Rodrigo + Pedro (skip Diana, Henrique)
         - Se só design → roda Diana + Henrique + Rodrigo + Pedro

Step 02: Comparar v1 vs v2
         - GA4 data side-by-side
         - Screenshots before/after
         - Auditoria QA comparison
```

**Economia de tempo:** Em vez de 14 steps, rode só 4-6 relevantes.

---

### Template: Brief de Iteração

```markdown
# V2 — Landing Page Iteration

## O que mudou desde V1

### Hipótese
"Social proof fraco reduz conversão. Se adicionar 5 depoimentos + logos, CR sobe de 0.8% → 2%+"

### Impacto esperado
- CR: 0.8% → 2%+ (+150%)
- Bounce rate: Mesmo

### Escopo de mudança
Apenas **Seção 3 (Social Proof)**

## V1 Data
- GA4 conversions: 15 em 1800 visitors (CR = 0.83%)
- Scroll depth: 65% chegam a social proof
- Heatmap: Scroll decline 30% antes de social proof

## Instruções para Beatriz
"Extraia 5 depoimentos + logos reais de clientes. 
V1 teve nenhum — isso é o gap.
Valide com CEO sobre quem podemos citar (NDA check)."

## Instruções para Carlos
"Refine 3 headlines para social proof que demonstrem impacto mensurável.
V1: 'Confiam em nós' (genérico)
V2: '500+ equipes entregam 40% mais em 30% menos tempo. Aqui estão algumas delas.'"

## Instruções para Diana
"Redesenha seção social proof: Organize logos em grid limpo + depoimentos lado-a-lado com foto.
Priorize: Logo prominence + photo + quote impactante + stat mencionada."

## Instruções para Henrique
"Rebuild apenas seção 3. Mantém hero, value, CTA igual.
Mobile: Stack depoimentos em coluna, logos em grid 2-3 cols."

## V2 Esperado
- Seção 3 robusta com prova social
- CR target: 2%+
- Mantém rest da página igual
```

---

## 📊 Template: Comparação V1 vs V2

```
Métrica                 V1          V2        Δ           %
─────────────────────────────────────────────────────────
Visitantes              1800        1800      -           -
Conversões              15          35        +20         +133%
Conversion Rate         0.83%       1.94%     +1.11pp     +133%
Bounce Rate (Hero)      68%         65%       -3pp        -4%
Scroll (até FAQ)        65%         72%       +7pp        +11%
Avg Session Duration    2:15        2:45      +30s        +22%
Hero CTA Click-through  18%         16%       -2pp        -12%*
Social Proof CTR        -           25%       New         New*
─────────────────────────────────────────────────────────

* Hero CTR subiu porque agora + gente chega a social proof
* Social proof seção nova = 25% dos que veem clicam no CTA final

Conclusão: 
✅ Hipótese confirmada: Social proof aumentou CR em 133%
✅ Próximo teste: Remover FAQ (5 objetos) vs Manter?
❌ Bounce rate não mudou (problema maior não é hero)
```

---

## 🔄 Ciclo Contínuo

### Roadmap Típico (Primeiros 3 meses)

```
Semana 1-2: V1 lançada. Coleta GA4 + Hotjar
↓
Semana 2-3: Diagnóstico. Identifica maior gap (ex: falta social proof)
↓
Semana 3-4: V2 iterada. Re-roda squad 4h. Deploy.
↓
Semana 4-5: Mede V2. CR 0.83% → 1.94% ✅
↓
Semana 5-6: V3 hipótese (ex: reduzir form de 3 → 1 campo)
↓
...
↓
Semana 12: V6-V8 rodada. CR 1.94% → 3.5% (alvo SaaS)
```

**Frequência:** 1 grande iteração a cada 2 semanas + 2-3 A/B testes simultâneos

---

## 🧪 A/B Testing (Simultâneamente com Iterações)

### Setup Google Optimize (Google Analytics)

```
1. GA4 > Experiment
2. Crie 2 variants:
   - Control: V2 atual
   - Variant: CTA azul → laranja
3. Split: 50/50
4. Duração: 2 semanas (até N=1000 visitors/variant)
5. Métrica: Conversion rate
6. Significância: 95%+ (p < 0.05)
```

### Ideias de A/B Tests Rápidos

| Elemento | Control | Variant | Esperado |
|----------|---------|---------|----------|
| CTA Color | Azul | Laranja | +10-30% CTR |
| CTA Text | "Iniciar Grátis" | "Agendar Demo" | +5-15% (contexto-dependente) |
| Form Fields | 3 (nome, email, tel) | 1 (email) | +20-50% form submit |
| FAQ State | Fechado | Aberto (primeira) | +5-10% scroll depth |
| Headline | "Entregue 40% mais rápido" | "Economize 20h/semana" | ±20% (varia) |

---

## 📋 Checklist de Iteração

- [ ] V1 rodou por 1-2 semanas? Mínimo N=500 visitantes
- [ ] GA4 dashboard criada + eventos customizados rastreados
- [ ] Hotjar/Clarity ligados? (20-50 recordings min)
- [ ] Top 3 gaps identificados (não mais de 3)
- [ ] Hipótese é testável? (métrica clara + target definido)
- [ ] Escopo limitado? (não redesenhe tudo)
- [ ] Brief de iteração escrito (instruções claras para agentes)
- [ ] Squad mode=iterate ativado? (rode só agentes relevantes)
- [ ] Comparação V1 vs V2 pronta para análise

---

## 🎯 Targets por Fase (Semestral)

```
Mês 1:   V1 → CR 0.5-1.5% (baseline)
Mês 2:   V2-V3 iteradas → CR 1.5-2.5% (+100-200%)
Mês 3:   V4-V6 otimizadas → CR 2.5-4% (+target SaaS)
↓
Se plateou em mês 3: 
  → Problema é produto/preço (não landing page)
  → Ou audiência errada
  → Ou CTA não alinhado com promise
```

---

## 🚨 Red Flags (Itere Imediatamente)

- CR cai 50% entre semanas (bug, traffic shift, platform change)
- Bounce rate 80%+ em primeira 30s (headline problema)
- Form submits caem sem mudança no site (audience shift ou bot traffic)
- Heatmap mostra "rage clicks" em CTA (botão não funciona ou confuso)
- Scroll depth cai drasticamente em uma seção (conteúdo confuso)

---

## 📖 Referências

- **Growth Bible:** Sean Ellis (GrowthHackers)
- **Conversion Rate Optimization:** Neil Patel, Unbounce
- **A/B Testing:** Morten Randomsen (User Testing at Scale)
- **Lean Analytics:** Alistair Croll, Benjamin Yoskovitz (métrica de acompanhamento)
