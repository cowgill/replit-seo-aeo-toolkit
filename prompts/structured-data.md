# Structured Data (JSON-LD) Optimization

Audit and optimize structured data across all public, indexable pages using Schema.org and current Google Search guidelines.

Implement relevant, accurate JSON-LD that helps search engines and AI systems understand the website, its organization, products, services, people, and page content.

Automatically maintain structured data whenever pages are created, updated, or removed.

Use the existing framework's native metadata and structured data capabilities. Preserve valid existing markup and make the smallest necessary changes.

**Important:** Do not invent business information, social profiles, reviews, ratings, prices, dates, or entity relationships. Ask for missing information when required.

## 1. Audit & Schema Discovery

Inspect the existing website, page types, content, and structured data implementation.

Reference Google's current supported structured data documentation:

https://developers.google.com/search/docs/appearance/structured-data/search-gallery

Also follow Schema.org definitions:

https://schema.org/

Identify applicable structured data based on actual page content.

Common types include:

- Organization
- LocalBusiness
- WebSite
- WebPage
- ProfilePage
- Person
- Product
- SoftwareApplication
- Article / BlogPosting
- BreadcrumbList
- VideoObject
- FAQPage
- JobPosting
- Event
- Service

Consider other supported types when relevant.

**Do not implement every schema type automatically.** Only use types that accurately represent existing entities and content.

Distinguish between:

- Schema.org types that improve machine-readable context.
- Google-supported structured data features that may qualify for enhanced search appearances.

Valid Schema.org markup does not guarantee Google rich results, higher rankings, or AI search visibility.

## 2. Request Missing Business & Profile Information

Before implementing Organization, LocalBusiness, Person, or ProfilePage markup, inspect the existing website and configuration for verified information.

Ask the user to confirm missing or uncertain details.

Collect only information relevant to the website.

### Organization Information

Request confirmation when necessary:

- Official organization or business name
- Production website URL
- Official logo URL
- Business description
- Business type or industry
- Contact information, if publicly available

For local businesses, also request applicable details:

- Physical address
- Phone number
- Business hours
- Service area
- Business category

Do not invent missing details or assume every business has a physical location.

### Social & Authoritative Profiles

Ask the user to provide any official profiles they want associated with the entity.

Examples:

- LinkedIn
- X / Twitter
- Instagram
- Facebook
- YouTube
- TikTok
- GitHub
- Wikipedia
- Crunchbase
- Other authoritative profiles

**Present one concise, optional request for profile URLs.**

Allow the user to provide any combination of URLs or skip the request entirely.

Do not require every social platform. Do not create or guess profile URLs.

Use confirmed, relevant URLs in `sameAs` where appropriate.

Store verified organization and profile information centrally so it can be reused across pages.

Do not repeatedly request information already confirmed.

## 3. JSON-LD Implementation

Use JSON-LD as the preferred structured data format.

- Prefer one centrally managed `@graph` per page when practical.
- Use stable `@id` values to reference shared entities.
- Reuse Organization, WebSite, Person, and other shared entities across pages.
- Avoid duplicate or conflicting entity definitions.
- Generate structured data using the existing framework's server-rendering or static-generation capabilities.
- Prefer including JSON-LD in the initial HTML response, without relying on client-side JavaScript.
- Place JSON-LD in the document `<head>` where supported by the existing architecture.
- Ensure JSON-LD is valid and safely serialized.
- Avoid unnecessary dependencies or custom rendering systems.

Multiple JSON-LD scripts are acceptable when required by the framework or existing implementation, provided the data remains valid and consistent.

Do not migrate frameworks or modify rendering architecture as part of this task.

If the current architecture cannot safely deliver structured data in the initial HTML, report the limitation.

## 4. Core Website Entities

### Organization

Use Organization or an appropriate subtype for the business operating the website.

Include relevant, verified properties such as:

- `@id`
- `name`
- `url`
- `logo`
- `description`
- `sameAs`
- `contactPoint`

Include only applicable properties supported by available information.

Use one consistent primary organization identity across the website.

### WebSite

Represent the overall website.

