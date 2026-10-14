> How I moved a serialized novel off Movable Type 3.33 to static hosting, keeping all 953 old URLs: entries, archive pages, feeds, TrackBack files, and images.
>
> Source: https://christopherabraham.com/case-studies/movable-type-novel/ · Updated 2026-10-14 · By Christopher Abraham

# A serialized novel: 17 years of Movable Type URLs, all kept

This one is my own work, not a client's. A serialized novel I published as a blog from 2005 to 2022 ran on Movable Type 3.33 until its CGI stopped working on the old shared host. I moved it to static HTML on free hosting, and every address the old site ever published still answers.

## Counting what the old site published

Movable Type publishes far more than its entries. Besides 309 chapters, the old site had monthly, weekly, daily, and category archive pages, per entry TrackBack files, three separate feed formats, and an images folder that other sites had linked to for years. I took the list from the database dump and the old web root, not from memory, and it came to 953 URLs.

## Same addresses, not redirects

Where I could, I kept each URL exactly rather than redirecting it. Each chapter carries an explicit permalink matching its original path. The 389 old archive addresses are generated stubs, and the few pages Movable Type left behind after entries moved get redirects. The TrackBack files still answer, minus the spam pings that had piled up in them. All three feed URLs still serve their original formats, and the images keep their paths.

## Cleaner for search than before

The archive pages repeat chapter text, so they are now noindex, follow and left out of the sitemap, and only the chapters and the main pages are indexable. Every chapter got a hand written title and description, checked by a script. Spelling and typography fixes went into a log, one row per change, so any of them can be undone.

## Cutting over in the right order

The old host also ran the domain's DNS, so canceling hosting would have taken DNS down with it. I moved DNS first, with the old records and the Search Console verification record copied exactly, and only then switched the site. A check script confirmed all 953 URLs, the https and www redirects, and the canonicals before I told Google and Bing.

## The point

A small site gets the same discipline as a large one: count every URL first, keep the ones you can, and redirect the rest. The same approach carried a [medical clinic from WordPress to Next.js](https://christopherabraham.com/case-studies/clinic-migration/). See my [migration services](https://christopherabraham.com/services/migrations/).

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)

Updated October 14, 2026
