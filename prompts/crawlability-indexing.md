# Crawlability, Indexing & XML Sitemap Optimization

Audit and optimize the website's crawlability, indexing configuration, XML sitemaps, robots.txt, and internal links.

Ensure public pages can be discovered, crawled, and indexed by search engines, while preserving intentional restrictions on private or excluded content.

Automatically maintain sitemaps, indexing directives, and link integrity as pages are created, updated, or removed.

Use the project's existing framework, routing system, CMS, and deployment configuration. Make the smallest necessary changes and preserve existing functionality.

**Important:** Do not remove intentional indexing restrictions, expose private content, change public URLs, or publish automatically.

## 1. Initial Crawlability & Indexing Audit

Inspect the existing website and identify:

- Public, indexable pages
- Pages intentionally excluded from indexing
- Authenticated, private, or application-only routes
- Existing XML sitemaps and robots.txt rules
- Canonical URLs and redirects
- Broken internal links and missing pages
- Orphan pages with no meaningful internal links
- Pages that cannot be crawled or rendered reliably
- Development or staging URLs accidentally exposed to search engines

Verify that public pages intended for search visibility:

- Return HTTP 200 responses.
- Are accessible without authentication.
- Are not unintentionally blocked by robots.txt.
- Do not contain unintended `noindex` directives.
- Do not contain unintended `nofollow` directives.
- Have valid canonical URLs.
- Are discoverable through internal links or sitemaps.
- Provide meaningful page content to search crawlers.

**Indexable public pages should generally use the default `index, follow` behavior.** Explicit meta robots tags are optional.

Preserve intentional `noindex`, `nofollow`, canonicalization, authentication, and access restrictions.

Do not make private pages public to improve SEO.

## 2. XML Sitemap Generation

Audit the existing XML sitemap implementation.

If a valid, automatically maintained sitemap already exists, preserve and improve it where necessary.

If no sitemap exists, generate one using the existing framework's native capabilities where available.

Examples include Astro sitemap integrations, Next.js sitemap generation, or an appropriate build-time solution for React + Vite.

### Sitemap Requirements

- Publish the sitemap at `/sitemap.xml` where appropriate.
- Use valid XML following the Sitemap Protocol.
- Include absolute production URLs.
- Include public, indexable, canonical pages.
- Exclude private, authenticated, `noindex`, redirected, duplicate, and error pages.
- Exclude development, staging, and preview URLs.
- Respect the site's canonical domain and URL conventions.
- Support static, nested, dynamic, and CMS-generated routes.
- Support localized pages and hreflang sitemap annotations when applicable.
- Use a sitemap index when the website exceeds protocol limits.
- Avoid duplicate URLs and invalid XML.

Do not include arbitrary `priority` or `changefreq` values unless there is a specific supported reason.

### Automatic Sitemap Updates

Integrate sitemap generation into the existing routing, CMS, publishing, or production build workflow.

Ensure that:

- Newly published public pages are automatically added.
- Deleted or unpublished pages are automatically removed.
- Pages marked `noindex` are excluded.
- Canonical URL changes are reflected.
- Dynamic routes are discovered from their actual source of published URLs.
- Sitemap updates occur automatically when relevant content changes are deployed or published.
- Unchanged pages are not unnecessarily regenerated.

Do not require manual sitemap editing whenever a page is created.

If the existing architecture cannot discover dynamic URLs automatically, identify the limitation and implement the safest available solution.

## 3. Accurate Last-Modified Dates

Include `<lastmod>` for sitemap URLs when reliable modification dates are available.

Requirements:

- Reflect the last meaningful change to the page.
- Use valid W3C date or date-time formatting.
- Prefer CMS timestamps or reliable content metadata.
- Preserve modification dates across unrelated deployments.
- Update dates when primary content, structured data, or meaningful page links change.
- Do not update dates for unrelated builds, minor footer changes, or deployment timestamps.
- Never invent modification dates.

