# Open Graph & Social Preview Optimization

Audit and optimize Open Graph and social sharing metadata across all public pages. Ensure that shared URLs produce accurate, visually appealing previews on platforms such as LinkedIn, Facebook, X, and messaging applications.

Apply the same requirements automatically whenever new pages are created or existing page content is updated.

Use the project's existing framework, metadata system, and image-generation capabilities. Preserve high-quality existing social previews and make the smallest necessary changes.

**Important:** Do not replace existing custom-designed images, modify brand assets, or introduce new visual designs without approval.

## 1. Open Graph Metadata

Ensure each public, shareable page has appropriate Open Graph metadata:

- `og:title`
- `og:description`
- `og:image`
- `og:url`
- `og:type`
- `og:locale` where applicable

For X (Twitter), configure:

- `twitter:card` — Prefer `summary_large_image` when a suitable image is available.
- `twitter:title`
- `twitter:description`
- `twitter:image`
- `twitter:site` — Include only when a verified account is configured.

Use the existing metadata system to avoid duplicate or conflicting tags.

### Titles & Descriptions

- Write concise, page-specific social titles that accurately represent the content.
- Communicate the primary topic, value, or benefit.
- Write clear descriptions that explain what visitors will gain by opening the page.
- Preserve effective existing copy.
- Reuse SEO titles and descriptions when appropriate rather than generating unnecessary variations.
- Avoid keyword stuffing, clickbait, exaggerated claims, and misleading messaging.

### URLs & Metadata

- Use absolute production URLs for `og:url` and image references.
- Align `og:url` with the page's intended canonical URL.
- Respect existing URL and trailing-slash conventions.
- Use appropriate page types, such as `website` or `article`.
- Ensure metadata is available in the initial HTML response, not exclusively through client-side JavaScript.
- If the current architecture cannot provide server-visible metadata, report the limitation without changing rendering architecture.

## 2. Existing Social Image Review

Before generating or replacing any social image, evaluate the existing asset.

Check whether it:

- Accurately represents the page's content.
- Uses current branding and correct product or company information.
- Has sufficient resolution and visual quality.
- Displays readable text at typical social preview sizes.
- Uses appropriate dimensions and aspect ratio.
- Loads successfully from a publicly accessible URL.

**Preserve existing images that are relevant, accurate, and high quality.**

Recommend replacement only when an image is missing, broken, outdated, misleading, or unsuitable for social previews.

Do not automatically replace custom-designed or brand-controlled assets.

## 3. Social Image Generation & Optimization

For pages without a suitable social image, use the existing framework's image-generation capabilities or approved design templates.

### Image Requirements

- Prefer a 1200 × 630 px image (approximately 1.91:1).
- Use a broadly supported format such as PNG or JPEG. Use WebP only when compatibility with target platforms is established.
- Optimize file size without visible quality loss.
- Use descriptive, lowercase, dash-separated filenames for generated static assets.
- Ensure the image is publicly accessible without authentication.
- Preserve important content within safe margins to accommodate platform cropping.

### Design Guidelines

Generated images should:

- Accurately represent the page's topic.
- Use existing brand colors, typography, and approved visual assets.
- Include concise, readable text when appropriate.
- Maintain clear visual hierarchy and sufficient contrast.
- Use recognizable product visuals or logos only when available and permitted.
- Remain legible in smaller previews.

Avoid generic stock imagery, unsupported claims, excessive text, and misleading visuals.

Do not invent logos, screenshots, customer results, or product capabilities.

### Page-Specific Relevance

Use page context to select appropriate imagery:

- **Product pages:** Product name, approved product visuals, or primary benefit.
- **Integration pages:** Relevant platforms and their relationship.
- **Customer stories:** Approved customer branding and accurate story context.
- **Articles:** Article topic, approved imagery, or a branded title template.
- **General pages:** A relevant branded template when custom imagery is unnecessary.

Do not generate a separate image when an existing suitable image or approved reusable template provides an equivalent result.

## 4. Localization

For multilingual websites, ensure social metadata matches the language of the shared page.

- Use localized titles and descriptions from the page's existing content.
- Set `og:locale` appropriately.
- Use localized social images when the image contains text and a suitable localized version is available.
- Preserve correct product names, trademarks, and brand terminology.
- Avoid mixing English metadata with non-English page content unless intentionally configured.
- Do not invent translations or introduce a new localization system.

Support locale-specific routes through the existing metadata architecture.

## 5. Automatic Handling of Future Pages

Integrate social metadata into the project's existing shared components, page templates, CMS, or content workflow.

Ensure that:

- New public pages automatically receive appropriate Open Graph and X metadata.
- Titles and descriptions derive from page-specific content or existing metadata fields.
- Social image generation uses approved templates or existing suitable assets.
- Changes to relevant page content or image inputs trigger metadata and image updates through the existing workflow.
- Unchanged images are not unnecessarily regenerated.
- Static, nested, dynamic, and localized pages are supported where applicable.
- Missing required inputs are reported rather than silently replaced with misleading defaults.
- Metadata remains compatible with the production deployment configuration.

Prefer native capabilities such as Next.js metadata and image generation, Astro integrations, or existing Vite-compatible tooling.

Do not introduce paid services, unnecessary dependencies, or a separate image-generation system without approval.

## 6. Validation

Verify representative public pages, including static, dynamic, and localized routes where applicable.

Check that:

- Required Open Graph and X metadata is present and accurate.
- Metadata appears in the initial HTML response.
- Social titles, descriptions, and images accurately reflect visible page content.
- `og:url`, `og:image`, and `twitter:image` use valid absolute production URLs.
- Image requests return successful HTTP responses and appropriate image content types.
- Image dimensions, formats, and file sizes are suitable for social sharing.
- Images are publicly accessible without authentication.
- No duplicate or conflicting metadata tags exist.
- Localized pages use appropriate localized metadata.
- New pages receive social metadata automatically.

Use existing tests or lightweight validation where possible.

If a social platform's preview debugger is unavailable, report that limitation rather than claiming the preview was verified on that platform.

## 7. Implementation & Reporting

1. Inspect the existing framework, metadata configuration, and image-generation workflow.
2. Reuse existing capabilities before adding dependencies.
3. Preserve valid metadata and high-quality existing social images.
4. Correct missing, broken, inaccurate, or conflicting metadata.
5. Implement automatic handling for future pages.
6. Validate representative routes and image URLs.
7. Confirm that changes do not affect the website's design, functionality, or deployment.

Do not redesign pages, migrate frameworks, replace approved brand assets, or publish automatically.

## Final Report

Provide a concise summary of:

- **Metadata updated:** Pages with meaningful title, description, or URL changes.
- **Images:** Existing assets preserved, new images generated, and replacements recommended.
- **Localization:** Changes or limitations affecting multilingual previews.
- **Future-page automation:** How new and updated pages receive social metadata and images.
- **Validation:** URLs and image assets tested, plus unresolved issues.

Avoid exhaustive reporting of unchanged pages, unnecessary dependencies, and unrelated code changes.
