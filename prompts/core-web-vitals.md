# Core Web Vitals & Website Performance Optimization

Audit and improve website performance, page speed, and Core Web Vitals across public-facing pages.

Identify the most significant performance bottlenecks and recommend improvements that deliver measurable benefits without compromising design, content, accessibility, SEO, analytics, or functionality.

Support common frameworks including Astro, Next.js, React + Vite, and other modern web architectures.

**Start in Plan Mode. Audit and recommend improvements first. Do not modify code until the user approves the implementation plan.**

## 1. Identify the Existing Architecture

Inspect the project before making assumptions.

Determine:

- Framework, version, build system, and hosting environment.
- Rendering approach: SSG, SSR, SPA, streaming, or hybrid.
- Homepage and other public routes.
- Shared layouts, components, and page templates.
- Existing image, font, caching, and performance optimizations.
- Analytics, consent management, and third-party integrations.
- Whether a production or publicly accessible deployment URL is available.

Reuse existing framework capabilities. Do not recommend migrating frameworks unless a significant architectural limitation is identified.

If performance optimizations are already implemented correctly, preserve them.

## 2. PageSpeed Insights & Lighthouse Testing

Use Google PageSpeed Insights and Lighthouse where available to establish a performance baseline.

### Optional PageSpeed Insights API Key

Ask the user whether they have a Google PageSpeed Insights API key.

Explain briefly:

- **With an API key:** Better support for repeated automated testing, quota management, and larger audits.
- **Without an API key:** PageSpeed Insights can still be used where unauthenticated requests are permitted. Test accuracy is not reduced, although API rate limits may restrict automated testing.

An API key is optional and must not block the audit.

Users can create one here:

https://console.cloud.google.com/apis/library/pagespeedonline.googleapis.com

Enable the PageSpeed Insights API and create an API key through Google Cloud Credentials.

If provided, store the key securely as `PAGESPEED_INSIGHTS_API_KEY` using the project's existing secret management system.

Never expose or commit API keys.

### Testing Without an API Key

If no API key is provided:

1. Attempt PageSpeed Insights without authentication where supported.
2. Use Lighthouse against a deployed site or production build when a compatible browser is available.
3. Use existing performance tooling and available Chrome UX Report data.
4. Fall back to build analysis, resource inspection, HTTP headers, and code review when browser testing is unavailable.

Do not install large browser dependencies or repeatedly retry failed external requests without justification.

Never fabricate Lighthouse scores or Core Web Vitals measurements.

### Testing Strategy

- Test the homepage first.
- Identify unique page templates.
- Test representative URLs for each template.
- Prioritize high-traffic, conversion-critical, and media-heavy pages where known.
- Investigate significant performance outliers.
- Run mobile and desktop tests separately.
- Repeat tests when needed to establish reliable results, rather than automatically testing every URL multiple times.

For large websites, avoid redundant testing of pages sharing the same implementation.

Clearly distinguish production measurements from local or simulated tests.

## 3. Core Web Vitals

Evaluate the current Core Web Vitals using Google's published thresholds.

### Largest Contentful Paint (LCP)

Target: 2.5 seconds or less at the 75th percentile of real-user visits.

Investigate:

- Server response time.
- LCP element and resource discovery.
- Hero images and background images.
- Render-blocking CSS and JavaScript.
- Image loading priority.
- Fonts and text rendering.
- Client-side rendering and hydration delays.
- Slow API or CMS requests.

Prioritize improvements that address the actual LCP bottleneck.

### Interaction to Next Paint (INP)

Target: 200 milliseconds or less at the 75th percentile.

Investigate:

- Long JavaScript tasks.
- Main-thread blocking.
- Expensive event handlers.
- Excessive hydration.
- Large client-side bundles.
- Unnecessary re-renders.
- Third-party script execution.

Use available interaction diagnostics when field INP data is unavailable.

Do not treat Total Blocking Time as a direct replacement for INP.

### Cumulative Layout Shift (CLS)

Target: 0.1 or less at the 75th percentile.

Investigate:

- Images without reserved dimensions.
- Fonts causing layout changes.
- Dynamically inserted content.
- Embeds and iframes.
- Banners, notifications, and consent interfaces.
- Animations that affect layout.

