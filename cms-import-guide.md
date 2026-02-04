# CMS Import Automation Guide

## Overview

Instead of manually entering articles in Framer, you can import content from **Notion** or **Google Sheets** using Framer Marketplace plugins.

## Option 1: Google Sheets Import (Recommended)

### Plugin: Google Sheets Import
**Price**: Free  
**Link**: [Framer Marketplace](https://www.framer.com/marketplace/plugins/google-sheets-import-bro0pb4vc2lrb4012vale2qhf/)

### How It Works

1. **Prepare your Google Sheet** with columns matching your CMS fields:
   ```
   | title | excerpt | content | author | tags | publish_date | featured_image |
   ```

2. **Share the sheet** as "Anyone with the link can view"

3. **In Framer**:
   - Open **Plugins** panel
   - Install "Google Sheets Import"
   - Paste your sheet URL
   - Map columns to CMS fields
   - Import as drafts
   - Review and publish

### Features

- ✅ Smart column mapping (auto-detects field names)
- ✅ Creates items as drafts (safe importing)
- ✅ Supports all field types (text, images, dates, references)
- ✅ Validates data before import
- ✅ Skips duplicates (no overwrites)
- ✅ Batch import multiple articles at once

### Best For

- Bulk importing existing content
- Team collaboration (non-designers can edit sheets)
- Content workflows with editors/reviewers
- Regular content updates

---

## Option 2: Notion Import

### Plugin: Notion Import
**Price**: Free  
**Link**: Available in Framer Marketplace

### How It Works

1. **Set up Notion database** with properties matching CMS fields
2. **Connect Notion integration** in Framer
3. **Map Notion properties** to CMS fields
4. **Sync** - one-click import

### Features

- ✅ Syncs Notion databases directly
- ✅ Imports page content, images, and properties
- ✅ Keeps content in sync (re-sync anytime)
- ✅ Great for content teams using Notion

### Best For

- Teams already using Notion for content
- Collaborative writing workflows
- Content with rich formatting in Notion

---

## Option 3: FramerSync (Paid Alternative)

**Price**: Subscription  
**Note**: FramerSync has been discontinued, use the free plugins above instead.

---

## Recommended Workflow

### For Bulk Import (One-time)

1. Use **Google Sheets Import** plugin
2. Export existing articles to CSV → import to Google Sheets
3. Format columns to match CMS fields
4. Import all at once

### For Ongoing Content (Regular)

**Option A - Google Sheets**:
1. Content team writes in Google Sheets
2. Editor reviews in Sheets
3. Import to Framer when ready
4. Publish in Framer CMS

**Option B - Notion**:
1. Content team writes in Notion
2. Editor reviews in Notion
3. Sync to Framer
4. Review in Framer preview
5. Publish

---

## Setup Instructions

### Google Sheets Method

#### Step 1: Create Template Sheet

Create a Google Sheet with these columns:

```
Column A: title (required)
Column B: slug (optional - auto-generated from title)
Column C: excerpt (required)
Column D: content (required)
Column E: author (optional)
Column F: publish_date (format: YYYY-MM-DD)
Column G: featured_image (URL to image)
Column H: tags (comma-separated)
Column I: seo_title (optional)
Column J: seo_description (optional)
Column K: draft (TRUE/FALSE)
```

#### Step 2: Prepare Content

Example row:
```
| Understanding Vault Deposits | understanding-vault-deposits | Learn how vault deposits fund GPU acquisition... | Vault deposits are the foundation... | Alex Chen | 2026-01-15 | https://.../image.jpg | DeFi,Beginners | Vault Deposits Guide | Learn how vault deposits work... | FALSE |
```

#### Step 3: Install Plugin

1. In Framer, open **Plugins** panel (sidebar)
2. Click **+** to browse marketplace
3. Search "Google Sheets Import"
4. Install plugin

#### Step 4: Import

1. Open plugin
2. Paste Google Sheets share URL
3. Plugin auto-detects columns
4. Review mapping
5. Click **Import**
6. Items created as drafts
7. Review in CMS
8. Publish

---

## Content Formatting Tips

### For Google Sheets

**Rich Text (Content Field)**:
- Use markdown syntax in cells:
  - `## Heading 2`
  - `**bold**` 
  - `*italic*`
  - `- list item`
  - `[link text](url)`

**Images**:
- Upload images to Google Drive/Cloudinary
- Use direct image URLs in sheet

**Multiple Tags**:
- Format: `Tag1,Tag2,Tag3` (comma-separated, no spaces)

**Dates**:
- Use ISO format: `2026-01-15`
- Or Sheets date format

### For Notion

**Properties**:
- Title → Title field
- Rich Text → Content field
- Select/Multi-select → Tags
- Date → Publish Date
- Files & Media → Featured Image

**Content**:
- Notion page content imports as formatted text
- Images embedded in content need URLs

---

## Automation Options

### Make.com / Zapier Integration

For true automation (no manual importing):

1. **Trigger**: New row in Google Sheets OR New page in Notion
2. **Action**: Send to Framer CMS via API
3. **Note**: Requires Framer API access (contact Framer for enterprise)

### Webhook Integration

For developers:
- Use Framer's CMS API
- Build custom integration
- Automate from any source

---

## Comparison Table

| Feature | Manual Entry | Google Sheets | Notion |
|---------|--------------|---------------|---------|
| **Setup Time** | None | 10 mins | 15 mins |
| **Ease of Use** | Easy | Easy | Medium |
| **Bulk Import** | No | Yes | Yes |
| **Team Collaboration** | Poor | Good | Excellent |
| **Formatting** | Full WYSIWYG | Markdown | Rich Text |
| **Images** | Direct upload | URL only | URL or upload |
| **Cost** | Free | Free | Free |
| **Best For** | <10 articles | Bulk import | Content teams |

---

## Recommended Approach

### For Your HypurrFi Project

1. **Initial Setup**:
   - Create 3-5 sample articles manually in Framer CMS
   - Test the templates and layouts

2. **Content Strategy**:
   - If writing yourself → Google Sheets
   - If team collaboration → Notion
   - If <20 articles total → Manual entry

3. **Ongoing Workflow**:
   - Draft content in Sheets/Notion
   - Import to Framer as drafts
   - Review in Framer preview
   - Publish

---

## Quick Start: Google Sheets Import

### 5-Minute Setup

1. Create Google Sheet with columns:
   ```
   title | excerpt | content | author | publish_date | tags | draft
   ```

2. Add 2-3 test rows with sample articles

3. Share sheet → "Anyone with the link can view"

4. In Framer:
   - Install "Google Sheets Import" plugin
   - Paste sheet URL
   - Click Import

5. Review imported drafts in CMS

6. Publish test articles

7. Verify pages look correct

8. Ready for bulk import!

---

## Troubleshooting

### Import Errors

**"Column not found"**:
- Check column names match CMS field names exactly
- Use snake_case (lowercase with underscores)

**"Invalid date format"**:
- Use YYYY-MM-DD format
- Or standard Sheets date format

**"Image not loading"**:
- Ensure image URLs are publicly accessible
- Use direct links (not Google Drive share links)
- Consider hosting on Cloudinary or similar

**"Content formatting lost"**:
- Use markdown syntax in Sheets
- Or import plain text and format in Framer

### Best Practices

1. **Always import as drafts first** - Review before publishing
2. **Test with 1-2 articles** before bulk import
3. **Backup your CMS** before major imports
4. **Use consistent formatting** in source documents
5. **Validate all URLs** (images, links) before import

---

## Resources

- [Google Sheets Import Plugin](https://www.framer.com/marketplace/plugins/google-sheets-import-bro0pb4vc2lrb4012vale2qhf/)
- [Notion Import Plugin](https://www.framer.com/marketplace/plugins/notion/)
- [Framer CMS Documentation](https://www.framer.com/help/articles/cms/)
- [Framer University: CMS Automation](https://framer.university/blog/how-i-automate-cms-collections-in-framer)
