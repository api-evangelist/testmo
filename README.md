# Testmo (testmo)

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
