> Step by step: take a domain off a parking page, move DNS to Cloudflare, point it at GitHub Pages, get HTTPS, and avoid the caching traps on launch day.
>
> Source: https://christopherabraham.com/guides/parked-domain-launch/ · Updated 2026-10-06 · By Christopher Abraham

# Launch a site on a parked domain with Cloudflare and GitHub Pages

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 6, 2026

Many people own a domain that has sat for years on a registrar's parking page, showing ads or a "this domain may be for sale" banner. Putting a real site there is quick once you know the order of operations. This is the sequence I use for static sites on GitHub Pages with DNS at Cloudflare.

## Before you start: inventory the domain

Look up the current DNS records with a public DNS lookup tool or a DNS-over-HTTPS query. Note the nameservers, A and AAAA records, MX records, and TXT records. A parked domain usually has the registrar's parking nameservers, a couple of parking A records, and often a null MX or no mail at all. If the domain receives email, write down every mail-related record before you touch anything; moving nameservers without copying them breaks email.

Also check the registrar account itself. Domains on parking pages are sometimes listed on aftermarket sale platforms by default. Turn that off.

## Step 1: Build and publish the site to GitHub Pages first

Publish the site to its github.io address before touching DNS, and keep it out of search indexes while it's a preview: a noindex robots meta tag on every page does the job. That way you can check every page and link on the preview, and the domain only switches once the site is ready.

## Step 2: Add the domain to Cloudflare

Create a free Cloudflare account, add the domain, and let Cloudflare scan the existing records. Review the scan carefully. Delete the parking records: the old A records pointing at the parking service will otherwise compete with your new ones.

## Step 3: Create the GitHub Pages records
| Type | Name | Value |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| AAAA | @ | 2606:50c0:8000::153 through 2606:50c0:8003::153, four records |
| CNAME | www | your-username.github.io |

Set them all to **DNS only**, the grey cloud. GitHub needs to see the traffic directly to issue its HTTPS certificate. You can switch to Cloudflare's proxy later, with SSL set to Full (strict).

One rule worth knowing: a name with a CNAME can't have any other record. If the scan left a TXT record on www next to your CNAME, delete it.

## Step 4: Lock down email if the domain doesn't send any

If no one will send or receive mail at this domain, publish records that say so, so spammers can't use it. The details are in [locking down a domain that never sends email](https://christopherabraham.com/guides/non-sending-domain/).

## Step 5: Switch the nameservers

At the registrar, replace the parking nameservers with the two Cloudflare assigns you. Cloudflare marks the domain active once it sees the change, often within minutes and sometimes after a few hours.

## Step 6: Go live on GitHub Pages
1. Remove the noindex tag from every page and rebuild.
2. Add a CNAME file at the repository root containing the bare domain.
3. In the repository's Pages settings, set the custom domain.
4. Wait for GitHub to issue the certificate, then turn on **Enforce HTTPS**.

Check that http, https, and www all end up at the https bare domain with a single 301 redirect.

## The caching trap

Your own computer, your router, and your internet provider cache DNS answers. For a while after the switch, you may keep seeing the old parking page while the rest of the world sees your new site. Before panicking, check public resolvers such as Google's and Cloudflare's DNS-over-HTTPS services, or request the page directly from one of GitHub's IP addresses. If those show your site, the launch worked and your local cache will catch up.

## A launch-day checklist

Load the home page, one deep page, and a missing page to see the custom 404. Confirm the sitemap and robots.txt load at the new address and that canonical tags point at the bare domain.

## After launch
- Verify the domain in Google Search Console as a Domain property, using a TXT record in Cloudflare, and submit your sitemap.
- Import the site into Bing Webmaster Tools and set up IndexNow.
- Verify the domain in your GitHub account settings, so no one else can claim it for their Pages site.
- Leave Cloudflare's AI bot blocking off if you want AI assistants to read and cite the site.

For a full migration from an existing site rather than a parked domain, see [site migrations and 301 redirects](https://christopherabraham.com/services/migrations/).

## Sources
- [GitHub Docs: Managing a custom domain for your GitHub Pages site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
- [Cloudflare Docs: Full DNS setup](https://developers.cloudflare.com/dns/zone-setups/full-setup/)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