If accurate dates cannot be determined, omit `<lastmod>` rather than generating misleading values.

For dynamically generated pages, use the most relevant underlying content modification date.

## 4. Robots.txt Configuration

Audit the existing robots.txt configuration.

If no robots.txt exists, create one using the existing framework or deployment setup.

Ensure the production website serves it at:

`/robots.txt`

### Requirements

- Allow crawling of public content intended for indexing.
- Preserve intentional crawler restrictions.
- Avoid blocking essential CSS, JavaScript, or image resources required for rendering.
- Include the absolute production sitemap URL.
- Avoid development or preview URLs.
- Use valid robots.txt syntax.
- Respect existing crawler-specific rules when intentional.
- Do not add unnecessary or speculative crawler restrictions.

Include a sitemap declaration such as:

`Sitemap: https://example.com/sitemap.xml`

**Important:** Robots.txt is not a security mechanism and does not guarantee that blocked URLs will remain out of search results.

Use appropriate authentication, access controls, or `noindex` directives for content that should not be indexed.

Do not automatically block or unblock AI crawlers without user approval.

## 5. Indexing Directives & Canonicals

Audit indexing directives across all public routes.

Check:

- Meta robots tags
- X-Robots-Tag HTTP headers
- Canonical URLs
- Robots.txt restrictions
- Redirects
- HTTP status codes
- Client-side versus initial HTML metadata

For pages intended to be indexed:

- Ensure no unintended `noindex` or `nofollow` directives.
- Verify the preferred canonical URL.
- Confirm the canonical destination is accessible.
- Ensure the page is not blocked from crawling.
- Confirm the page is included in the sitemap when appropriate.

For intentionally excluded pages:

- Preserve existing restrictions.
- Exclude them from XML sitemaps.
- Do not expose private content.
- Avoid conflicting indexing signals.

Do not force every public route to be indexed.

Preserve legitimate canonical relationships, redirects, and exclusions.

If indexability depends on client-side JavaScript, report the limitation without changing rendering architecture.

## 6. Broken Links, Redirects & HTTP Errors

Audit internal links and important public routes for:

- HTTP 404 and 410 errors
- Broken navigation links
- Broken image or document references
- Redirect chains and loops
- Internal links pointing to redirected URLs
- Invalid canonical destinations
- Sitemap URLs returning errors
- Links to removed or unpublished pages
- Soft 404 pages that return HTTP 200 without meaningful content

### Fixing Issues

- Correct clearly identifiable broken internal links.
- Update links to known final destinations.
- Remove references to pages that no longer exist when appropriate.
- Preserve intentional redirects.
- Recommend permanent redirects for moved pages when their replacements are known.
- Avoid unnecessary redirect chains.
- Preserve intentional 404 or 410 responses for genuinely removed content.

Do not invent replacement URLs or redirect unrelated pages to the homepage.

Ask for clarification when the intended destination is uncertain.

For external links, identify significant broken destinations but do not automatically replace them without confidence in the intended target.

Use bounded checks and avoid repeatedly crawling the same URLs.

## 7. Internal Linking & Page Discovery

Evaluate whether important public pages are discoverable through the site's navigation and internal links.

Identify:

- Orphan pages
- Broken navigation paths
- Important pages accessible only through JavaScript interactions
- Links using invalid or non-crawlable destinations
- Excessive redirect chains
- Inconsistent internal URL formats

Use real HTML links with valid `href` attributes for navigational destinations.

Preserve client-side navigation and existing interaction behavior.

Recommend meaningful internal links where appropriate.

Do not automatically rewrite editorial content, add excessive links, or change navigation architecture without approval.

## 8. Google & Bing Search Engine Submission

Determine whether the website is already configured with:

- Google Search Console
- Bing Webmaster Tools
- IndexNow

### Google Search Console

If the site is verified and authorized API access is available:

