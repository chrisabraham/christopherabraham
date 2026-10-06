# christopherabraham.com

Christopher Abraham, independent SEO consultant. Static pages on GitHub Pages: plain HTML with inline CSS and no JavaScript except the Google Analytics 4 tag (consent mode: ad storage off everywhere, analytics cookies off in the EEA, Switzerland, and the UK; see /privacy/). Plone classic look (tabs, slate-blue links), built for legibility and accessibility (black Verdana at 18px, AAA link contrast, visible focus, skip link, labeled landmarks, breadcrumb list, table header scopes, descriptive link text).

This site stands alone: it never names or links to any other site or brand of its owner. `ISLAND` in `tools/build.py` enforces that on every source and generated file.

## Editing

1. Edit the page sources in `src/`. Each file starts with `name:` (menu and breadcrumb label), `title:`, `description:`, `keywords:` (2 to 6 phrases), and `updated:`; guides add `type: guide` and `published:`. Then `---`, then the HTML body. Write `{root}` before internal links, and `{email}`, `{phone}`, `{tel}`, `{upwork}` for contact details (set once at the top of `tools/build.py`).
2. Run `python3 tools/build.py`. It writes every page, a Markdown twin of each (`index.md`), the HTML site map at `/sitemap/`, `404.html`, `sitemap.xml` with its browser stylesheet `sitemap.xsl`, `robots.txt`, `feed.xml` (Atom), `rss.xml` (RSS), `llms.txt`, `llm.txt`, `llms-full.txt`, and `.well-known/security.txt`. Then it checks the house rules:
   - titles 50–60 characters, descriptions 140–160, no pipes, dashes, or hyphens in either, all unique; one h1 per page;
   - the name "Christopher Abraham" only in the titles of Home, About, and Contact;
   - 2 to 6 meta keywords per page, no repeats;
   - minimum word counts (guides 700, services 450, other pages 250); no em dashes; first person singular;
   - no link text that says nothing on its own ("read more", "click here");
   - no links to missing pages;
   - no two pages sharing more than 15% of their phrasing, and no repeated sentence of ten or more words;
   - no page sharing more than 10% of its phrasing with any page of the sibling site checked out next to this repo (`SIBLING` in `tools/build.py`), and no shared sentence of eight or more words (skipped if that folder is absent);
   - the island rule.
3. Commit the sources and the generated files together, and push.

To add a page, create its source file and add it to `FILES` in `tools/build.py` (and to `SERVICE_GROUPS` for a service). Marking up a `<section class="faq">` or a `<dl class="glossary">` produces FAQPage or DefinedTermSet structured data automatically.

Preview locally: `python3 -m http.server`, then open http://localhost:8000

## Search and AI

- Per-page title, description, keywords, canonical, Open Graph, and Twitter card; 1200×630 `social-card.png`.
- JSON-LD on every page: WebSite, ProfessionalService (Arlington, VA 22204, with geo and area served), Person, Place, and the page itself with its own keywords, `about` topics, and a `speakable` selector; plus breadcrumbs, `Service` on service pages, `Article` on case studies, `TechArticle` on guides, `FAQPage` wherever there are questions, `DefinedTermSet` on the glossary, and `ItemList` on section pages.
- `robots.txt` welcomes every crawler and names the AI crawlers explicitly. `llms.txt` and `llm.txt` link to Markdown versions of every page; `llms-full.txt` holds the full text.
- IndexNow: the `<key>.txt` file, `tools/indexnow.py`, and `.github/workflows/indexnow.yml` ping Bing and the other IndexNow engines after each push, once christopherabraham.com really serves this site.

## Going live

The site starts as a noindexed preview at https://chrisabraham.github.io/christopherabraham/ (`LIVE = False`). christopherabraham.com currently sits on Afternic parking nameservers (ns3/ns4.afternic.com) with a null MX and `v=spf1 -all`, so it sends and receives no email; nothing there needs preserving. To go live:

1. Point DNS at GitHub Pages, either at the registrar or by moving the domain to Cloudflare:
   - A @: 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153
   - AAAA @: 2606:50c0:8000::153, 2606:50c0:8001::153, 2606:50c0:8002::153, 2606:50c0:8003::153
   - CNAME www: chrisabraham.github.io
   - Keep the null MX and `v=spf1 -all` TXT records (the domain sends no mail; cja@well.com is the contact).
2. Set `LIVE = True` in `tools/build.py`, rebuild, commit, and push (this writes `CNAME`).
3. In the repo's Settings → Pages, set the custom domain to christopherabraham.com and turn on Enforce HTTPS once the certificate is issued.
4. Verify the domain in Google Search Console (Domain property, DNS TXT) and Bing Webmaster Tools, submit `https://christopherabraham.com/sitemap.xml`, and run the IndexNow workflow once by hand.
