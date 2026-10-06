> Ten rules for 301 redirects in migrations and redesigns: map one to one, avoid chains, keep redirects for years, use 410 on purpose, and test in bulk.
>
> Source: https://christopherabraham.com/guides/redirect-rules/ · Updated 2026-10-06 · By Christopher Abraham

# Ten rules for 301 redirects that keep your rankings

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 6, 2026

A 301 redirect tells browsers and search engines that a page has moved permanently and where to find it. Handled well, redirects carry rankings, links, and bookmarks to a new address. Handled carelessly, they quietly erase years of search equity. These are the rules I follow on every migration.

## 1. Inventory before you redirect

You can't redirect URLs you don't know about. Build the old URL list from several sources: a full crawl, every XML sitemap, Search Console's performance and indexing exports, analytics landing pages over at least a year, and backlink tools. Old campaign pages and PDFs that nobody links from the menu often carry the most external links.

## 2. Map one to one, to the closest equivalent

Each old URL should point to the new page that best serves the same visitor. A product goes to the same product, a category to the same category, an article to its new address. When the content is merged, point to the merged page.

## 3. Don't send everything to the home page

Redirecting hundreds of old pages to the home page is easy and almost worthless. Google treats irrelevant redirects as soft 404s, and the equity those pages carried is lost. If there's no real equivalent, use rule 6.

## 4. Use 301 or 308 for permanent moves

A 301 (or 308, which also preserves the request method) signals a permanent move. A 302 or 307 says "temporarily elsewhere," and search engines may keep the old URL indexed. Meta refresh and JavaScript redirects work in some cases, but server-side redirects are the clear signal.

## 5. No chains, no loops

Each redirect should go straight to the final destination in one hop. Chains build up over years: http to https, then www to apex, then old path to new path. Every hop adds delay and risks the crawler giving up. When you add new redirects, update the old ones to point at the final URL.

## 6. Use 410 deliberately

For pages that are gone for good with no replacement, a 410 status says so plainly and gets them dropped from the index faster than a 404. Use it for retired products with no successor, expired events, and spam pages left from a hack.

## 7. Keep redirects for years

Search engines need time to process a move, and links, bookmarks, and old emails keep sending visitors for years. Keep redirects in place for at least a year, and for valuable URLs, indefinitely. Removing them to "clean up" the configuration is a common way to lose traffic a second time.

## 8. Update everything that points at old URLs

Redirects are a safety net, not the plan. Update internal links, canonical tags, hreflang annotations, XML sitemaps, structured data, and your Google Business Profile website link to point directly at new URLs. Ask the sites that link to you most to update their links too.

## 9. Preserve parameters and casing on purpose

Decide how query strings, trailing slashes, and uppercase URLs are handled. Tracking parameters should usually pass through; old filter parameters may need their own rules. Test a handful of odd real URLs from your logs, not just the clean ones.

## 10. Test in bulk, then watch

Before launch, run the full old URL list against staging and confirm each returns one 301 to the expected destination, which then returns 200. Repeat on launch day against production. Afterward, watch 404 reports in Search Console and Bing Webmaster Tools, your server logs, and traffic by page group for several weeks.

## Where redirects live
- **Apache:** .htaccess or the virtual host configuration.
- **Nginx:** server blocks with return 301 or map files for large lists.
- **WordPress:** Rank Math, Yoast Premium, or the Redirection plugin, or the server for large maps.
- **Shopify:** URL Redirects under Navigation, with CSV import.
- **Netlify and Vercel:** _redirects files or the platform's configuration file.
- **Cloudflare:** Bulk Redirects or Redirect Rules at the edge, useful when the origin can't do it.
- **GitHub Pages and other static hosts:** no server redirects, so a page with a meta refresh and a canonical tag is the fallback.

## A note on disavow files

Migrations are a common moment to review backlinks. Disavow only genuinely manipulative or spammy links, and keep legitimate ones; disavowing good links throws away the equity your redirects are trying to preserve.

For a full move, see [site migrations and 301 redirects](https://christopherabraham.com/services/migrations/), or [a clinic's redirect decisions URL by URL](https://christopherabraham.com/case-studies/clinic-migration/).
