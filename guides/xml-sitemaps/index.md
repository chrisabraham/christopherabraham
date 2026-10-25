> What an XML sitemap should hold in 2026: canonical URLs that answer 200, honest lastmod dates, no priority games, and how I audit one against a crawl.
>
> Source: https://christopherabraham.com/guides/xml-sitemaps/ · Updated 2026-10-24 · By Christopher Abraham

# XML sitemaps that tell the truth

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 24, 2026

An XML sitemap is a list you hand to search engines that says, in effect, "these are the pages I want found, and this is when each one last changed." Search engines treat it as a hint, never an order, and they decide how much to trust it by checking it against what they actually find. A sitemap that lists redirects, duplicates, and dates that change every night teaches them to ignore it. A sitemap that matches the site exactly earns the opposite. Most of the sitemaps I audit fall somewhere in between, and the fixes are almost always about honesty rather than tags.

## What a sitemap is for, and what it can't do

A sitemap helps discovery. It's most useful on large sites, new sites with few links pointing in, sites with pages that sit deep in the navigation, and sites that publish or change often. On a twenty page site where every page is linked from the menu, Google will find everything without one, though a sitemap still costs nothing and gives you a tidy report in Search Console.

What a sitemap can't do is make a page indexable. If a page is thin, duplicated, blocked, or canonicalized somewhere else, listing it in the sitemap doesn't overrule any of that. It just adds a line to the Page indexing report explaining why the URL you submitted wasn't indexed. If your real problem is pages that are discovered and then left out, that's a quality and duplication question, and my guide to [reading the Page indexing report](https://christopherabraham.com/guides/page-indexing-report/) is the better starting point.

## The one rule: list only the URLs you want in search

Every URL in the file should pass four tests at once:
1. **It answers 200.** Not a 301, not a 404, not a soft 404 that says "no results" with a 200 status.
2. **It's the canonical.** The page's own canonical tag points to itself, exactly as written in the sitemap: same protocol, same host, same trailing slash.
3. **It's indexable.** No noindex in the robots meta tag or the X-Robots-Tag header.
4. **It's crawlable.** robots.txt doesn't block it.

That rules out a lot of what plugins and platforms put in by default: tag archives you've set to noindex, paginated listings, internal search results, attachment pages, staging hostnames, and the http or non-www versions of URLs. The sitemap and the canonical tags have to agree. When they contradict each other, you've sent two signals and asked Google to pick one.

## Honest lastmod dates

Of the optional tags, `lastmod` is the only one that still matters. Google has said it uses lastmod when the dates are consistently and verifiably accurate, and Bing has written publicly that it leans on lastmod to decide what to recrawl. The key word is accurate. A lastmod should change when the main content of the page changes: a rewritten section, a corrected fact, new prices. It shouldn't change because the footer copyright year rolled over, a sidebar widget updated, or the site was rebuilt.

The common failure is a generator that stamps every URL with the build time. Every page claims it changed today, every day, and the search engine learns that this site's dates mean nothing. On this site, each page's source carries an `updated` date that I change by hand when the content changes, and the build writes that date into the sitemap, the visible "Updated" line, and the structured data. One date, set on purpose, appearing in three places that agree.

## The tags to leave out

`priority` and `changefreq` are in the original protocol, and Google ignores both. You can leave them in without harm, but I take them out, because every field in a file should mean something, and these give people the false comfort of having "prioritized" pages that no crawler is listening to.

The same goes for most of the image sitemap extension. Google retired the image caption, title, geographic location, and license tags in 2022. Only the image location is still read. Image entries are worth including for images that matter in search, such as products, diagrams, and original photography, and not worth bloating the file with every icon and spacer.

## Size limits and sitemap index files

One sitemap file can hold up to 50,000 URLs and be up to 50 MB uncompressed. Past either limit, split it into several files and list them in a sitemap index file, then submit the index. You can gzip the files to save bandwidth; the size limit applies to the uncompressed version.

Splitting is useful well below the limit. On a programmatic site of more than 20,000 pages, I gave each content type its own sitemap, so Search Console reported indexing for each group separately, and a problem in one template stood out instead of hiding in a site-wide average. The [price index case study](https://christopherabraham.com/case-studies/card-price-index/) shows how that played out. Split by template or section, not alphabetically or at random, because the point is to make the reports readable.

## Telling search engines where it lives
- **robots.txt.** Add a line such as `Sitemap: https://example.com/sitemap.xml`. It must be an absolute URL, and it can sit anywhere in the file. Every crawler that reads robots.txt finds it there, including ones you'll never submit to by hand.
- **Search Console and Bing Webmaster Tools.** Submit it once in each. You don't need to resubmit after every change; they fetch it again on their own.
- **No more pings.** Google retired its old sitemap ping address in 2023, so scripts that still call it are doing nothing. For Bing and the other engines that support it, IndexNow is the way to announce changed URLs quickly.

One ordering detail I care about: if you announce new URLs with IndexNow, do it after the new sitemap is actually live, not the moment you push. On this site, the IndexNow job waits until the public sitemap matches what the release meant to publish, because an announcement about a page that's still deploying wastes the crawl.

## How I audit a sitemap

I compare three lists: what the sitemap says, what a crawl finds, and what Search Console reports. In Screaming Frog, I run a normal crawl with the option to crawl linked XML sitemaps switched on, then look at the Sitemaps tab. Three filters do most of the work:
- **Non-indexable URLs in sitemap.** Redirects, errors, noindexed pages, and canonicalized pages that shouldn't be listed. Each one is a broken promise.
- **URLs not in sitemap.** Indexable pages the crawl found that the sitemap forgot. Often a whole post type or a newer section the generator wasn't told about.
- **Orphan URLs.** Pages in the sitemap that nothing on the site links to. Search engines can find them, but an orphan with no internal links rarely ranks. Usually the fix is [a few good internal links](https://christopherabraham.com/guides/internal-linking/), sometimes it's deleting a page nobody meant to keep.

Then I open Search Console's Sitemaps report to confirm the file was read without errors, and filter the Page indexing report to submitted URLs only. The gap between "submitted" and "indexed" for each sitemap is the clearest single measure of how much of your intended site Google has accepted.

I also open the file in a browser and read it. A sitemap with a stylesheet attached shows as a readable table instead of raw XML, which makes it easy to spot a staging hostname, a duplicated section, or a run of identical dates at a glance. The [sitemap for this site](https://christopherabraham.com/sitemap.xml) works that way.

## Common mistakes I find
- Two sitemaps from two plugins, both submitted, listing different versions of the same URLs.
- An old sitemap still submitted in Search Console from a previous platform, full of URLs that now redirect.
- Development or staging hostnames inside the production file.
- The sitemap itself blocked in robots.txt, or served with a noindex header that some crawlers read as a reason to drop it.
- Trailing slash or capitalization mismatches between the sitemap and the canonical tags.
- A cache layer serving a sitemap that's weeks old, so new pages never appear in it.

None of these is dramatic on its own. Together they make a sitemap that search engines treat as noise.

## Questions people ask about sitemaps

### Does a sitemap help me rank?

Not directly. It helps search engines find and recrawl pages. Ranking comes from what's on the pages and who links to them.

### Do AI search tools read XML sitemaps?

Many of the crawlers that feed AI answers read robots.txt and follow its sitemap line, and Bing's index, which several AI tools draw on, uses sitemaps and IndexNow. An accurate sitemap is part of being easy to read for every kind of machine, alongside an [llms.txt file](https://christopherabraham.com/guides/llms-txt/).

### Should I list PDFs in my sitemap?

Yes, if they're useful documents you want found in search and they answer 200 at a stable address. Leave out drafts and duplicates of HTML pages.

### How often should the sitemap update?

Whenever a page is added, removed, or meaningfully changed. Generate it from the same source as the site, so it can't fall behind.

If your sitemap and Search Console disagree and you can't tell why, that's the kind of thing I sort out in a [crawling and indexing engagement](https://christopherabraham.com/services/indexing/). The bigger picture of crawl health is in my [site-wide technical SEO](https://christopherabraham.com/services/sitewide-technical-seo/) work.

## Let me help you with this

If you'd rather have this done than do it yourself, it's exactly the work I do for clients. Tell me about your site and I'll tell you where I'd start.

[Book a 30 minute call](https://calendly.com/chrisabraham/30) [Call +1 202-352-5051](tel:+12023525051) [Email cja@well.com](mailto:cja@well.com)

Prefer to hire through Upwork? I'm [Top Rated there too](https://www.upwork.com/freelancers/chrisjabraham).

## Sources
- [Sitemaps.org: Sitemaps XML format](https://www.sitemaps.org/protocol.html)
- [Google Search Central: Build and submit a sitemap](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap)
- [Google Search Central: Image sitemaps](https://developers.google.com/search/docs/crawling-indexing/sitemaps/image-sitemaps)
- [Bing Webmaster Blog: The importance of setting the lastmod tag in your sitemap](https://blogs.bing.com/webmaster/february-2023/The-Importance-of-Setting-the-lastmod-Tag-in-Your-Sitemap)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
