# christopherabraham.com

This repository builds https://christopherabraham.com, live since October 6, 2026. For who Christopher Abraham is and what he does, read the site; this file only explains how the site is built.

Christopher Abraham, independent SEO consultant. Static pages on GitHub Pages: plain HTML with inline CSS and no JavaScript except a Google Analytics 4 tag that loads after the reader's first scroll or tap (consent mode: ad storage off everywhere, analytics cookies off in the EEA, Switzerland, and the UK; see /privacy/) and a speculation rule that prefetches the next page. Plone classic look (tabs, slate-blue links), built for legibility and accessibility (black Verdana at 18px, AAA link contrast, visible focus, skip link, labeled landmarks, breadcrumb list, table header scopes, descriptive link text).

This site stands on its own: it links to Upwork and Calendly, and "Chris" is fine, but it never names or links the owner's other sites and brands. `ISLAND` in `tools/build.py` enforces that on every source and generated file.

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
   - no page sharing more than 10% of its phrasing with any page of the sibling site checked out next to this repo (`SIBLING` in `tools/build.py`, or `SIBLING_DIR`), and no shared sentence of eight or more words. The build fails if that checkout is missing; the build workflow checks it out itself;
   - the island rule.
3. Commit the sources and the generated files together, and push.

To add a page, create its source file and add it to `FILES` in `tools/build.py` (and to `SERVICE_GROUPS` for a service). Marking up a `<section class="faq">` or a `<dl class="glossary">` produces FAQPage or DefinedTermSet structured data automatically.

Preview locally: `python3 -m http.server`, then open http://localhost:8000

## Search and AI

- Per-page title, description, keywords, canonical, Open Graph, and Twitter card; 1200×630 `social-card.png`.
- JSON-LD on every page: WebSite, ProfessionalService (Arlington, VA 22204, with geo and area served), Person, Place, and the page itself with its own keywords, `about` topics, and a `speakable` selector; plus breadcrumbs, `Service` on service pages, `Article` on case studies, `TechArticle` on guides, `FAQPage` wherever there are questions, `DefinedTermSet` on the glossary, and `ItemList` on section pages.
- `robots.txt` welcomes every crawler and names the AI crawlers explicitly. `llms.txt` and `llm.txt` link to Markdown versions of every page; `llms-full.txt` holds the full text.
- IndexNow: the `<key>.txt` file, `tools/indexnow.py`, and `.github/workflows/indexnow.yml` ping Bing and the other IndexNow engines after each push.

## Live

The site went live on christopherabraham.com on October 6, 2026 (`LIVE = True` in `tools/build.py`, custom domain set in the repo's Pages settings, HTTPS enforced). The github.io address redirects to it. The domain sends no email: it keeps a null MX and `v=spf1 -all`, and cja@well.com is the contact.


## Guides syndication

`/rss.xml` and `/feed.xml` contain every Guide, with full HTML article content,
stable source URL identifiers, publication and revision dates, and absolute
links and image addresses. RSS uses `content:encoded`; Atom uses HTML content.
Entries are sorted by revision date, newest first. For Plone, import the RSS URL
and test one entry before enabling scheduled ingestion. Attribution and any
canonical setting must be configured in the destination CMS.

The IndexNow workflow waits for the public sitemap to match the repository's
intended inventory before submitting. A key that already exists is insufficient
to prove that a new release has deployed. API acceptance is not indexing proof.


## Guide section navigation

Guides with at least 700 words and four main sections receive a collapsible
"On this page" list after the introduction. `tools/guide_navigation.py` adds
section IDs while rendering HTML; editorial sources, Markdown twins, and
syndication feeds keep their original content. Existing heading IDs are retained.
To keep a shared section URL stable when renaming a heading, give that source
heading an explicit `id` before changing its wording.
