# D2 API Specification (Deliverable 2)

## Scope
The OpenAPI contract in docs/api/API_SAP_FinSight.yaml defines 12 source extraction endpoints (SRC-001..SRC-012) and 12 destination write endpoints (DST-001..DST-012).

## Contract Principles
- Explicit request/response schemas.
- Deterministic error formats for retry classification.
- Pagination, filtering, and delta windows for source domains.
- Idempotency key in destination write operations.

## Authentication and Authorization
- OAuth2 client credentials for service calls.
- Token refresh and scope-based endpoint isolation.
- Access log correlation using x-correlation-id.

## API Reliability Requirements
- 429 handling with retry-after semantics.
- 5xx classified as transient unless policy exception.
- Domain-specific SLAs and timeout budgets.

## Quality Controls
- YAML syntax reviewed.
- Naming and path consistency validated against endpoint registry.
- Versioned for backward-compatible evolution.
