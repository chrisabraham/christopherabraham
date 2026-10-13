> An SEO who can read your codebase and work with Claude Code, Copilot, or ChatGPT fixes causes in templates, not symptoms page by page. What to expect and ask.
>
> Source: https://christopherabraham.com/guides/seo-in-your-repository/ · Updated 2026-10-11 · By Christopher Abraham

# Why your SEO should work in your Git repository, with AI at their side

By [Christopher Abraham](https://christopherabraham.com/about/) · Published October 11, 2026

Most SEO stops at the admin screen: plugin settings, a crawler export, a spreadsheet of recommendations. Your website doesn't live in the admin screen. If it was built by developers, it lives in a code repository, and that's where its search problems are caused and where they get fixed. An SEO who can work in the repository, with an AI coding assistant doing the heavy reading, fixes causes instead of reporting symptoms. That's how I work, and here is what it means for you.

## What a repository is, in plain English

A repository is the master copy of your site's code, with its entire history. Almost every team now keeps it in Git, the version control system Linus Torvalds and the Linux community created in 2005, usually hosted on GitHub, GitLab, or Bitbucket. Older systems such as CVS and Subversion did the same job before Git took over.

The history is the point. Every change is recorded with who made it, when, and why. Changes are proposed as pull requests that someone reviews before they go live, and any change can be rolled back. That's exactly the discipline SEO changes have usually lacked.

## Plugins and crawlers report. The code is where it's fixed.

Yoast is a fine plugin and Screaming Frog is the best crawler I own. Both tell you what's wrong on the pages they can see. Neither can tell you why a template produces the problem, and neither can change the template. On a site built with Next.js, Nuxt, Astro, Shopify themes, or a headless CMS, there may be no SEO plugin at all. The titles, canonicals, structured data, redirects, robots rules, and sitemaps are all code.

When the SEO can read that code, the work changes:
- **One fix instead of a thousand.** A duplicate title on 3,000 product pages is one line in one template.
- **Redirects where they belong:** in the framework's configuration or the host's rules file, tested before launch.
- **Structured data built into components,** so every new page gets it automatically.
- **JavaScript problems traced to the line.** When content only appears after a scroll or a click, the cause is in a component, and that's where to look.
- **No lost work.** Every SEO change has a commit, a reviewer, and a way back.

## What AI coding assistants add

A medium sized site can have thousands of files. Reading them used to be the developer's job alone. Now AI coding assistants such as Anthropic's Claude Code, GitHub Copilot, and OpenAI's Codex can read an entire codebase, explain how it's organized, trace a problem to the files that cause it, and draft the change. GitHub describes Copilot planning changes, editing code, running tests, and reviewing pull requests. Claude Code works the same way from a terminal.

That puts an SEO who knows what to look for within reach of answers that used to take a developer a week. Two examples from my own client work:
- During [a clinic's move from WordPress to Next.js](https://christopherabraham.com/case-studies/clinic-migration/), a read only analysis of the repository with an AI coding assistant found thousands of image references still pointing at the old media library and traced them to a handful of central files. The developer got a short, concrete plan.
- For [a local business on Sanity, Vercel, and GitHub](https://christopherabraham.com/case-studies/headless-local/), I made the metadata changes myself in a pull request the developer reviewed and merged.

The assistant is fast, tireless, and sometimes confidently wrong. The skill is knowing what search engines need, asking the right questions of the code, and checking every answer. AI doesn't replace that judgment; it multiplies it.

## How I work in a client's repository
1. **Read only first.** I start with read access, map the templates and routes, and compare the code to what crawlers actually see.
2. **Findings tied to files.** Every issue comes with the file and line that cause it, so your developer can act without guessing.
3. **Small pull requests.** When you want me to make changes, each one is a separate branch with a clear description, reviewed by your developer before it merges.
4. **Nothing reaches production without your approval,** and no passwords or API keys go into the code or into an AI tool.
5. **Verified on the live site** after deploy, with a crawl and Search Console.

## Questions to ask any SEO you're about to hire
- Can you read the site's templates, or only the pages they produce?
- Will you hand the developer findings tied to specific files?
- Can you open a pull request, and will you follow the team's review process?
- How do you use AI tools on the code, and how do you check what they produce?
- What access do you need, and what will you never touch?

For the broader hiring checklist, see [how to hire an SEO on Upwork](https://christopherabraham.com/guides/hiring-an-seo/).

## Work with me

I've built websites since 1994 and practiced SEO since 1998, and today I work the way modern sites are built: in the repository, through pull requests, with AI coding assistants doing the heavy reading under my direction. If your site lives in GitHub and your SEO lives in a spreadsheet, [send me the site](https://christopherabraham.com/contact/) or see my [sitewide technical SEO](https://christopherabraham.com/services/sitewide-technical-seo/), [JavaScript SEO](https://christopherabraham.com/services/javascript-seo/), and [technical audit](https://christopherabraham.com/services/seo-audit/) services. I'll tell you what the code is doing to your search visibility and how to fix it.

## Let me help you with this

If you'd rather have this done than do it yourself, it's exactly the work I do for clients. Tell me about your site and I'll tell you where I'd start.

[Book a 30 minute call](https://calendly.com/chrisabraham/30) [Call +1 202-352-5051](tel:+12023525051) [Email cja@well.com](mailto:cja@well.com)

Prefer to hire through Upwork? I'm [Top Rated there too](https://www.upwork.com/freelancers/chrisjabraham).

## Sources
- [Git: A short history of Git](https://git-scm.com/book/en/v2/Getting-Started-A-Short-History-of-Git)
- [Anthropic: Claude Code overview](https://code.claude.com/docs/en/overview)
- [GitHub Docs: GitHub Copilot on GitHub.com](https://docs.github.com/en/copilot/concepts/copilot-surfaces/copilot-on-github)

**[Christopher Abraham](https://christopherabraham.com/about/)** is an independent SEO consultant in Arlington, Virginia, Top Rated on Upwork with 100% Job Success, who writes from his own client work and checks every claim against primary sources. He has built websites since 1994 and practiced SEO since 1998. [How these pages are written](https://christopherabraham.com/about/editorial-policy/) · [LinkedIn](https://www.linkedin.com/in/chrisabraham) · [Upwork](https://www.upwork.com/freelancers/chrisjabraham)
