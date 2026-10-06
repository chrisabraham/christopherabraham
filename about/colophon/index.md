> How christopherabraham.com is made: hand written HTML, a small Python generator with strict checks, GitHub Pages, Cloudflare, accessible colors, Lynx testing.
>
> Source: https://christopherabraham.com/about/colophon/ · Updated 2026-10-06 · By Christopher Abraham

# Colophon

Book publishers end a fine edition with a colophon, a few lines on the type, the paper, and the press. Here are the equivalent details for this website.

## Look and type

The design is deliberately plain, after the classic Plone theme: a row of tabs, a breadcrumb trail, and generous black text in Verdana. The CA monogram and the social sharing card were drawn in code with Python and the Pillow imaging library. My name is set in burnt orange, page titles in blue, and section headings in teal, and every one of those colors clears the 4.5 to 1 contrast ratio that accessibility guidelines ask for.

## Under the hood

Each page is a hand-written HTML file with a few lines of metadata on top. A short Python script assembles them into the finished site and generates the extras machines look for: a Markdown version of every page, llms.txt and llms-full.txt, an XML sitemap and a readable one, RSS and Atom feeds, and structured data describing every page, every guide's sources, and me. The script also refuses to publish anything that breaks the house rules, from title length to repeated sentences to any slip into the royal plural.

I built it in a terminal session from a ThinkPad X220, connected over SSH to a DigitalOcean droplet, with Claude Code, Anthropic's AI coding assistant, as my collaborator. I decided what the site would say and checked every fact in it; the assistant handled much of the typing. The rules for that collaboration are spelled out in [how these pages are written](https://christopherabraham.com/about/editorial-policy/).

## Where it lives

GitHub Pages serves the static files over HTTPS, and Cloudflare handles DNS. Nothing on the server runs code, which keeps the site fast and leaves nothing to hack. Google Analytics is the one script on the page, with advertising features off and no analytics cookies for visitors in Europe and the UK; the [privacy page](https://christopherabraham.com/privacy/) has the details.

## How it's checked
- Every page read in Lynx, the text-only browser, as described in [the Lynx test](https://christopherabraham.com/guides/lynx-test/).
- PageSpeed Insights scores of 100 for performance, accessibility, best practices, and SEO on mobile and desktop, plus 3 of 3 for agentic browsing, as of October 6, 2026.
- Search Console and Bing Webmaster Tools, with IndexNow notifying Bing whenever a page changes.

## Code and launch

The source is public at [github.com/chrisabraham/christopherabraham](https://github.com/chrisabraham/christopherabraham). The site launched on October 6, 2026, the same day the first line of it was written.

Updated October 6, 2026
