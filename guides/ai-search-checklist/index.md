> A practical checklist for AI search: crawler access, server rendered content, entity schema, answer shaped pages, llms.txt, outside evidence, and measurement.
>
> Source: https://christopherabraham.com/guides/ai-search-checklist/ · Updated 2026-10-06 · By Christopher Abraham

# The AI search readiness checklist

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 6, 2026

AI assistants answer questions by retrieving pages, reading them quickly, and quoting what's clear. This checklist covers what has to be true for your site to be retrieved, understood, and cited. Work through it in order; the early items block everything after them.

## 1. Can AI crawlers reach you?
- **robots.txt** allows the crawlers you want. The main ones: GPTBot and OAI-SearchBot (OpenAI), ClaudeBot and Claude-SearchBot (Anthropic), PerplexityBot, Google-Extended (Gemini training), Applebot-Extended, Bingbot (which also feeds Copilot), and CCBot (Common Crawl).
- **Your CDN and firewall** let them through. Cloudflare, Sucuri, and hosting firewalls can block AI crawlers by default, regardless of robots.txt. Check the setting and check the logs.
- **Pages respond quickly** and without errors. Retrieval systems working against a time limit skip slow pages.

Blocking AI crawlers is a legitimate business choice. Just make it deliberately, knowing that a blocked site can't be cited.

## 2. Is your content in the HTML?
- Fetch a key page with scripts turned off, or use "View source." Is the main text there?
- No important content hidden behind tabs, accordions, or "load more" buttons that require JavaScript to populate.
- Prices, specifications, hours, and addresses in text, not only in images or PDFs.

Googlebot renders JavaScript. Most AI crawlers don't. If the answer isn't in the HTML, most assistants will never see it.

## 3. Do machines know who you are?
- **Organization or LocalBusiness schema** on the home page, with your legal name, logo, address, phone, and founding date.
- **sameAs links** from that schema to your official profiles: LinkedIn, Crunchbase, Wikipedia or Wikidata if you have them, and major directories.
- **Person schema** for founders and authors whose expertise matters.
- **One description, everywhere.** The same name, the same one-sentence description, and the same facts on your site, your profiles, and directories.
- An **About page** that states plainly who you are, what you do, where, since when, and for whom.

## 4. Is your content shaped like an answer?
- Each important page opens with a direct, one- or two-sentence answer to its main question.
- Sections are self-contained. A paragraph pulled out alone still makes sense, without "as mentioned above."
- Terms are defined where they're used. A glossary page helps.
- Specific numbers, dates, and names are stated rather than implied: prices, sizes, service areas, years.
- FAQs are written around questions your customers actually ask, with the answers visible on the page.
- Comparison pages are fair. Assistants are more willing to cite a balanced comparison than a sales pitch.
- Pages show who wrote them and when they were last updated.

## 5. Have you published files for machines?
- **XML sitemap** with accurate last-modified dates, submitted to Google and Bing.
- **IndexNow** enabled, so Bing learns about changes within minutes.
- **llms.txt** at your site root: a short Markdown summary of who you are with links to your most important pages. It's an emerging convention, inexpensive to add, and some AI tools already read it.
- Optionally, clean Markdown versions of key pages linked from llms.txt.

## 6. Does the rest of the web agree?
- Your Google Business Profile, Bing Places listing, and Apple Business Connect are complete and consistent.
- Industry directories and review sites list current information.
- You know which third-party pages assistants cite when they answer questions in your category, and whether you appear on them.
- Outdated or wrong information elsewhere has been corrected at the source where possible.

## 7. Are you measuring it?
- A fixed set of 20 to 50 prompts your buyers would ask, run across ChatGPT, Perplexity, Gemini, Claude, Copilot, and Google's AI Overviews.
- The same prompts repeated monthly. Answers vary, so trends matter more than any single answer.
- For each run: whether you appear, how you're described, whether facts are correct, and which sources are cited.
- AI assistant referrals segmented in GA4, using referrers such as chatgpt.com, perplexity.ai, gemini.google.com, and copilot.microsoft.com.

## Where to start

If you only do three things this month, make them these: confirm crawlers can reach you, confirm your main content is in the HTML, and make your About page and Organization schema say exactly who you are. Everything else builds on those.

For help running the checklist against your own site, see [AI SEO, GEO, and AEO](https://christopherabraham.com/services/ai-search/). Terms used here are defined in the [glossary](https://christopherabraham.com/guides/glossary/).

## Sources
- [Google Search Central: AI features and your website](https://developers.google.com/search/docs/appearance/ai-features)
- [OpenAI: Overview of OpenAI crawlers](https://platform.openai.com/docs/bots)
- [Google Search Central: Introduction to robots.txt](https://developers.google.com/search/docs/crawling-indexing/robots/intro)
- [The llms.txt proposal](https://llmstxt.org/)
- [IndexNow](https://www.indexnow.org/)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
