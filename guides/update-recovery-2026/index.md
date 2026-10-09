> How to tell whether a 2026 Google core or spam update hit your site, rule out reporting quirks, find the pages that lost, and fix them in the right order.
>
> Source: https://christopherabraham.com/guides/update-recovery-2026/ · Updated 2026-10-09 · By Christopher Abraham

# Hit by a 2026 Google update? A recovery checklist that works

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 9, 2026

Google confirmed two core updates and four spam updates between March and October 2026. When traffic falls in a year like that, the first instinct is to change everything at once. Resist it. Recovery starts with knowing which update, if any, actually touched you, and which pages took the loss. Here is the order I work in when a client calls with a graph that points down.

## 1. Line the drop up with the calendar

Open Google's Search Status Dashboard and note this year's ranking updates: a spam update on March 24, the March core update from March 27, the May core update from May 21, and spam updates starting June 24, August 18, and September 24. Then open Search Console, set the date range to sixteen months, and compare. A drop that begins within a few days of a rollout's start is a strong lead. A drop that began weeks before one, or on the day a redesign launched, points somewhere else.

## 2. Rule out the reporting quirks
- **The num=100 change.** In September 2025 Google stopped serving a hundred results per page to rank trackers, and desktop impressions in Search Console fell for most sites while average position rose. If your comparison spans that month and clicks held steady, nothing happened to real visitors.
- **Seasonality.** Compare against the same weeks last year before blaming an algorithm.
- **Tracking breaks.** If analytics fell but Search Console clicks didn't, a broken tag or consent banner is the suspect.

## 3. Decide which kind of update it was

The two kinds behave differently. A core update re-ranks pages against each other; losses tend to spread across many queries and pages, often by moderate amounts. A spam update applies detection systems for policy violations; losses are usually steep, fast, and concentrated in the sections that triggered them. Also check Search Console's Manual actions report. Algorithmic hits stay off that report, so an empty report plus a cliff on a spam update date tells you an automated system made the call.

## 4. Find the pages that lost

In the Performance report, compare the two weeks after the update with the two weeks before, by page. Sort by lost clicks. Usually a minority of pages accounts for most of the loss, and they share something: the same template, the same author, the same type of content, or the same section of the site. That shared trait is the real finding.

## 5. Match the losers against the spam policies

Read Google's spam policies with that list of pages open. The ones that matter most this year:
- **Scaled content abuse:** lots of pages made mainly to rank, by AI, by people, or both. Programmatic city pages, mass "best of" lists, and unreviewed AI articles are the usual suspects.
- **Site reputation abuse:** third-party content hosted in your subfolder or subdomain to borrow your site's standing.
- **Expired domain abuse:** an old domain repurposed for unrelated, low-value content.
- **Manipulating AI answers:** since May, hidden text or instructions aimed at AI Overviews and AI Mode count as spam too.

If any of these describe the losing pages, remove or rewrite them before anything else. A policy problem outweighs every improvement elsewhere.

## 6. Fix in order of value
1. **Delete or consolidate** thin and duplicate pages, redirecting any with links or traffic to the closest strong page.
2. **Rewrite the pages worth keeping** with what only you can add: real examples, photos, numbers, procedures you follow, and the name of the person who knows the subject.
3. **Check access** for every crawler you care about, Googlebot, Bingbot, and the AI search crawlers, at the robots.txt, CDN, and firewall levels.
4. **Make structured data honest:** every claim in the markup should be visible on the page.

## 7. Set the right expectations

Google describes core updates as broad changes that don't target specific sites, and says it can take several months for its systems to confirm that improved content is helpful; if nothing moves after a few months, the next core update is the one to watch. Spam systems reassess too, after the problems are gone. Keep a dated change log so each later movement can be tied to a specific fix. Avoid the panic moves: buying links, mass-deleting pages that performed well, or rewriting the whole site in a week.

## What I'd watch next

Expect another core update before the year ends, and more enforcement against manipulation of AI answers. Sites built on original work have done well through all of 2026; sites built on volume have struggled. For the AI side of visibility, see [my AI search checklist](https://christopherabraham.com/guides/ai-search-checklist/), or [send me the domain and the date your traffic changed](https://christopherabraham.com/contact/).

## Sources
- [Google Search Status Dashboard: Ranking incident history](https://status.search.google.com/products/rGHU1u87FJnkP6W2GwMi/history)
- [Google Search Central: Google Search's core updates](https://developers.google.com/search/updates/core-updates)
- [Google Search Central: Spam policies for Google web search](https://developers.google.com/search/docs/essentials/spam-policies)
- [Search Console Help: Manual actions report](https://support.google.com/webmasters/answer/9044175)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
