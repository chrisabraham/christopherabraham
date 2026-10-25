> A technical SEO skills list where each line links to evidence: rendering forensics, pull requests, crawl automation, redirects, schema, AI search, and servers.
>
> Source: https://christopherabraham.com/about/skills/ · Updated 2026-10-24 · By Christopher Abraham

# Technical SEO skills, and the proof for each one

"Technical SEO" on a profile can mean anything from installing a plugin to rebuilding a rendering pipeline. So here's my list, specific enough to check. Every skill below is something I've done on a real site, and wherever I can show it, it links to the case study or guide that proves it. My full career history lives in my [CV on chrisabraham.com](https://chrisabraham.com/cv); this page is the technical inventory.

## Crawling and auditing whole sites
- Full site crawls in Screaming Frog with JavaScript rendering, run in raw and rendered modes and compared, so I can see which content exists only after scripts run.
- Custom extraction with XPath and regex to audit every URL for heading counts, canonicals, robots tags, schema types, and tracking IDs. My [extraction recipes](https://christopherabraham.com/guides/custom-extraction/) are published.
- Near-duplicate detection and multiple H1 audits across entire sites, with a decision per cluster. See [how I find both](https://christopherabraham.com/guides/near-duplicates-and-h1s/).
- XML sitemap audits that compare the file, a crawl, and Search Console, so every listed URL is canonical, indexable, and dated honestly. My checklist is in [XML sitemaps that tell the truth](https://christopherabraham.com/guides/xml-sitemaps/).
- Before-and-after crawl comparisons to prove a fix landed on every URL, described in [proving an SEO fix worked](https://christopherabraham.com/guides/prove-seo-fixes/).
- Crawl and index management for a programmatic site of more than 20,000 pages: segmented sitemaps, robots rules for parameter URLs, and baselines per segment. [Programmatic price index](https://christopherabraham.com/case-studies/card-price-index/).

## JavaScript rendering forensics
- Traced a Magento and Hyvä store's traffic loss to Alpine.js sections that loaded specs, FAQs, and reviews only on scroll, and proved it with crawler extraction counts. [Hidden product content](https://christopherabraham.com/case-studies/scroll-gated-products/).
- Found 2,000 event pages Google never discovered in a Create React App build, and wrote the 13 page developer spec, ranked P0 to P3, that fixed it. [React event app](https://christopherabraham.com/case-studies/event-app-links/).
- Diagnosed a consent platform that blocked the script displaying every article, so bots saw empty pages. [Consent banner case](https://christopherabraham.com/case-studies/consent-banner/).
- Hunted hydration errors sitewide by loading every URL in scripted headless Chrome and collecting console errors by template.

## Working in the code
- Hacked Perl and PHP by the bucketful long before AI coding assistants: Movable Type's Perl CGI scripts, PHP-Nuke and PostNuke portals, and scripts of my own. Reading somebody else's codebase has felt like home ever since.
- Made metadata changes in a client's Sanity and Vercel codebase through a GitHub pull request the developer reviewed and merged, then verified prerendering. [Headless local business](https://christopherabraham.com/case-studies/headless-local/).
- Read whole repositories with OpenAI Codex and Claude Code to trace a crawl finding to the component or import script that causes it, checking every answer against the live site.
- Built SEO checks into the build of sites I run, so a page with a bad title, a duplicate description, a broken internal link, or borrowed phrasing fails before it publishes. That's how this site is built.
- Turned a podcast RSS feed into a static site that rebuilds itself every day, with a page, share card, and alt text for each of 458 episodes. [Podcast site](https://christopherabraham.com/case-studies/podcast-site/).
- Automated IndexNow submissions with GitHub Actions, gated on the new sitemap actually being live.
- Built a 12,000 line command line assistant in Python with 140 end-to-end tests, directing Claude Code the way a technical lead directs a team.

## Migrations, redirects, and recovery
- Audited a Squarespace to Shopify move that left 3,400 broken URLs and duplicate product paths, and did the theme schema work. [Shopify cleanup](https://christopherabraham.com/case-studies/shopify-cleanup/).
- Rebuilt the redirect map for a site that had lived on three platforms over fourteen years, by pulling every URL the Wayback Machine ever captured, testing all 848 against the live site, and redirecting every one that had ever served a page.
- Moved my own 17 year Movable Type blog to static hosting with all 953 of its old addresses still answering, three feed formats and the TrackBack files included. [Movable Type novel](https://christopherabraham.com/case-studies/movable-type-novel/).
- Diagnosed a WooCommerce store's loss of indexing, traffic, and AI referrals after its SEO plugin was switched off, and checked the recovery. [Plugin outage](https://christopherabraham.com/case-studies/plugin-outage/).

## Schema, entities, and AI search
- Separated a multi-state brand from its first showroom in schema and on the page, so search engines stopped blurring the two. [Closet locations](https://christopherabraham.com/case-studies/closet-locations/).
- Fixed a gym whose brand name Google read as an ordinary word, which lifted calls and visits. [Training gym](https://christopherabraham.com/case-studies/training-gym/).
- Audited how ChatGPT and Perplexity described an AI company's jobs and pay, and planned the fix. [Recruiting answers](https://christopherabraham.com/case-studies/recruiting-answers/).
- Built JSON-LD graphs, llms.txt files, Markdown twins of every page, and full-text feeds for AI crawlers, on this site and others I run.

## Servers, DNS, and email
- Got my first root access on a Sun SPARCstation running Solaris, the pizza box kind, as the image lab administrator at PNI, Picture Network International.
- Ran Linux servers and built on Apache, MySQL, Perl, and PHP for years before anyone called that combination the LAMP stack, right up until my SEO career began in 2002.
- Revived a stalled Node application on a DigitalOcean server over SSH: read the logs, fixed the configuration, managed it with PM2, and found the port conflict keeping it down.
- Administer my own Debian servers with key only SSH, firewalls, and unattended security updates.
- Moved domains to Cloudflare DNS without breaking Google Workspace mail, and set up SPF, DKIM, and DMARC. See [protecting a domain that sends no mail](https://christopherabraham.com/guides/non-sending-domain/).

## Email and Google Workspace
- Run Google Workspace administration end to end: users, aliases, groups, Gmail routing, Calendar, and Drive sharing.
- Know mail from the server up: Sendmail on Linux, IMAP and POP3, SMTP ports, and the DNS records that tell the world where your mail lives and who may send it.
- Diagnose mail that bounces or lands in spam, and lock down domains that never send mail so nobody can borrow their names, as in [protecting a domain that sends no mail](https://christopherabraham.com/guides/non-sending-domain/).

## Local search and Google Business Profile
- Got a suspended profile reinstated with a documented appeal. [Profile reinstated](https://christopherabraham.com/case-studies/profile-reinstated/).
- Rescue profiles stuck in failed verification: reconcile the listing with the real business and its paperwork, then script the owner's one-take video so it shows every proof Google asks for. My [video verification checklist](https://christopherabraham.com/guides/gbp-video-verification/) is published.
- Build appeals like a legal brief: the most authoritative document first, nothing that exposes private data, and no date claimed that the paperwork doesn't support.

## Data
- Wrote Python pipelines that built an 88,900 contact master list, merged two 28,800 record exports at 94% email coverage, and caught an AI-built tracker inventing its data.

## Strengths that don't fit on a skills list

These are habits, not tools, and they shape every engagement.
- **I keep two problems apart.** When a traffic loss and a spam spike land in the same month, I run them as separate investigations until the evidence connects them, so nobody spends a quarter fixing the wrong thing. It's built into every [technical SEO audit](https://christopherabraham.com/services/seo-audit/).
- **I catch AI tools inventing things.** I use AI every day and trust none of it unchecked, which is how I caught an AI-built outreach tracker logging messages to contacts who didn't exist. My guide to [correcting what AI says about you](https://christopherabraham.com/guides/correct-ai-answers/) comes from the same habit.
- **I build a case like a brief.** I captained my high school speech and debate team, and my Google appeals still read that way: the strongest document first, nothing that exposes private information, and no date claimed without paper behind it. That's how a [suspended profile came back](https://christopherabraham.com/case-studies/profile-reinstated/).
- **I vet sources for a living.** At Edelman my job included checking online influencers for a genuine, multi-year track record before clients went near them. I bring the same suspicion to every crawl export, vendor dashboard, and confident AI answer.
- **I write for the developer and the owner at once.** The same finding becomes a ranked ticket with acceptance criteria for engineering and a plain summary for the person paying, as in the [13-page spec for a React app](https://christopherabraham.com/case-studies/event-app-links/).
- **I ship at speed without dropping the checks.** This site went from first commit to 75 pages and more than 50,000 words in a week, built with Claude Code under my direction, and every page passes automated checks for title and description length, duplicate wording, broken links, and voice before it publishes.
- **I've made myself machine readable.** Two decades of publishing under one name, tied together with structured data so search engines and AI tools know the profiles belong to one person. The method is in [two names, one entity](https://christopherabraham.com/guides/two-names-one-entity/).
- **I know how online communities behave from the inside.** I moderate a Reddit community of more than 16,000 runners and have for nine years, and Reddit threads turn up constantly in AI answers. The story is [off the clock](https://christopherabraham.com/about/off-the-clock/).

## Platforms

WordPress with Yoast, Rank Math, Elementor, and WooCommerce; Shopify and Liquid; Magento 2 and Hyvä; Umbraco; Drupal; Squarespace; Wix; Webflow; Next.js, React, and Create React App; Sanity; Vercel, Netlify, Cloudflare, and GitHub Pages; Jekyll and hand-built Python generators; and Plone on the Zope application server, which I've run since the early 2000s.

## Tools

OpenAI Codex and Claude Code are my main coding assistants. I also use GitHub Copilot, Gemini, and Grok, with Perplexity on occasion. I choose tools for the work at hand and check their output against the code, the crawl, and the published page.

Screaming Frog SEO Spider, Google Search Console and its APIs, Bing Webmaster Tools, GA4, Semrush, PageSpeed Insights and the Chrome UX Report, Playwright, OpenAI Codex, Claude Code, GitHub Copilot, Gemini, Grok, Perplexity, Git and GitHub, GitHub Actions, Python, and the command line.

## What I don't do

Paid search and paid social. Everything here is organic.

Want this on your site? [Send me the URL and the problem](https://christopherabraham.com/contact/), or see how I work on [Hire Me](https://christopherabraham.com/hire-me/). The longer story is on the [About page](https://christopherabraham.com/about/), and the full bio is at [chrisabraham.com/bio](https://chrisabraham.com/bio).

Updated October 24, 2026
