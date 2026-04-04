# SEO Checklist para Landing Pages

## On-Page

- [ ] **Title Tag** (50-60 chars)
  - Formato: "Primary keyword — Secondary keyword | Brand"
  - Ex: "Landing Page Builder — No-code tool | Opensquad"

- [ ] **Meta Description** (120-160 chars)
  - Descreva o valor: "Crie landing pages conversoras em 30 minutos. Sem código."

- [ ] **H1 Único** 
  - Deve ser o headline do hero
  - Exatamente 1 H1 por página

- [ ] **H2-H3 Estruturados**
  - Progressão lógica: H1 → H2 → H3

- [ ] **Imagens com Alt Text**
  - Descreva: "Logo do HUB R.E.C.", não "logo"

- [ ] **Open Graph Tags**
  ```html
  <meta property="og:title" content="...">
  <meta property="og:description" content="...">
  <meta property="og:image" content="...">
  ```

## Technical SEO

- [ ] **Mobile Responsive** (viewport meta tag)
- [ ] **HTTPS** (não HTTP)
- [ ] **Robots Meta** (não noindex)
- [ ] **Core Web Vitals** > 80 Lighthouse
- [ ] **Sitemap.xml** (se multi-page)
- [ ] **Robots.txt** (se site maior)

## Schema Markup (Optional)

```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "HUB R.E.C.",
  "image": "...",
  "description": "...",
  "url": "https://...",
  "phone": "+55..."
}
```

## Linkbuilding

- [ ] Link para homepage (se landing page é subpage)
- [ ] Link em social media (Instagram bio, etc)
- [ ] Mencionar em blog post (if applicable)

## Analytics

- [ ] Google Analytics 4 integrado
- [ ] Goal tracking (agendamento = conversão)
- [ ] UTM parameters em links (se multi-source)
