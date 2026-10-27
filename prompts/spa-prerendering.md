# SPA Prerendering: Complete Public HTML for SEO, AEO & GEO

Optimize this website’s rendering architecture for SEO, AEO, GEO,
and initial page-load performance.

## Phase 1: Audit and recommend (plan mode only)

Inspect the existing project configuration, routing, rendering,
build process, and deployment setup. Do not modify files yet.

Determine whether every public page already satisfies the HTML
and navigation requirements below. Check the actual initial HTML
response, not only the browser-rendered DOM.

If all requirements are met, report that no changes are needed.
If only some requirements are met, identify the gaps and recommend
targeted fixes. Do not recommend a rendering migration when a
smaller navigation or deployment fix is sufficient.

### HTML and navigation requirements

- Every public page URL must return its own complete, substantive,
  build-time-rendered HTML document. Its static content must be
  readable with JavaScript disabled.
- Do not return an empty root, JavaScript shell, loading placeholder,
  or skeleton that requires client-side rendering or fetching to
  display the page’s static content. A root element is fine when
  it already contains the page’s rendered content.
- Include page-specific primary content, headings, navigation,
  important FAQ/accordion content, and metadata in the initial HTML.
- Use native `<a href>` links for page-to-page navigation. Do not
  use client-router Link components, pushState routing, or
  fetch-and-swap rendering for public page navigation. Disable
  framework navigation interception on these links.
- Preserve URL bases, query parameters, hashes, back/forward history,
  modified clicks, and new-tab behavior. Same-page anchor links
  must continue to work normally.
- JavaScript may progressively enhance forms, filters, tabs,
  accordions, media, and other on-page interactions. It must not
  be required for static content or ordinary navigation.
- Hydration and JavaScript failures must not erase or hide readable
  HTML. Static content must not depend on a successful hydration
  step to become visible.
- Never place private data, including private form submissions,
  in public HTML or URLs. Keep private data out of public build
  artifacts and serialized hydration data too.

These requirements apply to public pages, including public pages
marked `noindex`. Private, authenticated, and app-only routes are
outside this public-page rendering scope. Preserve their existing
access controls and behavior.

### Audit requirements

- Identify public pages and distinguish indexable and noindex pages.
- Identify private, authenticated, and app-only routes.
- Check how page content, metadata, and navigation are rendered.
- Check whether all public routes and their static content can be
  discovered and generated at build time.
- Identify existing SSR, SSG, or prerendering capabilities.
- Check deployment, reverse proxy paths, URL bases, asset URLs,
  redirects, and direct requests to nested routes.
- Identify hydration, navigation, and compatibility risks.
- Identify public routes that currently depend on request-time or
  client-side data, and explain how to separate static public
  content from interactive or private functionality.

### Choose the smallest suitable solution

1. **Prerender the existing SPA (preferred when compatible).**
   Use a maintained solution compatible with the existing stack.
   Preserve React and on-page interactivity. Replace public
   client-router navigation with native document navigation.
2. **Consider Astro.** For primarily static, content-driven sites
   where it would simplify build-time rendering and maintenance.
3. **Consider Next.js.** When the wider application needs its
   capabilities and the public pages can still be generated at
   build time with native document navigation.

Do not recommend a framework migration without a clear technical
advantage. Framework choice alone does not prove these requirements
are met. Request-time SSR does not satisfy the build-time requirement;
if a route cannot meet it, explain the blocker and request an explicit
scope decision rather than silently substituting SSR or a client shell.

Do not install packages, modify code, run expensive tests, or make
architectural changes during this phase.

Provide a concise report with:

1. Current rendering and navigation architecture.
2. Requirements already met and gaps found, with representative URLs.
3. Recommended solution and why.
4. Estimated complexity, risks, and blockers.
5. Implementation and validation steps.

End with the next-step menu below, then stop and wait for a choice.
Do not treat a request for more detail as implementation approval.

## Phase 2: Implement only after approval

Implement the approved solution with minimal changes, following
all HTML and navigation requirements above.

### Automatic page generation

- Discover public routes from the existing router, filesystem,
  content files, CMS if present, or other appropriate source of truth.
- Include newly created public pages in future builds without
  requiring a second manually maintained route list.
- Support dynamic route patterns when their published URLs and
  static content are available at build time.
- Regenerate pages when a build is triggered. Explain the existing
  build trigger and any required publishing workflow changes.
- Exclude private, authenticated, and app-only routes from public
  generation. Do not exclude a public page solely because it is noindex.
- Fail the build if a required public page cannot be generated.
  Never silently fall back to empty HTML or a shared SPA shell.

### Preserve existing functionality

Preserve the website’s design, content, header, footer, forms,
authentication, analytics, integrations, and responsive behavior.
Preserve visible navigation and destinations while changing the
public navigation mechanism as required above.

Preserve deployment configuration, proxy paths, asset URLs, and
existing public URLs unless an approved change is necessary.
Do not migrate frameworks without explicit approval.

### Validation

Keep validation focused on affected functionality. After implementation:

1. Run the production build and confirm every required public route
   has a corresponding generated HTML document.
2. Serve the production output using the intended deployment routing.
   Directly request representative public URLs, including nested
   and generated dynamic routes. Verify page-specific content and
   metadata in each initial HTTP response, before JavaScript runs.
3. With JavaScript disabled, verify readable static content, ordinary
   page navigation, and same-page anchors.
4. With JavaScript enabled, confirm public links still use native
   document navigation and preserve URL bases, queries, hashes,
   back/forward history, modified clicks, and new-tab behavior.
5. Verify on-page interactions, forms, analytics, and integrations.
   Check for hydration errors and confirm that blocked or failed
   JavaScript does not erase or hide the static HTML.
6. Check representative desktop and mobile layouts.
7. Confirm no private data appears in generated HTML, public build
   artifacts, hydration payloads, or URLs.
8. Confirm a newly added public route is discovered and generated
   in a subsequent build without manual route-list updates.
9. Verify unknown routes return an actual HTTP 404, rather than a
   successful response containing a generic SPA shell.
10. Check that deployment rules serve each URL’s correct document
    and preserve redirects and access controls.

Do not publish or deploy automatically. After the user publishes,
remind them to verify the actual public URLs, including any reverse
proxy, return the expected page-specific HTML.

### Final report

Summarize changes, routes generated, routes excluded and why,
automatic handling of future pages, validation results, and remaining
limitations. Distinguish verified results from checks that still
require access to the live deployment.

## Next-step menu

At the end of the audit, present these choices:

1. **Implement the recommendation.** Apply the proposed changes and
   run focused validation. Do not publish or deploy.
2. **Show the detailed plan first.** List affected files, dependencies,
   deployment changes, and tradeoffs without modifying anything.
3. **Compare alternatives.** Explain other viable approaches and their
   maintenance costs without modifying anything.
4. **Stop after the audit.** Make no changes.

If no changes are needed, replace the implementation choice with
“Show the verification evidence.” If there is an unresolved blocker,
offer a scope decision before implementation rather than presenting
the blocked approach as ready to proceed.

After implementation, offer only relevant follow-ups: review the
changes, address remaining issues, or provide a publishing and live
verification checklist. A menu selection never authorizes automatic
publishing or deployment.

Keep responses concise and avoid unnecessary explanations.
