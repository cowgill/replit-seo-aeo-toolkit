# SPA Prerendering: Optimize React + Vite for SEO, AEO & GEO

Optimize this website's rendering architecture for SEO,
AEO, GEO, and initial page-load performance.

PHASE 1: AUDIT & RECOMMEND (PLAN MODE ONLY)

Inspect the existing project configuration, routing,
rendering, build process, and deployment setup.

Determine whether public pages already deliver complete,
crawlable HTML in the initial server response.

If they do, report that no rendering changes are needed
and stop. Do not modify any files.

If public pages rely on client-side JavaScript to render
their primary content, recommend the safest solution:

1. PRERENDER EXISTING SPA (PREFERRED)
   Add build-time static prerendering using a maintained
   solution compatible with the existing stack.
   Preserve React, Vite, routing, and interactivity.

2. MIGRATE TO ASTRO
   Consider for primarily static, content-driven websites
   where HTML-first rendering would simplify maintenance.

3. MIGRATE TO NEXT.JS
   Consider for complex applications requiring dynamic
   server rendering, authentication, or full-stack features.

Prefer the smallest change that solves the problem.
Use request-time SSR only when static generation is
insufficient. Do not recommend a framework migration
unless there is a clear technical advantage.

AUDIT REQUIREMENTS

- Identify public, indexable routes.
- Identify private, authenticated, and app-only routes.
- Check how page content and metadata are rendered.
- Check whether dynamic routes can be generated at build time.
- Identify existing SSR, SSG, or prerendering capabilities.
- Check deployment, proxy paths, and asset URL requirements.
- Identify potential hydration or compatibility risks.

Do not install packages, modify code, run expensive tests,
or make architectural changes during this phase.

Provide a concise report containing:
1. Current rendering architecture.
2. Whether public pages need prerendering.
3. Recommended solution and why.
4. Estimated complexity and potential risks.
5. Implementation steps.

STOP and wait for my approval before implementing.

PHASE 2: IMPLEMENTATION (ONLY AFTER APPROVAL)

Implement the approved solution with minimal changes.

RENDERING

- Generate complete HTML for every public, indexable page.
- Include primary content, headings, navigation links,
  and important FAQ/accordion content in the initial HTML.
- Preserve React interactivity and client-side navigation.
- Avoid hydration errors and unnecessary JavaScript.
- Never expose private or user-specific data in public HTML.

AUTOMATIC PAGE GENERATION

- Automatically discover public routes from the existing
  router, filesystem, CMS, or appropriate source of truth.
- Include newly created public pages in future builds
  without requiring manual route configuration.
- Support dynamic routes when published URLs and content
  are available at build time.
- Regenerate affected pages when a new build is triggered.
- Exclude authenticated, private, and non-indexable routes.
- Report or fail builds when required public pages cannot
  be prerendered. Never silently fall back to empty HTML.

PRESERVE EXISTING FUNCTIONALITY

Do not change the website's design, content, navigation,
header, footer, forms, authentication, analytics,
integrations, or responsive behavior.

Preserve deployment configuration, proxy paths,
asset URLs, and existing public URLs.

Do not migrate frameworks without explicit approval.

VALIDATION

After implementation:

1. Run the production build.
2. Verify representative public routes return complete
   HTML without requiring JavaScript.
3. Confirm page-specific metadata appears in initial HTML.
4. Confirm React interactivity and navigation still work.
5. Check for hydration errors and broken routes.
6. Verify desktop and mobile layouts.
7. Confirm no private data appears in generated HTML.
8. Confirm newly added public routes are automatically
   included in subsequent builds.
9. Verify deployment configuration serves the correct
   HTML for each URL.

Keep validation focused on affected functionality.
Avoid unnecessary full-project audits.

Do not publish or deploy automatically.

After publishing, remind me to verify the actual public
URL, including any reverse proxy, serves the expected HTML.

FINAL REPORT

Summarize:
- Changes made.
- Routes prerendered.
- Routes excluded and why.
- Automatic handling of future pages.
- Validation results.
- Any remaining limitations.

Keep responses concise and avoid unnecessary explanations.
