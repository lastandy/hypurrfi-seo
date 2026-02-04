# CMS Schema Reference

## Articles Collection

### Field Definitions

#### 1. Title
- **Type**: Plain Text
- **Required**: Yes
- **Character Limit**: 100
- **Validation**: Required
- **Purpose**: Article headline, used in H1 and SEO title
- **Example**: "Understanding Vault Deposits in GPU Compute Networks"

#### 2. Slug
- **Type**: Slug
- **Required**: Yes
- **Auto-generate**: From Title
- **Format**: URL-friendly, lowercase, hyphen-separated
- **Example**: `understanding-vault-deposits-in-gpu-compute-networks`

#### 3. Featured Image
- **Type**: Image
- **Required**: Yes
- **Dimensions**: 1200x675px (16:9 ratio)
- **Max File Size**: 5MB
- **Purpose**: Hero image, OG image, thumbnail
- **Alt Text**: Article title or descriptive text

#### 4. Excerpt
- **Type**: Plain Text
- **Required**: Yes
- **Character Limit**: 160
- **Purpose**: Article summary, meta description fallback
- **Example**: "Learn how vault deposits fund GPU acquisition and create sustainable yield through compute sales in decentralized networks."

#### 5. Content
- **Type**: Formatted Text
- **Required**: Yes
- **Features**: 
  - Headings (H2, H3)
  - Paragraphs
  - Lists (bulleted, numbered)
  - Bold, italic, links
  - Code blocks
  - Blockquotes
- **Purpose**: Main article body

#### 6. Publish Date
- **Type**: Date
- **Required**: Yes
- **Default**: Today
- **Purpose**: Publication timestamp, sorting
- **Display Format**: January 15, 2026

#### 7. Author
- **Type**: Plain Text
- **Required**: No
- **Character Limit**: 100
- **Purpose**: Author byline
- **Alternative**: Use Author Reference field for multiple authors

#### 8. Tags
- **Type**: Multi-Reference → Tags Collection
- **Required**: No
- **Max Items**: 5
- **Purpose**: Categorization, filtering, related content

#### 9. SEO Title
- **Type**: Plain Text
- **Required**: No
- **Character Limit**: 60
- **Purpose**: Custom meta title (overrides default)
- **Fallback**: Article Title + " | HypurrFi"

#### 10. SEO Description
- **Type**: Plain Text
- **Required**: No
- **Character Limit**: 160
- **Purpose**: Custom meta description (overrides excerpt)
- **Fallback**: Excerpt field

#### 11. Canonical URL
- **Type**: Link
- **Required**: No
- **Purpose**: For republished or syndicated content
- **Example**: `https://original-source.com/article`

#### 12. Modified Date
- **Type**: Date
- **Required**: No
- **Purpose**: Content update tracking
- **Display**: "Updated January 20, 2026"

## Tags Collection

### Field Definitions

#### 1. Tag Name
- **Type**: Plain Text
- **Required**: Yes
- **Character Limit**: 50
- **Purpose**: Display name
- **Example**: "DeFi", "GPU Compute", "Tutorials"

#### 2. Slug
- **Type**: Slug
- **Required**: Yes
- **Auto-generate**: From Tag Name
- **Purpose**: URL-friendly identifier
- **Example**: `defi`, `gpu-compute`, `tutorials`

#### 3. Description
- **Type**: Plain Text
- **Required**: No
- **Character Limit**: 200
- **Purpose**: Tag page description, SEO

#### 4. Color
- **Type**: Color
- **Required**: No
- **Purpose**: Visual distinction in UI
- **Default**: Brand primary color

## Author Collection (Optional Enhancement)

If managing multiple authors, create this collection:

### Field Definitions

#### 1. Full Name
- **Type**: Plain Text
- **Required**: Yes

#### 2. Slug
- **Type**: Slug
- **Required**: Yes
- **Auto-generate**: From Full Name

#### 3. Bio
- **Type**: Plain Text
- **Required**: No
- **Character Limit**: 300

#### 4. Avatar
- **Type**: Image
- **Required**: No
- **Dimensions**: 400x400px (1:1)

#### 5. Social Links
- **Type**: Multi-Reference → Social Links Collection
- **Required**: No

#### 6. Role/Title
- **Type**: Plain Text
- **Required**: No
- **Example**: "Technical Writer", "Founder"

## Sample Content Structure

### Example Article Entry

