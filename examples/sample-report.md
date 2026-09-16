# Sample AegisTrace Report

This fictional example illustrates the expected reporting standard. It is not a real finding.

## Executive summary

One confirmed, directly reachable authorization flaw allows an authenticated user to download another tenant's invoice by changing an invoice identifier. Fix the tenant ownership check before shipping.

## Coverage

- Commands run: `npm test`, `npm run lint`
- Inspected: invoice API routes, authorization middleware, invoice service, repository queries, and related tests
- Not fully covered: background export worker and legacy admin routes

## Finding AT-001

**Title:** Missing tenant ownership check in invoice download

| Field | Value |
| --- | --- |
| Status | Confirmed |
| Severity | High |
| Confidence | High |
| Reachability | Directly reachable |
| Affected files | `src/routes/invoices.ts:42`, `src/services/invoices.ts:87` |
| Affected component | `GET /api/invoices/:invoiceId/download` |

**Root cause:** The route passes an attacker-controlled `invoiceId` to a lookup that filters by ID but not by the authenticated user's tenant.

**Attack path:** Authenticated user -> `GET /api/invoices/{another-tenant-id}/download` -> route handler -> `getInvoiceById` -> file response -> cross-tenant invoice disclosure.

**Evidence:** The route reads `req.params.invoiceId`; the service query lacks `tenant_id = currentUser.tenantId`; a local test account can retrieve a fixture invoice from a second tenant.

**Minimal local reproduction:** Sign in as a fixture user in tenant A, request an invoice fixture ID from tenant B, and observe a successful download.

**Recommended fix:** Pass the authenticated tenant ID to the service and filter the lookup by both invoice and tenant ID. Return the same not-found response for absent and unauthorized invoices.

**Regression tests to add:** Assert a tenant A user receives `404` when requesting a tenant B invoice; preserve the successful same-tenant case.

**Related variants:** Inspect all downloads and exports that call `getInvoiceById`.
