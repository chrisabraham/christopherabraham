> When a product sells out or retires: keep the URL for a restock, redirect a true replacement, return a 404 when nothing fits, and keep availability accurate.
>
> Source: https://christopherabraham.com/guides/out-of-stock-products/ · Updated 2026-11-19 · By Christopher Abraham

# Out-of-stock and discontinued product pages

By [Christopher Abraham](https://christopherabraham.com/about/) · Published November 19, 2026

Every store eventually has to decide what happens to a product page when the shelf is empty. Most stores never make the decision on purpose, so the platform makes it for them: the page vanishes from the category, the URL starts returning an error, or the product sits there for years with an "unavailable" badge and nothing else to say. Each of those defaults has a cost in search. The fix is a short written policy that sorts every empty product into one of four cases and treats each case the same way every time.

## Sold out for now, or gone for good

The first question is whether the product is coming back. A product that is sold out with a restock date, on backorder, or seasonal is temporarily unavailable, and its page should stay exactly where it is. The URL has collected links, reviews, and search history, and all of that is waiting for the stock to arrive. A product the manufacturer has stopped making, or one you have decided to stop carrying, is permanently unavailable, and it needs a different treatment.

Store owners usually know the answer, but the store itself rarely records it. The inventory count says zero in both cases. I ask clients for one extra field per product, or a tag, that separates "restocking" from "retired," because every later decision depends on it and nobody can tell the two apart from the outside.

## Case one: the product is coming back

Keep the page live, keep it returning a 200 status, and keep it in the XML sitemap. Then make the page useful to the person who lands on it while the product is out:
- Say plainly that it's out of stock, and give the expected date if you have one.
- Offer a back-in-stock email signup, and link the two or three closest alternatives that are in stock now.
- Leave the description, specifications, photos, and reviews in place. A page stripped down to a title and a "sold out" badge looks empty to Google, and Search Console can report it as a soft 404, the label Google uses for a page that answers 200 but reads like an error or a blank.

Shopify and WooCommerce both have settings that change what happens at zero stock, and they are worth checking before the holidays. Shopify's "Continue selling when out of stock" keeps taking orders past zero, which suits preorders and products already on the truck. WooCommerce's "Out of stock visibility" box hides out-of-stock items from the store catalog. Hiding them pulls the product out of category pages and internal search, which also removes the internal links pointing at it, so I leave that box unticked for products that are coming back. Before changing either setting on a live store, load one affected product URL and look at what it actually returns.

## Case two: there's a true replacement

When a product is retired and a successor does the same job, a 301 redirect from the old URL to the new product is the right call. Google treats a permanent redirect as a signal that the destination should be the canonical URL and shows the new page in results. The test is whether a shopper who searched for the old model would be satisfied to land on the new one. A newer version of the same item, the same product under a new SKU, or a renamed product all pass. A different brand at a similar price usually doesn't.

Some retired products still get traffic from people who own them and need parts, manuals, or compatibility answers. Those pages earn their keep as reference pages: mark the product discontinued, keep the specifications and support material, and link the replacement prominently. Redirecting them throws away the reason people come.

## Case three: nothing fits

If the product is gone and there's no close successor, let the URL return a 404 or a 410. Google's documentation says it handles every 4xx status other than 429 the same way: the URL drops out of the index, and Google crawls it less over time. A 404 here is the honest answer, and Search Console's own help says a 404 isn't necessarily a problem when a page was removed with no replacement.

The tempting shortcut is to redirect every dead product to the home page or to the top of a category. A redirect only helps when the destination answers the same need, and a shopper who clicked a specific product and arrived on the home page has learned nothing. I send a retired product to its category only when the category is a fair substitute, such as a single colorway of an item that is still sold in other colors. Otherwise the page gets a helpful 404 template with search and the main categories, and the URL comes out of the sitemap.

## Case four: variants and colorways

When one size or color sells out on a product that is otherwise available, the product page stays as it is. The work is in making the sold-out variant clear on the page and in the data: grey out the option, say it's out of stock, and keep the variant's own availability accurate in the structured data and the product feed. If variants have their own URLs, treat each variant URL by the same four cases.

## Tell machines the same thing you tell shoppers

The page, the structured data, and the Merchant Center feed should all agree about availability. On the page, Product markup carries an `offers.availability` value, and Google's merchant listing documentation accepts one value per offer, including InStock, OutOfStock, BackOrder, PreOrder, SoldOut, and Discontinued. In Merchant Center, the `availability` attribute takes in_stock, out_of_stock, preorder, or backorder, and preorder and backorder items also need an availability date that matches the shipping date shown on the page.

Mismatches are the common failure. A theme that hardcodes InStock in its JSON-LD, or a feed that syncs once a day while the store sells out in an hour, tells Google one thing and shoppers another. My [small business schema guide](https://christopherabraham.com/guides/small-business-schema/) covers the Product markup itself, and the [Merchant Center free listings guide](https://christopherabraham.com/guides/merchant-center-free-listings/) covers the feed.

## Write the policy down

The policy fits on one page: the restocking and retired tag, the rule for each of the four cases, who decides which replacement is close enough, and a monthly check. For the check, I export every product with zero stock, compare it against the URLs that return 404 or redirect, and look in Search Console's Page indexing report for soft 404s on product templates. The [Page indexing report guide](https://christopherabraham.com/guides/page-indexing-report/) explains how to trace those counts back to the template, and the [301 redirect rules](https://christopherabraham.com/guides/redirect-rules/) cover how to build and test the redirect map in bulk.

After the holidays is the natural time to run it, when the season's best sellers have sold through and the January catalog cleanup starts. A store that writes the policy in November makes those January decisions in an afternoon.

## Questions about out-of-stock pages

### Should I delete out-of-stock products from my store?

Only if they are never coming back. A product that will restock should keep its page and URL live, with the description, reviews, and an honest note about availability, so it keeps its search history for the day the stock returns.

### Is it bad to redirect discontinued products to the home page?

Yes. A redirect helps only when the destination meets the same need. Send a discontinued product to a true replacement if one exists, keep it as a reference page if owners still need its specifications, and otherwise let it return a 404.

### What availability value should a sold-out product use in structured data?

Use OutOfStock for a product that is temporarily unavailable, BackOrder or PreOrder when orders are still taken, and Discontinued when it's gone for good. Google's merchant listing documentation allows one value per offer, and the value should match the page and the Merchant Center feed.

## Related reading

More guides on online stores and the selling season:
- [Black Friday sale pages that keep their rankings](https://christopherabraham.com/guides/black-friday-pages/)
- [Google Merchant Center free listings for small shops](https://christopherabraham.com/guides/merchant-center-free-listings/)
- [Selling inside AI assistants: the real state of play](https://christopherabraham.com/guides/agentic-checkout/)

When you want it done for you:
- [Ecommerce SEO](https://christopherabraham.com/services/ecommerce-seo/)
- [Peak season readiness](https://christopherabraham.com/services/peak-season-readiness/)
- [AI shopping readiness for small online shops](https://christopherabraham.com/services/ai-shopping-readiness/)

## Let me help you with this

If you'd rather have this done than do it yourself, it's exactly the work I do for clients. Tell me about your site and I'll tell you where I'd start.

[Book a 30 minute call](https://calendly.com/chrisabraham/30) [Call +1 202-352-5051](tel:+12023525051) [Email cja@well.com](mailto:cja@well.com)

Prefer to hire through Upwork? I'm [Top Rated there too](https://www.upwork.com/freelancers/chrisjabraham).

## Sources
- [Google Search Central: Merchant listing (Product, Offer) structured data](https://developers.google.com/search/docs/appearance/structured-data/merchant-listing)
- [Google Search Central: How HTTP status codes and network errors affect Google Search](https://developers.google.com/search/docs/crawling-indexing/http-network-errors)
- [Google Search Central: Redirects and Google Search](https://developers.google.com/search/docs/crawling-indexing/301-redirects)
- [Search Console Help: Page indexing report](https://support.google.com/webmasters/answer/7440203)
- [Google Merchant Center Help: Availability](https://support.google.com/merchants/answer/6324448)
- [Shopify Help Center: Selling out of stock products](https://help.shopify.com/en/manual/products/inventory/getting-started-with-inventory/selling-when-out-of-stock)
- [WooCommerce: Products settings](https://woocommerce.com/document/configuring-woocommerce-settings/products/)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
