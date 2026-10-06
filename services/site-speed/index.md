> Speed up a website for real visitors: Core Web Vitals diagnosis, image and script cleanup, page caching, and Cloudflare rules that still welcome crawlers.
>
> Source: https://christopherabraham.com/services/site-speed/ · Updated 2026-10-06 · By Christopher Abraham

# Core Web Vitals and Cloudflare

Slow pages lose visitors before they lose rankings. I find what's making your pages slow for real people on real phones, fix what I can reach, and specify the rest, then confirm the improvement in field data, which is what Google uses.

## The three numbers
- **Largest Contentful Paint (LCP)**: how long the main content takes to appear. Good is under 2.5 seconds.
- **Interaction to Next Paint (INP)**: how quickly the page responds when someone taps or types. Good is under 200 milliseconds.
- **Cumulative Layout Shift (CLS)**: how much the layout jumps while loading. Good is under 0.1.

Google judges each at the 75th percentile of real visits over 28 days, which is why a perfect lab score on your laptop can coexist with a failing report in Search Console. My [plain-English guide to Core Web Vitals](https://christopherabraham.com/guides/core-web-vitals/) goes deeper.

## Where the time goes
- Hero images served at desktop size to phones, without modern formats or proper sizing.
- Render-blocking CSS and JavaScript from themes, page builders, and plugins nobody uses anymore.
- Third-party tags: chat widgets, heatmaps, ad pixels, and tag managers loading tag managers.
- Slow server response from shared hosting, uncached database queries, or a missing page cache.
- Web fonts that block text or swap late and shift the layout.
- Ads and embeds without reserved space.

## Cloudflare, configured carefully

Cloudflare can make a site dramatically faster, and it can also block the crawlers you need. I set up caching rules, compression, image optimization, and HTTP/3, and I review security settings so that Googlebot, Bingbot, and the AI crawlers you want are allowed through. Bot-fight modes and "block AI crawlers" switches are decisions, and I make sure they're made on purpose. I also handle DNS moves to Cloudflare without disturbing email records.

## How I work
1. Pull field data from Search Console and the Chrome UX Report to find which templates fail, on which devices.
2. Profile representative pages in PageSpeed Insights and browser developer tools to find the specific resources at fault.
3. Fix what's within reach: image compression and sizing, caching plugins, script deferral, Cloudflare rules.
4. Write tickets for theme and code changes, with the measurement each should improve.
5. Watch field data over the following 28-day window and report what moved.

## Speed and SEO together

Some speed tricks hurt search: lazy loading the main content, deferring scripts that build the page's text, or caching pages with the wrong canonical. I check every optimization against how crawlers see the page, so speed gains don't cost indexing.

## What you receive

A short report naming each failing template, the resource responsible, and the expected gain from each fix, followed by a before-and-after comparison once the field data has caught up.

## Platforms

WordPress with WP Rocket, LiteSpeed Cache, or W3 Total Cache; WooCommerce; Shopify themes; Magento; static sites; and Next.js. For WordPress specifics, see [WordPress SEO](https://christopherabraham.com/services/wordpress-seo/).

Updated October 6, 2026
