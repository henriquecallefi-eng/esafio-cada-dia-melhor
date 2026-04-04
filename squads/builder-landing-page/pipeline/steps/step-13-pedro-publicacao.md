# Step 13 — Pedro Publicação

**Type:** Agent  
**Agent:** Pedro Publicação  
**Input:** `index-animated.html` (Ana), `auditoria.md` (Rodrigo)  
**Output:** `/dist` folder + deploy instructions

## Descrição

Pedro prepara o site para deploy:
1. Gera screenshots em 3 viewports
2. Cria `/dist` folder com `.nojekyll`, `.gitignore`
3. Gera `deploy-github-pages.md` com instruções passo-a-passo
4. Gera `checklist-deploy.md` para validação pré-deploy

## Execution

Pedro Publicação agent executa automaticamente.

## Output

- `output/dist/` — Folder pronta para deploy
- `output/screenshots/` — Desktop, tablet, mobile previews
- `deploy-github-pages.md` — Como fazer deploy no GitHub Pages
- `checklist-deploy.md` — Pre-deploy checklist

## Next

Step 14 — Entrega Final (checkpoint)
