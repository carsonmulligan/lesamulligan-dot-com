# Browser LLM Instructions for lesamulligan.com Setup

You are helping set up hosting for Dr. Lesa Mulligan's OBGYN website. The user is logged into both Cloudflare and Namecheap in their browser.

## Current Status
- Website files are ready in local directory
- GitHub repo created: https://github.com/carsonmulligan/lesamulligan-dot-com (private)
- Domain owned: lesamulligan.com (on Namecheap)
- Need to: Deploy to Cloudflare Pages and point DNS

---

## TASK 1: Deploy to Cloudflare Pages

### Option A: Via Cloudflare Dashboard (Recommended)
1. Go to https://dash.cloudflare.com
2. Click **"Workers & Pages"** in left sidebar
3. Click **"Create"** button
4. Select **"Pages"** tab
5. Click **"Connect to Git"**
6. Select **GitHub** and authorize if needed
7. Find and select repository: **carsonmulligan/lesamulligan-dot-com**
8. Configure build settings:
   - **Project name:** `lesamulligan-dot-com`
   - **Production branch:** `main`
   - **Build command:** (leave empty - static site)
   - **Build output directory:** `/` or `.` (root)
9. Click **"Save and Deploy"**
10. Wait for deployment to complete (~1-2 minutes)

### Option B: Via Wrangler CLI
User will run in terminal:
```bash
wrangler login
wrangler pages deploy . --project-name lesamulligan-dot-com
```

---

## TASK 2: Add Custom Domain to Cloudflare Pages

1. In Cloudflare dashboard, go to **Workers & Pages**
2. Click on project **lesamulligan-dot-com**
3. Go to **"Custom domains"** tab
4. Click **"Set up a custom domain"**
5. Enter: `lesamulligan.com`
6. Click **"Continue"**
7. Also add: `www.lesamulligan.com`
8. Note the DNS records Cloudflare shows you

---

## TASK 3: Update Namecheap DNS

### Go to Namecheap:
1. Visit https://www.namecheap.com
2. Go to **Dashboard** → **Domain List**
3. Click **"Manage"** next to **lesamulligan.com**
4. Click **"Advanced DNS"** tab

### Delete OLD records:
- Delete: `CNAME | www | parkingpage.namecheap.com`
- Delete: `URL Redirect | @ | http://www.lesamulligan.com/`

### Add NEW records:

| Type | Host | Value | TTL |
|------|------|-------|-----|
| CNAME | @ | lesamulligan-dot-com.pages.dev | Automatic |
| CNAME | www | lesamulligan-dot-com.pages.dev | Automatic |

**Note:** If CNAME on @ (root) doesn't work, you may need to use Cloudflare's nameservers instead (see Alternative below).

---

## ALTERNATIVE: Use Cloudflare Nameservers (Better Option)

This gives you more control and Cloudflare's CDN benefits.

### In Cloudflare:
1. Go to https://dash.cloudflare.com
2. Click **"Add a site"** (top right)
3. Enter: `lesamulligan.com`
4. Select **Free** plan
5. Cloudflare will scan DNS and show nameservers like:
   - `aria.ns.cloudflare.com`
   - `blake.ns.cloudflare.com`
6. Copy these nameserver addresses

### In Namecheap:
1. Go to **Domain List** → **lesamulligan.com** → **Domain** tab
2. Find **"Nameservers"** section
3. Change from "Namecheap BasicDNS" to **"Custom DNS"**
4. Enter the two Cloudflare nameservers
5. Click green checkmark to save
6. Wait 1-48 hours for propagation (usually faster)

### Back in Cloudflare:
1. Once nameservers propagate, go to **DNS** settings
2. Add these records:

| Type | Name | Content | Proxy |
|------|------|---------|-------|
| CNAME | @ | lesamulligan-dot-com.pages.dev | Proxied |
| CNAME | www | lesamulligan-dot-com.pages.dev | Proxied |

---

## TASK 4: Verify SSL/HTTPS

1. In Cloudflare Pages → Custom domains
2. Wait for SSL status to show **"Active"** (1-15 minutes)
3. Test: https://lesamulligan.com

---

## TASK 5: Submit to Search Engines

### Google Search Console
1. Go to https://search.google.com/search-console
2. Click **"Add property"**
3. Choose **"URL prefix"**
4. Enter: `https://lesamulligan.com`
5. Verify ownership (Cloudflare DNS or HTML file)
6. Once verified, go to **Sitemaps** section
7. Submit: `https://lesamulligan.com/sitemap.xml`

### Bing Webmaster Tools
1. Go to https://www.bing.com/webmasters
2. Add site: `https://lesamulligan.com`
3. Submit sitemap

### Google Business Profile
1. Go to https://business.google.com
2. Search for "Dr. Lesa Mulligan Norman Oklahoma"
3. Claim/update the listing
4. Update website URL to: `https://lesamulligan.com`

---

## Verification Checklist

After setup, verify these URLs work:
- [ ] https://lesamulligan.com
- [ ] https://www.lesamulligan.com
- [ ] https://lesamulligan.com/robots.txt
- [ ] https://lesamulligan.com/llm.txt
- [ ] https://lesamulligan.com/sitemap.xml
- [ ] https://lesamulligan.com/ai.txt
- [ ] https://lesamulligan.com/feed.xml

---

## Quick Reference

**Domain:** lesamulligan.com
**GitHub:** https://github.com/carsonmulligan/lesamulligan-dot-com
**Cloudflare Pages URL:** lesamulligan-dot-com.pages.dev (after deploy)
**Business Phone:** (405) 364-0643
**Address:** 1139 NW 36th St Suite 100, Norman, OK 73072
