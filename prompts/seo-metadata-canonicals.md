# SEO Metadata & Canonical URL Optimization

Audit and optimize SEO titles, meta descriptions, and canonical URLs across all public, indexable pages. Apply the same requirements automatically to future pages.

Use the project's existing framework, shared metadata configuration, and page templates. Preserve valid metadata and existing functionality. Make the smallest necessary changes.

## 1. SEO Titles

Ensure every indexable page has a unique, descriptive `<title>` that accurately reflects its content and search intent.

- Place the primary topic or value proposition near the beginning.
- Aim for 50–60 characters where practical. Prioritize clarity over strict character limits.
- Append the website or brand name when appropriate, typically separated by ` | `. e.g. " | Replit"
- Keep titles concise, descriptive, and relevant to the intended audience.
- Titles do not need to match the H1 exactly.
- Use simple, descriptive titles for category and index pages.
- Avoid keyword stuffing, generic titles, unnecessary repetition, and mechanical truncation.
- Preserve existing titles unless a meaningful improvement is warranted.

## 2. Meta Descriptions

Ensure every indexable page has a unique `<meta name="description">` that summarizes its content and encourages relevant clicks.

- Aim for 140–160 characters where practical, without enforcing a hard limit.
- Describe what visitors will find or accomplish on the page.
- Complement the title with additional context rather than repeating it.
- Use clear, natural language appropriate to the intended audience.
- Avoid generic marketing language, unsupported claims, keyword stuffing, and clickbait.
- Preserve existing descriptions that are accurate and effective.

## 3. Canonical URLs

Implement consistent, page-specific canonical URLs using the site's production domain.

### Production Configuration

- Identify the production domain and any applicable base path from existing configuration.
- If the final production URL cannot be confirmed, ask before making canonical changes.
- Store the production URL configuration centrally for reuse.
- Never generate canonicals using development, preview, or temporary deployment domains.

### Canonical Requirements

- Every indexable canonical page should have exactly one self-referencing `<link rel="canonical">`.
- For intentional duplicate or alternate URLs, use the appropriate preferred canonical URL rather than forcing self-reference.
- Generate canonical URLs automatically from the production configuration and final page routes.
- Exclude tracking parameters and URL fragments unless explicitly required.
- Respect existing trailing-slash, capitalization, and URL conventions.
- Never point unrelated pages to the homepage or another generic URL.
- Avoid canonical URLs that redirect, return errors, or are blocked from crawling.
- Preserve intentional canonical relationships and `noindex` directives.
- Remove duplicate, conflicting, or outdated canonical implementations.
- Do not rename existing routes or modify URL structures.

## 4. Automatic Handling of Future Pages

Implement metadata generation within the existing shared architecture so new static, nested, and dynamic pages inherit these requirements.

- Automatically generate page-specific titles, descriptions, and canonical URLs from page content and metadata inputs.
- Support dynamic routes, including CMS-generated pages and blog posts.
- Require missing page-specific metadata when accurate values cannot be generated.
- Avoid generic fallback metadata on indexable pages.
- Ensure new pages follow the same canonical URL conventions.
- Add lightweight validation to the existing build or publishing workflow to detect missing, duplicate, or invalid metadata.
- Avoid introducing unnecessary dependencies or a separate metadata management system.

## 5. Rendering & Validation

For existing pages and future pages, verify that:

- Each indexable page has one unique title and meta description.
- Canonical URLs are valid, absolute, and consistent with the preferred production URLs.
- Metadata accurately represents each page's content.
- Titles, descriptions, and canonicals appear in the initial HTML response.
- The rendered DOM contains no duplicate or conflicting metadata.
- Client-side navigation preserves or correctly updates page-specific metadata.
- No development or preview URLs appear in production canonical tags.

**Important:** If the existing architecture relies entirely on client-side rendering, identify the limitation. Do not migrate frameworks or implement SSR/SSG as part of this task. Recommend the separate SPA prerendering optimization instead.

## 6. Implementation & Verification

1. Inspect the existing metadata implementation before making changes.
2. Reuse existing components, utilities, and framework capabilities wherever possible.
3. Update only metadata that requires correction or improvement.
4. Validate representative homepage, static, nested, and dynamic routes.
5. Confirm that future pages receive metadata automatically through the existing creation workflow.
6. Run relevant build checks and ensure no regressions.

Preserve existing design, content, routing, analytics, and functionality. Do not publish or deploy automatically.

## Final Report

Provide a concise summary of:

- Metadata and canonical changes made.
- Pages requiring manual metadata input.
- How future pages are handled automatically.
- Validation results and unresolved issues.

Avoid unnecessary dependencies, unrelated code changes, and extensive reporting.
