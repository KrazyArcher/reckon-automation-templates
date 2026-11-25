# ReckonSEO — Active Distribution Pack (Reddit, LinkedIn, Clay & n8n)

## 1. Reddit Post (r/n8n & r/coldemail — Case Study Style, Zero Hard Sell)
**Title:** Built an automated pipeline that audits local business sites in ~10s (SSL, mobile leaks, SEO, AI-search/GEO) + generates white-label PDF reports

**Body:**
When scraping local businesses from Google Maps, the biggest time sink is manually checking which websites are actually broken or leaking leads before sending outreach.

I packaged a lightweight Python auditor on Apify (`KrazyArcher/reckonseo-auditor`) that connects directly to n8n or Clay via one HTTP call:
- **Infra & Security:** Expired SSL + days left, HTTP->HTTPS redirect, parked domains, slow TTFB, passive WordPress exposures (`xmlrpc.php`, exposed `/wp-json/wp/v2/users`)
- **Conversion Leaks:** Missing mobile viewport, missing quote form / `tel:` link, thin content
- **Technical SEO + AI-Search (GEO):** Missing `sitemap.xml`, duplicate titles, broken internal 404s, missing JSON-LD schema, `robots.txt` AI-bot blocks (`GPTBot`, `ClaudeBot`, `PerplexityBot`), `/llms.txt`
- **Outputs:** Deterministic 0–100 Health & Opportunity score (so healthy sites are auto-filtered out), extracted email/phone/socials, and a white-label HTML + PDF client report with your agency name.

Happy to share the n8n JSON workflow template in the comments if anyone wants to plug it after Google Maps Scraper.

---

## 2. LinkedIn Post (Agency Founders & Freelancers)
Most cold emails fail because people pitch "website redesigns" to businesses whose sites work fine.

When we audited 12 US local contractor sites automatically this week:
- 4 were actually healthy (auto-filtered out — saved wasted outreach)
- 1 had a broken SSL certificate throwing Chrome warnings
- 1 had 12 verified issues: no mobile viewport, no quote form, no click-to-call, missing sitemap, duplicate page titles, and zero JSON-LD schema

We turned that exact audit engine into **ReckonSEO** on Apify — ~10s per site, plugs straight into n8n/Clay, and exports a white-label PDF report you can attach directly to outreach.

Drop "WORKFLOW" if you want the free n8n JSON template to connect it to your lead list.

---

## 3. Clay HTTP API Setup (1-Step Enrichment)
- **Endpoint:** `POST https://api.apify.com/v2/acts/KrazyArcher~reckonseo-auditor/run-sync-get-dataset-items?token=YOUR_APIFY_TOKEN`
- **Body:** `{"urls": ["{{Website}}"], "brandName": "Your Agency", "maxPagesPerSite": 5, "generateReports": true}`
- **Map Columns:** `scores.leak_tier`, `scores.opportunity_score`, `email`, `cms`, `outreach_pitch.subject`, `outreach_pitch.body`