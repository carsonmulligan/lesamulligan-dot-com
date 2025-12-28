# Cloudflare + Namecheap Setup Instructions

## Step 1: Deploy to Cloudflare Pages (CLI)

Run these commands in your terminal:

```bash
# Login to Cloudflare (opens browser)
wrangler login

# Create and deploy the Pages project
wrangler pages project create lesamulligan-dot-com --production-branch main

# Deploy the site
wrangler pages deploy . --project-name lesamulligan-dot-com
```

After deployment, Cloudflare will give you a URL like: `lesamulligan-dot-com.pages.dev`

## Step 2: Add Custom Domain in Cloudflare (Browser)

1. Go to https://dash.cloudflare.com
2. Click on "Pages" in the sidebar
3. Click on your project "lesamulligan-dot-com"
4. Go to "Custom domains" tab
5. Click "Set up a custom domain"
6. Enter: `lesamulligan.com`
7. Click "Continue"
8. Cloudflare will show you the DNS records needed

## Step 3: Update Namecheap DNS (Browser)

Go to Namecheap > Domain List > lesamulligan.com > Advanced DNS

**DELETE these existing records:**
- CNAME Record: www -> parkingpage.namecheap.com
- URL Redirect Record: @ -> http://www.lesamulligan.com/

**ADD these new records:**

| Type | Host | Value | TTL |
|------|------|-------|-----|
| CNAME | @ | lesamulligan-dot-com.pages.dev | Auto |
| CNAME | www | lesamulligan-dot-com.pages.dev | Auto |

**OR use Cloudflare Nameservers (Recommended):**

1. In Cloudflare, go to Websites > Add a Site > Enter lesamulligan.com
2. Select Free plan
3. Cloudflare will give you 2 nameservers like:
   - `aria.ns.cloudflare.com`
   - `blake.ns.cloudflare.com`
4. In Namecheap, go to Domain List > lesamulligan.com > Domain
5. Under "Nameservers", select "Custom DNS"
6. Enter the two Cloudflare nameservers
7. Click the green checkmark to save

## Step 4: Verify SSL/HTTPS

1. In Cloudflare Pages > Custom domains
2. Wait for SSL certificate to be issued (usually 1-15 minutes)
3. Status should show "Active"

## Step 5: Test Your Site

Visit these URLs to verify:
- https://lesamulligan.com
- https://www.lesamulligan.com
- https://lesamulligan.com/robots.txt
- https://lesamulligan.com/llm.txt
- https://lesamulligan.com/sitemap.xml

## CLI Quick Reference

```bash
# Re-deploy after changes
wrangler pages deploy . --project-name lesamulligan-dot-com

# View deployment logs
wrangler pages deployment list --project-name lesamulligan-dot-com

# View project info
wrangler pages project list
```

## Submit to Search Engines

After your site is live, submit it to:

1. **Google Search Console**: https://search.google.com/search-console
   - Add property > URL prefix > https://lesamulligan.com
   - Submit sitemap: https://lesamulligan.com/sitemap.xml

2. **Bing Webmaster Tools**: https://www.bing.com/webmasters
   - Add site > Submit sitemap

3. **Yandex Webmaster**: https://webmaster.yandex.com

4. **Google Business Profile**: https://business.google.com
   - Update website URL to lesamulligan.com
