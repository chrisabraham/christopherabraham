> Proof that an SEO fix shipped: compare before-and-after crawls in Screaming Frog, check change detection, then confirm in Search Console with validation.
>
> Source: https://christopherabraham.com/guides/prove-seo-fixes/ · Updated 2026-10-13 · By Christopher Abraham

# How to prove an SEO fix actually worked

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 13, 2026

"Done" is the most dangerous word in SEO. A developer marks the ticket closed, the CMS shows the new titles, and three months later a crawl finds the old ones still live on half the site. A cache never cleared, a second template was missed, or the change only applied to new pages. I don't call a fix finished until two crawls and Search Console agree that it is. Here is the routine.

## Step 1: crawl before you change anything

The baseline is the step people skip, and without it there's nothing to compare. Before any fix ships, crawl the site with the settings you'll use afterward: the same start URL, the same rendering mode, the same exclusions, the same custom extractors. Save it.

In Screaming Frog, comparison needs a licence and database storage mode, which you switch on under File > Settings > Storage Mode. Database storage saves every crawl automatically and lists it under File > Crawls, and it copes with large sites far better than memory storage. Crawls saved in the old file format can be imported and converted.

## Step 2: crawl again after the release

Once the fix is live and caches have cleared, crawl again with identical settings. Then switch to Mode > Compare, pick the two crawls, and run the comparison. The newer crawl becomes Current and the older one Previous.

## Step 3: read the four change columns

For every tab and filter, the comparison sorts URLs into four groups, and the difference between them is the whole point:
- **Added:** URLs present in both crawls that have moved into this filter. If the filter is an error, these are new problems on existing pages.
- **Removed:** URLs present in both crawls that have left this filter. For an error filter, these are your fixes.
- **New:** URLs found only in the current crawl.
- **Missing:** URLs found only in the previous crawl.

If you fixed duplicate titles on 600 product pages, you want to see roughly 600 in Removed under Page Titles > Duplicate, and close to zero in Added. A large New count after a fix that wasn't supposed to create pages tells you something else changed, often a parameter or a pagination pattern now exposed to crawlers.

## Step 4: turn on change detection

Filters only notice changes that move a URL between filters. A title rewritten from one acceptable wording to another triggers nothing. For that, open Config > Compare before you run the comparison and select the elements you changed: page titles, meta descriptions, H1s, word count, crawl depth, internal links, structured data, or content. A Change Detection tab then lists every URL where those elements differ between the crawls.

This is how I answer the question every client eventually asks: did the new titles actually go live everywhere? The tab gives a URL by URL answer, and the pages that didn't change are the ones to chase.

## Step 5: check structure and internal links

The Site Structure tab in a comparison shows the directory tree with URLs added and removed, and how crawl depth shifted. The lower window's inlinks view can filter to links added or removed. When a menu change quietly pushes a section of pages one click deeper, this is where it shows up, along with the exact links that went away.

## Comparing staging with live

Before a migration or a redesign launches, URL Mapping under Config > Compare lets you compare crawls whose URLs differ. A regex maps the previous crawl's URLs onto the current crawl's, so a staging hostname can be compared page for page with the live site. Run it before launch and you'll catch missing titles, dropped schema, and lost internal links while they're still cheap to fix.

## Step 6: confirm with Google

A clean crawl proves what your site serves. Search Console shows what Google has noticed.
- **URL Inspection** on a handful of representative URLs. The live test shows whether Google can index the page as it stands now, and the indexed result shows the version Google currently holds, including its chosen canonical.
- **Validate fix** in the Page indexing report, once every instance of an issue is fixed. Google rechecks the affected URLs and emails you when the fix is confirmed or when it finds one still broken, which stops the validation. Google says this typically takes up to about two weeks and sometimes longer.
- **A smaller sitemap** for speed. Google suggests submitting a sitemap of your most important affected pages and filtering the report to it before validating, since a smaller set can finish sooner.

## Write it down

A verification note after each release can be short: the two crawl dates, the counts in Removed and Added for each targeted issue, a list of any URLs that didn't change and why, and the Search Console validation status with its date. It turns "fixed" into a record anyone can check, and it catches the missed template before Google does.

Verification is built into my [sitewide technical SEO](https://christopherabraham.com/services/sitewide-technical-seo/) work and every [site migration](https://christopherabraham.com/services/migrations/). The extractors I use for before-and-after comparisons are in [Screaming Frog custom extraction recipes](https://christopherabraham.com/guides/custom-extraction/).

## Let me help you with this

If you'd rather have this done than do it yourself, it's exactly the work I do for clients. Tell me about your site and I'll tell you where I'd start.

[Book a 30 minute call](https://calendly.com/chrisabraham/30) [Call +1 202-352-5051](tel:+12023525051) [Email cja@well.com](mailto:cja@well.com)

Prefer to hire through Upwork? I'm [Top Rated there too](https://www.upwork.com/freelancers/chrisjabraham).

## Sources
- [Screaming Frog: How to compare crawls](https://www.screamingfrog.co.uk/seo-spider/tutorials/how-to-compare-crawls/)
- [Google Search Console Help: Page indexing report](https://support.google.com/webmasters/answer/7440203)
- [Google Search Console Help: URL Inspection tool](https://support.google.com/webmasters/answer/9012289)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
