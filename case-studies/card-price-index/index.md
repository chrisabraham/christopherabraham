> A trading card price site of more than 20,000 programmatic pages indexed well, then lost large sections of the index. How crawling is managed at that scale.
>
> Source: https://christopherabraham.com/case-studies/card-price-index/ · Updated 2026-10-06 · By Christopher Abraham

# Trading card price site: managing 20,000 pages in Google's index

A new site publishing prices for more than 20,000 trading cards, generated programmatically and launched on an expired domain, was indexed quickly at first. Then whole sections began dropping out.

## The engagement

Hourly technical SEO focused on crawling and indexing, working with the owner over Microsoft Teams and with access to the GitHub repository where the site is built.

## Thinking in collections

A site like this can't be managed page by page. The useful questions are about groups: which page types deserve to be indexed, which URL variations the site's tools and filters create, and how a crawler reaches a card page five levels deep.

## What I put in place
- **One sitemap per content type**, so Search Console reports coverage for each group on its own.
- **A baseline by segment**, so every later change is judged against numbers rather than impressions.
- **Robots rules for parameter-driven tools** whose endless URL variations add nothing to the index and pull crawl attention from the pages that matter.
- **Lag-aware checks.** Reports trail reality, so live behavior gets checked before any change is called a success or a failure.
- **The domain's past treated as one factor**, kept apart from the site's own technical issues.

## Working through the code

Because the site is built by developers, fixes go through the repository. Seeing how URLs are generated lets me specify changes precisely instead of describing symptoms. Every recommendation reaches the owner in writing, with its evidence attached.

## Status

Ongoing. I'm not claiming recovery numbers here; at this scale, indexing moves over weeks and months, and honest reporting means waiting for the trend. See [indexing repair](https://christopherabraham.com/services/indexing/).

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)

Updated October 6, 2026
