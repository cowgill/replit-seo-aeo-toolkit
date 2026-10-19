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
| [Technical SEO, AEO & GEO Audit](./prompts/01-technical-seo-audit.md) | Comprehensive technical SEO analysis and recommendations. |
| [SPA Prerendering](./prompts/02-spa-prerendering.md) | Generate static HTML for existing and future public pages. |
| [Metadata & Structured Data](./prompts/03-metadata-structured-data.md) | Optimize metadata and implement appropriate structured data. |
| [Sitemaps & Robots.txt](./prompts/04-sitemap-robots.md) | Improve crawling and search engine discovery. |
| [Performance Optimization](./prompts/05-performance-optimization.md) | Identify and improve Core Web Vitals and page performance. |

*Additional prompts and resources may be added over time.*

## Recommended SEO Tools

| Tool | Purpose |
|------|---------|
| [Google Search Console](https://search.google.com/search-console) | Monitor indexing, crawling, and organic search performance. |
| [PageSpeed Insights](https://pagespeed.web.dev/) | Analyze page performance, Core Web Vitals, and opportunities for improvement. |
| [Chrome UX Report (CrUX)](https://developer.chrome.com/docs/crux) | Monitor real-world Core Web Vitals and historical performance trends using Chrome user data. |
| [Google Rich Results Test](https://search.google.com/test/rich-results) | Validate structured data eligible for Google rich results. |
| [Ahrefs SEO Toolbar](https://chromewebstore.google.com/detail/ahrefs-seo-toolbar/hgmoccdbjhknikckedaaebbpdeebhiei) | Chrome extension for auditing on-page SEO, metadata, canonical tags, indexability, redirects, and broken links. |
| [Screaming Frog](https://www.screamingfrog.co.uk/seo-spider/) | Crawl websites and identify technical SEO issues. |

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

These prompts provide a starting point for technical optimization. Results depend on your application's architecture, content, and configuration.

Always validate changes before deploying to production. No optimization guarantees search rankings, indexing, or inclusion in AI-generated answers.

---

Built for the Replit community.