Include:

- `@id`
- `url`
- `name`
- `publisher` when applicable

Reference the existing Organization entity rather than duplicating it.

### WebPage

Represent individual public pages where useful.

Include relevant properties such as:

- `@id`
- `name`
- `description`
- `url`
- `isPartOf`
- `about`
- `primaryImageOfPage`
- `breadcrumb`

Use the preferred canonical URL.

Add `mentions`, `datePublished`, `dateModified`, or other properties only when relevant and supported by actual content.

Do not add properties simply to maximize schema coverage.

## 5. Page-Specific Structured Data

### LocalBusiness

Use when the website represents an actual local business or a specific physical business location.

Include verified information where applicable:

- Business name and type
- Address
- Phone number
- Opening hours
- Geographic location
- Service area
- Official website

Do not create physical locations or business hours that have not been confirmed.

For multi-location businesses, use location-specific entities where appropriate.

### Product

Use for pages representing identifiable products or eligible commercial offerings.

Include applicable properties:

- `name`
- `description`
- `image`
- `brand`
- `offers`
- `aggregateRating`
- `review`

Only include prices, availability, ratings, and reviews when they are genuine, current, and supported by visible content.

Do not fabricate ratings, reviews, or commercial information.

Do not apply Product schema indiscriminately to generic marketing or service pages.

### SoftwareApplication

Use for actual software products or applications.

Include relevant properties such as:

- `name`
- `description`
- `applicationCategory`
- `operatingSystem`
- `url`
- `creator` or `publisher`

Add offers or ratings only when supported by verified information.

### ProfilePage & Person

Use ProfilePage when a page primarily profiles an identifiable person or organization in a context supported by the schema and applicable search guidelines.

Examples may include:

- Public author profiles
- Community member profiles
- Employee or contributor profiles, when appropriate

Use Person for identifiable authors or individuals when relevant.

Include verified properties such as:

- `name`
- `url`
- `image`
- `description`
- `sameAs`

Do not invent biographies, affiliations, credentials, or social profiles.

### Article / BlogPosting

Use for editorial content, articles, and blog posts.

Include applicable properties:

- `headline`
- `description`
- `author`
- `publisher`
- `image`
- `datePublished`
- `dateModified`

Reference existing Person or Organization entities for authors and publishers.

### BreadcrumbList

Use where the website has a meaningful navigational hierarchy.

- Reflect the actual page hierarchy.
- Use valid production URLs.
- Include correctly ordered ListItem positions.
- Match visible breadcrumbs when present.
- Do not invent unnecessary hierarchy levels.

### VideoObject

Use for relevant video content available on the page.

Include supported properties such as:

- `name`
- `description`
- `thumbnailUrl`
- `uploadDate`
- `duration`
- `contentUrl` or `embedUrl`

Only include verified information.

Do not invent video URLs, dates, or durations.

### FAQPage

Evaluate FAQPage only when the page contains genuine, visible questions and answers.

- Structured questions and answers must match the visible content.
- Do not generate hidden or artificial FAQs.
- Follow Google's current FAQ rich result eligibility requirements.
- Do not add FAQPage solely to pursue rich results on ineligible websites.

### JobPosting

Use on individual, publicly accessible job detail pages.

Include applicable information such as:

- Job title and description
- Hiring organization
- Employment type
- Job location or remote-work details
- Date posted
- Application URL
- Salary information, when available

Ensure structured data stays synchronized with the actual job listing.

Remove or update markup when a position closes, expires, or changes.

Follow Google's current JobPosting requirements.

### Event & Other Types

Evaluate additional structured data types when relevant to actual content, such as events, courses, recipes, services, or other eligible page types.

Check Google's current documentation and required properties before implementation.

Do not create unsupported or unnecessary schema.

## 6. Entity Relationships

Use consistent entity identifiers and references to establish meaningful relationships.

Examples:

- WebSite → publisher → Organization
- WebPage → isPartOf → WebSite
- Article → author → Person
- Product → brand → Organization
- SoftwareApplication → creator → Organization

Use stable, production-based `@id` values.

