> AI app builders ship a site in an afternoon. Here is how to check that Google and AI crawlers can read it: rendering, links, titles, status codes, and sitemaps.
>
> Source: https://christopherabraham.com/guides/ai-built-websites/ · Updated 2026-10-13 · By Christopher Abraham

# SEO for websites built with AI app builders: what to check before you launch

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 13, 2026

Describe a business to Lovable, Bolt, v0, or a coding assistant, and an afternoon later there's a good looking website. Plenty of founders now launch exactly this way, and I'm all for it. The catch is that a site can look perfect in your browser while search engines and AI crawlers receive something close to an empty page. These are the checks I run on every AI-built site, in the order I run them.

## Know how your site renders

Everything else depends on one question: does the server send finished HTML, or does it send a script that builds the page in the visitor's browser? The second approach, client-side rendering, is how many React single page apps work. Google can render JavaScript, but its own documentation describes rendering as a separate step after crawling, and recommends server-side rendering or prerendering because it's faster for everyone and because not every bot runs JavaScript. Many AI crawlers fetch the raw HTML and stop there.

Defaults change quickly, so check rather than assume. Lovable is a good example. Its documentation says apps created from May 13, 2026 (June 22, 2026 for Enterprise workspaces) use TanStack Start, which renders pages on the server. Older Lovable apps are React and Vite apps that render in the browser; for those, Lovable serves prerendered copies of published pages to verified search engines, social preview bots, and AI crawlers, and it offers an upgrade path to the newer stack. If your site was built before the change, find out which one you have.

## The two minute test

Open a page, then open its source with View Source (not the inspector, which shows the page after scripts run). Search the source for a sentence from the middle of the page. If it's there, crawlers that don't run JavaScript can read it. If the source is mostly a single empty `div` and a script tag, your content exists only after rendering. For a fuller picture, run the URL through Search Console's URL Inspection tool and look at the rendered HTML Google captured. My [text browser test](https://christopherabraham.com/guides/lynx-test/) is another quick way to see a page the way the simplest bots do.

## Check that every page has its own address

Search engines index URLs. If the "Services" and "About" sections are views inside one page, or live behind a `#` in the address, they may never be indexed as pages at all. Each page you want found needs its own clean path, such as `/services/`, that loads that page directly when someone pastes it into a new tab.

## Check the links are real links

Generated code often moves between pages with a button and a click handler. It works for people and is invisible to crawlers. Google says plainly that it can follow links only when they're `<a>` elements with an `href`. Crawl the site with a crawler such as Screaming Frog; if it finds only the home page, your navigation is the reason. Ask the builder to change navigation to its router's link component, which produces real anchors.

## Check titles and descriptions per page

A common result of a fast build is one title, written for the home page, on every URL. Look at the browser tab on five different pages. Each needs its own title and meta description, present in the HTML the server sends. The same goes for the canonical tag: one that points every page at the home page tells Google to ignore the rest.

## Check what a missing page returns

Type a nonsense address on your site. Single page apps often show a friendly "not found" message while telling crawlers everything is fine, with a 200 status code. Google calls these soft 404s, and a site with many of them wastes crawling on pages that don't exist. A missing page should return a real 404, and a moved page a 301 redirect.

## Give crawlers a map and an open door
- **A sitemap.** An XML sitemap listing every real page, submitted in Google Search Console and Bing Webmaster Tools.
- **A robots.txt that allows the bots you want.** Check it by hand; generated files sometimes block everything, a leftover from a staging setup.
- **Structured data.** Organization or LocalBusiness markup in the server HTML, matching what the page says. My [small business schema guide](https://christopherabraham.com/guides/small-business-schema/) has examples.

## Own the code

Most AI builders can sync a project to GitHub. Do it on day one, in an account your business controls. A repository means any developer, or any SEO who works in code, can fix problems at the template level instead of patching pages through a chat window. I explain why that matters in [SEO in your Git repository](https://christopherabraham.com/guides/seo-in-your-repository/).

## Where I fit

Rendering problems are my specialty; I once found 2,000 event pages Google had never discovered in a React app, and the [case study](https://christopherabraham.com/case-studies/event-app-links/) shows how. If you built your site with an AI tool and it isn't showing up in search, [send me the URL](https://christopherabraham.com/contact/). I'll tell you what the crawlers see, and if there's a problem, I'll write the fix in a form you can paste straight back into the builder. More on that work is on my [JavaScript SEO](https://christopherabraham.com/services/javascript-seo/) page.

## Let me help you with this

If you'd rather have this done than do it yourself, it's exactly the work I do for clients. Tell me about your site and I'll tell you where I'd start.

[Book a 30 minute call](https://calendly.com/chrisabraham/30) [Call +1 202-352-5051](tel:+12023525051) [Email cja@well.com](mailto:cja@well.com)

Prefer to hire through Upwork? I'm [Top Rated there too](https://www.upwork.com/freelancers/chrisjabraham).

## Sources
- [Lovable Documentation: FAQ (rendering and SEO)](https://docs.lovable.dev/introduction/faq)
- [Google Search Central: Understand the JavaScript SEO basics](https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics)
- [Google Search Central: Dynamic rendering as a workaround](https://developers.google.com/search/docs/crawling-indexing/javascript/dynamic-rendering)
- [Google Search Central: Make your links crawlable](https://developers.google.com/search/docs/crawling-indexing/links-crawlable)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
