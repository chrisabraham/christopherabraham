> Find near-duplicate pages and heading problems across an entire site with Screaming Frog, then decide which pages to rewrite, merge, redirect, or canonicalize.
>
> Source: https://christopherabraham.com/guides/near-duplicates-and-h1s/ · Updated 2026-10-13 · By Christopher Abraham

# How to find near-duplicate pages and multiple H1s across a whole site

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 13, 2026

Two findings turn up in almost every full crawl I run: clusters of pages that say nearly the same thing, and headings that don't describe the page. Neither can be judged one URL at a time. Here is how I find both across every page, and how I decide what to do about each.

## Crawl the rendered page, not only the source

Set Screaming Frog to JavaScript rendering under Configuration > Spider > Rendering before you start. On sites built with React, Next.js, or a page builder, the H1 a browser shows can differ from the one in the raw HTML. A component may replace it after load, or a script may inject a second one. If you crawl only the source, you're auditing a page nobody sees.

## Turn on near-duplicate detection

Screaming Frog finds exact duplicates by default. Near duplicates need switching on, under Configuration > Content > Duplicates, which tells the crawler to store each page's text. The default similarity threshold is 90%, and you can lower it to cast a wider net. By default it compares only indexable pages, which is usually what you want.

Before crawling, open Configuration > Content > Area and exclude the navigation, header, and footer elements. Otherwise every page shares hundreds of words of menu text, and pages that differ in their main content can still score as near twins. You can adjust the content area and threshold after a crawl without crawling again.

One step trips people up: the Near Duplicates filter stays empty until you run Crawl Analysis at the end of the crawl. The overview pane marks the filters that are waiting on it. Once the analysis finishes, the Content tab lists each page's closest similarity match and how many near duplicates it has, and the Duplicate Details tab shows the matching text and highlights where the pages differ.

## Count headings with custom extraction

The crawler's H1 columns show you the heading text page by page. A custom extraction gives you a number you can sort by. Under Configuration > Custom > Custom Extraction, add an XPath rule in Function Value mode with `count(//h1)`. Every URL gets a column with its H1 count. Add `count(//h2)` alongside it if you want to see which templates skip a level. Group the results by URL pattern and the template behind each problem usually becomes obvious.

## What multiple H1s actually cost you

Less than most audit tools suggest. Google's SEO Starter Guide says headings in semantic order are fantastic for screen readers, and that from Google Search's perspective it doesn't matter if they're out of order. There is no ranking penalty for two H1s. The W3C's accessibility tutorial explains why order still matters: people using screen readers move through a page by its headings, so the ranks should describe how the page is organized.

So I treat headings as a clarity and accessibility problem. The cases worth fixing are:
- **No H1 at all,** often because a theme styles the page title as a div.
- **The logo wrapped in an H1** on every page, so the site name is the main heading of every URL.
- **An H1 split across styled elements,** such as two spans with no space between them, so extracted text reads "BestPrices" instead of "Best Prices."
- **The same H1 sitewide,** usually from a layout that hard codes it.

Each of these is one template fix. That's the payoff of finding them by count rather than by spot checking.

## Where near duplicates come from

When I group near-duplicate clusters by URL pattern, the same handful of causes come up again and again:
- **City swap location pages,** where the only difference is the town name.
- **Tag and category archives** that list the same posts under different labels.
- **Parameter URLs** for sorting, filtering, or tracking that serve the same content.
- **Printer friendly versions** of articles and recipes.
- **Quiz or calculator variants** that share an explanation and change a few inputs.

## Decide, cluster by cluster

Every cluster gets one of three decisions:
1. **Differentiate.** If each page has a real reason to exist, such as location pages for offices that actually differ, rewrite them so each carries information the others don't: staff, services, directions, local proof.
2. **Merge and 301.** If the pages serve the same purpose, keep the strongest, fold in anything useful from the rest, and permanently redirect the others to it. Google's documentation calls a redirect a strong signal, and recommends redirects when you want to get rid of duplicate pages.
3. **Canonicalize.** If the duplicates have to stay reachable, as parameter and printer versions usually do, point them at the main version with rel="canonical." Google treats that as a strong signal too.

Noindex is rarely the right tool here. Google specifically advises against using noindex to steer canonical selection within a site, since it removes the page from Search entirely. I reserve it for pages that should never appear in results at all.

## Check the fix with a second crawl

After the changes ship, crawl again with the same settings and compare the two crawls. The clusters you merged should now show redirects, the canonicalized URLs should point where you meant, and the H1 count column should read 1 across the templates you fixed. Then give Google a few weeks and check the Page indexing report in Search Console for duplicates it has resolved.

## Get help

This is part of the full crawl and repair work I describe on [sitewide technical SEO](https://christopherabraham.com/services/sitewide-technical-seo/). If heading and title patterns are the main issue, see [on-page SEO](https://christopherabraham.com/services/on-page-seo/). Unfamiliar terms are in the [glossary](https://christopherabraham.com/guides/glossary/).

## Let me help you with this

If you'd rather have this done than do it yourself, it's exactly the work I do for clients. Tell me about your site and I'll tell you where I'd start.

[Book a 30 minute call](https://calendly.com/chrisabraham/30) [Call +1 202-352-5051](tel:+12023525051) [Email cja@well.com](mailto:cja@well.com)

Prefer to hire through Upwork? I'm [Top Rated there too](https://www.upwork.com/freelancers/chrisjabraham).

## Sources
- [Google Search Central: SEO Starter Guide](https://developers.google.com/search/docs/fundamentals/seo-starter-guide)
- [Google Search Central: How to specify a canonical URL](https://developers.google.com/search/docs/crawling-indexing/consolidate-duplicate-urls)
- [W3C WAI: Headings tutorial](https://www.w3.org/WAI/tutorials/page-structure/headings/)
- [Screaming Frog: How to check for duplicate content](https://www.screamingfrog.co.uk/seo-spider/tutorials/how-to-check-for-duplicate-content/)
- [Screaming Frog: SEO Spider configuration](https://www.screamingfrog.co.uk/seo-spider/user-guide/configuration/)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
