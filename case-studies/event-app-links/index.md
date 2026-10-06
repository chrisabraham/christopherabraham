> An event discovery app built with Create React App had 2,000 event pages Google never found. A 13 page spec, ranked P0 to P3, gave the developer exact fixes.
>
> Source: https://christopherabraham.com/case-studies/event-app-links/ · Updated 2026-10-06 · By Christopher Abraham

# Event discovery app: 2,000 pages with no way in

A nightlife and event discovery app built on Create React App needed roughly 2,000 event pages in Google. After three months, Search Console showed impressions for the home page and close to nothing anywhere else.

## The engagement

I diagnosed, wrote the specification, and verified the work. The founder's developer built the fixes.

## Four findings
1. **The home page was empty to crawlers.** The server returned a single empty root element; everything visible was drawn later by JavaScript.
2. **Event cards weren't links.** They navigated with click handlers, so there were no anchor tags for a crawler to follow.
3. **The event pages were orphans.** Ironically, the event pages already had server-side rendering and decent HTML. Nothing pointed to them.
4. **Canonicals pointed home.** The events and community sections declared the home page as their canonical, effectively telling Google they were copies of it.

## The deliverables

A short plain-language summary for the founder, and a 13-page specification for the developer covering 12 items ranked from P0 to P3. Each item carried the evidence, why it mattered, the build steps, and an acceptance test. The P0 items: real anchor links on every event card, server rendering for the home page and the event feed, and indexing requests for priority pages once those shipped.

## Verification

Every item had a test anyone could run, for example "event links appear in the server HTML of the feed" and "each section's canonical references itself." I checked the developer's work against those tests with a crawl and Search Console's live URL test.

## The takeaway

Good pages can still be invisible if nothing links to them in a way crawlers understand. Real links in real HTML remain the foundation of discovery. More under [JavaScript SEO](https://christopherabraham.com/services/javascript-seo/).

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)

Updated October 6, 2026
