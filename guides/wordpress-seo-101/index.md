> A beginner's WordPress SEO primer: the settings to change on day one, the plugins I recommend, alt text, descriptive links, speed, and accessibility.
>
> Source: https://christopherabraham.com/guides/wordpress-seo-101/ · Updated 2026-10-09 · By Christopher Abraham

# WordPress SEO 101: the settings and habits that matter most

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 9, 2026

WordPress runs a huge share of the web, and it is a genuinely good platform for search right out of the box. Most WordPress SEO problems I'm hired to fix come from a handful of settings nobody changed, a few plugins that fight each other, and habits like linking the words "read more" a thousand times. Here is what a beginner should do, in order, on a new site or an old one.

## Day one: five settings to check
1. **Settings, then Reading:** find "Discourage search engines from indexing this site" and make sure it is unchecked. Developers tick it while building and forget it at launch more often than you'd believe. One checkbox can keep an entire business out of Google.
2. **Settings, then Permalinks:** choose "Post name," so addresses read `/kitchen-remodeling/` instead of `/?p=123`. On an established site, change this only with redirects in place.
3. **Settings, then General:** set a real Site Title and a tagline that says what you do. Many themes print them on every page.
4. **HTTPS:** both addresses in General settings should start with `https://`. Your host can install a free certificate.
5. **Users:** give every author a real display name and a short bio. Pages signed by an actual person are easier to trust.

## The plugins I recommend

