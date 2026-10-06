> Fix Google indexing problems: pages crawled but not indexed, discovered but never crawled, soft 404s, canonical conflicts, and sitemaps that mislead.
>
> Source: https://christopherabraham.com/services/indexing/ · Updated 2026-10-06 · By Christopher Abraham

# Indexing repair

A page that isn't indexed can't rank, can't appear in AI Overviews, and is far less likely to be cited by an answer engine. When the Page indexing report in Search Console starts filling with excluded URLs, I find out which ones matter, why they're excluded, and what will bring them back.

## The statuses I untangle

**Crawled, currently not indexed**
Google fetched the page and chose to leave it out. Common causes: content that isn't in the rendered HTML, near-duplicates of stronger pages, thin templates, and weak internal links.

**Discovered, currently not indexed**
Google knows the URL exists but hasn't spent the crawl on it. Usually a sign of too many low-value URLs, slow servers, or pages buried deep in the link structure.

**Alternate page with proper canonical tag**
Fine when it's intended. A problem when a template points every section's canonical at the home page.

**Duplicate, Google chose different canonical than user**
Google overruled your canonical, often because internal links, sitemaps, and redirects disagree with it.

**Soft 404**
A page that returns success but looks empty or missing to Google: out-of-stock products, empty search results, placeholder pages.

**Excluded by noindex, blocked by robots.txt**
Sometimes deliberate, often left over from a staging site or a plugin setting someone forgot.

## How I work through it
1. **Segment.** Group excluded URLs by template and section, so you see that 80% of the problem is one product template rather than 4,000 unrelated pages.
2. **Sample and inspect.** URL Inspection, live tests, and rendered HTML on representative pages from each group.
3. **Find the mechanism.** Missing content after rendering, conflicting canonicals, parameter sprawl, thin variants, or crawl paths that never reach the page.
4. **Decide what deserves an index slot.** Every page doesn't need to be indexed. Some should be consolidated, noindexed, or removed, which frees attention for the ones that earn traffic.
5. **Fix and resubmit.** Correct the templates, sitemaps, and links, then request indexing for priority pages.
6. **Measure by segment.** Separate sitemaps per page type make Search Console report coverage for each group, so progress is visible instead of averaged away.

## Reporting lag

Search Console reports trail reality by days and sometimes weeks. I check the live site and the URL Inspection tool before deciding whether a fix worked, and I tell you which numbers are stale so nobody panics over a chart that hasn't caught up.

## Bing counts too

Bing's index feeds Copilot and several other AI assistants, and Bing Webmaster Tools reports problems Google won't mention. I check both, and I set up IndexNow where your platform supports it, so changes reach Bing within minutes.

## Related

Indexing problems on React, Next.js, and other script-heavy sites are covered under [JavaScript SEO](https://christopherabraham.com/services/javascript-seo/). For a walkthrough of the report itself, read [how to read the Page indexing report](https://christopherabraham.com/guides/page-indexing-report/). A real example: [indexing a 20,000-page programmatic site](https://christopherabraham.com/case-studies/card-price-index/).

Updated October 6, 2026
