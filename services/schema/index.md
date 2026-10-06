> Structured data that validates, matches the visible page, and connects your organization, people, products, and locations as entities for Google and AI.
>
> Source: https://christopherabraham.com/services/schema/ · Updated 2026-10-06 · By Christopher Abraham

# Schema markup and entity SEO

Structured data tells machines, in their own language, what a page is about: this is a business, here is its address, this is the product, this is its price, this person wrote the article. Done well, it earns rich results in Google and helps AI systems connect the facts. Done carelessly, it contradicts the page and gets ignored.

## What I build
- **Organization and LocalBusiness** with name, logo, address, phone, hours, service area, and sameAs links to the profiles that confirm the business.
- **Person** for founders, authors, and practitioners whose expertise matters to the page.
- **Product and Offer** with price, availability, brand, identifiers, and review data from the platform's real reviews.
- **Service** for service businesses, tied to the provider and the area served.
- **Article, BlogPosting, and TechArticle** with author, dates, and publisher.
- **FAQPage, HowTo, and DefinedTermSet** where the page truly contains questions, steps, or definitions.
- **BreadcrumbList and WebSite** to describe structure.

## Entities, connected

The real value is in the connections. A multi-location business is one Organization with several locations as branches, each linking to its own page and its own Google Business Profile. An author is a Person who works for the Organization that publishes the article. I use stable @id identifiers so every page refers to the same entities in the same way, and search engines and AI systems assemble one consistent picture instead of several conflicting ones.

## Common problems I fix
- Two Product blocks on one page, one from the theme and one from a plugin, each with different data.
- Review stars marked up from reviews that aren't on the page.
- A home page and its first location described as the same business.
- FAQ markup on pages with no visible questions.
- Schema hardcoded once and never updated as prices, hours, or addresses changed.
- Plugins emitting conflicting graphs that no validator flags as errors but no search engine trusts.

## How it's delivered

Depending on your platform, I install the JSON-LD myself through the theme, a plugin like Rank Math or Yoast, Shopify's theme files and metafields, or a pull request to your repository. Otherwise I hand your developer finished, validated code. Theme work happens on a duplicate theme or staging copy first. Every template is checked in the Rich Results Test and the Schema.org validator, and then watched in Search Console's enhancement reports.

## What schema can and can't do

Structured data makes your facts unambiguous; it doesn't make a weak page strong. Google decides when to show rich results. The work pays off most when it matches strong, visible content, which is why I review the page and the markup together.

Not sure which types you need? Read [the schema markup a small business actually needs](https://christopherabraham.com/guides/small-business-schema/), or see [entity markup for a brand with locations in several states](https://christopherabraham.com/case-studies/closet-locations/).

Updated October 6, 2026