These are my personal picks after years of building and fixing WordPress sites. Install one SEO plugin only; two will fight over your titles and sitemaps.
- **[Yoast SEO Premium](https://yoast.com/wordpress/plugins/seo/).** The free version handles titles, meta descriptions, XML sitemaps, schema, and archive settings well. Premium adds a redirect manager, so changed or deleted pages never strand a visitor, and internal linking suggestions that help you connect related posts as you write. It pays for itself the first time you rename a page.
- **[WPCode](https://wpcode.com/), and WPCode Pro for schema.** The safe way to add snippets: a verification tag, a tracking code, a small PHP tweak. It keeps them in one place, survives theme changes, and spares you from editing `functions.php`, where one typo can take the site down. I use the paid Pro version for structured data: it lets me add bespoke schema to any individual page or post, so a service page, an event, or a case study can each carry markup written for exactly what that page says. Keep it consistent with what Yoast already outputs, and test every page in Google's [Rich Results Test](https://search.google.com/test/rich-results).
- **[Site Kit by Google](https://sitekit.withgoogle.com/).** Google's own plugin connects Search Console, Analytics, and PageSpeed Insights to your dashboard and verifies site ownership for you. It hardwires your site into Google's tools in a few clicks, and puts the numbers where you'll actually see them.

## Archive pages: keep the duplicates out of search

WordPress automatically makes extra pages that list your posts by tag, category, date, and author. On most small sites those pages repeat content that already lives on the posts themselves. In Yoast's settings I set tag archives, date archives, and author archives on single-author sites to stay out of search results, and leave categories indexed only when each one has a real introduction of its own. Media attachment pages, which give every uploaded image its own thin page, have been off by default for new sites since WordPress 6.4; on older sites, Yoast can redirect them to the image itself.

## Writing a post that ranks
- **The post title is your H1.** Use Heading 2 and Heading 3 blocks for sections, in order. Never pick a heading level for its size.
- **Fill in the SEO title and meta description** in the Yoast box under every post: a unique title around 50 to 60 characters and a description around 150.
- **Edit the slug** to a short, readable phrase before you publish.
- **Answer the question early,** in plain words, and add what only you know: prices, photos of your work, your process, your results.

## Alt text in the media library

Every image block and every media library item has an "Alternative text" field. Describe what the image shows in a short sentence, including any words visible in it. Leave out "image of," because screen readers already say that. Leave the field empty only for purely decorative images, so screen readers skip them. Fill it in once in the media library and WordPress reuses it wherever you insert that image.

## Kill "read more" for good

Many themes end every excerpt with a "Read more" or "Continue reading" link. On a blog page with twenty posts that's twenty identical links, each one telling crawlers and screen reader users nothing about where it goes. Link the post title instead, or change the theme's excerpt link to include the post's name. In your own writing, put links on words that describe the destination: "my [guide to accessible websites](https://christopherabraham.com/guides/accessible-websites/)," never "click here." Link new posts to your older related posts, and older posts forward to new ones; this is the internal linking that helps both readers and crawlers find your best pages.

## Put Cloudflare in front of WordPress

My strongest piece of advice after the plugins: move the domain's DNS to [Cloudflare](https://www.cloudflare.com/) and let it cache the site. The free plan is plenty for most small businesses; I pay for the Pro plan on my own main site. Both my own experience and every AI assistant I've put the question to land in the same place. And no, Cloudflare pays me nothing, which is a shame given how often I recommend it.
- **Faster pages everywhere:** Cloudflare keeps copies of your pages, images, and scripts in data centers around the world and serves them from the one nearest each visitor.
- **HTTPS done right:** choose Full (strict) for SSL/TLS, switch on Always Use HTTPS, then turn on HSTS once every page loads securely.
- **Bots on your terms:** review the bot and AI crawler settings rather than accepting the defaults. I welcome search engines and AI crawlers, since being cited by AI assistants is part of being found.
- **Cheaper domains:** Cloudflare Registrar charges what the registry charges, with no markup, at registration and renewal.

Pair it with a WordPress plugin that clears Cloudflare's cache when you update a post, so visitors never see a stale page. One caution: if your site lives on a hosted builder such as Shopify, Squarespace, or Wix, those platforms provide their own CDN and certificates. Keep any Cloudflare records there on DNS only, the gray cloud, and follow the builder's setup instructions.

## Tell the search engines
1. Verify the site in [Google Search Console](https://search.google.com/search-console/about) (Site Kit can do it for you) and submit the sitemap Yoast creates at `/sitemap_index.xml`.
2. In [Bing Webmaster Tools](https://www.bing.com/webmasters/), use the import from Google Search Console option. It copies every verified site and sitemap across in a few clicks.
3. Make sure IndexNow is on. Yoast SEO Premium includes it and pings Bing and the other participating engines every time you publish or update a post.
4. Check both consoles every few weeks for sitemap errors and pages that aren't indexed.

## Speed
- **Hosting matters most.** A good managed WordPress host beats any plugin on cheap shared hosting.
- **Use fewer plugins.** Each one can add scripts to every page. Remove what you don't use.
- **Upload sensible images.** WordPress already creates smaller sizes and lazy loads images below the fold, but a 6 MB photo straight from a phone still slows the first view. Resize before uploading, or use an image optimization plugin.
- **Add caching** if your host doesn't provide it, and test in PageSpeed Insights. My [Core Web Vitals guide](https://christopherabraham.com/guides/core-web-vitals/) covers what the scores mean.

## Accessibility

Choose a theme tagged "accessibility ready" in the WordPress theme directory; those themes have passed a review for keyboard navigation, contrast, and structure. Then keep your content accessible with real headings, alt text, descriptive links, and captions on video. Accessibility and SEO reward the same work; see [the SEO dividends of accessibility](https://christopherabraham.com/guides/accessibility-seo-dividends/).

## Updates and spam

Keep WordPress, your theme, and your plugins updated; hacked sites get spam pages injected and drop out of search fast. Turn off comments if you don't moderate them. And treat any offer of cheap backlinks, guaranteed rankings, or "AI content at scale" as the spam it is.

## Further reading
- [WordPress: the Reading settings screen](https://wordpress.org/documentation/article/settings-reading-screen/) and [the Permalinks screen](https://wordpress.org/documentation/article/settings-permalinks-screen/)
- [WordPress's built-in XML sitemaps](https://make.wordpress.org/core/2020/07/22/new-xml-sitemaps-functionality-in-wordpress-5-5/) and [the attachment page change in 6.4](https://make.wordpress.org/core/2023/10/16/changes-to-attachment-pages/)
- [WordPress performance optimization](https://developer.wordpress.org/advanced-administration/performance/optimization/)
- [Accessibility ready themes](https://wordpress.org/themes/tags/accessibility-ready/) and the [WordPress accessibility handbook](https://make.wordpress.org/accessibility/handbook/)
- [Yoast help center](https://yoast.com/help/), [WPCode on WordPress.org](https://wordpress.org/plugins/insert-headers-and-footers/), and [Site Kit on WordPress.org](https://wordpress.org/plugins/google-site-kit/)
- [Google's SEO Starter Guide](https://developers.google.com/search/docs/fundamentals/seo-starter-guide) and [Google's link best practices](https://developers.google.com/search/docs/crawling-indexing/links-crawlable)
- [Google's image SEO best practices](https://developers.google.com/search/docs/appearance/google-images) and [WebAIM on alt text](https://webaim.org/techniques/alttext/)
- [Google Search Console](https://search.google.com/search-console/about) and [PageSpeed Insights](https://pagespeed.web.dev/)

Inherited a WordPress site and not sure what's been done to it? [Send me the address](https://christopherabraham.com/contact/) and I'll tell you what I'd fix first, or see how I handle [WordPress SEO for clients](https://christopherabraham.com/services/wordpress-seo/).

## Sources
- [Yoast: We are launching an IndexNow integration in Yoast SEO](https://yoast.com/why-an-indexnow-integration/)
- [WordPress.org: Settings Reading screen](https://wordpress.org/documentation/article/settings-reading-screen/)
- [WordPress.org: Settings Permalinks screen](https://wordpress.org/documentation/article/settings-permalinks-screen/)
- [Make WordPress Core: Changes to attachment pages](https://make.wordpress.org/core/2023/10/16/changes-to-attachment-pages/)
- [Make WordPress Core: New XML sitemaps functionality in WordPress 5.5](https://make.wordpress.org/core/2020/07/22/new-xml-sitemaps-functionality-in-wordpress-5-5/)
- [Google Search Central: Link best practices](https://developers.google.com/search/docs/crawling-indexing/links-crawlable)
- [WebAIM: Alternative text](https://webaim.org/techniques/alttext/)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
