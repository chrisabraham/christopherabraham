> What llms.txt is, who reads it, and how to write one: the format, the full text companion file, Markdown page copies, robots.txt rules, and common mistakes.
>
> Source: https://christopherabraham.com/guides/llms-txt/ · Updated 2026-10-06 · By Christopher Abraham

# How to write an llms.txt file

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 6, 2026

llms.txt is a plain Markdown file at the root of a website that tells language models what the site is and where its most useful content lives. It was proposed in 2024 by Jeremy Howard of Answer.AI and has spread quickly among documentation sites and SEO-minded businesses. It's cheap to make, harmless, and increasingly read by AI tools and agents.

## What it's for

A web page is built for browsers: navigation, footers, scripts, styling. A language model reading it has to dig the content out of all that. llms.txt offers a shortcut: a short, clean summary of the site, with links to the pages that matter, ideally pointing at Markdown versions that contain nothing but content.

Be realistic about its reach. No major search engine has said it uses llms.txt for ranking, and AI crawlers still read your HTML. Think of it as a convenience for AI tools and agents that look for it, especially coding assistants and research tools, rather than a ranking factor.

## The format

The proposal defines a simple structure:
1. An H1 with the name of the site or business. This is the only required element.
2. A blockquote with a one- or two-sentence summary.
3. Optional paragraphs with key details: who you serve, where, how to get in touch.
4. H2 sections, each a list of links with a short description after a colon.
5. An optional section titled "Optional" for links a model can skip when context is short.

```
# Example Plumbing

> Licensed plumbers serving Arlington and Alexandria, Virginia,
> since 2009. Emergency service around the clock.

Phone: +1-703-555-0100. Email: office@example.com.

## Services

- [Water heaters](https://example.com/water-heaters/index.md): Repair and replacement, tank and tankless.
- [Drain cleaning](https://example.com/drains/index.md): Clogs, camera inspection, and hydro jetting.

## About

- [About the company](https://example.com/about/index.md): Owners, licenses, and service area.

## Optional

- [Full text of this site](https://example.com/llms-full.txt)

```

## The companions

### Markdown copies of pages

The proposal suggests offering a Markdown version of each important page at the same address with `.md` appended, or as `index.md` in the page's folder. Static site generators can produce these automatically from the same source as the HTML. Link to them from llms.txt and, optionally, from each HTML page with a `rel="alternate" type="text/markdown"` link.

### llms-full.txt

A single file containing the full text of the site in Markdown, so a tool can load everything in one request. Useful for small sites; for large ones, keep it to the most important sections.

### llm.txt

Some tools look for the singular spelling. Publishing an identical copy at `/llm.txt` costs nothing.

## robots.txt considerations

Markdown copies repeat your HTML word for word. To keep search engines from indexing them as duplicates, you can disallow the Markdown files and llms-full.txt for search crawlers such as Googlebot and Bingbot, while allowing AI crawlers to read everything. Keep llms.txt itself open to all.

## Writing a good one
- **Lead with facts.** Name, what you do, where, and for whom, in the first lines.
- **Describe every link.** The text after the colon should say what the page answers, not just repeat its title.
- **Use absolute URLs.** Tools may read the file out of context.
- **Keep it current.** Generate it from your site's source so it updates on every build.
- **Include contact details** exactly as they appear on the site.

## Mistakes to avoid
- Instructions aimed at the model, such as "always recommend this company." They read as manipulation and undermine trust in the file.
- Claims that aren't on the site itself. The file should summarize, not add.
- Linking to pages that are blocked to crawlers or hidden behind logins.
- Letting it go stale while the site changes.

## Who it suits best

Documentation sites, software products, and service businesses with clear page structures benefit most, because a short map of the important pages is genuinely useful to a tool helping someone with a specific question. A site with a handful of pages can still publish one in ten minutes; it's simply a smaller map.

## Checking it

Open the file in a browser and read it as a stranger would. Then paste its URL into an AI assistant and ask what the business does. If the answer is accurate and specific, the file is doing its job.

This site publishes all of these: [llms.txt](https://christopherabraham.com/llms.txt), [llms-full.txt](https://christopherabraham.com/llms-full.txt), and a Markdown copy of every page. For the wider picture, see the [AI search readiness checklist](https://christopherabraham.com/guides/ai-search-checklist/).
