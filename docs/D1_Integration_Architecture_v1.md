# D1 Integration Architecture (Deliverable 1)

## 1. Business Objective
Meridian Manufacturing requires near-real-time and scheduled extraction of SAP finance and operational domains into FinSight for analytics, forecasting, and compliance reporting. The architecture must provide deterministic delivery, transparent audit trails, and predictable operational behavior under transient and systemic failures.

## 2. C4-Level Design Summary
### Level 1: System Context
Actors: Finance Controller, Treasury Analyst, Plant Ops Analyst, Platform Engineering, Security Officer, and Client IT.
External systems: SAP S/4HANA, Identity Provider, FinSight API platform, Notification and Incident tooling.

### Level 2: Container Model
- API Gateway: inbound policy enforcement, authentication, and rate control.
- Extraction Orchestrator: schedules batch pulls and delta extraction windows.
- Event Streaming Layer (Kafka): decouples extraction from transformation and delivery.
- Transformation Engine: schema normalization, enrichment, canonical mapping.
- Delivery Adapter: idempotent writes to destination endpoints.
- Reconciliation Service: compares source-vs-target by count/value/hash dimensions.
- Monitoring Stack: metrics, logs, traces, alerting workflows.

### Level 3: Component Model
- Source connector adapters per domain.
- Contract validator and schema evolution guardrail.
- Data quality rule executor and rejection pipeline.
- Retry policy engine and circuit breaker manager.
- DLQ processor with reprocess controls.

## 3. Non-Functional Architecture
- Availability target: 99.9% monthly integration uptime.
- Throughput target: 1M+ records/day with peak scaling buffer.
- Security: OAuth2, token rotation, least-privilege scopes, audit logging.
- Compliance: data minimization and retention controls.

## 4. Data Flow Patterns
- Real-time ODP delta for critical journals and receivables.
- Batch extraction for inventory and bank reconciliation domains.
- Exactly-once equivalent behavior through idempotency key strategy.

## 5. Risks and Mitigations
- API throttling: adaptive backoff and domain-level scheduling.
- Schema drift: strict contract validation with change review gate.
- Duplicate writes: idempotency fingerprints with conflict logging.
- Partial failure: per-domain circuit breaker and DLQ replay.

## 6. Success Criteria
- 100% schema-valid payloads at destination.
- Reconciliation mismatch rate below agreed threshold.
- P1 incidents within defined MTTR window.
- Complete data lineage from SAP extract to FinSight write.
