> Core Web Vitals explained without jargon: what LCP, INP, and CLS measure, why lab scores differ from field data, the usual causes, and the fixes that work.
>
> Source: https://christopherabraham.com/guides/core-web-vitals/ · Updated 2026-10-06 · By Christopher Abraham

# Core Web Vitals in plain English

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 6, 2026

Core Web Vitals are Google's three measurements of how a page feels to a real person: how fast it shows up, how quickly it responds, and whether it holds still. They're a modest ranking factor and a large conversion factor. Here's what each one means and what usually fixes it.

## The three measurements

### Largest Contentful Paint (LCP): does it show up fast?

The time until the biggest thing in the first screen, usually a hero image or headline, finishes appearing. **Good: 2.5 seconds or less.** Poor: over 4 seconds.

### Interaction to Next Paint (INP): does it respond fast?

How long the page takes to visibly react when someone taps, clicks, or types, measured across the visit and reported near the worst case. **Good: 200 milliseconds or less.** Poor: over 500. Google swapped INP in for the older First Input Delay metric in March 2024.

### Cumulative Layout Shift (CLS): does it hold still?

How much content jumps around while the page loads, the effect that makes you tap the wrong button. **Good: 0.1 or less.** Poor: over 0.25.

## Field data versus lab data

This confuses almost everyone. **Field data** comes from real Chrome users visiting your site over the past 28 days, collected in the Chrome UX Report. It's what Google uses for ranking and what Search Console's Core Web Vitals report shows. A page passes when 75% of visits meet the "good" threshold.

**Lab data** is a single simulated test, like the score at the top of PageSpeed Insights or Lighthouse in your browser. It's useful for diagnosing causes, but it isn't the number Google judges you on. A site can score 95 in the lab and fail in the field because real visitors use slower phones and networks, or the reverse.

In PageSpeed Insights, the section titled "Discover what your real users are experiencing" is field data. Start there.

## Common causes and fixes

### Slow LCP
- **Huge hero images.** Serve correctly sized images in WebP or AVIF, with srcset for different screens.
- **Lazy-loaded hero image.** Lazy loading the main image delays it. Load it eagerly and add fetchpriority="high".
- **Slow server response.** Add page caching, upgrade from overloaded shared hosting, or cache HTML at a CDN.
- **Render-blocking CSS and JavaScript.** Defer scripts that aren't needed for the first screen and remove unused stylesheets.
- **Content drawn by JavaScript.** If the main content waits for a script, render it on the server instead.

### Poor INP
- **Too much JavaScript.** Page builders, sliders, and stacks of third-party tags keep the browser busy. Remove what you don't use.
- **Heavy third-party scripts.** Chat widgets, session recorders, and ad scripts are common culprits. Load them later or after interaction.
- **Long tasks in your own code.** Developers can break up long JavaScript tasks and avoid expensive work in event handlers.

### High CLS
- **Images without dimensions.** Always set width and height so the browser reserves space.
- **Ads, embeds, and banners** that push content down. Reserve their space in advance.
- **Web fonts** that swap late and change text size. Preload key fonts and use matching fallback metrics.
- **Cookie banners** inserted at the top of the page. Overlay them instead.

## Where to look
1. **Search Console, Core Web Vitals report.** Groups failing URLs by similar pages, which usually means by template. Fix the template, fix the group.
2. **PageSpeed Insights.** Field data for a URL or the whole origin, plus lab diagnostics pointing at specific resources.
3. **Chrome DevTools, Performance panel.** For developers tracing exactly what blocks rendering or interaction.

## How long until it improves

Field data is a rolling 28-day window, so a fix shipped today shows its full effect about four weeks later. Use lab tests to confirm the fix works immediately, then watch field data climb.

## A quick self-check

Open Search Console's Core Web Vitals report and note which group of URLs fails and on which metric. Run one example through PageSpeed Insights and read the field data first, then the diagnostics. If the failing metric is LCP, look at the hero image and server response time; if INP, count the third-party scripts; if CLS, look for images without dimensions and late banners.

## Keep it in proportion

Core Web Vitals won't lift weak content above strong content. But between comparable pages they can tip the balance, and they always affect whether visitors stay. Fix the templates that carry your revenue first.

For hands-on help, see [Core Web Vitals and Cloudflare](https://christopherabraham.com/services/site-speed/). Terms are defined in the [glossary](https://christopherabraham.com/guides/glossary/).

## Sources
- [Google Search Central: Understanding Core Web Vitals and Google search results](https://developers.google.com/search/docs/appearance/core-web-vitals)
- [web.dev: Web Vitals](https://web.dev/articles/vitals)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
