# SEO Configuration Guide

## Framer SEO Settings

### Site-Wide SEO

1. **Site Settings** (gear icon) → **SEO**
2. Configure:

```
Site Title: HypurrFi | Educational Resources
Site Description: Learn about decentralized finance, GPU compute networks, and financial AI through our comprehensive educational content.
Favicon: Upload logo (32x32px, .png or .ico)
Social Image: Default OG image (1200x630px)
```

### Page-Level SEO

For each page (Home, Articles Library, Article Detail):

1. Select page in **Pages Panel**
2. Click **Page Settings** (cog icon)
3. Configure:

#### Homepage SEO
```
Title: HypurrFi | Educational Resources & Insights
Description: Discover educational content about DeFi, GPU compute networks, and financial AI. Learn how vault deposits fund GPU acquisition for financial applications.
```

#### Articles Library SEO
```
Title: Articles & Resources | HypurrFi
Description: Browse our collection of educational articles about decentralized finance, compute networks, and financial AI applications.
```

#### Article Detail SEO (Dynamic)

**Important**: Use CMS fields for dynamic SEO

1. On Article Detail page → **Page Settings** → **SEO**
2. Set dynamic values:
   - **Title**: Connect to `SEO Title` field (fallback: `Title` + " | HypurrFi")
   - **Description**: Connect to `SEO Description` field (fallback: `Excerpt`)
   - **Social Image**: Connect to `Featured Image`

### URL Structure

- Homepage: `/`
- Articles Library: `/articles`
- Article Detail: `/articles/{slug}` (auto-generated from CMS)

## Technical SEO Configuration

### 1. Semantic HTML Structure

Framer generates semantic HTML automatically. Verify:

```
✓ One H1 per page
✓ Logical heading hierarchy (H1 → H2 → H3)
✓ Article pages use <article> tags
✓ Navigation uses <nav> tags
✓ Main content wrapped in <main>
```

### 2. Image Optimization

- **Alt Text**: Always add to images
  - Featured images: Descriptive alt text
  - Decorative images: Leave empty (Framer handles)
  
- **Dimensions**: Use consistent aspect ratios
  - Featured: 16:9 (1200x675px)
  - OG Images: 1.91:1 (1200x630px)
  - Thumbnails: 4:3 or 1:1

### 3. Internal Linking Strategy

**Article Content Links:**
- Link to related articles using CMS references
- Link to key concepts (create glossary pages)
- Use descriptive anchor text (not "click here")

**Navigation Links:**
- Breadcrumbs on article pages
- "Related Articles" section
- Tag-based cross-linking

## Structured Data (JSON-LD)

Add structured data for rich snippets:

### Article Schema

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "[Article Title]",
  "description": "[Article Excerpt]",
  "image": "[Featured Image URL]",
  "datePublished": "[Publish Date]",
  "dateModified": "[Modified Date]",
  "author": {
    "@type": "Person",
    "name": "[Author Name]"
  },
  "publisher": {
    "@type": "Organization",
    "name": "HypurrFi",
    "logo": {
      "@type": "ImageObject",
      "url": "[Logo URL]"
    }
  }
}
```

**Implementation:**
1. Add **Embed** element to Article Detail page
2. Set to "Head" position
3. Insert JSON-LD with CMS field bindings

### Organization Schema (Homepage)

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "HypurrFi",
  "url": "https://your-domain.com",
  "logo": "https://your-domain.com/logo.png",
  "description": "GPU-backed compute network for financial AI applications"
}
```

## Meta Tags & Open Graph

### Essential Meta Tags

Framer auto-generates:
- `<title>`
- `<meta name="description">`
- `<meta name="viewport">`
- `<meta charset="UTF-8">`

### Open Graph (Social Sharing)

Framer generates automatically based on SEO settings:
```html
<meta property="og:title" content="...">
<meta property="og:description" content="...">
<meta property="og:image" content="...">
<meta property="og:url" content="...">
<meta property="og:type" content="article">
```

### Twitter Cards

```html
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="...">
<meta name="twitter:description" content="...">
<meta name="twitter:image" content="...">
```

