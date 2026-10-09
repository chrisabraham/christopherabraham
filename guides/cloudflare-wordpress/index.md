> How to put a WordPress site behind Cloudflare: moving DNS, what the free plan already does, APO and Polish on paid plans, HTTPS settings, and a monthly budget.
>
> Source: https://christopherabraham.com/guides/cloudflare-wordpress/ · Updated 2026-10-09 · By Christopher Abraham

# Cloudflare for WordPress: setup, plans, and what to budget

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 9, 2026

If I could make one change to most of the WordPress sites I'm asked to look at, it would be putting them behind Cloudflare. It makes them faster, safer, and cheaper to run, and the free plan alone covers a lot of ground. My own experience and every AI assistant I've put the question to agree. For the record, Cloudflare pays me nothing for saying so, which, given how often I say it, is a little sad.

## Two ways to use Cloudflare

Every DNS record in Cloudflare shows a cloud. A gray cloud means DNS only: Cloudflare tells browsers where your server is, then steps aside. An orange cloud means proxied: visitors reach Cloudflare's network first, and it serves what it can from the data center nearest them before passing the rest to your host. The speed and protection only apply to orange records.
- **Gray, DNS only:** if Cloudflare just registers the domain and answers DNS, the free plan is all you need.
- **Orange, proxied:** this is where WordPress gains the most, and where the paid features become worth considering.

## What the free plan does once you're proxied
- Caches your images, scripts, and stylesheets close to visitors. HTML pages aren't cached by default; that takes APO or a cache rule, below.
- Compresses files on the way out.
- Provides HTTPS certificates at no cost.
- Absorbs denial of service attacks before they reach your host.
- Tells Bing and other engines that support IndexNow when your content changes, through a free feature called Crawler Hints.

## The paid features that matter for WordPress
- **Automatic Platform Optimization (APO):** caches whole WordPress pages at Cloudflare's edge, so even the first byte arrives fast from anywhere. It works with the official Cloudflare WordPress plugin, comes included with the Pro plan and above, and costs $5 a month on the free plan.
- **Polish:** compresses images and can convert them to WebP automatically. Available on Pro and above.

Even though Cloudflare can cost nothing, when a WordPress site runs through it I recommend budgeting about $50 a month for Cloudflare's paid services, starting with Pro. WordPress almost always benefits. I pay for Pro on my own main site.

## Setting it up
1. **Add the site** in a free Cloudflare account. Cloudflare scans your existing DNS records; compare them against your current DNS provider line by line, especially mail records, before going further.
2. **Change the nameservers** at your registrar to the two Cloudflare gives you. Or transfer the domain to Cloudflare Registrar, which charges the registry's wholesale price with no markup on renewals.
3. **Turn the website records orange.** Leave mail records gray.
4. **Set SSL/TLS to Full (strict)**, which requires a valid certificate on your host; most hosts provide one free. Flexible mode can trap WordPress in an endless redirect loop.
5. **Switch on Always Use HTTPS,** then HSTS once every page loads securely.
6. **Install the official Cloudflare WordPress plugin,** connect it, and turn on APO if you have it, so your cache clears automatically when you publish or edit.
7. **Check the bot and AI crawler settings.** Make sure search engines and the AI crawlers you want, such as the ones behind ChatGPT search and Perplexity, aren't blocked. I let them in; being cited by AI assistants is part of being found.
8. **Turn on Crawler Hints** under Caching.
9. **Test** your home page and a post in PageSpeed Insights before and after.

## What to leave alone
- **Rocket Loader** rewrites how scripts load. It can speed up a simple site and break a complex one, including forms, analytics, and cookie banners. If anything acts strangely, turn it off first.
- **Caching the admin.** Never cache `/wp-admin/`, the login page, carts, checkouts, or account pages. APO is built to skip logged-in visitors and the admin; any cache rule you write by hand has to exclude them too.
- **Under Attack Mode** challenges every visitor, search engine crawlers included. Use it during an actual attack only.

## When Cloudflare isn't the right layer

If a site runs on a hosted builder such as Shopify, Squarespace, or Wix, the builder already provides a CDN and certificates. Cloudflare can still hold the domain and answer DNS, but keep those records gray and follow the builder's own connection instructions. Some managed WordPress hosts also bundle Cloudflare or their own CDN; ask before stacking two.

For the rest of the WordPress basics, see [WordPress SEO 101](https://christopherabraham.com/guides/wordpress-seo-101/), and for what the speed scores mean, my [Core Web Vitals guide](https://christopherabraham.com/guides/core-web-vitals/). Want Cloudflare set up on your site without the guesswork? [Tell me about it](https://christopherabraham.com/contact/).

## Sources
- [Cloudflare Docs: Default cache behavior](https://developers.cloudflare.com/cache/concepts/default-cache-behavior/)
- [Cloudflare: Automatic Platform Optimization for WordPress](https://www.cloudflare.com/automatic-platform-optimization/wordpress/)
- [Cloudflare Docs: Automatic Platform Optimization](https://developers.cloudflare.com/automatic-platform-optimization/)
- [Cloudflare Docs: Polish](https://developers.cloudflare.com/images/polish/)
- [Cloudflare Docs: Crawler Hints](https://developers.cloudflare.com/cache/advanced-configuration/crawler-hints/)
- [Cloudflare Docs: Cloudflare Registrar](https://developers.cloudflare.com/registrar/)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
