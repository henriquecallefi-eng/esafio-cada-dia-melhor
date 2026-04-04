# Step 11 — Rodrigo Revisão

**Type:** Agent  
**Agent:** Rodrigo Revisão  
**Input:** `index-animated.html` (Ana)  
**Output:** `auditoria.md`

## Descrição

Rodrigo audita o site em 4 eixos:
1. **Conversão** (CTA funciona? Copy é assertiva?)
2. **Acessibilidade** (WCAG AA? Contraste OK?)
3. **SEO** (Title, meta, H1, mobile?)
4. **Performance** (Lighthouse > 80?)

## Execution

Rodrigo Revisão agent executa automaticamente.

## Output

- `output/auditoria.md` — Relatório com scores 0-10 por eixo, bugs e sugestões

## Score Mínimo

Cada eixo deve ter score >= 7/10. Se algum ficar abaixo, há fix loop.

## Next

Step 12 — Aprovação QA (checkpoint)
