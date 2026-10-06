> A field guide to Search Console's Page indexing report: what each exclusion reason means, which ones need action, and how to find the template behind them.
>
> Source: https://christopherabraham.com/guides/page-indexing-report/ · Updated 2026-10-06 · By Christopher Abraham

# How to read the Page indexing report in Search Console

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 6, 2026

The Page indexing report is the closest thing Google gives you to a list of its decisions about your site. It's also easy to misread. This guide explains what each reason means, which ones deserve worry, and how to get from a scary number to the one template causing it.

## Where to find it

In Google Search Console, open **Indexing**, then **Pages**. The chart shows indexed and not-indexed URLs over time. Below it, the table "Why pages aren't indexed" lists each reason with a count. Click any reason to see example URLs and a trend for that reason alone.

## Rule one: not indexed isn't always bad

A healthy site always has excluded URLs. Redirects, deliberate noindex tags, parameter variants pointing to a canonical, and old 404s all belong outside the index. The question is never "why is this number above zero?" It's "are any pages I need in the index sitting in this list?"

## The reasons, sorted by how much attention they deserve

### Usually fine
- **Page with redirect.** The URL redirects elsewhere. Expected after any migration. Check only that the targets are indexed.
- **Alternate page with proper canonical tag.** Google accepted your canonical. Fine when the canonical is the page you intended.
- **Not found (404).** Pages that no longer exist. Fine unless they have links or traffic, in which case they deserve a 301.
- **Excluded by "noindex" tag.** Fine if you put the noindex there on purpose. Scan the examples for pages you didn't mean to hide.

### Worth a look
- **Blocked by robots.txt.** Check that no important section or resource is disallowed. A blocked CSS or JavaScript file can break rendering for the pages that need it.
- **Duplicate without user-selected canonical.** Google found near-identical pages and you didn't say which one is primary. Add canonicals or consolidate.
- **Duplicate, Google chose different canonical than user.** Google disagreed with your canonical. Look for internal links, sitemaps, or redirects that point at the other version.
- **Soft 404.** The page returns a success code but looks empty: an out-of-stock product with no content, an empty search result, a client-side "not found" screen.
- **Server error (5xx).** Google got an error when it tried. Even occasional errors slow crawling. Check hosting, firewalls, and rate limits.

### Usually where the real problem is
- **Crawled, currently not indexed.** Google fetched the page and decided it wasn't worth indexing. On a site with good content, this is often a rendering problem: the text you see isn't in what Google receives.
- **Discovered, currently not indexed.** Google knows the URL exists but hasn't fetched it. Common on large sites with weak internal linking, slow servers, or floods of low-value URLs competing for crawl attention.

## From a count to a cause
1. **Export the examples.** Each reason lists up to 1,000 example URLs. Export them.
2. **Group by pattern.** Sort by URL path. You'll usually see the problem cluster in one directory or page type, such as /product/, /tag/, or /events/.
3. **Inspect a sample.** Run URL Inspection on five or six from the cluster, then click **Test live URL** and **View tested page**. Compare the rendered HTML and screenshot with what a visitor sees.
4. **Check the content made it.** Search the rendered HTML for a sentence from the page's main content. If it's missing, you've found a rendering problem.
5. **Check the signals.** Canonical, robots meta tag, status code, and whether the page is in your sitemap and linked from other pages.
6. **Compare with a healthy page.** Find a page of the same type that is indexed. Whatever differs between the two is your lead.

## Make the report work for you

Submit separate XML sitemaps for each page type: products, categories, articles, locations. Then filter the Page indexing report by sitemap. Instead of one blended number, you see that 96% of articles are indexed and 41% of products are not, which tells you exactly where to look.

## Mind the lag

The report updates days behind reality, and counts can move in steps rather than smoothly. After a fix, check individual URLs with the live test rather than waiting for the chart. When you've fixed a cluster, use **Validate fix** on that reason, and Google will recheck the examples and report progress.

## Check Bing too

Bing Webmaster Tools has its own URL Inspection and index coverage reports. When Bing indexes pages Google won't, the difference often points straight at the cause, because the two crawlers render JavaScript and apply consent and robots rules differently.

## When to get help

If the cause isn't obvious after a few inspections, or if important pages keep falling out, a structured diagnosis saves time. See [indexing repair](https://christopherabraham.com/services/indexing/), or a real example where [a consent tool caused the exclusions](https://christopherabraham.com/case-studies/consent-banner/).

## Sources
- [Search Console Help: Page indexing report](https://support.google.com/webmasters/answer/7440203)
- [Google Search Central: How to specify a canonical URL](https://developers.google.com/search/docs/crawling-indexing/consolidate-duplicate-urls)
- [Bing Webmaster Guidelines](https://www.bing.com/webmasters/help/webmaster-guidelines-30fba23a)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
