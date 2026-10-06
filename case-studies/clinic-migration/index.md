> SEO oversight for a clinic moving from WordPress to Next.js on Netlify: a decision for every legacy URL, an AI assisted code review, and a careful disavow.
>
> Source: https://christopherabraham.com/case-studies/clinic-migration/ · Updated 2026-10-06 · By Christopher Abraham

# Medical clinic: WordPress to Next.js without losing the trail

A clinical practice replaced its managed WordPress site with a new Next.js build hosted on Netlify. The developer built the site. My job was continuity: making sure people and search engines could follow every old address to the right new one, and investigating whatever went wrong after launch.

## A decision for every URL

I reviewed the legacy URLs and reconciled the redirect map line by line. Each URL got one of four outcomes: unchanged, redirected to an existing destination, given a new migration redirect, or deliberately retired. I also separated faults the migration introduced from faults the old site already had, so neither the developer nor the old host took blame that wasn't theirs.

## Reading the code with an AI assistant

Alongside crawls and exports, I ran a read-only analysis of the Next.js repository with an AI coding assistant. It surfaced thousands of image references still pointing at the old WordPress media library and traced them to a handful of central files. That became a short, concrete plan for the developer to move the media. No code was changed by the analysis.

## A conservative disavow

I reviewed the backlink profile and rebuilt the disavow file to drop truly toxic domains while keeping legitimate ones. Over-disavowing throws away the very equity a migration is trying to keep.

## After launch

Blurry images from the image CDN, script and stylesheet errors, instability, and analytics oddities all came up. When engagement dipped over a short window, the obvious story was that blurry images drove people away. I checked tracking, engagement, and stability separately before accepting any explanation, and found the data didn't yet support that one.

## The point

Migrations rarely fail on launch day. They fail weeks later, through media still on the old host, missing redirects, and stories told too early. Read my [rules for 301 redirects](https://christopherabraham.com/guides/redirect-rules/) or see [migration services](https://christopherabraham.com/services/migrations/).

Updated October 6, 2026
