> Make JavaScript and headless websites visible to search and AI crawlers: rendering comparisons, crawlable links, prerendering, and code level review.
>
> Source: https://christopherabraham.com/services/javascript-seo/ · Updated 2026-10-06 · By Christopher Abraham

# JavaScript and headless SEO

A modern site can look perfect in a browser and nearly empty to a crawler. If your content depends on JavaScript to appear, some crawlers will see it late, some will see part of it, and most AI crawlers will never see it at all. I find the gap and specify the fix in terms your developers can build.

## Why it matters more every year

Googlebot renders JavaScript, eventually, in a second pass with limits on time and resources. Bingbot renders less reliably. Most of the crawlers that feed AI assistants, including those from OpenAI, Anthropic, and Perplexity, fetch the HTML and move on. Content that exists only after scripts run is content those systems can't quote.

## Patterns I find again and again
- **An empty shell.** A single-page app whose server HTML holds one empty root element.
- **Links that aren't links.** Cards and menus that navigate with click handlers instead of real anchor tags, leaving crawlers no path to deeper pages.
- **Content gated on interaction.** Specs, reviews, and FAQs that mount only on scroll, hover, or tab click. Crawlers don't scroll or click.
- **Consent tools blocking content scripts.** A cookie banner holding back the script that builds the article, so bots, which never consent, get a blank page.
- **Head tags set late.** Titles, canonicals, and robots directives written by client-side code, which crawlers may read before or after the change.
- **Soft 404s.** Missing routes that return a 200 status with a "not found" message drawn by the app.

## How I diagnose it

For each important template, I compare three versions of the page: the raw HTML from the server, the DOM after rendering, and the text a crawler extracts. Screaming Frog in JavaScript mode, Search Console's URL Inspection live test, and a plain fetch with no scripts at all make the differences obvious. When I have repository access, I read the routes, components, and build configuration to find exactly where the content is gated.

## What the fix usually looks like
- Server-side rendering or static prerendering for pages that need to rank.
- Real anchor links in the server HTML for every navigable item.
- Interactive effects kept as progressive enhancement, on top of content that's already in the HTML.
- Head tags rendered on the server, with self-referencing canonicals per route.
- Proper 404 and 410 status codes for missing routes.

## Stacks I've worked in

React and Create React App, Next.js on Vercel and Netlify, Vue, Alpine.js on Magento's Hyvä theme, Sanity and other headless CMSs, Shopify themes, and WordPress builds with heavy page builders. I can open a pull request for metadata and template changes, or hand your developer a spec with acceptance criteria and verify what ships.

## Examples

See [product content hidden behind scroll triggers](https://christopherabraham.com/case-studies/scroll-gated-products/), [a React app with 2,000 unreachable pages](https://christopherabraham.com/case-studies/event-app-links/), and [SEO fixes merged through GitHub on Sanity and Vercel](https://christopherabraham.com/case-studies/headless-local/).

Updated October 6, 2026
