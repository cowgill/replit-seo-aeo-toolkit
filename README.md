# Replit SEO Toolkit

A collection of prompts, tools, and resources to help Replit builders optimize their websites for search engines and AI-powered discovery.

Whether you're building a personal website, launching a SaaS product, or creating websites for clients, this toolkit helps you improve your site's technical SEO, crawlability, indexability, and performance.

## Getting Started

1. Open your project in [Replit](https://replit.com).
2. Browse the prompts in the [`prompts/`](./prompts/) directory.
3. Copy the prompt relevant to your website.
4. Paste it into Replit Agent.
5. Review the proposed changes and test your website before publishing.

> **Important:** Not every prompt applies to every project. Review the changes Agent proposes, especially when modifying rendering architecture, routing, or deployment settings.

## Available Prompts

| Prompt | Description |
|--------|-------------|
| [SPA Prerendering](./prompts/spa-prerendering.md) | Improve crawlability by generating complete HTML for existing and future public pages. |
| [SEO Metadata & Canonicals](./prompts/seo-metadata-canonicals.md) | Audit and optimize titles, meta descriptions, and canonical URLs for existing and future pages. |
| [Image Optimization](./prompts/image-optimization.md) | Optimize images, responsive delivery, and loading performance automatically. |
| [Accessibility](./prompts/accessibility.md) | Improve semantic HTML, keyboard navigation, screen reader support, and accessibility. |
| [Open Graph](./prompts/open-graph.md) | Optimize social sharing metadata, preview images, and Open Graph tags. |
| [Structured Data](./prompts/structured-data.md) | Implement and validate Schema.org structured data for eligible pages. |
| [Crawlability & Indexing](./prompts/crawlability-indexing.md) | Optimize XML sitemaps, robots.txt, internal links, and search engine indexing. |
| [Core Web Vitals](./prompts/core-web-vitals.md) | Improve LCP, INP, CLS, page speed, and mobile performance. |


## Recommended SEO Tools

| Tool | Purpose |
|------|---------|
| [Google Search Console](https://search.google.com/search-console) | Monitor indexing, crawling, and organic search performance. |
| [PageSpeed Insights](https://pagespeed.web.dev/) | Analyze page performance, Core Web Vitals, and opportunities for improvement. |
| [Chrome UX Report (CrUX)](https://developer.chrome.com/docs/crux) | Monitor real-world Core Web Vitals and historical performance trends using Chrome user data. |
| [Google Rich Results Test](https://search.google.com/test/rich-results) | Validate structured data eligible for Google rich results. |
| [Ahrefs SEO Toolbar](https://chromewebstore.google.com/detail/ahrefs-seo-toolbar/hgmoccdbjhknikckedaaebbpdeebhiei) | Chrome extension for auditing on-page SEO, metadata, canonical tags, indexability, redirects, and broken links. |
| [OpenGraph.to](https://www.opengraph.to/) | Preview and validate Open Graph metadata and social sharing images across platforms. |
| [Screaming Frog](https://www.screamingfrog.co.uk/seo-spider/) | Crawl websites and identify technical SEO issues. |
| [Marketing Skills](https://github.com/coreyhaines31/marketingskills) | Marketing skills for Claude Code and AI agents. |

## Understanding SEO, AEO & GEO

**SEO (Search Engine Optimization)**  
Improve your website's visibility in traditional search engines such as Google and Bing.

**AEO (Answer Engine Optimization)**  
Help answer-focused search experiences find and understand your content.

**GEO (Generative Engine Optimization)**  
Improve your website's ability to be discovered, understood, and referenced by generative AI systems.

These disciplines share many technical foundations, including crawlability, accessible HTML, semantic structure, and structured data.

## A Note on React + Vite

Many Replit applications use React + Vite with client-side rendering.

While this architecture works well for interactive applications, public-facing websites may benefit from server-rendered or statically generated HTML.

This toolkit includes prompts to help you:

- Prerender existing React + Vite applications.
- Automatically generate HTML for new public pages.
- Preserve React interactivity.
- Improve content accessibility for search engines and AI crawlers.

You don't necessarily need to rebuild your entire website or migrate to another framework.

## Contributing

Have a useful SEO prompt, improvement, or resource?

Contributions and pull requests are welcome.

## Disclaimer

These prompts are provided for educational and informational purposes only, on an "as-is" basis, without warranties or guarantees of any kind.

Results vary depending on your application's architecture, configuration, and content. AI-generated changes may introduce errors, security vulnerabilities, performance issues, or unintended functionality changes.

We recommend using Plan Mode first, reviewing all proposed changes, testing thoroughly, and maintaining backups or version control before deploying to production. You are responsible for reviewing, validating, and approving any changes made to your application.

Use these prompts at your own risk. No results are guaranteed, including improvements in search rankings, indexing, website performance, accessibility compliance, or visibility in AI-generated answers.

---

Built for the Replit community.
