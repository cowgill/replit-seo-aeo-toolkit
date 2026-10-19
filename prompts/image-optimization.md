# Image Optimization & Responsive Delivery

Audit and optimize the website's raster content images for performance, responsive delivery, and Core Web Vitals. Automatically apply the same optimization requirements whenever images are added, uploaded, replaced, or modified.

Use the existing framework's native image optimization capabilities wherever possible, including Astro, Next.js, React + Vite, or equivalent tooling. Make the smallest necessary changes and preserve the website's visual appearance and functionality.

**Scope:** Optimize photos, screenshots, illustrations, hero images, and other raster content images. Exclude logos, icons, brand assets, and SVG files from automatic modifications.

## 1. Responsive Image Delivery

For each qualifying image:

- Use the framework's native image component or existing image optimization pipeline when available.
- Generate appropriately sized image variants based on actual rendered dimensions and responsive layouts.
- Implement `srcset` and `sizes` where supported, avoiding unnecessarily large downloads.
- Account for high-density displays, typically targeting up to 2× the rendered dimensions where appropriate.
- Preserve image aspect ratios and prevent stretching, cropping changes, or visual distortion.
- Set explicit dimensions or aspect ratios to minimize Cumulative Layout Shift (CLS).
- Preserve existing alt text. Flag missing or inaccurate alt text for review.
- Avoid upscaling low-resolution source images.

For React + Vite projects without built-in image optimization, use a lightweight, maintained build-time solution compatible with the existing architecture.

Avoid introducing a new image CDN, paid service, or unnecessary dependencies without approval.

## 2. Image Formats & Compression

Optimize image files without introducing visible quality degradation.

- Prefer modern formats such as WebP or AVIF when supported by the existing delivery pipeline.
- Preserve JPEG or PNG when more appropriate for compatibility, transparency, or visual quality.
- Compress oversized images when meaningful savings are possible.
- Resize unnecessarily large source images based on actual display requirements.
- Preserve transparency, color accuracy, and important visual details.
- Remove unnecessary metadata where safe.
- Avoid recompressing images that are already efficiently optimized.
- Preserve original source assets where required by the existing workflow.

Do not enforce arbitrary file-size or dimension limits. Optimize based on image content, rendered size, and expected performance benefit.

## 3. Image Loading & Core Web Vitals

Optimize image loading to improve Largest Contentful Paint (LCP) and Cumulative Layout Shift (CLS).

- Identify likely LCP images, particularly hero and prominent above-the-fold images.
- Never lazy-load the primary LCP image.
- Apply appropriate loading priority or preload hints when beneficial.
- Lazy-load below-the-fold images where appropriate.
- Use asynchronous decoding when supported and beneficial.
- Avoid excessive preloading or competing high-priority image requests.
- Ensure images have reserved layout space to prevent CLS.
- Avoid unnecessarily large inline or base64-encoded images.
- Ensure image processing does not introduce unnecessary request-time overhead or increase server response times.

Use existing browser and framework capabilities before adding custom loading logic.

## 4. CSS Background Images

Identify content images implemented through CSS `background-image`.

Where practical, convert meaningful content images to the framework's native image component or responsive `<img>` element.

- Preserve existing layout, cropping, positioning, and responsive behavior.
- Use `object-fit` and `object-position` where appropriate.
- Retain CSS background images for decorative assets and design elements.
- Do not refactor backgrounds when doing so would introduce visual or functional regressions.

## 5. Automatic Optimization for Future Images

Integrate optimization into the project's existing image upload, asset processing, CMS, or production build workflow.

Ensure that:

- New images are automatically optimized when added or uploaded.
- Modified or replaced images are reprocessed when their source content changes.
- Responsive variants are generated or served automatically where appropriate.
- Unchanged images are not unnecessarily reprocessed.
- New image references use the optimized delivery mechanism by default.
- Optimization works for static assets and CMS-managed images where supported.
- Failed image processing is reported rather than silently ignored.
- Generated assets remain compatible with the existing deployment configuration.

Prefer native framework capabilities, incremental processing, and caching to minimize build times and compute costs.

If images are uploaded directly to external storage or a CMS outside the build pipeline, identify the appropriate integration or limitations rather than claiming those images will be automatically optimized.

**Do not require developers to run a separate manual optimization prompt for future images.**

## 6. SVG & Brand Asset Protection

Do not automatically modify:

- SVG files
- Logos and brand marks
- Icons
- Design-controlled illustrations or assets

Audit these assets for unusually large file sizes or inefficient delivery and report recommendations separately.

Do not modify SVG paths, colors, dimensions, `viewBox`, or internal structure without approval.

## 7. Implementation & Validation

1. Inspect the existing framework, image components, asset directories, and upload workflow.
2. Identify existing optimization capabilities before installing anything.
3. Reuse or extend the current image pipeline wherever possible.
4. Optimize existing qualifying images and implement automatic processing for future images.
5. Verify responsive image delivery and loading behavior on representative desktop and mobile layouts.
6. Confirm there are no broken images, visual regressions, unexpected cropping changes, or layout shifts.
7. Verify that adding or replacing an image triggers the appropriate optimization workflow.
8. Run relevant build checks and validate image-related performance improvements where practical.

Preserve the existing design, routing, functionality, and deployment configuration.

Do not redesign pages, migrate frameworks, introduce paid services, or publish automatically.

## Final Report

Provide a concise summary of:

- **Images optimized:** Significant format, dimension, or file-size improvements.
- **Responsive delivery:** Changes to image components, `srcset`, sizing, or loading priority.
- **Automatic processing:** How future image uploads, additions, and modifications are handled.
- **Skipped assets:** Images excluded from automatic optimization and why.
- **Remaining issues:** Low-resolution sources, SVG recommendations, or performance limitations requiring manual attention.

Avoid unnecessary dependencies, unrelated code changes, and exhaustive reporting of unchanged images.
