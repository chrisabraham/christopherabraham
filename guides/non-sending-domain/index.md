> Four DNS records stop spammers from forging mail from a domain you never send from: a null MX, an SPF that allows nothing, strict DMARC, and an empty DKIM key.
>
> Source: https://christopherabraham.com/guides/non-sending-domain/ · Updated 2026-10-06 · By Christopher Abraham

# How to lock down a domain that never sends email

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 6, 2026

Most people own a few domains that never send a single email: a personal brand site, a parked name, an old company domain, a campaign microsite. Spammers love those domains, because with no email records in place, receiving servers have no instructions for rejecting forged mail. Four DNS records close the gap in about ten minutes.

## Why an unused domain is a risk

Anyone can put any address in the "From" line of an email. Receiving servers decide whether to trust it by checking the sending domain's DNS: SPF lists who may send, DKIM proves a message was signed, and DMARC tells receivers what to do when those checks fail. A domain with none of these records gives receivers nothing to go on, so forged messages have a better chance of reaching inboxes, with your name on them.

## The four records
| Type | Name | Value | What it says |
| --- | --- | --- | --- |
| MX | @ | 0 . | This domain accepts no mail. |
| TXT | @ | v=spf1 -all | No server is allowed to send as this domain. |
| TXT | _dmarc | v=DMARC1; p=reject; sp=reject; adkim=s; aspf=s | Reject anything that fails, including from subdomains. |
| TXT | *._domainkey | v=DKIM1; p= | Every DKIM key for this domain is revoked. |

### Null MX

A single MX record with priority 0 and a target of just a dot is the standard way, defined in RFC 7505, to declare that a domain receives no email. Senders get an immediate, clear bounce instead of retrying for days. Some DNS dashboards are fussy about the bare dot; if yours refuses it, the other three records still do most of the work.

### SPF that allows nothing

`v=spf1 -all` lists no permitted senders and ends with a hard fail. Any message claiming to be from the domain fails SPF everywhere. Some administrators add the same record on a wildcard name, so invented subdomains are covered too.

### Strict DMARC

The DMARC record tells receivers to reject messages that fail authentication, for the domain and every subdomain, with strict alignment. You can add a reporting address (`rua=mailto:...`) if you want to see who's trying to spoof you, but it's optional; the reports arrive at whatever mailbox you name, which must exist on another domain.

### Empty DKIM wildcard

A DKIM record with an empty key, on the wildcard selector, tells receivers that no valid signing key exists for any selector. Signatures claiming to come from the domain can't verify.

## What about subdomains?

The `sp=reject` tag in the DMARC record covers subdomains automatically, and the wildcard SPF record covers invented ones such as `billing.example.com`. If you later add a real subdomain that sends mail, it needs its own SPF and DKIM records, and you'll want to relax the subdomain policy deliberately rather than by accident.

## When you later start sending

Plans change. If the domain ever needs to send mail, remove the null MX, replace the SPF record with one listing your actual mail provider, publish that provider's DKIM key, and move DMARC to a monitoring policy while you confirm everything passes.

## Common mistakes
- **Copying records into one.** When pasting a zone file, two records can merge into one long TXT value. Check that the DMARC record contains only the DMARC policy.
- **Using these records on a domain that does send mail.** If the domain sends even occasional mail, such as contact form notifications or invoices from an accounting tool, these records will block it. Inventory every service first.
- **Forgetting old domains.** Every domain you own needs this, including the ones you forgot you renewed.
- **A record conflicting with a CNAME.** Don't put TXT records on a name that already has a CNAME, such as www pointing to a hosting service.

## Checking your work

Look up each record with a DNS lookup tool or a DNS-over-HTTPS query, and run the domain through a free DMARC and SPF checker. The tools should report a valid SPF record with a hard fail, a DMARC policy of reject, and a null MX.

## Where to send people instead

If your website lists an email address, it should be on a domain that really does handle mail. A personal site can happily publish an address hosted elsewhere, while its own domain stays locked down.

For the full setup of parking a domain on Cloudflare and GitHub Pages, see [launching a site on a parked domain](https://christopherabraham.com/guides/parked-domain-launch/). Domains that do send email need SPF, DKIM, and DMARC configured for every service that sends on their behalf, a different job entirely.

## Sources
- [RFC 7505: A "Null MX" No Service Resource Record](https://www.rfc-editor.org/rfc/rfc7505)
- [RFC 7208: Sender Policy Framework (SPF)](https://www.rfc-editor.org/rfc/rfc7208)
- [RFC 7489: Domain-based Message Authentication, Reporting, and Conformance (DMARC)](https://www.rfc-editor.org/rfc/rfc7489)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
