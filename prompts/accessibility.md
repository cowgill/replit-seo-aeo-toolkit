# Accessibility Audit & Optimization (WCAG 2.2 AA)

Audit and improve the accessibility of all public-facing pages using WCAG 2.2 Level AA as the target standard.

Identify accessibility issues and implement safe fixes using the project's existing framework, components, and styling conventions. Apply the same accessibility requirements automatically to new pages and components.

Preserve the existing design, branding, content, and functionality. Do not redesign interfaces or make unnecessary changes.

**Important:** Do not change visible button or link text, colors, backgrounds, or brand styling without approval. If a contrast issue requires a visual change, report it and recommend a solution rather than modifying it automatically.

## 1. Document Structure & Semantics

- Ensure `<html lang>` accurately identifies the page's primary language.
- Use semantic HTML elements such as `<header>`, `<nav>`, `<main>`, `<section>`, and `<footer>` where appropriate.
- Ensure each page has a clear primary heading, preferably one `<h1>`.
- Maintain a logical heading hierarchy that reflects the content structure.
- Avoid using headings solely for visual styling.
- Ensure pages have meaningful titles and appropriate landmarks.
- Identify duplicate IDs and invalid accessibility-related markup.
- Preserve existing layouts and CSS styling.

## 2. Images & Embedded Content

- Provide meaningful alt text for informative images.
- Use `alt=""` for purely decorative images.
- Avoid redundant descriptions such as "image of" or "picture of."
- Preserve accurate existing alt text.
- Ensure linked images have accessible names describing their destination or action.
- Provide descriptive `title` attributes for meaningful iframes.
- Identify videos or audio requiring captions, transcripts, or other accessible alternatives.
- Do not invent descriptions when image meaning or context is unclear; flag them for review.

## 3. Links, Buttons & Interactive Elements

- Ensure buttons and links have meaningful accessible names.
- Add accessible labels to icon-only controls where missing.
- Prefer native HTML semantics over unnecessary ARIA attributes.
- Preserve existing visible button and link text.
- Ensure interactive elements can be operated using a keyboard.
- Provide visible keyboard focus indicators.
- Ensure focus order follows the logical interaction sequence.
- Avoid keyboard traps.
- Verify dialogs, menus, dropdowns, tabs, and accordions expose appropriate roles, states, and keyboard behavior.
- Ensure expanded, selected, disabled, and error states are communicated to assistive technologies.

## 4. Forms & Input Accessibility

- Ensure every form field has an associated visible label or appropriate accessible name.
- Associate help text, required states, and validation errors with their respective fields.
- Ensure form errors are clearly identified and accessible to screen readers.
- Preserve existing form behavior, validation, and submission workflows.
- Ensure form controls can be completed using a keyboard.
- Verify accessible names and roles for custom inputs, checkboxes, radio buttons, and selects.
- Do not change form copy, field requirements, or business logic without approval.

## 5. Color, Contrast & Visual Accessibility

Evaluate contrast against WCAG 2.2 AA requirements:

- Normal text: at least 4.5:1.
- Large text: at least 3:1.
- Meaningful UI components and graphical objects: at least 3:1 where applicable.
- Ensure information is not conveyed through color alone.
- Verify that text remains readable when resized or zoomed.
- Check responsive layouts for clipping, overlapping content, and inaccessible controls.
- Ensure focus indicators are visible and not obscured.

**Do not automatically change button text, colors, backgrounds, or brand styling.** Report contrast failures requiring visual changes and provide recommended fixes for approval.

## 6. Dynamic Content & Motion

- Ensure dynamic content updates are communicated appropriately to assistive technologies.
- Manage keyboard focus correctly after navigation, modal interactions, and significant UI changes.
- Use ARIA live regions only where appropriate.
- Ensure loading indicators and asynchronous states are accessible.
- Respect reduced-motion preferences where applicable.
- Avoid animations or interactions that interfere with accessibility.
- Ensure hover-triggered functionality is also accessible through keyboard and touch interactions.

## 7. Accessibility for Future Pages

Integrate accessibility best practices into the project's existing shared components, templates, and page-creation workflow.

- Apply semantic HTML and accessible interaction patterns by default.
- Ensure new images, forms, buttons, and links follow the same accessibility requirements.
- Reuse existing accessible components instead of creating duplicate implementations.
- Add lightweight automated accessibility checks to the existing development or build workflow where practical.
- Validate new pages against WCAG 2.2 AA requirements before publishing.
- Avoid unnecessary dependencies or separate accessibility infrastructure.

Do not assume automated tests alone establish WCAG compliance.

## 8. Implementation & Validation

1. Inspect the existing framework, components, and accessibility tooling.
2. Reuse existing capabilities before installing new dependencies.
3. Audit representative pages and shared components.
4. Implement safe, nonvisual accessibility fixes.
5. Verify keyboard navigation, focus behavior, form labels, accessible names, and semantic structure.
6. Run existing accessibility tests or a lightweight automated audit where available.
7. Identify issues requiring manual testing, content decisions, or visual design approval.
8. Confirm that changes do not introduce visual or functional regressions.

Preserve the existing design, content, routing, analytics, and functionality.

Do not migrate frameworks, redesign components, change brand styling, or publish automatically.

## Final Report

Provide a concise summary of:

- **Issues fixed:** Accessibility improvements implemented.
- **Issues requiring approval:** Contrast, design, or content changes that were not made automatically.
- **Future-page enforcement:** How accessibility checks are incorporated into existing components and workflows.
- **Validation:** Automated checks performed and manual testing still required.
- **Remaining limitations:** Unresolved accessibility issues or potential WCAG compliance gaps.

Use [WebAIM's WCAG checklist](https://webaim.org/standards/wcag/checklist) and the [W3C WCAG 2.2 standard](https://www.w3.org/TR/WCAG22/) as references.

Keep changes focused, minimize unnecessary dependencies, and avoid exhaustive reporting of pages without issues.
