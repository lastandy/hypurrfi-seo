# Framer Project Setup Guide

## Step 1: Create New Framer Project

1. Go to [Framer Dashboard](https://framer.com)
2. Click **New Project**
3. Select **Start from scratch** or choose a CMS-ready template (recommended: Hanssen, Kajo, or Viper)
4. Name project: `HypurrFi SEO`

## Step 2: Set Up CMS Collection for Articles

### Create Collection

1. Open **CMS Panel** (sidebar icon or press `C`)
2. Click **+ New Collection**
3. Name: `Articles`
4. Configure fields:

| Field Name | Type | Required | Notes |
|------------|------|----------|-------|
| Title | Plain Text | Yes | Article headline |
| Slug | Slug | Yes | Auto-generated from title |
| Featured Image | Image | Yes | Hero image (1200x630px) |
| Excerpt | Plain Text | Yes | 150-160 character summary |
| Content | Formatted Text | Yes | Rich text with headings, lists, code blocks |
| Publish Date | Date | Yes | Article publication date |
| Author | Plain Text | Optional | Author name |
| Tags | Multi-Reference | Optional | Link to Tags collection |
| SEO Title | Plain Text | Optional | Custom meta title (60 chars max) |
| SEO Description | Plain Text | Optional | Custom meta description (160 chars max) |
| Canonical URL | Link | Optional | For republished content |

### Create Tags Collection (Optional but Recommended)

1. **+ New Collection** → Name: `Tags`
2. Fields:
   - Tag Name (Plain Text, Required)
   - Slug (Slug, Required)
   - Description (Plain Text, Optional)

## Step 3: Create CMS Pages

### Article Detail Page (Template)

1. **Pages Panel** → **+ New Page**
2. Select **CMS Page** → Choose `Articles` collection
3. Page name: `Article Detail`
4. Design the template:

**Layout Structure:**
```
[Navigation Component]
    |
[Hero Section]
    - Featured Image (Full width, 16:9 ratio)
    - Title (H1)
    - Author + Date metadata
    |
[Article Content]
    - Rich text content
    - Proper heading hierarchy (H2, H3)
    - Internal links
    |
[Tags Section]
    - Tag pills linked to library
    |
[Related Articles]
    - Carousel of 3 related posts
    |
[Newsletter CTA]
    - Email signup form
    |
[Footer]
```

### Article Library Page

1. **+ New Page** → Name: `Articles Library`
2. Set as index page (optional)
3. Design:

**Layout:**
```
[Navigation]
    |
[Hero]
    - Page Title: "Educational Resources"
    - Subtitle/Description
    |
[Filter Bar]
    - Search input
    - Tag filters (horizontal scroll)
    - Sort dropdown (Newest, Popular, A-Z)
    |
[Article Grid]
    - 3-column grid (desktop)
    - 2-column (tablet)
    - 1-column (mobile)
    - Cards with:
      - Featured image
      - Title
      - Excerpt (truncated)
      - Date
      - Read time estimate
    |
[Load More / Pagination]
    |
[Footer]
```

## Step 4: Add Article Carousel to Main Page

1. Navigate to your main/homepage
2. Scroll to bottom section where carousel should go
3. **Insert** → **Components** → **Carousel**
4. Configure carousel:

### Carousel Settings

**Content:**
- Connect to: `Articles` collection
- Filter: Published articles only
- Sort: By date (newest first)
- Limit: 6-8 articles

**Layout:**
- Visible slides: 3 (desktop), 2 (tablet), 1 (mobile)
- Gap: 24px
- Card design:
  ```
  [Image - 16:9 ratio]
  [Title - 2 lines max]
  [Excerpt - 2 lines]
  [Date]
  ```

**Navigation:**
- Arrows: Yes (left/right)
- Dots: Yes (bottom)
- Autoplay: Optional (5s interval)
- Swipe: Enabled for mobile

**Styling:**
- Card background: White or subtle gray
- Border radius: 8-12px
- Shadow: Subtle elevation
- Hover state: Slight scale up (1.02) + shadow increase

## Step 5: Navigation Setup

1. Create Navigation component:
   - Logo (left)
   - Links: Home, Articles, About, Contact
   - CTA button (optional)

2. Apply to Layout Template:
   - **Layouts** panel → **+ New Layout**
   - Add navigation to top
   - Add footer to bottom
   - Apply to all pages

## Step 6: Responsive Design

### Breakpoints to Configure

- **Desktop**: 1200px+ (3-column grid)
- **Tablet**: 768px-1199px (2-column grid)
- **Mobile**: <768px (1-column, hamburger menu)

### Mobile Optimizations

- Touch-friendly carousel (swipe enabled)
- Stacked layout for article detail
- Collapsible filters on library page
- Optimized images (Framer auto-optimizes)

## Step 7: Styling & Branding

### Color Palette

Define in Site Styles:
- Primary: [Your brand color]
- Secondary: [Accent color]
- Background: #FFFFFF or #F5F5F5
- Text: #1A1A1A (headings), #4A4A4A (body)
- Links: Primary color

### Typography

- Headings: Inter, SF Pro, or your brand font
- Body: System sans-serif or matching heading
- Sizes:
  - H1: 48px/40px/32px (desktop/tablet/mobile)
  - H2: 36px/32px/28px
  - H3: 28px/24px/20px
  - Body: 18px/16px/16px

## Step 8: Preview & Test

1. **Preview** (top right) → Test all pages
2. Check mobile responsiveness
3. Test carousel functionality
4. Verify all links work
5. Check CMS preview with sample content

## Step 9: Publish

1. Click **Publish** (top right)
2. Choose domain:
   - Free: `hypurrfi-seo.framer.website`
   - Custom: See `dns-setup.md`

## Next Steps

- Configure SEO settings: `seo-configuration.md`
- Set up custom domain: `dns-setup.md`
- Add sample content to test CMS
- Connect analytics

---

## Framer Resources

- [Framer CMS Academy](https://www.framer.com/academy/courses/getting-started-with-framer-cms)
- [Carousel Component](https://www.framer.com/academy/lessons/carousel)
- [SEO Features](https://www.framer.com/help/articles/guide-to-seo-features-and-tools/)