Preserve existing visual design while eliminating unexpected shifts.

### Additional Metrics

Evaluate where available:

- Time to First Byte (TTFB)
- First Contentful Paint (FCP)
- Speed Index
- Total Blocking Time (TBT)
- JavaScript execution time
- Total page weight
- Network request count

Distinguish real-user field data from Lighthouse lab measurements.

Do not promise specific score improvements without supporting evidence.

## 4. Server Response & Caching

Inspect server and network delivery performance.

Check:

- Static versus dynamic rendering.
- CDN and edge caching.
- Cache-Control and related response headers.
- HTML, CSS, JavaScript, and asset caching.
- Compression such as Brotli or gzip.
- Sequential or duplicate API requests.
- Database and CMS response times.
- Redirect chains.
- Middleware overhead.
- Unnecessary server-side processing.
- Preload and preconnect opportunities.

Recommend caching improvements appropriate to the existing framework.

Do not cache authenticated, personalized, or sensitive responses publicly.

Preserve correct cache invalidation and content freshness.

Avoid changing hosting infrastructure without approval.

## 5. Images & Media

Identify image and media delivery issues affecting performance.

Check:

- Responsive image sizing and `srcset`.
- Appropriate modern formats.
- Compression and file dimensions.
- Lazy loading of below-the-fold images.
- Correct priority for the LCP image.
- Unnecessary image preloads.
- Image caching.
- Layout stability.
- Video and iframe loading behavior.

Do not reduce visible image quality or modify approved brand assets.

Avoid duplicating work already handled by the site's image optimization pipeline.

For extensive image changes, recommend the dedicated Image Optimization prompt.

## 6. Fonts

Inspect font loading and delivery.

Check:

- Unused font families and weights.
- Duplicate font downloads.
- WOFF2 support.
- Font subsetting where appropriate.
- `font-display` behavior.
- Unnecessary font preloads.
- Layout shifts caused by font swapping.
- Excessive font requests.
- Existing framework-native font optimization.

Preserve brand typography and intended visual appearance.

Do not replace fonts or modify typography without approval.

## 7. JavaScript, CSS & Rendering

Identify unnecessary browser work and render-blocking resources.

Check:

- Large JavaScript bundles.
- Unused or duplicated dependencies.
- Excessive client-side hydration.
- Unnecessary client-rendered components.
- Route-level code splitting.
- Dynamic import opportunities.
- Long-running tasks.
- Expensive event handlers.
- Render-blocking CSS.
- Unused or duplicated styles.
- Unnecessary global CSS.
- Animation and scroll-listener overhead.

Recommend framework-appropriate improvements.

Do not remove code solely because automated tooling reports it as unused. Verify whether it supports interactions, responsive layouts, or delayed functionality.

Preserve important page content in crawlable HTML.

Do not migrate rendering architecture as part of this task without approval.

## 8. Third-Party Scripts & Embeds

Inventory significant third-party resources, including:

- Analytics and tag managers
- Consent management
- Advertising and conversion tracking
- Chat widgets
- Session recording
- A/B testing
- Video players
- Social embeds
- Maps
- External forms

Identify scripts that:

- Block rendering.
- Delay LCP.
- Create long tasks.
- Load unnecessarily on every page.
- Duplicate existing functionality.
- Download large resources before interaction.

Recommend deferred loading or click-to-load approaches where appropriate.

Preserve analytics, consent requirements, accessibility, and business-critical functionality.

**Do not remove, disable, or modify analytics, security, consent, or revenue-related scripts without approval.**

## 9. Below-the-Fold Optimization

Identify resources that do not need to load immediately.

Consider:

- Lazy-loading images and videos.
- Deferring noncritical scripts.
- Delaying third-party embeds.
- Dynamically importing expensive interactive components.
- Avoiding unnecessary initial requests.
- Using native browser loading capabilities.

Preserve important page content, accessibility, and search engine discoverability.

Do not hide or remove content merely to improve performance scores.

## 10. Performance Recommendations & Prioritization

After completing the audit, produce a concise, prioritized implementation plan.

For each significant issue, include:

- Affected page, template, or component.
- Verified issue