- Check whether the production sitemap is already submitted.
- Submit the sitemap if necessary, with user approval.
- Report the submission result.

If access is unavailable, provide the sitemap URL and concise manual submission instructions.

Do not use deprecated Google sitemap ping endpoints.

Do not attempt to submit ordinary pages through Google's Indexing API, which is restricted to specific supported content types.

### Bing Webmaster Tools

If authorized access is available:

- Check whether the sitemap is already submitted.
- Submit it when appropriate, with user approval.
- Report the submission result.

Otherwise, provide manual submission instructions.

### IndexNow

Evaluate whether IndexNow is appropriate for the website.

When supported and approved:

- Use an existing integration where available.
- Configure domain verification correctly.
- Notify participating search engines when public URLs are added, meaningfully updated, or deleted.
- Trigger notifications only after changes are publicly available.
- Avoid duplicate submissions and unnecessary API requests.
- Never submit private, staging, or intentionally excluded URLs.

Do not introduce credentials, external services, or automatic submission workflows without approval.

**Search engine submission does not guarantee crawling, indexing, or rankings.**

## 9. Automatic Maintenance for Future Pages

Integrate crawlability and indexing checks into the existing page creation, CMS, build, or publishing workflow.

Whenever public pages are created, updated, or removed:

- Update the XML sitemap automatically.
- Maintain accurate last-modified dates.
- Apply the appropriate indexing directives.
- Preserve canonical URL conventions.
- Exclude unpublished and private pages.
- Detect broken internal links where practical.
- Validate sitemap entries against actual published routes.
- Trigger approved IndexNow notifications where configured.

Prefer native framework capabilities and lightweight incremental checks.

Avoid unnecessary dependencies, full-site recrawls on every small edit, and repeated search engine submissions.

## 10. Validation

Validate representative public routes and the generated sitemap.

Verify:

- `/robots.txt` returns a successful response.
- The sitemap URL returns valid XML.
- Sitemap entries use correct production URLs.
- Sitemap URLs resolve to the intended canonical pages.
- No private, redirected, `noindex`, or broken pages are included.
- Last-modified dates are accurate where present.
- Public pages are not unintentionally blocked.
- Important internal links resolve correctly.
- Removed pages disappear from the sitemap.
- Newly published pages appear automatically.
- Canonical and indexing directives are consistent.
- No unintended deployment or preview URLs are exposed.

Run available build checks and focused crawl tests.

If the production website cannot be accessed, validate the available build output and clearly identify which production checks remain outstanding.

Do not claim that a page is indexed merely because it is crawlable or included in a sitemap.

## 11. Implementation & Reporting

1. Inspect the existing framework, routes, CMS, and deployment configuration.
2. Audit crawlability, indexing directives, sitemaps, robots.txt, and internal links.
3. Reuse existing capabilities before installing new dependencies.
4. Fix clear, low-risk technical issues.
5. Implement automatic sitemap and indexing maintenance.
6. Validate representative pages and generated files.
7. Identify issues requiring user approval or production access.
8. Report search engine submission options and status.

Preserve existing design, content, routing, authentication, analytics, and functionality.

Do not migrate frameworks, change URL structures, remove intentional indexing restrictions, expose private content, or publish automatically.

## Final Report

Provide a concise summary of:

- **Sitemap:** Location, number of URLs, generation method, and automatic update behavior.
- **Robots.txt:** Existing or newly created configuration and any changes.
- **Indexing:** Unintentionally blocked or excluded pages identified and corrected.
- **Broken links:** Issues found, fixes applied, and unresolved destinations.
- **Canonical & redirect issues:** Corrections and remaining concerns.
- **Search engine submission:** Google, Bing, and IndexNow configuration or required setup.
- **Future-page automation:** How new, updated, and deleted pages are handled.
- **Validation:** Tests completed and remaining production checks.

Avoid exhaustive reporting of unaffected pages, unnecessary dependencies, and unrelated code changes.
