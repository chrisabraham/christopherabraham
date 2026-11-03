> A step by step build: a Cloudflare domain at wholesale, a free GitHub Pages site, DNS records pasted in, and an AI doing the typing. About $10 a year.
>
> Source: https://christopherabraham.com/guides/github-pages-website/ · Updated 2026-11-03 · By Christopher Abraham

# Own Your Website Outright and Never Pay Platform Rent

By [Christopher Abraham](https://christopherabraham.com/about/) · Published November 3, 2026

A complete small-business website can run on GitHub Pages with a domain bought at wholesale from Cloudflare Registrar: hosting $0, domain about $10 to $15 a year, and an AI chat doing the typing. The build takes an afternoon and needs no software installed.

Most small-business websites are rented. A builder platform charges $200 to $480 a year, holds the site inside its own system, and deletes the site when payments stop. An alternative exists and it is not a compromise: a folder of plain files, hosted free by GitHub Pages, on a domain bought at wholesale, maintained by pasting text into a browser with an AI doing the typing. Five sites under my name run exactly this way, including this one. The steps below are the full build, in order.

## Why buy the domain from Cloudflare Registrar?

[Cloudflare Registrar](https://www.cloudflare.com/products/registrar/) sells domains at the wholesale price charged by the registry. No markup is added, the teaser-year pattern (cheap first year, tripled renewal) is absent, and WHOIS privacy is included rather than sold as an add-on. A .com renewal runs about $10 to $15 a year at recent registry prices. Two settings matter on day one: auto-renew switched on, and two-factor authentication on the account. An expired domain remains the most common cause of death for small websites.

## What is a repository, in plain terms?

A repository is a folder with a memory. It stores the site's files: pages, images, and a settings file or two. Every saved change becomes a commit, a dated snapshot with a note attached. Any earlier snapshot can be restored, so no edit is permanent unless it is kept. The only vocabulary the build requires is folder, files, and commits. GitHub describes [GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages) as a service that takes HTML, CSS, and JavaScript files directly from a repository and publishes them as a website. Files in, website out.

## How does GitHub Pages get switched on?

Create a free [GitHub](https://github.com/pricing) account, create a repository, and open Settings, then Pages, then choose the main branch as the publishing source. GitHub's [guide to creating a Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site) documents the same steps. The site answers within minutes at a free address in the form `username.github.io/repository`. The [published limits](https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits) for the free service (sites up to 1 GB, generous monthly bandwidth) sit far above anything a brochure site, consultancy site, or weblog approaches.

## Which DNS records connect the domain?

The domain points at GitHub through DNS records, and Cloudflare's DNS is included free with the domain. GitHub documents the records in its guide to [managing a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site):
1. In the repository's Pages settings, enter the custom domain. GitHub adds a small `CNAME` file to the repository; leave that file untouched afterward.
2. In Cloudflare's DNS panel for the domain, add a **CNAME** record: name `www`, target `username.github.io`.
3. For the bare domain, add four **A** records: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`.
4. Set those records to DNS only (the grey cloud) until GitHub verifies the domain.
5. In the Pages settings, enable **Enforce HTTPS**. GitHub issues the certificate free and renews it automatically.

Propagation usually completes in minutes and occasionally takes a few hours. After verification, the records rarely need attention again. Cloudflare's [DNS documentation](https://developers.cloudflare.com/dns/manage-dns-records/) explains each record type for anyone who wants the background.

## What does the first page consist of?

One file named `index.html` in the repository is a complete website. The file can be written by an AI chat: supply the business name, city, phone number, services, and the instruction to use only those facts, and ask for a single self-contained HTML page back. Paste the result into GitHub's web editor (Add file, then Create new file), add a commit note, and save. The page is live at the domain within about a minute.

## How does publishing work after day one?

The daily method is a four-step loop, and none of it requires local tools:
1. **Draft words anywhere.** Notes, dictation, a customer question answered in full.
2. **Paste the words into the AI chat** and request the finished page or section back, with facts supplied and invented facts forbidden.
3. **Paste the returned file into GitHub's web editor** and commit it with a plain note.
4. **Reload the page.** The change is live; the commit history keeps the prior version for instant rollback.

Images follow the same loop. The AI generates or processes the image, the file is uploaded to the repository through the same Add file menu, and the page references the file by name. Keeping images under a few hundred kilobytes keeps the site fast at no cost.

## What does this stack actually cost per year?

The domain renewal, about $10 to $15. GitHub Pages hosting is $0. Cloudflare DNS is $0. The HTTPS certificate is $0 and self-renewing. A paid AI subscription, if one is used, buys content production rather than hosting. By contrast, Wix and Squarespace plans run roughly $17 to $40 a month after introductory pricing, and managed WordPress hosting lands in a similar band before plugin and maintenance time is counted. The structural difference matters more than the arithmetic: the files are plain HTML in an account the owner controls, portable to any host, so the site is an owned asset rather than a subscription.

## What are the honest limits?

GitHub Pages serves static sites only. It has no built-in store or checkout, no form handling, and no per-visitor logic such as logins or dashboards. Selling works through a hosted payment link or checkout from Stripe or PayPal, or through a separate store platform. Forms work through a helper service (Formspree, Basin, and similar) that forwards submissions by email. Anything dynamic is a different project class, with a developer and server hosting. Two companion guides go deeper on adjacent problems: the [AI-built websites guide](https://christopherabraham.com/guides/ai-built-websites/) lists the checks to run on builder-generated sites, and the [SEO in your repository](https://christopherabraham.com/guides/seo-in-your-repository/) guide explains why the code itself belongs under the owner's account.

## When does hiring help still make sense?

A technical partner earns the fee at the seams: registering and configuring the domain and DNS correctly the first time, designing the page structure, keeping the repository tidy, and handling the changes an owner finds fiddly. The sensible division of labor leaves selling, client relationships, and business judgment with the owner, and the plumbing with the partner. Because the underlying stack costs almost nothing and belongs entirely to the owner, the partnership price buys labor and judgment rather than platform rent.

## Questions buyers ask me

### Is GitHub Pages really free for a business website?

Yes. GitHub's free tier includes GitHub Pages hosting for a site in a public repository, subject to the published size and bandwidth limits. The only recurring charge in this build is the domain renewal at Cloudflare.

### Does a site built this way rank in Google and appear in AI answers?

Yes, provided each page carries real text in finished HTML at its own URL, which a static site does by construction. Search engines and AI crawlers read the same files a browser receives. Ranking depends on the content itself: specific facts, original answers, and pages that each address one question completely.

### What happens if GitHub Pages shuts down or an account is lost?

The repository is a folder of plain files. A downloaded copy can be uploaded to any static host (Cloudflare Pages, Netlify, an ordinary web server) and the domain repointed by editing the same DNS records. Nothing in the build is locked to GitHub's platform beyond the free hosting itself.

### Can this stack run an online store?

Not by itself. The standard pattern is a static site for the business and a hosted checkout or store platform for transactions, linked from the product pages. Businesses whose store is the entire operation usually belong on a dedicated commerce platform from the start.

### Who owns the site if a consultant builds it?

The owner should, provided the domain sits in the owner's Cloudflare account and the repository sits in the owner's GitHub account. Grant the consultant access to those accounts rather than letting the site live in the consultant's accounts. Ownership of the two accounts is ownership of the site.

## Let me help you with this

If you'd rather have this done than do it yourself, it's exactly the work I do for clients. Tell me about your site and I'll tell you where I'd start.

[Book a 30 minute call](https://calendly.com/chrisabraham/30) [Call +1 202-352-5051](tel:+12023525051) [Email cja@well.com](mailto:cja@well.com)

Prefer to hire through Upwork? I'm [Top Rated there too](https://www.upwork.com/freelancers/chrisjabraham).

## Sources
- [GitHub Docs: What is GitHub Pages?](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages)
- [GitHub Docs: Creating a GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)
- [GitHub Docs: Managing a custom domain for your GitHub Pages site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
- [GitHub Docs: GitHub Pages limits](https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits)
- [Cloudflare Registrar](https://www.cloudflare.com/products/registrar/)
- [Cloudflare Docs: Manage DNS records](https://developers.cloudflare.com/dns/manage-dns-records/)
- [GitHub Pricing](https://github.com/pricing)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
