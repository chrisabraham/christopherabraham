> How I turned my own podcast feed into a static site with a page, share card, and alt text for each of 458 episodes, plus transcripts, updated daily.
>
> Source: https://christopherabraham.com/case-studies/podcast-site/ · Updated 2026-10-15 · By Christopher Abraham

# My own podcast: 458 episodes, each with a page of its own

My show, [The Chris Abraham Show](https://thechrisabrahamshow.com/), has published episodes since 2019, and for most of that time it lived only where the platforms put it. On October 8, 2026, I built it a website from its RSS feed with Claude Code. This is the site I point to when someone asks what a podcast website from me looks like, because you can open any page of it right now.

## What the build produced

Claude Code handled the original build described here. For ongoing site work I use OpenAI Codex as well, with the same requirements for stable episode URLs, readable HTML, and a checked build.
- 458 episode pages, one per episode, each at an address recorded once and never changed.
- Full transcripts on 151 episodes, every one the host provides, rendered in the HTML where crawlers can read them.
- A written description for each of more than 230 distinct cover images, done by looking at the art and quoting any words on it.
- PodcastEpisode and Person structured data, a 467-address sitemap, an llms.txt file, and IndexNow notices when pages change.
- An articles section, where episodes that drew a response grow into longer written pieces.

The generator is a single Python file. GitHub Pages hosts the site, Cloudflare handles DNS, and the domain is the only bill.

## It runs every morning

A scheduled GitHub Actions job reads the feed at 9:17 UTC, adds any new episode, picks up transcripts that arrive late, rebuilds, and commits. I record and upload as I always have; the site follows on its own.

## Tags that passed, previews that didn't

On October 14 I audited the social tags on all 469 pages. Every page had complete Open Graph and X card tags, and every image existed at its declared size. The audit still turned up a fault: episode pages offered square cover art inside large preview cards, so Facebook, LinkedIn, and X cropped off the top and bottom of every cover, and more than two hundred episodes shared one default cover and looked identical when shared. I added a generated 1,200 by 630 card for each episode, with the cover beside the episode title. Every one of the 469 pages now offers an image at the size the platforms ask for. The method is in my guide to [social share cards](https://christopherabraham.com/guides/social-share-cards/).

## Corrections, made in public

On one episode I misidentified a car I'd photographed. The episode's page now carries the correction, the photo, and the threads where readers identified it. Articles on the site go through a line-by-line fact-check before they're published, the same one I offer as [fact-checked articles written with AI](https://christopherabraham.com/services/fact-checked-articles/).

## The point

A podcast feed already holds everything a website needs. What keeps the site honest and current is a set of rules the build enforces every day. If you want the same for your show, see [podcast website SEO](https://christopherabraham.com/services/podcast-website/).

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)

Updated October 15, 2026
