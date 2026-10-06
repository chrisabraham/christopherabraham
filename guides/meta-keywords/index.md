> Google ignores the meta keywords tag and Bing has called stuffing it a spam signal. Why some sites still use it, and how to write one that does no harm at all.
>
> Source: https://christopherabraham.com/guides/meta-keywords/ · Updated 2026-10-06 · By Christopher Abraham

# Meta keywords in 2026: ignored, mostly harmless, used honestly

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 6, 2026

The meta keywords tag is the oldest SEO tactic still floating around. In the late nineties it was how you told AltaVista what a page was about, and it was abused so thoroughly that every major engine stopped trusting it. It still appears on plenty of sites, including this one, so here's the straight story.

## What it is

A line in a page's head that lists the page's topics:

```
<meta name="keywords" content="technical SEO audit, traffic drop diagnosis">
```

Visitors never see it. Crawlers can read it.

## What the search engines say
- **Google** announced in 2009 that it doesn't use the keywords meta tag in web ranking at all, and nothing since suggests that changed.
- **Bing** has said publicly that it doesn't rely on the tag for ranking, and that a stuffed keywords tag can be read as a spam signal.
- **Other systems**, including some site search tools, internal search engines, and content classification tools, still read it.

So the tag won't help you rank, and stuffing it can hurt. Used sparingly and honestly, it's neutral.

## Why use it at all

There are a few modest reasons:
- **Discipline.** Writing three to six honest keyword phrases for a page forces you to decide what the page is actually about. If you can't, the page probably needs work.
- **Structured data.** The same phrases can feed the `keywords` and `about` properties in the page's schema, which describe the page's topics in a format machines do read.
- **Internal tools.** Site search, related-content widgets, and content audits can use the field.
- **No cost.** One line per page, generated from the same source as the rest of the head.

## How to write one that does no harm
1. **Two to six phrases.** Enough to describe the page, not enough to look like stuffing.
2. **Phrases, not single words.** "Core Web Vitals" says more than "speed."
3. **Only what the page covers.** Every phrase should match something in the visible content.
4. **No repetition.** Don't list the same term in five variations.
5. **No competitor or brand names you don't own.** It's misleading and pointless.
6. **Different on every page.** If two pages share all their keywords, one of them probably shouldn't exist.

## A worked example

For a guide to reading Search Console's Page indexing report, a reasonable tag reads: "Page indexing report, Search Console indexing, crawled not indexed." Three phrases, each describing a real section of the page. An unreasonable one adds "SEO, Google, best SEO, SEO expert, rank higher, cheap SEO," none of which the page is about.

## Where the tag came from

Meta tags arrived with early HTML as a way for authors to describe their own documents, and the first search engines leaned on them heavily, because analyzing full page text at scale was expensive. Within a few years, site owners were filling the tag with hundreds of terms, including popular searches that had nothing to do with their pages. The engines responded by discounting the tag, then ignoring it, and moved toward signals that are harder to fake, such as links and on-page text.

## Other meta tags that do matter
- **Title.** Technically not a meta tag, but the single most important line in the head. It names the page in search results and browser tabs.
- **Meta description.** Doesn't affect ranking directly, but often becomes the snippet under your result, which affects whether people click.
- **Meta robots.** Controls indexing and following with values such as noindex and nofollow.
- **Viewport.** Tells phones how to scale the page; without it, mobile layouts break.
- **Open Graph and Twitter card tags.** Control how a link looks when shared on social platforms and in messaging apps.

## Should you remove it from an existing site?

Only if it's stuffed. A keywords tag with dozens of terms, or the same list on every page, is worth cleaning up, because it's the one version that might count against you. A short, honest tag can stay; removing it gains nothing.

## Enforcing it on a site

On a site built with a generator, the simplest guardrail is a build check: fail the build if a page has fewer than two or more than six keywords, or repeats one. That's how this site does it, alongside checks on title and description length.

## Where to put the effort instead

Everything the keywords tag once promised now comes from elsewhere: the title tag, the H1, the opening paragraph, descriptive headings, internal anchor text, and structured data. If you have an hour for SEO, spend fifty-nine minutes on those and one on the keywords tag.

For the elements that do carry weight, see [on-page SEO](https://christopherabraham.com/services/on-page-seo/). Terms are defined in the [glossary](https://christopherabraham.com/guides/glossary/).

## Sources
- [Google Search Central Blog: Google does not use the keywords meta tag in web ranking (2009)](https://developers.google.com/search/blog/2009/09/google-does-not-use-keywords-meta-tag)
- [Bing Webmaster Guidelines](https://www.bing.com/webmasters/help/webmaster-guidelines-30fba23a)
- [Google Search Central: SEO Starter Guide](https://developers.google.com/search/docs/fundamentals/seo-starter-guide)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
