> Lynx, a text browser, shows what search engines and AI crawlers that skip JavaScript receive. How to install it, what to check, and online alternatives.
>
> Source: https://christopherabraham.com/guides/lynx-test/ · Updated 2026-10-06 · By Christopher Abraham

# The Lynx test: see your website the way crawlers and AI read it

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 6, 2026

Lynx is a web browser with no pictures, no styling, and no JavaScript: just text, headings, and links, in the order they appear in your HTML. That makes it the fastest honest preview of what many AI crawlers, and Googlebot before rendering, actually receive from your site. If your page reads well in Lynx, machines can read it too.

## Why a text browser from the nineties still matters

Most of the crawlers that feed AI assistants fetch your HTML and move on without running scripts. Googlebot renders JavaScript, but in a second pass, with limits. Whatever exists only after scripts run is invisible or delayed for those systems. Lynx shows you the pre-script version in seconds. Every site I build gets looked at this way before launch, and it's how I first spot content that a framework hides from crawlers.

## Installing Lynx

On Debian, Ubuntu, or a Linux server you reach over SSH:

```
sudo apt update && sudo apt install lynx
```

On a Mac with Homebrew, run `brew install lynx`. On Windows, install the Windows Subsystem for Linux and use the apt command above inside it. Fedora and Red Hat systems use `sudo dnf install lynx`.

## The three commands you need
- `lynx https://example.com/` opens the page interactively. Arrow keys move between links, Enter follows one, the left arrow goes back, and q quits.
- `lynx -dump https://example.com/` prints the whole page as text, with numbered references to every link listed at the bottom. Pipe it to `less` to read it, or save it to a file.
- `lynx -dump -listonly https://example.com/` prints only the links: the paths a crawler can follow from that page.

## What to look for

### Is your main content there?

Search the dump for a sentence from the middle of your page. If product descriptions, reviews, FAQs, or article text are missing, they're being added by JavaScript, and AI crawlers that don't render scripts will never see them. This single check has explained more mysterious indexing problems for my clients than any other.

### Does the page start with what it's about?

Look at the first screen of the dump. If it's thirty navigation links, a cookie notice, and a newsletter pitch before the first heading, the page's real subject is buried. Machines weigh what comes first.

### Do the headings tell the story?

Lynx shows headings plainly. Read just those: they should outline the page. If they say "Welcome," "Learn more," and "About," they're telling a search engine nothing.

### Do the links make sense?

The link list shows every link's text out of context. A column of "click here" and "read more" is weak for search and useless for screen reader users. Links that don't appear at all, such as cards that navigate with JavaScript, are links crawlers can't follow.

### Do images explain themselves?

Lynx shows alt text in place of images. Images with no alt text appear as a bare file name or as "[INLINE]," which tells you, and every machine, nothing.

### Is anything there that shouldn't be?

Hidden text, leftover placeholder copy, and duplicated blocks from a page builder are all easy to miss in a styled browser and obvious in Lynx.

## No terminal? Use one of these instead
- **[Lynx Viewer](https://www.delorie.com/web/lynxview.html)**, a long-running free service that shows a page roughly as Lynx would. Fine for a quick look at a public page.
- **[SEO Browser](https://www.seo-browser.com/)** compares what a browser receives with what a crawler receives, and what JavaScript changes in between.
- **Search Console's URL Inspection** shows the HTML Google actually fetched and rendered for your own pages. It's the authoritative view for Google specifically.
- **Your own browser with JavaScript off.** Chrome's developer tools can disable JavaScript for the current tab; reload and see what's left.
- **Accessibility tools.** The [WAVE](https://wave.webaim.org/) checker can show a page without styles, and a free screen reader such as [NVDA](https://www.nvaccess.org/) on Windows, or VoiceOver built into Macs and iPhones, reads your page in the same linear order Lynx shows.

## A five-minute routine
1. Dump your home page, a key service or product page, and one article.
2. Check each one for its main content, a sensible first screen, meaningful headings, and descriptive links.
3. Run the link list on the home page and confirm your important pages appear in it.
4. Repeat after every redesign, theme update, or new plugin.

If the Lynx view of an important page is thin, that's the starting point for [JavaScript SEO](https://christopherabraham.com/services/javascript-seo/) work. For the accessibility side of the same coin, see [website accessibility without overlays](https://christopherabraham.com/guides/accessible-websites/).

## Sources
- [Lynx project home](https://lynx.invisible-island.net/)
- [Google Search Central: JavaScript SEO basics](https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics)
- [Search Console Help: URL Inspection tool](https://support.google.com/webmasters/answer/9012289)
- [OpenAI: Overview of OpenAI crawlers](https://platform.openai.com/docs/bots)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
