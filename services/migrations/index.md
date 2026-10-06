> Plan and verify a website migration: full URL inventories, one to one 301 redirect maps, launch day checks, and recovery when a move has already lost traffic.
>
> Source: https://christopherabraham.com/services/migrations/ · Updated 2026-10-06 · By Christopher Abraham

# Site migrations and 301 redirects

A migration is the single riskiest thing most websites ever do. A new platform, a new domain, or a redesign that changes URLs can erase years of search equity in a weekend. I plan the move so that every old URL lands somewhere sensible, check it on launch day, and stay on watch until rankings settle.

## Kinds of moves I handle
- Platform changes: WordPress to Shopify, Squarespace to Shopify, WordPress to Next.js on Netlify or Vercel, Magento upgrades, and more.
- Domain changes, mergers of several domains into one, and HTTP to HTTPS or www to apex consolidation.
- Redesigns that change URL structure, navigation, or templates.
- Hosting and CDN moves, including DNS cutovers to Cloudflare.
- Recovery after a migration that has already lost traffic.

## Before launch
1. **Inventory every URL that matters.** From crawls, XML sitemaps, Search Console, analytics, and backlink data, so pages with links or traffic aren't missed just because they're no longer in the menu.
2. **Map each one.** A one-to-one 301 to the closest equivalent page. Pages that are going away get a deliberate decision: redirect to a true replacement, or return 410.
3. **Carry the signals across.** Titles, descriptions, headings, structured data, internal links, hreflang, and canonical rules rebuilt on the new templates.
4. **Check staging.** Crawl the new site before launch, with the redirect map tested against it, while blocking staging from being indexed.

## Launch day
- Redirects tested in bulk against the live site, with chains and loops removed.
- Robots rules and noindex tags checked, since staging settings that reach production are a common disaster.
- New sitemaps submitted in Search Console and Bing Webmaster Tools; Change of Address filed for domain moves.
- Analytics and Search Console verified on the new setup.

## After launch

I monitor 404s, crawl stats, indexing, and rankings by page group for the following weeks, and I keep the problems the migration caused apart from problems the site already had, so the new platform isn't blamed for old faults or credited with fixing them. Media still loading from the old host, broken image CDNs, and lost structured data are common late discoveries.

## Who owns what

Migrations involve a developer, a host, often a designer, and sometimes an agency. I write down who owns each step: who exports the old URLs, who loads the redirect map, who flips DNS, who files Change of Address. A one-page runbook with names and times prevents the most common launch-day failure, which is everyone assuming someone else handled it.

## When the move already happened

If traffic fell after a migration, the old site is usually the best evidence. I reconstruct the old URL set from archives, logs, and analytics, rebuild the redirect map, and prioritize the pages that carried the most traffic and links.

My rules for redirects are in [ten rules for 301 redirects](https://christopherabraham.com/guides/redirect-rules/). Examples: [a clinic's move from WordPress to Next.js](https://christopherabraham.com/case-studies/clinic-migration/) and [cleaning up after a Squarespace to Shopify move](https://christopherabraham.com/case-studies/shopify-cleanup/).

Updated October 6, 2026
