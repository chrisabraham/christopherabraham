> A bilingual film review site was indexed by Bing but nearly invisible in Google. A consent platform blocked the script that displayed every article to bots.
>
> Source: https://christopherabraham.com/case-studies/consent-banner/ · Updated 2026-10-06 · By Christopher Abraham

# Film review site: a consent tool that emptied every article for Google

A WordPress site publishing film reviews in English and Italian had a strange split: Bing indexed it normally, while Google left almost every review out. No crawl errors, no manual action, just a long list of pages marked "Crawled, currently not indexed."

## The engagement

A paid diagnosis for the owner, followed by a call to walk through what I found.

## The cause

Each review's text sat inside jQuery UI tabs. The site's cookie consent platform was set to prior-consent blocking, holding back scripts until a visitor clicked Accept. One of the scripts held back was the one that initialized the tabs.

Googlebot never clicks Accept. It visits every page as a visitor who has declined, so it rendered each review with the layout intact and the tab panels empty. Bing processed the pages differently, which explained the gap between the two engines.

## What made it worse
- 97% of pages carried identical hardcoded H2 headings from the theme.
- 95% of internal links had no anchor text at all.

Even the parts Google could see said almost nothing that distinguished one review from another.

## Recommendations
- Exempt content-building scripts from consent blocking, or put the review text directly in the HTML. Consent rules belong on analytics and advertising scripts, never on the article.
- Generate H2s from each review's own content.
- Add descriptive anchor text to internal links.

## How I confirmed it

Side-by-side browser sessions, one consenting and one not, showed the tabs empty in the second. The blocked script was identified in the consent platform's settings and matched to the exclusion pattern.

## Why it matters

Consent platforms are installed by legal and marketing teams and almost never tested against crawlers. If your site uses one, load a page with consent declined and check what's left. See [reading the Page indexing report](https://christopherabraham.com/guides/page-indexing-report/).

Updated October 6, 2026
