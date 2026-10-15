> I crawl every URL on your site, trace each problem to the template, component, or script behind it, fix the cause once, then crawl again to prove it held.
>
> Source: https://christopherabraham.com/services/sitewide-technical-seo/ · Updated 2026-10-15 · By Christopher Abraham

# Sitewide technical SEO: crawl, trace, fix, recrawl

This is the deep tissue work. I crawl every URL your site serves, group what I find by the template, component, or import script that produces it, fix that cause once, and then crawl the whole site again to show the fix held everywhere it should. You get fewer, larger fixes, and proof that each one landed.

## Why the whole site and not a sample

A sample of fifty pages tells you what fifty pages look like. The expensive problems live in the patterns: one archive template that clones its title onto 900 tag pages, one product import that writes the same description into every variant, one layout component that drops a second H1 into every post. Patterns only show up when every URL sits in the same table, sorted and grouped. A full crawl also catches the pages nobody remembers publishing, which are often the ones causing trouble.

## What a full sweep covers
- **Status and indexability:** every response code, every noindex, every canonical pointing somewhere unexpected.
- **Sitemaps compared with the crawl:** URLs listed in the sitemap that the crawl can't reach, and reachable, indexable URLs the sitemap leaves out.
- **Titles and descriptions,** including suffixes a theme appends without asking and wording that changed during a migration.
- **Headings:** missing H1s, a logo wrapped in an H1 on every page, and H1s split across styled elements so the words run together.
- **Duplicate and near-duplicate content,** with a decision for each cluster: rewrite to differentiate, merge and redirect, or canonicalize.
- **Redirects and links:** chains, loops, internal links still aimed at old URLs, and orphaned pages.
- **Images and alt text:** oversized files and missing or meaningless alternatives.
- **Structured data coverage:** which templates emit JSON-LD, which don't, and whether it matches the visible page.
- **Rendering faults,** including hydration errors, found by loading each page in headless Chrome and collecting what the console reports.

## From a crawl row to its cause

A row in a crawl export is a symptom. The cause is a file. When I have access to the codebase, I use OpenAI Codex and Claude Code to read it, find which component writes the faulty title or the extra heading, and draft small scripts that test for the problem across the site. Those assistants are quick and occasionally wrong, so every claim they make gets checked against the live site before it goes into a finding. My guide to [doing SEO inside your Git repository](https://christopherabraham.com/guides/seo-in-your-repository/) explains the approach in more detail.

## How fixes reach the site

There are three routes, and I'll use whichever your setup allows:
- **In the CMS.** I export the affected fields before touching anything, make the changes, and export again, so there's a clean before-and-after record.
- **In the repository.** I work on a branch, open a pull request, and check the preview build before anyone merges it.
- **Through your developer.** I write the ticket with the file, the cause, the fix, and a test that proves it's done, then confirm what ships.

## Protecting the pages that earn the clicks

Search Console tells me which pages bring in most of your organic visits. Those pages get changed last. A new title pattern or heading standard goes first onto a lower traffic section, where I can watch how it behaves for a few weeks, and only then onto the pages that pay the bills.

## Proving the fix held

After each release, I crawl again and compare the two crawls row by row, so you can see exactly which URLs changed and which didn't. Scripted Chrome sessions confirm what a real browser renders. Search Console shows Google picking up the changes over the following weeks. I report what moved, what didn't, and why.

## What you receive
- The full crawl and a findings report grouped by cause, with example URLs for each.
- A ranked fix list that names the template, file, or setting behind each problem.
- Changes made directly where I have access, as CMS edits or pull requests.
- A recrawl comparison after release, and a Search Console read once Google has caught up.

## What the industry calls this work

If you're searching for someone to do this, the labels you'll see are technical SEO, technical SEO implementation, SEO engineering, and SEO QA. On sites built in React or Next.js it goes by JavaScript SEO, Next.js SEO, or headless SEO, and covers rendering (SSR, SSG, CSR, and hydration). The underlying checks are crawlability, indexability, canonicalization, duplicate and near-duplicate content, heading hierarchy, template level SEO, internal linking, structured data and JSON-LD for entity SEO, Core Web Vitals (LCP, INP, and CLS), and site migrations with redirect mapping. Newer labels for the AI side are GEO and AEO, which includes making sure AI crawlers such as GPTBot, ClaudeBot, and PerplexityBot can read your pages. I do it in Git, through pull requests and deploy previews. I don't do paid search; this is all organic.

## Tools

Screaming Frog SEO Spider with JavaScript rendering, near-duplicate detection, and custom extraction; Playwright for scripted headless Chrome; OpenAI Codex and Claude Code for reading and testing codebases; Google Search Console; and Bing Webmaster Tools.

## Who it suits

Sites with hundreds or thousands of URLs built from a handful of templates: ecommerce catalogs, publishers, directories, and businesses on Next.js, React, or a headless CMS whose team will grant read access to the repository. It also suits WordPress and Shopify sites where a theme or plugin is quietly repeating the same mistake on every page.

## Related services and guides

This sweep draws on several narrower services: the [technical SEO audit](https://christopherabraham.com/services/seo-audit/) when the question is why traffic fell, [JavaScript and headless SEO](https://christopherabraham.com/services/javascript-seo/), [indexing repair](https://christopherabraham.com/services/indexing/), [on-page SEO](https://christopherabraham.com/services/on-page-seo/), [schema markup](https://christopherabraham.com/services/schema/), [Core Web Vitals](https://christopherabraham.com/services/site-speed/), [site migrations](https://christopherabraham.com/services/migrations/), and [AI search visibility](https://christopherabraham.com/services/ai-search/). For the method behind two of the most common findings, read [finding near duplicates and multiple H1s across a whole site](https://christopherabraham.com/guides/near-duplicates-and-h1s/). Examples from past work: [product details Googlebot never loaded](https://christopherabraham.com/case-studies/scroll-gated-products/) and [a React app with 2,000 pages Google missed](https://christopherabraham.com/case-studies/event-app-links/).

To start, [send me your site and what's bothering you about it](https://christopherabraham.com/contact/), or see how engagements run on [Hire Me](https://christopherabraham.com/hire-me/).

Updated October 15, 2026
