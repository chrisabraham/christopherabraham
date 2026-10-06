> Which schema types a small business needs, which to skip, and example structured data for local businesses, services, FAQs, and breadcrumbs, kept accurate.
>
> Source: https://christopherabraham.com/guides/small-business-schema/ · Updated 2026-10-06 · By Christopher Abraham

# The schema markup a small business actually needs

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 6, 2026

Schema.org has more than 800 types. A typical small business needs about five. This guide covers which ones, shows example code, and lists the rules that keep structured data accurate enough for Google and AI systems to trust.

## Why bother

Structured data states your facts in a format machines don't have to guess at. It can earn rich results in Google, such as review stars, FAQs, and breadcrumbs, and it helps search engines and AI assistants connect your business, its location, and its services into one clear entity. It won't rescue a weak page, but it makes a good page unambiguous.

## The five you need

### 1. LocalBusiness or Organization, on the home page

Use the most specific LocalBusiness subtype that fits: Dentist, Plumber, LegalService, Restaurant, HomeAndConstructionBusiness, and so on. If customers never visit you and you don't serve a defined area, use Organization instead.

```
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Plumber",
  "@id": "https://example.com/#business",
  "name": "Example Plumbing",
  "url": "https://example.com/",
  "logo": "https://example.com/logo.png",
  "telephone": "+1-703-555-0100",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "100 Main Street",
    "addressLocality": "Arlington",
    "addressRegion": "VA",
    "postalCode": "22204",
    "addressCountry": "US"
  },
  "openingHours": "Mo-Fr 08:00-17:00",
  "areaServed": ["Arlington, VA", "Alexandria, VA"],
  "sameAs": [
    "https://www.linkedin.com/company/example-plumbing",
    "https://www.yelp.com/biz/example-plumbing"
  ]
}
</script>
```

The `@id` is a permanent identifier for the business. Use the same one on every page that refers to it.

### 2. Service, on each service page

```
{
  "@context": "https://schema.org",
  "@type": "Service",
  "name": "Water heater replacement",
  "provider": { "@id": "https://example.com/#business" },
  "areaServed": "Arlington, VA",
  "url": "https://example.com/water-heaters/"
}
```

The provider points back to the business by its `@id`, connecting each service to the company that offers it.

### 3. BreadcrumbList, on every page below the home page

Describes where the page sits in your site. Most SEO plugins generate this automatically if breadcrumbs are turned on.

### 4. FAQPage, only where questions are visible

Mark up FAQs only when the questions and answers are visible on the page. Google shows FAQ rich results for few sites now, but the markup still helps AI systems match your answers to questions.

### 5. Person, for the owner or practitioner

If customers choose you partly because of who you are, such as a lawyer, therapist, consultant, or chef, add Person markup on the About page with name, job title, image, and sameAs links to professional profiles, connected to the business with `worksFor`.

## Add if they apply
- **Product and Offer** if you sell products online.
- **Article or BlogPosting** on blog posts, with author and dates.
- **Event** for classes, workshops, or performances with dates.
- **Review** markup only for reviews that are visible on the page. Self-serving review stars on your own business are ignored by Google.

## The rules
1. **Match the page.** Everything in the markup should be visible to visitors. Hidden facts in schema get ignored or penalized.
2. **Match the world.** Name, address, and phone should match your Google Business Profile exactly.
3. **One source of truth.** Don't let a theme, an SEO plugin, and a reviews app each output their own business markup. Pick one.
4. **Keep it current.** Hours, prices, and addresses change. Hardcoded markup goes stale; markup generated from your CMS fields stays accurate.
5. **Validate.** Test every template in Google's Rich Results Test and the Schema.org validator, then watch Search Console's enhancement reports.

## How to add it

On WordPress, Yoast SEO and Rank Math generate Organization, WebSite, Breadcrumb, and Article markup and let you add more. On Shopify, the theme usually outputs Product markup; check for duplicates before adding an app. On Squarespace and Wix, add JSON-LD through code injection or the platform's SEO settings. On custom sites, generate it from the same data that renders the page.

## A five-minute self-check
1. Paste your home page address into Google's Rich Results Test and note every type it detects.
2. Open the Schema.org validator on the same page and look for duplicates: two Organization or LocalBusiness blocks usually mean a theme and a plugin are both writing markup.
3. Compare the name, address, and phone in the markup with your Google Business Profile, character by character.
4. Repeat on one service page and one blog post.
5. In Search Console, open the Enhancements section and check for errors and warnings on each detected type.

If all five checks come back clean, your structured data is in better shape than most.

## Multiple locations

With more than one location, the home page describes the Organization, and each location page describes its own LocalBusiness with `parentOrganization` pointing to it. Never describe the company and its first location as the same entity.

For help with markup that validates and stays accurate, see [schema markup and entity SEO](https://christopherabraham.com/services/schema/).
