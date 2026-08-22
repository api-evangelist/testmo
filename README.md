# Testmo (testmo)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Testmo is a unified test management platform that brings manual test cases, test automation, and exploratory testing together in one tool, with reporting, milestones, and issue-tracker and CI integrations. Testmo exposes a documented REST API for reading its major entities - projects, test runs, run results, automation runs, automation sources, exploratory sessions, and milestones - so teams can build custom analytics, reporting, and integrations. A beta test case management API adds the only write surface (cases, folders, attachments), and the Testmo CLI (`@testmo/testmo-cli`) submits automation results into Testmo from CI/CD pipelines.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/testmo/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/testmo/refs/heads/main/apis.yml)

## Access Model (Honest Notes)

- **Testmo is a commercial, hosted SaaS product.** There is no free-forever plan - paid plans start at Team ($99/month) after a free trial. The API is available on your paid instance; it is not a public, open, sign-up-and-call API.
- **The API is per-instance.** The base URL is `https://{instance}.testmo.net/api/v1`, where `{instance}` is your own Testmo subdomain. There is no single shared api.testmo.com host.
- **Authentication is a personal API token (Bearer).** You generate an API key from your profile page inside Testmo and pass it as `Authorization: Bearer <token>`. Access is scoped to your permissions; some endpoints (users, groups, roles) are admin-only.
- **Mostly read-only.** The core REST API is read-only (GET) over projects, runs, results, automation runs, automation sources, sessions, and milestones - built for analytics, reporting, and integrations. The **test case management API** (cases, folders, attachments) adds create/update/delete but is in **beta** and may change.
- **Writing results is done via the CLI, not the REST API.** New automation runs and results are typically pushed with `testmo automation:run:submit` from CI, which parses JUnit-style XML and creates the run for you - there is no documented public REST endpoint for creating a manual or automation run.
- The OpenAPI file and Postman/Open Collection in this repo are **modeled** from Testmo's public documentation and blog posts. Endpoint paths, pagination, and auth are grounded in those sources; request/response schemas are illustrative. Verify against the live docs and your instance before relying on them.

## Tags

- Test Runs
- Test Management
- Test Automation
- QA
- Exploratory Testing
- CI/CD
- Quality Assurance

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Testmo Test Runs API

Read a project's manual test runs and their individual results. Get a single run or all active or closed runs with aggregated statistics and test numbers, and extract or filter individual test results (by status, creator, and date) from a run.

- **Human URL:** [https://docs.testmo.com/api](https://docs.testmo.com/api)
- **Base URL:** `https://{instance}.testmo.net/api/v1`

#### Tags

- Test Runs
- Test Management
- QA

#### Properties

- [Documentation](https://docs.testmo.com/api)
- [API Reference](https://www.testmo.com/blog/announcing-the-new-runs-results-api-in-testmo/)
- [OpenAPI](openapi/testmo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/testmo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/testmo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Testmo Automation Runs API

Read one or all automation runs for a project, including aggregated statistics of the test results and the overall run status. Automation runs are typically created from CI/CD via the Testmo CLI and read back through this API for reporting and analytics.

- **Human URL:** [https://docs.testmo.com/api](https://docs.testmo.com/api)
- **Base URL:** `https://{instance}.testmo.net/api/v1`

#### Tags

- Automation Runs
- Test Automation
- CI/CD

#### Properties

- [Documentation](https://docs.testmo.com/api)
- [API Reference](https://www.testmo.com/blog/api-update-analytics/)
- [OpenAPI](openapi/testmo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/testmo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/testmo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Testmo Automation Sources API

Query the test automation sources of a project, including average and aggregated source statistics and metrics. Sources group automation runs (for example "backend-unit" or "e2e") so trends can be tracked per pipeline over time.

- **Human URL:** [https://docs.testmo.com/api](https://docs.testmo.com/api)
- **Base URL:** `https://{instance}.testmo.net/api/v1`

#### Tags

- Automation Sources
- Test Automation
- Metrics

#### Properties

- [Documentation](https://docs.testmo.com/api)
- [OpenAPI](openapi/testmo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/testmo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/testmo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Testmo Sessions API

Read the exploratory test sessions of a project. Get a single session or all active or closed sessions, along with result statistics of the session notes, for reporting on exploratory testing effort.

- **Human URL:** [https://docs.testmo.com/api](https://docs.testmo.com/api)
- **Base URL:** `https://{instance}.testmo.net/api/v1`

#### Tags

- Exploratory Testing
- Sessions
- QA

#### Properties

- [Documentation](https://docs.testmo.com/api)
- [OpenAPI](openapi/testmo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/testmo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/testmo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Testmo Projects API

List all projects and retrieve a single project. Projects are the top-level container that runs, automation runs, sessions, milestones, and cases belong to, so this endpoint anchors most other API calls.

- **Human URL:** [https://docs.testmo.com/api](https://docs.testmo.com/api)
- **Base URL:** `https://{instance}.testmo.net/api/v1`

#### Tags

- Projects
- Test Management

#### Properties

- [Documentation](https://docs.testmo.com/api)
- [OpenAPI](openapi/testmo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/testmo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/testmo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Testmo Milestones API

Get one milestone or all milestones of a project, optionally including milestone statistics for the linked test runs and sessions, to report progress against a release or sprint.

- **Human URL:** [https://docs.testmo.com/api](https://docs.testmo.com/api)
- **Base URL:** `https://{instance}.testmo.net/api/v1`

#### Tags

- Milestones
- Test Management
- Reporting

#### Properties

- [Documentation](https://docs.testmo.com/api)
- [OpenAPI](openapi/testmo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/testmo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/testmo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Testmo Test Case Management API

Beta read/write API for the test case repository - list, create, update, and delete cases and folders in bulk (up to 100 per request) and manage case attachments. The only write surface in the Testmo API; endpoints are in beta and may change.

- **Human URL:** [https://www.testmo.com/blog/announcing-test-case-management-apis-in-testmo/](https://www.testmo.com/blog/announcing-test-case-management-apis-in-testmo/)
- **Base URL:** `https://{instance}.testmo.net/api/v1`

#### Tags

- Test Cases
- Test Management
- Beta

#### Properties

- [Documentation](https://www.testmo.com/blog/announcing-test-case-management-apis-in-testmo/)
- [OpenAPI](openapi/testmo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/testmo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/testmo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Authentication](authentication/testmo-authentication.yml)
- [LinkedIn](https://www.linkedin.com/company/testmo)
- [Website](https://www.testmo.com/)
- [Documentation](https://docs.testmo.com/)
- [Plans](plans/testmo-plans-pricing.yml)
- [Rate Limits](rate-limits/testmo-rate-limits.yml)
- [Fin Ops](finops/testmo-finops.yml)
- [Blog](https://www.testmo.com/blog/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
