> Keep images, PDFs, and share cards working during a website move. Inventory old media URLs, test the new files, and find references to the retiring host.
>
> Source: https://christopherabraham.com/guides/media-migration/ · Updated 2026-10-15 · By Christopher Abraham

# Moving a website? Check its images and PDFs before closing the old host

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 15, 2026

A website can finish its move while its pictures are still living in the old house. Every article loads, the new domain works, and the migration looks complete until somebody cancels the previous hosting account. Then the photos, brochures, and link previews disappear together. Media deserves its own inventory and its own acceptance check.

## Make a second list for files

The familiar migration spreadsheet maps old pages to new pages. Add a separate sheet for images, documents, and other files. Google's site move guidance explicitly includes hosted images and downloads in the move. That matters because a page address and the files used by that page can belong to different servers, accounts, and caching systems.

Start with the old site's crawl, the media library or storage export, and any list of downloads linked from the content. Include files referenced in templates as well as files an editor inserted into an article. A crawl of visible links alone may miss a social image declared in metadata or an alternative image used on a narrow screen.

I provide a [media migration inventory worksheet in CSV format](https://christopherabraham.com/downloads/media-migration-inventory.csv). Its example rows are fictional. Replace them with the old file address, its new destination, the page that uses it, and the checks that establish whether the move is complete. Keep the worksheet private if the real inventory contains unpublished documents.

## Record what the file is supposed to be

A successful request does not prove the file is right. An image URL can return an HTML error page with a successful status. A brochure link can open a different brochure from three years earlier. Record the expected file type and, where useful, its dimensions, page count, or another detail that distinguishes it from a placeholder.
| Item | Check | Evidence to keep |
| --- | --- | --- |
| Article image | The intended image opens at the new address. | Response type, dimensions, and a visual check. |
| PDF download | The document opens and contains the expected version. | Document title, version date, and referring page. |
| Share card | The page points to the correct public image. | Metadata URL, image size, and a preview check. |
| Responsive image | Each offered image variant can still be fetched. | The complete source set and its destinations. |

## Separate copying from updating references

There are two jobs. First, put the intended files somewhere the new site controls. Second, change the references that still ask for them at the previous location. Finishing the first does not finish the second. Search the repository or exported content for the retiring hostname, upload directory, and media delivery domain. Include any encoded versions your content system stores.

Look at image elements, responsive source sets, CSS backgrounds, document links, structured data, Open Graph images, and social card metadata. Check generated pages as well as source files: an import script may keep rebuilding the old addresses after a manual correction. Google's image guidance describes how standard image markup helps discovery; this inventory also checks whether that markup reaches a surviving file.

## Decide what happens at the old address

If the media URL changes, decide how visitors and existing links should reach the replacement. For a permanent move, Google's redirect guidance favors a permanent server redirect where possible. Map a file to its actual replacement rather than sending every missing image or download to the home page. A replacement page is a different thing from the image or document a browser requested.

Write down who controls the old hostname and how its redirects will be served after the old application closes. A redirect rule inside an account you are about to cancel will not provide continuity. If a particular hosting plan cannot keep those addresses working, resolve that limitation while the old service is still available.

## Check original artwork before resizing

A technically valid social card can still crop a face, stretch a square cover, or replace distinctive original artwork with a generic image. Compare the new card with the original. Decide whether the image should fill its frame or sit inside it with space around it, then inspect the result at the size a person will see. The [social share card guide](https://christopherabraham.com/guides/social-share-cards/) covers the metadata and preview side.

When a source file is small, record that fact instead of treating an enlarged copy as a new high-resolution original. Keep the source and the transformed output separately. That makes a later correction possible without downloading an already compressed derivative and processing it again.

## Test the dependency you intend to remove

Before shutting anything down, use a controlled test to find requests to the old media host. A developer can block that hostname locally in a test browser and load representative pages on the new site. Compare the network requests with the inventory. This is a diagnostic exercise in a test session, not a request to change public DNS or interrupt the live service.

Repeat it for a short article, an image heavy page, a page with a PDF, and a link shared on a social platform. Then run the wider crawl to find exceptions outside the sample. A cached picture in one browser is weak evidence that an external dependency has gone.

## Sign off the files as well as the pages

Close each inventory row with the destination checked, the references updated, the old address decision recorded, and any unresolved exception assigned to a person. Keep the date and the deployment being tested. That gives the owner a concrete basis for deciding when the old hosting can be retired.

My [clinic migration case study](https://christopherabraham.com/case-studies/clinic-migration/) describes repository analysis that exposed references to the previous media library. I can review this part of your move through [migration oversight](https://christopherabraham.com/services/migrations/) or a focused [SEO release QA review](https://christopherabraham.com/services/seo-release-qa/).

## Let me help you with this

If you'd rather have this done than do it yourself, it's exactly the work I do for clients. Tell me about your site and I'll tell you where I'd start.

[Book a 30 minute call](https://calendly.com/chrisabraham/30) [Call +1 202-352-5051](tel:+12023525051) [Email cja@well.com](mailto:cja@well.com)

Prefer to hire through Upwork? I'm [Top Rated there too](https://www.upwork.com/freelancers/chrisjabraham).

## Sources
- [Google Search Central: Site moves with URL changes](https://developers.google.com/search/docs/crawling-indexing/site-move-with-url-changes)
- [Google Search Central: Google image SEO best practices](https://developers.google.com/search/docs/appearance/google-images)
- [Google Search Central: Redirects and Google Search](https://developers.google.com/search/docs/crawling-indexing/301-redirects)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
