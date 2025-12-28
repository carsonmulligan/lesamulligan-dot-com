# lesamulligan.com

Static website for Dr. Lesa Mulligan MD, board-certified OBGYN in Norman, Oklahoma.

## Quick Start

```bash
# Deploy to Cloudflare Pages
wrangler pages deploy . --project-name lesamulligan-dot-com
```

## Structure

```
├── index.html          # Main page
├── styles.css          # Styles
├── robots.txt          # Search engine crawlers
├── llm.txt             # LLM/AI crawlers
├── ai.txt              # Machine-readable business data
├── sitemap.xml         # SEO sitemap
├── feed.xml            # RSS feed
├── humans.txt          # Human-readable info
├── assets/             # Images and logos
├── .well-known/        # Security and AI plugin manifests
└── .llm/               # Setup docs and logo prompts
```

## SEO & AI Optimization

- `robots.txt` - Allows all crawlers (Google, Bing, GPTBot, Claude, Perplexity, etc.)
- `llm.txt` - Structured markdown for LLM consumption
- `ai.txt` - Machine-readable key-value business data
- Schema.org JSON-LD in HTML (Physician, MedicalBusiness)

## Hosting

Cloudflare Pages at `lesamulligan-dot-com.pages.dev`

Custom domain: `lesamulligan.com`

## Contact

Dr. Lesa Mulligan MD
1139 NW 36th St Suite 100
Norman, OK 73072
(405) 364-0643
