> A junk removal company on Sanity, Vercel, and GitHub had thin rendered HTML and duplicate metadata. Priorities set, a pull request merged, prerendering checked.
>
> Source: https://christopherabraham.com/case-studies/headless-local/ · Updated 2026-10-06 · By Christopher Abraham

# Junk removal company on a headless stack: SEO through the repository

A local junk removal company had a modern website: content in Sanity, hosting on Vercel, code in GitHub. It also had every classic problem of a client-rendered site, and with no SEO plugin to configure, every fix had to go through code.

## What I found
- Client-side rendering left crawlers with thin initial HTML.
- Many pages shared the same title and meta description.
- Heading levels were skipped or repeated.
- Missing pages answered with a 200 status, producing soft 404s.
- Canonical tags and structured data were missing or inconsistent.

## Division of labor

The developer handled the infrastructure: prerendered HTML and deployment changes. I set the order of work, specified what each page type needed, reviewed the developer's changes, and checked the production site independently. For metadata, I made the code changes myself in a pull request that the developer reviewed and merged.

## How the result was checked
- Crawls before and after prerendering, comparing extracted text.
- Raw HTML fetched from production to confirm content was present without scripts.
- Search Console's live URL test on representative pages.
- A sitewide review of titles, descriptions, canonicals, and status codes.

## Why this way of working helps

On headless sites, SEO lives in templates, routes, and build settings. Working through the team's pull requests means every SEO change has a commit, a reviewer, and an easy rollback, and nobody has to wonder who changed what.

## Status

Core fixes are live and verified, with a final audit under way. See [JavaScript and headless SEO](https://christopherabraham.com/services/javascript-seo/).

Updated October 6, 2026
