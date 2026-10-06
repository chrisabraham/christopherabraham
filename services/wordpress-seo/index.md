> WordPress SEO done carefully: Yoast and Rank Math settings, theme and plugin conflicts, page builder bloat, caching, and old installs that need a steady hand.
>
> Source: https://christopherabraham.com/services/wordpress-seo/ · Updated 2026-10-06 · By Christopher Abraham

# WordPress SEO

WordPress runs a large share of the web, and a large share of the SEO problems I see. Not because WordPress is bad at SEO, but because years of themes, page builders, and plugins pile up on top of each other. I've worked in WordPress since its early days and know where the problems hide.

## SEO plugins, configured properly

Yoast SEO and Rank Math do a lot of work most owners never see: titles and descriptions, canonical tags, robots directives, XML sitemaps, breadcrumbs, and structured data. That's why turning one off, even for an afternoon, can knock pages out of the index. I review the settings that matter:
- Which content types, taxonomies, and archives appear in sitemaps and which are noindexed.
- Title and description templates per post type, with sensible fallbacks.
- Schema settings for the organization or person behind the site, and per post type.
- Breadcrumbs, redirects, and 404 monitoring.
- Conflicts when two SEO plugins, or a theme and a plugin, both write the same tags.

## Common WordPress problems
- **Attachment pages indexed** as thin pages for every image ever uploaded.
- **Tag and category archives** that duplicate each other and outnumber real content.
- **"Discourage search engines" left checked** after launch.
- **Page builder bloat** from Elementor, Divi, WPBakery, or Avada, adding layers of markup and scripts.
- **Plugins nobody remembers installing**, each loading assets on every page.
- **Mixed content and redirect loops** after an HTTPS change.
- **Spam pages** left behind by an old hack, still indexed.

## Performance on WordPress

A page cache, image compression, script deferral, database cleanup, and a CDN fix most slow WordPress sites. I configure WP Rocket, LiteSpeed Cache, or W3 Total Cache, test that caching doesn't serve the wrong canonical or a logged-in view to crawlers, and connect Cloudflare where it helps. More on speed under [Core Web Vitals and Cloudflare](https://christopherabraham.com/services/site-speed/).

## WooCommerce

Product and category templates, faceted navigation, out-of-stock handling, and product schema are covered under [ecommerce SEO](https://christopherabraham.com/services/ecommerce-seo/).

## How I work safely

I work with an editor or administrator role as the job requires, on a staging copy when one exists. Before changing plugin settings I export them, and every change goes in a written log so it can be undone. Theme edits go into a child theme, never the parent. If the site has no backups, setting them up comes first.

## Access I'll ask for

An administrator login for configuration work, or an editor login for content-only work, plus hosting or staging access when caching and server settings are in scope.

## Older installs

I'm comfortable inside a fifteen-year-old WordPress site with a custom theme nobody can explain. The goal is to make it sound for search without breaking what works, and to tell you honestly when a rebuild would cost less than another round of patches.

An example of what goes wrong when the SEO plugin is switched off: [recovering a WooCommerce store's indexing](https://christopherabraham.com/case-studies/plugin-outage/).

Updated October 6, 2026