Reference shared entities rather than generating conflicting duplicates.

Use `about`, `mentions`, `publisher`, `creator`, `provider`, and other relationships only when semantically appropriate.

Do not create artificial entity relationships or keyword-stuffed mentions.

## 7. Publication & Modification Dates

Use dates only on schema types and entities where they are appropriate.

### datePublished

- Represent the actual original publication date.
- Preserve the original date across future deployments.
- Derive it from reliable content metadata where available.
- Never substitute the current date when the original publication date is unknown.

### dateModified

- Represent the most recent meaningful content update.
- Update when relevant content changes.
- Do not update solely because the application was rebuilt or redeployed.
- Use reliable CMS timestamps or equivalent content metadata.

Use valid ISO 8601 dates or date-time values.

Ensure structured dates remain consistent with visible publication or update dates.

If reliable dates are unavailable, omit optional date properties or request the missing information.

## 8. Automatic Synchronization for Future Pages

Integrate structured data generation into the existing page templates, CMS, content models, or build workflow.

Whenever a page is created, updated, or removed:

- Identify applicable schema types based on its actual content.
- Generate structured data for newly introduced eligible content.
- Update structured data when corresponding content changes.
- Remove obsolete structured data when content is removed.
- Preserve shared entity references.
- Validate required properties and relationships.
- Prevent stale, duplicate, or conflicting markup.

Generate structured data from the same source used to render visible page content whenever possible.

Avoid manually maintaining separate copies of the same information.

Support static, nested, dynamic, and localized routes where applicable.

For multilingual pages, use the appropriate localized content and language information.

Prefer existing framework capabilities and incremental validation.

Do not introduce a new CMS, paid service, or unnecessary dependencies.

## 9. Actions & Conversion Elements

Do not automatically generate structured data for every CTA, button, form, or conversion element.

Evaluate Schema.org actions such as SearchAction or RegisterAction only when they accurately describe a meaningful, supported website capability.

- Use real, functional destinations.
- Follow current Schema.org definitions.
- Avoid speculative or unsupported actions.
- Do not add action markup solely for SEO coverage.

Prioritize meaningful entity and content schema over unnecessary action markup.

## 10. Validation

Validate representative pages and all implemented schema types.

Check that:

- JSON-LD parses correctly.
- Schema types and properties are valid.
- Required properties are present for applicable Google search features.
- Structured data accurately reflects page content.
- Canonical URLs and entity identifiers are consistent.
- Images and referenced URLs are valid.
- Shared entities are not duplicated inconsistently.
- Publication and modification dates are accurate.
- No fabricated ratings, reviews, prices, or business information are included.
- New pages automatically receive relevant structured data.
- Updated or removed content is reflected in the markup.

Use Google's Rich Results Test for supported search features:

https://search.google.com/test/rich-results

Use Schema.org validation for general structured data:

https://validator.schema.org/

A successful validation does not guarantee indexing, rich results, search rankings, or AI-generated citations.

If external validation tools cannot be accessed, run available local checks and report the limitation.

## 11. Implementation & Reporting

1. Inspect existing structured data, page templates, and content sources.
2. Identify applicable schema types and existing issues.
3. Ask the user once for missing essential business information and optional official profile URLs.
4. Preserve accurate existing markup.
5. Implement only relevant, supported structured data.
6. Centralize reusable entity definitions.
7. Integrate automatic updates into existing content workflows.
8. Validate representative pages and schema types.
9. Confirm no changes to design, routing, content, or functionality.

Do not migrate frameworks, invent business information, introduce paid services, or publish automatically.

## Final Report

Provide a concise summary of:

- **Schema added or updated:** Types implemented and representative pages.
- **Business information:** Missing or unconfirmed details requiring user input.
- **Entity relationships:** Shared entities and identifiers established.
- **Future-page automation:** How structured data stays synchronized with content.
- **Validation:** Checks completed and unresolved errors.
- **Remaining opportunities:** Relevant schema types that could not be safely implemented.

Avoid unnecessary dependencies, unrelated code changes, and exhaustive reporting of unchanged pages.
