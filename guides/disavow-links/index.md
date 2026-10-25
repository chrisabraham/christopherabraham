> A burst of junk backlinks rarely needs a response. When Google says the disavow tool fits, how to build a careful file, and the mistakes that cost rankings.
>
> Source: https://christopherabraham.com/guides/disavow-links/ · Updated 2026-10-24 · By Christopher Abraham

# Spam link spikes and the disavow file: when to act at all

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 24, 2026

Sooner or later a backlink tool shows a chart with a cliff in it: hundreds of new links in a month from domains nobody recognizes, scraped directories, foreign casino pages, and strings of nonsense. The instinct is to fight back with a disavow file. Usually the right response is to write the spike down, check one or two things, and leave it alone. Sometimes it isn't, and the difference matters.

## What Google does with junk links

Since the Penguin 4.0 update in 2016, Google has treated most manipulative links by discounting them rather than punishing the site they point to. Its people have repeated the point for years. In April 2024 John Mueller said Google ignores link spam and that links pointing at pages returning 404 count for nothing at all. In April 2025, speaking at a Search Central event, he went further: Google has no internal concept of "toxic backlinks," the disavow tool is not routine maintenance, and he would reach for it only with a manual action in hand.

Google's own help page for the tool says the same thing in drier language. Most sites don't need it. It is meant for a site with a considerable number of spammy, artificial, or low quality links that have caused a manual action or are likely to cause one. And it is labeled an advanced feature, because a careless file can hurt a site's performance in search.

## Why spikes look scarier than they are

Third party backlink tools count everything they find, and they find a lot of garbage. Scraper sites copy pages wholesale with the links intact. Automated directories list every domain they can reach. Spam networks link to well known sites to look legitimate. None of that was your doing, and Google has had about two decades of practice ignoring it. A "toxicity" score in a commercial tool is that tool's opinion, built on its own crawl, and Google doesn't share it.

Spikes also coincide with real traffic losses often enough to be framed for them. This year a client's tool showed close to nine times the usual monthly count of new referring links in the same weeks that branded searches fell. The links were real and ugly. They were also not the only thing that changed that month, so they went into the investigation as one hypothesis with a test, rather than as the answer.

## When a spike deserves attention
- **Search Console shows a manual action** for unnatural links to your site. This is the case the tool was built for.
- **Someone bought links in your name.** A previous agency, an old owner, or an overeager employee paid for placements, link exchanges, or private blog network posts. Google's spam policies treat those as link schemes whoever arranged them.
- **The pattern is targeted.** Hundreds of exact match commercial anchors pointing at one money page look like an attempt to trip a filter, which is different from random scraper noise.
- **The links point at real pages and the timing fits a loss** that survives every other test. Even then, the disavow is a contained experiment, not a cure.

If none of those apply, record the spike with its dates and sources in your SEO log, keep an eye on Search Console, and spend the hours on something that moves rankings.

## Build the file from Google's data first

Start with the Links report in Search Console, which shows the linking sites Google itself knows about, and use third party exports only to fill gaps. Review the list by domain, not by URL, and sort it into three piles: plainly manipulative, plainly fine, and unsure. Only the first pile goes in the file. The unsure pile stays out, because a wrongly disavowed link from a real publication throws away value you can't easily get back.

Before disavowing a link you arranged, try to get it removed. Google asks for that first, and if you're filing a reconsideration request after a manual action, documented removal attempts are part of a credible case.

## The file format, exactly
- A plain text file with a `.txt` extension, encoded in UTF-8 or 7-bit ASCII.
- One entry per line: a full URL, or a whole domain written as `domain:example.com`. Subfolders can't be disavowed on their own.
- Lines starting with `#` are comments and are ignored. Use them to date each batch and note why it's there.
- At most 100,000 lines, comments and blank lines included, and 2 MB. Each URL can be up to 2,048 characters.

```
# Reviewed 2026-10-24: paid placements from a former vendor, removal requests unanswered
domain:cheap-article-network.example
domain:spun-directory.example
# A single page on an otherwise legitimate site
https://news.example/sponsored/old-placement.html
```

## Uploading, replacing, and undoing

Only a property owner can upload, and the tool works with URL prefix properties, not Domain properties, so verify the right one first. A list applies to that property and its child properties, and the http and https versions need their own lists. Each upload replaces the previous file entirely, so always edit the current file rather than uploading a fresh one with only new entries; errors are flagged immediately and leave the old list in place. A button cancels every disavowal for the property. Google says changes in either direction take a few weeks, and disavowed links keep appearing in the Links report afterward, which surprises everyone the first time.

## Mistakes I clean up
- **Disavowing the whole export.** Someone uploads a tool's full "toxic" list and quietly throws away links from local news, suppliers, and universities.
- **Losing the old file.** A new upload replaces the old one, so years of careful entries vanish when someone starts over.
- **Forgetting a migration.** The old domain's file doesn't follow the site to a new domain or protocol.
- **Treating disavow as the fix for a traffic drop** while the real cause sits in templates, indexing, or redirects.

## How I handle link reviews

I don't sell link building, for reasons I explain in [why I turn down backlink work](https://christopherabraham.com/guides/buying-backlinks/), and I don't sell disavow files by the thousand lines. I review the profile against Search Console's data, keep the file conservative, and treat links as one hypothesis among several, as in [the clinic migration](https://christopherabraham.com/case-studies/clinic-migration/), where I rebuilt an inherited file to keep legitimate domains. If a spike landed in the same month as a traffic loss, start with a [technical SEO audit](https://christopherabraham.com/services/seo-audit/) that finds the cause before anyone uploads anything.

## Let me help you with this

If you'd rather have this done than do it yourself, it's exactly the work I do for clients. Tell me about your site and I'll tell you where I'd start.

[Book a 30 minute call](https://calendly.com/chrisabraham/30) [Call +1 202-352-5051](tel:+12023525051) [Email cja@well.com](mailto:cja@well.com)

Prefer to hire through Upwork? I'm [Top Rated there too](https://www.upwork.com/freelancers/chrisjabraham).

## Sources
- [Search Console Help: Disavow links to your site](https://support.google.com/webmasters/answer/2648487)
- [Search Engine Journal: Google says the disavow tool is not part of normal site maintenance (April 2025)](https://www.searchenginejournal.com/google-says-disavow-tool-not-part-of-normal-site-maintenance/543861)
- [Search Engine Roundtable: Google ignores link spam, including links to 404 pages (April 2024)](https://www.seroundtable.com/google-ignore-link-spam-404-pages-37217.html)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
