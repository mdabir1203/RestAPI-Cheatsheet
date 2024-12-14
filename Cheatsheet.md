# Microsoft Azure REST API Guidelines - DO Checklist

## HTTP Guidelines
- [ ] **URL pattern:** `https://<tenant>.<region>.<service>.<cloud>/<service-root>/<resource-collection>/<resource-id>`
- [ ] **Use kebab-casing** for URL path segments.
- [ ] **Ensure all HTTP methods are idempotent**.
- [ ] **HTTP methods are case-sensitive** and should always be **UPPERCASE**.
- [ ] **Return `204-No Content`** for DELETE operations, even if the resource does not exist.
- [ ] **Support optimistic concurrency** with `ETag` headers.
- [ ] **Use camel case** for query parameter names.

---

## REST Guidelines
- [ ] **Ensure clear and consistent naming** of resource paths and operations.
- [ ] **Simplify operations** by reducing required query parameters and JSON fields.
- [ ] **Use consistent JSON schema** across methods for request/response.
- [ ] **Fail with `400-Bad Request`** for unknown fields or improper formatting.
- [ ] **Keep fields shallow** and avoid deep nesting in JSON.

---

## Handling Errors
- [ ] **Return `x-ms-error-code`** in headers with a descriptive error string.
- [ ] **Provide a structured response body** for errors:
  - [ ] `code`, `message`, `target`, `details`, `innererror`.
- [ ] **Document top-level error codes** as part of the API contract.

---

## JSON Guidelines
- [ ] **Use camel case** for all JSON field names.
- [ ] **Follow RFC3339** for date/time formatting.
- [ ] **Use integers** within the acceptable JSON number range.
- [ ] **Ensure JSON is round-trippable** across programming languages.

---

## Collections
- [ ] **Return `nextLink`** for paginated results and include required query parameters.
- [ ] **Include `id` and `etag` fields** for collection items.
- [ ] **Support filtering, ordering, and pagination** with query options:
  - [ ] `filter`, `orderby`, `top`, `maxpagesize`.

---

## Versioning
- [ ] **Use `api-version`** as a required query parameter for every request.
- [ ] **Follow `YYYY-MM-DD` format** for versioning.
- [ ] **Return `400` errors** for missing or unsupported `api-version`.

---

## Actions
- [ ] **Use POST** for performing actions on resources or collections.
- [ ] **Support Repeatability headers** (`Repeatability-Request-ID`, `Repeatability-First-Sent`).
- [ ] **Return `200-OK`** for synchronous success.

---

## Long-Running Operations (LROs)
- [ ] **Implement LROs** for operations exceeding 1-second response times.
- [ ] **Provide an `operation-location` header** with an absolute status URL.

---

### Checklist Usage
- **Tick** each box as you implement or review each guideline.
- **Fill in** any necessary details or notes alongside the checklist items.
- Use this as a reference to ensure consistency and compliance with the guidelines.
