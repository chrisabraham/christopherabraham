> An equipment retailer on Magento and Hyvä lost organic traffic because Alpine.js loaded specs and reviews only on scroll. How the cause was isolated and proven.
>
> Source: https://christopherabraham.com/case-studies/scroll-gated-products/ · Updated 2026-10-06 · By Christopher Abraham

# Equipment retailer: product details that loaded only on scroll

An equipment retailer running Magento 2 with the Hyvä theme watched organic traffic slide for months. The odd part: non-brand category traffic was rising while brand searches and product pages fell.

## The engagement

Forensic diagnosis and technical direction. The client's contractor owned implementation; I owned the evidence and the specification.

## What the crawl showed

I crawled the site twice with Screaming Frog, once reading raw HTML and once rendering JavaScript, and compared extracted word counts by template. Category pages yielded thousands of words. Flagship product pages, each weighing more than 1.2 MB, yielded only 250 to 400.

## The mechanism

The product template wrapped its specifications, FAQs, and reviews in Alpine.js directives that created those sections only when a shopper scrolled them into view: an `x-intersect` trigger around an `x-if` block. Googlebot renders pages in a tall viewport without scrolling the way people do, so those sections were never built. Search Console agreed: a selective cluster of product URLs sat in "Crawled, currently not indexed" while the rest of the site was fine.

## The second problem, kept separate

During the same months, a burst of spam backlinks from cloud-hosting ranges arrived, along with a redirect fault. Tempting as it was to blame everything on one cause, I documented that track separately and requested fuller Search Console access to investigate it on its own evidence.

## Recommendations
- Render product sections in the server HTML; keep scroll animation as an enhancement on top.
- Remove the scroll gate on a test group of products first, so the effect is measurable before a sitewide rollout.
- A separate cleanup plan for the backlinks and redirects.

## The lesson

Page weight and word count can disagree wildly. When a heavy page yields little text to a crawler, look for content waiting on an interaction that bots never perform. More on this pattern under [JavaScript SEO](https://christopherabraham.com/services/javascript-seo/).

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)

Updated October 6, 2026
