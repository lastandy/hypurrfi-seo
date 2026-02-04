# DNS & Subdomain Setup Guide

## Overview

This guide covers setting up a custom subdomain for your Framer project with proper DNS configuration for SEO optimization.

## Option 1: Custom Subdomain (Recommended)

### Example Structure

```
Main Site: hypurrfi.io (existing)
Blog/Content: learn.hypurrfi.io or blog.hypurrfi.io
```

### DNS Configuration

#### Step 1: Choose Your Subdomain

Common options for educational content:
- `learn.hypurrfi.io` - Clear educational intent
- `blog.hypurrfi.io` - Traditional blog naming
- `resources.hypurrfi.io` - Comprehensive resources
- `academy.hypurrfi.io` - Course-like structure
- `docs.hypurrfi.io` - Documentation focus

**Recommendation**: `learn.hypurrfi.io`

#### Step 2: Configure DNS Records

Add the following DNS record to your domain registrar:

**DNS Record:**
```
Type: CNAME
Name: learn (or your chosen subdomain)
Value: sites.framer.app
TTL: 3600 (or default)
```

**Example Configurations:**

| Registrar | Record Type | Host | Points To | TTL |
|-----------|-------------|------|-----------|-----|
| Cloudflare | CNAME | learn | sites.framer.app | Auto |
| GoDaddy | CNAME | learn | sites.framer.app | 1 Hour |
| Namecheap | CNAME | learn | sites.framer.app | 30 min |
| Route 53 | CNAME | learn | sites.framer.app | 300 |

#### Step 3: Framer Domain Configuration

1. Open your Framer project
2. Click **Publish** (top right)
3. Click **Domains** → **Add Custom Domain**
4. Enter: `learn.hypurrfi.io`
5. Click **Verify**
6. Wait for SSL certificate provisioning (2-5 minutes)

#### Step 4: Verification

Test the setup:
```bash
# Check DNS propagation
nslookup learn.hypurrfi.io

# Expected output should show:
# sites.framer.app
# and your domain
```

**Propagation Time:** 5 minutes to 24 hours (usually within 1 hour)

## Option 2: Subdirectory Setup (Alternative)

If you prefer subdirectory structure (e.g., `hypurrfi.io/learn`):

### Using Reverse Proxy

This requires server-side configuration:

**Nginx Configuration:**
```nginx
server {
    listen 443 ssl;
    server_name hypurrfi.io;
    
    location /learn/ {
        proxy_pass https://yoursite.framer.website/;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

**Note**: Framer's native hosting doesn't support subdirectories. Requires custom server setup.

### Using Framer's Native Approach

Create a path within your main Framer project:
- Set up at: `hypurrfi.io/learn`
- Create `/learn` page for library
- Article pages: `/learn/articles/[slug]`

**Limitation**: All content hosted on same domain, less separation of concerns

## Option 3: Free Framer Subdomain

If not using custom domain yet:

**Default URLs:**
- Production: `hypurrfi-seo.framer.website`
- Staging: `hypurrfi-seo.framer.website?preview=true`

**Alternative Free Subdomains:**
```
hypurrfi-seo.framer.photos
hypurrfi-seo.framer.media
hypurrfi-seo.framer.wiki
```

## SSL/TLS Configuration

Framer automatically provisions SSL certificates for custom domains.

### HTTPS Redirection

Framer handles automatically:
- HTTP → HTTPS redirect
- SSL certificate renewal
- TLS 1.2+ support

### Custom SSL (if needed)

For enterprise requirements:
1. Contact Framer support
2. Provide SSL certificate
3. Configure in Site Settings

## Google Search Console Setup

### Verification Methods

#### Method 1: HTML Tag (Easiest)

1. Go to [Google Search Console](https://search.google.com/search-console)
2. Add property: `learn.hypurrfi.io`
3. Select **URL prefix** method
4. Copy HTML verification tag
5. In Framer: **Site Settings** → **Custom Code** → **Head**
6. Paste the meta tag:
   ```html
   <meta name="google-site-verification" content="YOUR_CODE_HERE" />
   ```
7. Click **Verify** in Search Console

#### Method 2: DNS TXT Record

1. Search Console → **Domain** method
2. Copy TXT record value
3. Add DNS record:
   ```
   Type: TXT
   Name: @
   Value: google-site-verification=YOUR_CODE_HERE
   TTL: 3600
   ```
4. Wait for DNS propagation
5. Click **Verify**

### Sitemap Submission

After verification:

1. Search Console → **Sitemaps**
2. Enter: `sitemap.xml`
3. Click **Submit**

Framer auto-generates at: `https://learn.hypurrfi.io/sitemap.xml`

## SEO Benefits of Subdomain Setup