```yaml
Title: "The Complete Guide to Vault Deposits"
Slug: "complete-guide-vault-deposits"
Featured Image: [Upload image]
Excerpt: "Discover how vault deposits create a sustainable flywheel in GPU compute networks, funding infrastructure while generating yield."
Content: |
  ## What Are Vault Deposits?
  
  Vault deposits are the foundation of compute networks...
  
  ## How It Works
  
  1. Users deposit capital
  2. Funds acquire GPU infrastructure
  3. Compute is sold to applications
  4. Revenue flows back to depositors
  
  ## Benefits
  
  - Immediate yield from compute sales
  - Points accumulation for token allocation
  - Exposure to growing AI compute market
Publish Date: 2026-01-15
Author: "Alex Chen"
Tags: ["DeFi", "Vaults", "Beginners"]
SEO Title: "Vault Deposits Guide: Fund GPUs & Earn Yield | HypurrFi"
SEO Description: "Learn how vault deposits work in GPU compute networks. Fund infrastructure, earn immediate yield, and accumulate points for token rewards."
```

## Content Templates

### Tutorial Article Template

```
Title: How to [Action] in [Context]
Slug: how-to-[action]-[context]
Tags: Tutorials, [Category]

Structure:
H1: Title
Intro paragraph (2-3 sentences)
H2: Prerequisites
H2: Step-by-Step Guide
  H3: Step 1
  H3: Step 2
H2: Common Issues
H2: Conclusion
```

### Explainer Article Template

```
Title: Understanding [Concept]
Slug: understanding-[concept]
Tags: Education, [Category]

Structure:
H1: Title
Intro: What is [Concept]?
H2: Why It Matters
H2: How It Works
  H3: Component A
  H3: Component B
H2: Real-World Examples
H2: Getting Started
```

### News/Update Template

```
Title: [Announcement]: [What Happened]
Slug: [announcement]-[what-happened]
Tags: News, [Category]

Structure:
H1: Title
Date stamp
H2: Summary
H2: Details
H2: What This Means for You
H2: Next Steps
```

## CMS Best Practices

### Content Entry Workflow

1. **Draft in CMS**:
   - Create article with all required fields
   - Save as draft
   - Review content formatting

2. **SEO Optimization**:
   - Write custom SEO title/description
   - Verify slug is URL-friendly
   - Check excerpt length

3. **Media Upload**:
   - Optimize images before upload
   - Use descriptive filenames
   - Add alt text

4. **Preview**:
   - Use CMS preview mode
   - Check mobile layout
   - Verify all links work

5. **Publish**:
   - Set publish date
   - Add relevant tags
   - Publish or schedule

### Image Specifications

| Use Case | Dimensions | Format | Max Size |
|----------|-----------|--------|----------|
| Featured Image | 1200x675px | JPG/PNG | 500KB |
| OG Image | 1200x630px | JPG/PNG | 500KB |
| Author Avatar | 400x400px | JPG/PNG | 200KB |
| Inline Images | 800x600px | JPG/PNG | 300KB |

### Tag Strategy

**Recommended Tag Categories:**

1. **Content Type**:
   - Tutorials
   - Explainers
   - News
   - Guides

2. **Topic**:
   - DeFi
   - GPU Compute
   - Financial AI
   - Vault Mechanics
   - Tokenomics

3. **Difficulty**:
   - Beginners
   - Intermediate
   - Advanced

**Tag Usage Rules:**
- Maximum 5 tags per article
- Use consistent naming
- Avoid single-use tags
- Review and consolidate quarterly

## Field Reference Table

Quick reference for CMS setup:

| Field | Articles | Tags | Authors |
|-------|----------|------|---------|
| Name/Title | ✓ | ✓ | ✓ |
| Slug | ✓ | ✓ | ✓ |
| Image | ✓ | - | ✓ |
| Description | - | ✓ | ✓ |
| Rich Text | ✓ | - | - |
| Date | ✓ | - | - |
| Multi-Reference | ✓ (Tags) | - | - |
| Plain Text | ✓ | ✓ | ✓ |

---

## CMS Setup Checklist

- [ ] Create Articles collection
- [ ] Add all required fields
- [ ] Configure field validations
- [ ] Create Tags collection
- [ ] Set up Tag multi-reference in Articles
- [ ] Create sample content (3-5 articles)
- [ ] Test CMS preview
- [ ] Verify field bindings in templates
- [ ] Check responsive layouts
- [ ] Publish and verify live site
