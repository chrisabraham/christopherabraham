> XPath and regex recipes for Screaming Frog custom extraction to audit a site: heading counts, canonicals, robots tags, schema types, alt text, and tag IDs.
>
> Source: https://christopherabraham.com/guides/custom-extraction/ · Updated 2026-10-13 · By Christopher Abraham

# Screaming Frog custom extraction recipes for sitewide SEO audits

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 13, 2026

The standard Screaming Frog tabs answer the standard questions. Custom extraction answers yours. With a few lines of XPath or regex, every URL in a crawl gets a new column holding exactly the fact you need, and a question like "which templates are missing a canonical?" becomes a sort and a filter. These are the extractors I load into almost every audit.

## Setting it up

Custom extraction needs a paid licence. Open Configuration > Custom > Custom Extraction and click Add. Each extractor gets a name, which becomes its column heading, a type, and an expression. You can run up to 100 extractors in one crawl.

There are three types:
- **XPath,** which selects elements and attributes from the HTML. Most of my recipes use it.
- **CSSPath,** the same idea using CSS selectors, often the quickest to write.
- **Regex,** for anything that isn't an HTML element, such as JSON inside a script tag or an ID in inline JavaScript.

For XPath and CSSPath you then choose what to return: the whole element, its inner HTML, its text, or, with Function Value, the result of a function such as a count. If you'd rather not write expressions at all, the visual extraction browser lets you click an element on a sample page and suggests the expression for you.

One setting matters more than any recipe. Screaming Frog extracts from the raw HTML unless JavaScript rendering is on, in which case it reads the rendered page. On a React or Next.js site, run the same extractors in both modes and compare. Any column that fills in only after rendering is content that depends on JavaScript to exist.

## Heading recipes
- **H1 count** (XPath, Function Value): `count(//h1)`. Sort descending to find templates with two or more, ascending to find pages with none.
- **All H1 text** (XPath, Extract Text): `//h1`. Shows when a logo or a hidden mobile heading is the H1.
- **H2 count** (XPath, Function Value): `count(//h2)`. A zero on a long page usually means the template styles its subheads as plain text.

## Indexing and canonical recipes
- **Canonical count** (XPath, Function Value): `count(//link[@rel='canonical'])`. More than one canonical tag on a page is a conflict worth fixing at once.
- **Canonical target** (XPath, Extract Inner HTML): `//link[@rel='canonical']/@href`. Screaming Frog reports canonicals already; I extract it anyway when I need it beside other custom columns in one export.
- **Robots meta** (XPath, Extract Inner HTML): `//meta[@name='robots']/@content`. Catches noindex left behind from a staging site.
- **Hreflang values** (XPath, Extract Inner HTML): `//link[@rel='alternate'][@hreflang]/@hreflang`. A quick check that every language version lists the same set.

## Structured data recipes

JSON-LD lives inside a script tag as JSON, so element selectors can't reach the fields inside it. Screaming Frog's own guidance is to use regex for any JSON in the code.
- **JSON-LD block count** (XPath, Function Value): `count(//script[@type='application/ld+json'])`. Zero on a template that should carry schema is the first thing to fix.
- **Schema types** (Regex): `"@type"\s*:\s*"(.*?)"`. Lists every type declared on the page, so you can see which templates emit Product, Article, or nothing at all.
- **The whole block** (Regex): `<script type="application/ld\+json">(.*?)</script>`. Useful for exporting and validating a sample per template.

## Content and authorship recipes
- **Published date** (XPath, Extract Inner HTML): `//meta[@property='article:published_time']/@content`. Finds articles with no machine readable date.
- **Author meta** (XPath, Extract Inner HTML): `//meta[@name='author']/@content`. Many themes leave this blank or set it to the site name.
- **Images with no alt attribute** (XPath, Function Value): `count(//img[not(@alt)])`. Counts per page, so you can see which template is the repeat offender.
- **Links inside the main content** (XPath, Function Value): `count(//main//a)`. Separates contextual internal links from the menu and footer, assuming the template uses a main element.

## Tracking recipes
- **Google Tag Manager container** (Regex): `["'](GTM-.*?)["']`. Shows pages with no container, or two different ones.
- **GA4 measurement ID** (Regex): `["'](G-[A-Z0-9]+)["']`. Same idea for sites that load GA4 directly.

## Reading the results

A column of numbers is only useful once it's grouped. Export the crawl, add a column for the URL pattern or template, and pivot. When every product page reports two H1s and every blog post reports one, the cause is in the product template, and one change fixes thousands of URLs. That is the habit that turns a crawl from a list of warnings into a short list of causes.

Check a few rows by hand before you trust a recipe. View the source of one page, confirm the extracted value matches, and adjust the expression if a theme uses different markup from the one you expected.

## Where this fits

Custom extraction is how I make a full crawl answer the specific questions in a [sitewide technical SEO](https://christopherabraham.com/services/sitewide-technical-seo/) engagement. For the licence question itself, read [whether a Screaming Frog licence is worth it](https://christopherabraham.com/guides/screaming-frog-licence/), and for two problems these recipes surface constantly, see [finding near duplicates and multiple H1s](https://christopherabraham.com/guides/near-duplicates-and-h1s/).

## Sources
- [Screaming Frog: Web scraping and data extraction](https://www.screamingfrog.co.uk/seo-spider/tutorials/web-scraping/)
- [Screaming Frog: SEO Spider configuration](https://www.screamingfrog.co.uk/seo-spider/user-guide/configuration/)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
