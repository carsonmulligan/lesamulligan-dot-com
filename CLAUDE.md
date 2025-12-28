# Claude Instructions

Static website for OBGYN practice. Optimized for search engines and AI crawlers.

## Key Files

- `index.html` - Single page with all content, Schema.org markup
- `llm.txt` - Primary file for LLM context (markdown format)
- `ai.txt` - Machine-readable business data (key-value format)
- `.llm/` - Internal docs: setup instructions, logo prompts

## Business Info

- **Name:** Dr. Lesa Mulligan, MD
- **Specialty:** Obstetrics & Gynecology
- **Location:** 1139 NW 36th St Suite 100, Norman, OK 73072
- **Phone:** (405) 364-0643
- **Site:** lesamulligan.com

## When Editing

- Keep SEO meta tags in sync with content changes
- Update `sitemap.xml` lastmod dates after changes
- Update Schema.org JSON-LD if business info changes
- Run `wrangler pages deploy .` after changes

## Deploy

```bash
wrangler pages deploy . --project-name lesamulligan-dot-com
```