### Advantages

1. **Clear Separation**: Content distinct from main product site
2. **Focused Authority**: Educational content builds topical authority
3. **Analytics**: Separate tracking for content performance
4. **Scalability**: Easy to expand content independently
5. **Team Management**: Different teams can manage content vs. product

### Potential Considerations

1. **Domain Authority**: Subdomain starts with zero authority (builds over time)
2. **Link Equity**: Internal linking strategy needed to pass authority
3. **Brand Consistency**: Ensure visual consistency with main site

### Internal Linking Strategy

Connect subdomain to main site:

**From Main Site (hypurrfi.io):**
- Footer link: "Learn" → `learn.hypurrfi.io`
- Navigation: Resources dropdown
- Blog/News section link

**From Subdomain (learn.hypurrfi.io):**
- Header: Logo links to main site
- Navigation: "Product" → `hypurrfi.io`
- CTA buttons: "Try HypurrFi" → `hypurrfi.io/app`
- Author bios: Link to team page

**Cross-linking in Content:**
- Articles reference product features
- Product docs link to explanatory articles
- Consistent footer with main site links

## Maintenance & Monitoring

### DNS Health Checks

Monthly verification:
```bash
# Check DNS records
dig learn.hypurrfi.io CNAME

# Verify SSL
curl -I https://learn.hypurrfi.io

# Check redirects
curl -I http://learn.hypurrfi.io
```

### Uptime Monitoring

Set up monitoring for:
- Subdomain availability
- SSL certificate expiration
- Page load times
- 404 errors

**Tools:**
- UptimeRobot (free tier)
- Pingdom
- BetterUptime
- Framer's built-in analytics

### Domain Renewal

- Set calendar reminders
- Enable auto-renewal
- Keep payment methods updated
- Monitor expiration emails

## Troubleshooting

### DNS Not Propagating

**Symptoms**: Site shows "Domain not found" or old content

**Solutions**:
1. Wait 24-48 hours for full propagation
2. Clear local DNS cache:
   - Mac: `sudo dscacheutil -flushcache`
   - Windows: `ipconfig /flushdns`
3. Check with different DNS servers (8.8.8.8, 1.1.1.1)
4. Verify CNAME record is correct

### SSL Certificate Issues

**Symptoms**: Browser shows "Not Secure"

**Solutions**:
1. Wait 5-10 minutes after domain verification
2. Check Framer domain settings
3. Verify domain DNS points to `sites.framer.app`
4. Clear browser cache
5. Try incognito mode

### Mixed Content Warnings

**Symptoms**: HTTPS page loads HTTP resources

**Solutions**:
1. Check all image URLs use HTTPS
2. Verify external embeds use HTTPS
3. Update any hardcoded HTTP links

### Search Console Verification Failed

**Symptoms**: "Verification failed" error

**Solutions**:
1. Ensure meta tag is in `<head>` section
2. Check for typos in verification code
3. Wait for page to be crawled (fetch as Google)
4. Try alternative verification method

## Advanced Configurations

### CDN & Caching

Framer uses Cloudflare automatically:
- Global CDN distribution
- Automatic caching
- DDoS protection
- No additional configuration needed

### Custom Headers (if needed)

For advanced SEO or security headers, contact Framer support for enterprise features.

### Geographic Routing

Framer handles automatically:
- Edge locations worldwide
- Low-latency delivery
- Automatic failover

## Setup Checklist

- [ ] Chosen subdomain name (e.g., `learn.hypurrfi.io`)
- [ ] Added CNAME DNS record
- [ ] Configured custom domain in Framer
- [ ] Verified SSL certificate active
- [ ] Tested site loads correctly
- [ ] Set up Google Search Console
- [ ] Verified domain ownership
- [ ] Submitted sitemap
- [ ] Configured internal linking to main site
- [ ] Set up uptime monitoring
- [ ] Tested mobile responsiveness
- [ ] Verified all pages load over HTTPS

## Post-Launch Tasks

1. **Week 1**:
   - Monitor Search Console for crawl errors
   - Check page indexing status
   - Verify analytics tracking

2. **Week 2-4**:
   - Review Core Web Vitals
   - Check mobile usability
   - Monitor search performance

3. **Ongoing**:
   - Monthly SEO audits
   - Quarterly content reviews
   - Annual domain renewal check

---

## Support Resources

- [Framer Custom Domains Help](https://www.framer.com/help/articles/how-to-connect-a-custom-domain/)
- [Google Search Console Help](https://support.google.com/webmasters)
- [DNSChecker.org](https://dnschecker.org/) - Verify DNS propagation
- [SSL Labs Test](https://www.ssllabs.com/ssltest/) - Check SSL configuration
