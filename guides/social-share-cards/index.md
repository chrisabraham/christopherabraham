> How Open Graph and X card tags control the preview when a link is shared, why square images get cropped, the 1200 by 630 standard, and refreshing old previews.
>
> Source: https://christopherabraham.com/guides/social-share-cards/ · Updated 2026-10-14 · By Christopher Abraham

# Social share cards: Open Graph tags and images that fit

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 14, 2026

When someone pastes your link into Facebook, LinkedIn, X, Slack, or a text message, the preview that appears is built from a few tags in your page's head. Those tags decide the headline, the summary, and the picture. When they're missing, the platform guesses, and it guesses badly. When they're present but the image is the wrong shape, the platform crops it, and the crop usually cuts off the part that mattered.

## The tags that build the preview

The Open Graph protocol, which Facebook introduced and almost every platform now reads, asks for four properties on every page:
- `og:title`: the headline as it should appear in the preview.
- `og:type`: what the page is, usually `website` or `article`.
- `og:image`: the full address of the preview image.
- `og:url`: the page's canonical address, which the platform treats as its permanent ID.

Add `og:description` and `og:site_name` as well. Then describe the image with three structured properties: `og:image:width` and `og:image:height` in pixels, and `og:image:alt`, which the protocol defines as a description of what is in the image, not a caption.

X reads its own set of tags. The one that matters most is `twitter:card`: `summary` shows a small square thumbnail beside the text, and `summary_large_image` shows a wide image above it. I add `twitter:title`, `twitter:description`, `twitter:image`, and `twitter:image:alt` too, so nothing depends on how a platform falls back.

## Why 1,200 by 630

Meta's documentation asks for images at least 1,200 by 630 pixels for the best display on high-resolution screens, and says to keep them as close to a 1.91 to 1 ratio as you can so the whole image shows in the feed without cropping. Images smaller than 600 by 315 get shown small. Files must stay under 8 MB. LinkedIn and X lay out their large previews as wide rectangles too, so one image at 1,200 by 630 serves all of them.

Declaring the width and height matters more than it looks. Meta says those two tags let its crawler render the image immediately. Without them, the first person to share a new page can get a preview with no picture while the platform downloads and measures the file.

## The square artwork trap

Square images are everywhere: podcast covers, product photos, logos, album art. Put a square image in a large card, and every platform crops it to a wide strip from the middle. The top and bottom are gone, and on cover art that's usually where the title is.

I found exactly this on a podcast site I built. Every page had complete Open Graph and X tags, and every image existed at the declared size, so a tag audit passed. But 458 episode pages pointed at square cover art inside large cards, so every shared episode lost the top and bottom of its cover. More than two hundred episodes shared the same default cover, so their previews were also identical. The fix was a generated card for each episode, 1,200 by 630, with the cover art on one side and the episode title in large type on the other. The build makes the card once, reuses it on every later build, and makes a new one when an episode is renamed.

If you can't generate cards, switch square images to the `summary` card on X, which shows a square thumbnail uncropped, and accept a smaller preview elsewhere.

## Making the image work as a preview
- **Put the page's own title in the image** when pages share artwork, so each preview is distinct.
- **Keep important content near the center.** Some apps trim the edges or round the corners.
- **Use large type.** Most previews are seen on phones, at a fraction of full size.
- **Use JPEG for photos and artwork** and keep files in the low hundreds of kilobytes.
- **Write alt text** that describes the image, since some apps read it aloud.

## Checking your pages

View the source of a page and confirm every tag is present, every image address is absolute and loads, and every declared size matches the real file. On a large site, crawl it with Screaming Frog and extract the `og:image` value from each page, then check the images in bulk; the method is in my guide to [custom extraction](https://christopherabraham.com/guides/custom-extraction/). Group the results by image. A single image behind hundreds of pages is a sign your previews all look the same.

## Refreshing previews that are already out there

Platforms cache what they fetch. Meta notes that changing the image for a URL doesn't update the preview on old shares. After fixing a page, paste its address into Meta's Sharing Debugger and ask it to scrape again, and do the same in LinkedIn's Post Inspector. Other platforms refresh on their own schedule.

## Where this fits

Share cards don't move rankings directly. They decide whether a shared link gets clicked, and clicks bring the visits, links, and mentions that do matter. I check them in every audit and build them into every site I make; see [static websites built for search](https://christopherabraham.com/services/static-sites/) and [podcast website SEO](https://christopherabraham.com/services/podcast-website/).

## Let me help you with this

If you'd rather have this done than do it yourself, it's exactly the work I do for clients. Tell me about your site and I'll tell you where I'd start.

[Book a 30 minute call](https://calendly.com/chrisabraham/30) [Call +1 202-352-5051](tel:+12023525051) [Email cja@well.com](mailto:cja@well.com)

Prefer to hire through Upwork? I'm [Top Rated there too](https://www.upwork.com/freelancers/chrisjabraham).

## Sources
- [The Open Graph protocol](https://ogp.me/)
- [Meta for Developers: Images in link shares](https://developers.facebook.com/docs/sharing/webmasters/images/)
- [Meta for Developers: Sharing Debugger](https://developers.facebook.com/tools/debug/)
- [LinkedIn Post Inspector](https://www.linkedin.com/post-inspector/)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
