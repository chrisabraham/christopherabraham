> How to make Google and AI assistants see that Christopher and Chris, or a pen name and a legal name, are one person, using schema, sameAs, and consistency.
>
> Source: https://christopherabraham.com/guides/two-names-one-entity/ · Updated 2026-10-06 · By Christopher Abraham

# One person, two names: entity SEO for pen names and nicknames

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 6, 2026

Plenty of professionals work under more than one name: a formal name on a freelance marketplace, a nickname on bylines, a maiden name on old publications, a pen name on fiction. Search engines and AI assistants treat names as clues, not proof. Unless you connect the names deliberately, they may think you're two people, or worse, merge you with a stranger.

## How machines decide who you are

Google's Knowledge Graph and the retrieval systems behind AI assistants build an *entity*: a single record for a person, with facts attached. They assemble it from pages that agree with each other. When one page says "Christopher Abraham, SEO consultant in Arlington" and another says "Chris Abraham, SEO and reputation specialist in Arlington," the overlap in field and place suggests one person. Structured data and links turn that suggestion into something close to certainty.

## Pick a primary name for each site

Each website should have one primary name for you, used consistently in its headings, bylines, and title tags. A site built for marketplace clients can lead with the name they know from the marketplace; a writing archive can lead with the byline name. Having different primaries on different sites is fine, as long as each site acknowledges the other names somewhere visible.

## Say it in plain words

Put a sentence on your About page that names the connection: "Most people know me as Chris, and nearly two decades of my bylines carry that name." Plain text is the strongest signal because every crawler reads it, including the ones that ignore structured data.

If you have a full legal name with a middle name, list it once. It distinguishes you from namesakes and matches public records, diplomas, and CVs.

## Connect the names in Person schema

Schema.org's Person type has properties built for exactly this:

```
{
  "@type": "Person",
  "@id": "https://example.com/#person",
  "name": "Christopher Abraham",
  "givenName": "Christopher",
  "additionalName": "James",
  "familyName": "Abraham",
  "alternateName": ["Christopher James Abraham", "Chris Abraham"],
  "jobTitle": "SEO consultant",
  "sameAs": [
    "https://www.linkedin.com/in/example",
    "https://www.upwork.com/freelancers/example",
    "https://publication.example/author/example"
  ]
}
```
- **name** is the primary name on this site.
- **alternateName** lists every other name you publish under.
- **additionalName** holds a middle name.
- **sameAs** points to profiles and author pages that are unmistakably you, whichever name they use.
- **@id** gives the entity a permanent identifier, so every page on the site refers to the same person.

## Choose sameAs links carefully

sameAs says "this other page is about the same person." Use it only for pages about you: your LinkedIn profile, marketplace profile, author pages at publications, a speaker bio, a consultancy team page. Never point it at a page that merely mentions you, and never at a domain you no longer control. If an old company site has lapsed and now redirects somewhere unrelated, remove it.

Old bios on reputable third-party sites are especially valuable. A team page from decades ago, still online, is independent evidence that you are who you say you are.

## Make the profiles agree

Go through each profile you list in sameAs and check the basics: field, city, current role, photo. They don't have to be identical, but they shouldn't contradict each other. A headshot used on every profile is a surprisingly strong signal; image search connects them instantly.

## Keep your field attached to your name

Namesakes are the biggest risk. Pair your name with your field everywhere it matters: title tags, page headings, social bios, and author lines. "Christopher Abraham, SEO consultant" repeated across consistent sources teaches the systems which Christopher Abraham this is, and keeps you apart from the theatre director and the novelist who share the name.

## What not to do
- Don't create a separate fake persona with its own invented history. Two names for one real person is normal; two biographies is a credibility problem.
- Don't hide the connection. A name that appears from nowhere, with no link to an established record, looks like a new entity with no history.
- Don't stuff every variant into titles and headings. Use the primary name in titles and let alternateName and the About page carry the rest.

## Check the result

A few weeks after publishing, search each name with your field and city, and ask the major AI assistants who each name is. When they connect the names and describe the same career, the entity has merged. If they don't, look for a profile that contradicts the others.

Related: [correcting what AI says about you](https://christopherabraham.com/guides/correct-ai-answers/), [proving expertise with third-party sources](https://christopherabraham.com/guides/third-party-proof/), and [schema markup and entity SEO](https://christopherabraham.com/services/schema/).

## Sources
- [Schema.org: Person](https://schema.org/Person)
- [Google Search Central: Introduction to structured data](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
