> Build accessibility into a small business website instead of bolting on an overlay: contrast, headings, links, images, keyboard use, forms, and testing it.
>
> Source: https://christopherabraham.com/guides/accessible-websites/ · Updated 2026-10-06 · By Christopher Abraham

# Website accessibility without overlays

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 6, 2026

An accessible website works for people who use screen readers, keyboards, magnification, captions, or simply older eyes. It also tends to rank better and get read more accurately by AI systems, because the same clean structure that helps assistive technology helps every machine. The good news: most of the work is basic, and none of it requires a plugin.

## Skip the overlay widgets

Accessibility overlays are scripts that add a toolbar or claim to fix a site automatically. Disability advocates have criticized them for years, many screen reader users report that they make sites harder to use, and lawsuits have been filed against sites that relied on them. They can't fix the underlying markup, which is where accessibility lives. Fix the site itself instead.

## The standard

The Web Content Accessibility Guidelines, WCAG, are the reference courts and regulators point to. Aim for WCAG 2.2 at level AA. Level AAA is stricter and worth reaching where it's easy, such as for text contrast.

## The essentials

### Contrast

Normal text needs a contrast ratio of at least 4.5 to 1 against its background; large text, roughly 24 pixels or 19 pixels bold, needs 3 to 1. Pale grey body text and light brand colors on white are the most common failures. Check each color pair with a contrast checker. Pure black text on white is never wrong.

### Headings

One H1 per page that says what the page is, then H2s and H3s in order, without skipping levels for visual effect. Screen reader users navigate by headings the way sighted readers skim.

### Link text

Every link should make sense on its own. "Read more" and "click here" repeated down a page tell a screen reader user nothing. Write "read the migration case study" instead.

### Images

Meaningful images need alt text that describes what matters about them. Decorative images get an empty alt attribute so they're skipped. Text should never live only inside an image.

### Landmarks and skip links

Use the real HTML elements: header, nav, main, and footer. Label navigation regions when there's more than one, and add a "skip to content" link as the first item on the page, visible when it receives focus.

### Keyboard use

Everything you can do with a mouse should work with the Tab, Enter, and arrow keys, in a sensible order, with a clearly visible focus outline. Never remove focus outlines without replacing them with something just as visible.

### Forms

Every field needs a visible label tied to it, error messages should say what went wrong and how to fix it, and required fields should be marked in text, not by color alone.

### Tables

Use tables only for data, with header cells marked as headers and given a scope, so screen readers announce which row and column each value belongs to.

### Text size and zoom

Use a readable base size, around 17 to 18 pixels for body text, and make sure the page still works when zoomed to 200 percent without sideways scrolling.

### Motion and media

Caption videos, provide transcripts for audio, and avoid autoplaying motion. Respect the reduced-motion setting where animation is used.

## Test it yourself
1. **Unplug the mouse.** Tab through the home page and a form. Can you reach and use everything, and always see where you are?
2. **Zoom to 200 percent.** Does everything still fit and work?
3. **Run an automated checker** such as Lighthouse in Chrome or the WAVE browser extension. Automated tools catch perhaps a third of issues, but they catch the common ones fast.
4. **Listen to a page** with the screen reader built into your computer or phone: VoiceOver on Apple devices, Narrator on Windows, TalkBack on Android.

## Why it helps search too

Descriptive headings, meaningful link text, alt text, and semantic HTML are exactly what search engines and AI systems use to understand a page. Accessible markup is machine-readable markup. Fixing one improves the other.

## Keep it from slipping

Accessibility decays as content is added: a new image without alt text, a color tweak, a "click here." Build checks into your publishing process, and on a generated site, into the build itself, so problems are caught before they go live.

Related: [Core Web Vitals in plain English](https://christopherabraham.com/guides/core-web-vitals/) and [on-page SEO](https://christopherabraham.com/services/on-page-seo/).
