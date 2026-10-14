> On a fast static site, gtag.js caused most of the blocking time. Loading it after the first scroll or tap took mobile Lighthouse to 100. How, and the cost.
>
> Source: https://christopherabraham.com/guides/ga4-pagespeed/ · Updated 2026-10-14 · By Christopher Abraham

# How to load Google Analytics 4 without hurting PageSpeed

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 14, 2026

On a lean site, the Google Analytics tag can be the heaviest thing on the page. When I tested this site in October 2026, gtag.js accounted for most of the main-thread work during load on mobile, about twice what the site's own code used. Loading the tag after the visitor's first scroll, tap, or key press, or four seconds after the page finishes loading, took the home page from a mobile Lighthouse score of 73 to 80 up to 100. Pageviews still count. The cost is the visitors who leave within a few seconds without touching the page.

## What the tag costs

The standard GA4 snippet loads gtag.js asynchronously, which keeps it from blocking the HTML parser. It still runs on the main thread once it arrives, and the script is large: about 176 KB on my pages. On a phone, parsing and running it lands in the same window as the page's first paint, and Lighthouse counts every long task in that window toward Total Blocking Time. On my home page, Total Blocking Time ran from 700 to 1,760 milliseconds, depending on the run.

Total Blocking Time is a lab measure. Google's ranking signals use field data, and the field measure for responsiveness is Interaction to Next Paint. Real phones on real networks still pay the cost of a large script parsed during load, so a lab fix that removes that work tends to show up in the field too, a month or so later, once enough visits have been recorded.

## Load the tag after the visitor acts

The fix keeps every analytics command and moves only the script download. The page defines dataLayer and the gtag function as usual, queues the consent defaults, the js timestamp, and the config call, and then waits. The first scroll, pointer press, touch, or key press loads gtag.js. If none comes, a timer loads it four seconds after the page's load event. When the script arrives it reads the queued commands in order, so the pageview is recorded with the right consent state.

```
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
  (function () {
    var done = false;
    function load() {
      if (done) return;
      done = true;
      var s = document.createElement('script');
      s.async = true;
      s.src = 'https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX';
      document.head.appendChild(s);
    }
    ['pointerdown', 'keydown', 'scroll', 'touchstart'].forEach(function (e) {
      addEventListener(e, load, {once: true, passive: true});
    });
    addEventListener('load', function () { setTimeout(load, 4000); });
  })();
</script>
```

Keep your consent mode defaults above the config line, exactly where they were. They are commands in the same queue and run before anything is sent.

## The result

I tested the original and the deferred version of the same page side by side, twice each, with Lighthouse in mobile mode on the same machine. The original scored 73 and 80, with 1,760 and 890 milliseconds of blocking time. The deferred version scored 100 both times, with 40 and 30 milliseconds. The two pages I measured on this site afterward scored 98 and 100.

## The cost, stated plainly

A visitor who opens a page and leaves within about four seconds without scrolling, tapping, or typing is never counted. On most sites that group is small and includes a share of bots, but it is real, and a client should hear it before the change ships. Bounce rate and short-session counts will shift on the day you deploy, so annotate the change in GA4 and compare like with like afterward.

Two cases call for the standard snippet instead. A site whose business depends on counting single-page visits exactly, such as a landing page measured by paid campaigns, should keep the tag loading immediately. So should any page where the tag fires conversion events the moment it loads.

## Check the rest of the page first

Deferring analytics is the right first move only when analytics is the problem. Run Lighthouse, open the diagnostics, and read which scripts take the main-thread time. If a theme, a page builder, or a chat widget is the larger cost, fix that first. My guide to [Core Web Vitals](https://christopherabraham.com/guides/core-web-vitals/) covers the other common causes.

## Where I fit

I find what is actually slowing a site, measure the fix before it ships, and explain the trade-offs to the people who own the analytics. If your PageSpeed scores are stuck and nobody can say why, [send me the URL](https://christopherabraham.com/contact/).

## Let me help you with this

If you'd rather have this done than do it yourself, it's exactly the work I do for clients. Tell me about your site and I'll tell you where I'd start.

[Book a 30 minute call](https://calendly.com/chrisabraham/30) [Call +1 202-352-5051](tel:+12023525051) [Email cja@well.com](mailto:cja@well.com)

Prefer to hire through Upwork? I'm [Top Rated there too](https://www.upwork.com/freelancers/chrisjabraham).

## Sources
- [Chrome for Developers: Total Blocking Time](https://developer.chrome.com/docs/lighthouse/performance/lighthouse-total-blocking-time)
- [Google Analytics: Set up consent mode](https://developers.google.com/tag-platform/security/guides/consent)
- [web.dev: Interaction to Next Paint](https://web.dev/articles/inp)
- [Google Search Central: Core Web Vitals and Google Search results](https://developers.google.com/search/docs/appearance/core-web-vitals)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
