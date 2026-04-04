# Guia de Deployment

## GitHub Pages (Recomendado)

### Pré-requisitos
- [ ] Git instalado
- [ ] GitHub repo criado
- [ ] GitHub Pages habilitado (Settings > Pages > Source: gh-pages)

### Passos

1. Copie `/dist` folder para raiz do repo
2. Terminal: `git add dist/`
3. Terminal: `git commit -m "deploy: landing page"`
4. Terminal: `git subtree push --prefix dist origin gh-pages`
5. Seu site estará em: `https://[user].github.io/[repo]/`

### Domínio Customizado

1. Crie arquivo `dist/CNAME` com seu domínio (ex: `meulanding.com`)
2. No registrador (Namecheap, etc): aponte CNAME para `[user].github.io`
3. Aguarde 24h

## Netlify (Alternativo)

1. Vá a Netlify.com
2. Drag-and-drop pasta `/dist`
3. Pronto. URL automática gerada.
4. Adicione domínio em Settings > Domain

## Vercel (Alternativo)

1. Vá a Vercel.com
2. Import Git repo
3. Select `/dist` como "Output Directory"
4. Deploy automático a cada git push

## Performance Monitoring

- [ ] Google Search Console (submit sitemap)
- [ ] Google Analytics 4 (track conversions)
- [ ] Lighthouse CI (cada deploy)
- [ ] Uptime monitoring (Uptime Robot, Pingdom)

## Post-Deployment

- [ ] Teste em mobile + desktop + tablet
- [ ] Teste em Chrome, Firefox, Safari
- [ ] Teste formulário (se houver)
- [ ] Teste CTA (vai para lugar certo?)
- [ ] Monitor analytics por 24-48h