## Sitemap & Robots.txt

### Sitemap

Framer auto-generates: `your-domain.com/sitemap.xml`

**Includes:**
- All static pages
- All CMS pages (articles)
- Last modified dates
- Priority levels

### Robots.txt

Framer auto-generates: `your-domain.com/robots.txt`

**Default:**
```
User-agent: *
Allow: /
Sitemap: https://your-domain.com/sitemap.xml
```

**To customize:** Contact Framer support or use custom domain with reverse proxy

## Performance Optimization

Framer handles automatically:
- ✓ Image optimization (WebP conversion, responsive srcset)
- ✓ Lazy loading for below-fold images
- ✓ Code splitting
- ✓ CDN distribution
- ✓ Caching headers

**Manual checks:**
- Minimize heavy animations
- Optimize video files (use external hosting for large videos)
- Keep page weight under 3MB

## Analytics & Tracking

### Google Analytics 4

1. **Site Settings** → **Integrations**
2. Add GA4 Measurement ID (G-XXXXXXXXXX)

### Google Search Console

1. Verify domain ownership:
   - Method 1: HTML tag (add to Framer Site Settings → Custom Code → Head)
   - Method 2: DNS TXT record (see dns-setup.md)
   
2. Submit sitemap: `https://your-domain.com/sitemap.xml`

3. Monitor:
   - Indexing status
   - Search queries
   - Core Web Vitals
   - Mobile usability

### Additional Tools

Consider adding:
- **Plausible Analytics** (privacy-friendly)
- **Hotjar** (heatmaps - add via custom code)
- **Ahrefs/SEMrush** (for tracking)

## Content SEO Best Practices

### Article Writing Guidelines

1. **Title Tags**: 50-60 characters, include primary keyword
2. **Meta Descriptions**: 150-160 characters, compelling CTA
3. **URL Slugs**: Short, descriptive, hyphen-separated
4. **Headings**: Use keywords naturally, one H1 per page
5. **Content Length**: Minimum 300 words, aim for 1000+ for key articles
6. **Internal Links**: 2-5 per article, link to relevant content
7. **Images**: Descriptive filenames, alt text, compressed

### Keyword Strategy

**Primary Keywords:**
- DeFi education
- GPU compute networks
- Financial AI
- Vault deposits
- Compute-to-yield

**Long-tail Keywords:**
- "how do vault deposits fund GPU acquisition"
- "financial AI applications on Hyperliquid"
- "compute revenue sharing models"

### Content Freshness

- Update top-performing articles quarterly
- Add "Last Updated" date
- Redirect outdated content to newer versions

## SEO Checklist

Pre-launch verification:

- [ ] Site title and description set
- [ ] All pages have unique titles
- [ ] All pages have meta descriptions
- [ ] Favicon uploaded
- [ ] OG image configured
- [ ] Semantic HTML verified
- [ ] Images have alt text
- [ ] Internal links working
- [ ] Mobile responsive
- [ ] Page speed < 3s load time
- [ ] Sitemap accessible
- [ ] Robots.txt accessible
- [ ] Structured data implemented
- [ ] Analytics connected
- [ ] Search Console verified
- [ ] SSL certificate active (Framer provides)

## Monitoring & Maintenance

### Monthly Tasks

1. Check Search Console for:
   - Crawl errors
   - Indexing issues
   - Performance drops

2. Review analytics for:
   - Top performing content
   - Bounce rates
   - User engagement

3. Content updates:
   - Update outdated information
   - Refresh stale articles
   - Add new internal links

### Quarterly Tasks

1. SEO audit:
   - Broken links check
   - Page speed test
   - Mobile usability check

2. Content strategy review:
   - Identify content gaps
   - Plan new articles
   - Update keyword targeting

---

## Resources

- [Framer SEO Guide](https://www.framer.com/help/articles/guide-to-seo-features-and-tools/)
- [Schema.org Documentation](https://schema.org/)
- [Google Search Console Help](https://support.google.com/webmasters)
- [PageSpeed Insights](https://pagespeed.web.dev/)
