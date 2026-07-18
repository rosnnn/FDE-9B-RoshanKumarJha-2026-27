# D6 Monitoring and Alerting (Deliverable 6)

## Dashboard Panels (12)
1. Ingestion throughput by domain
2. Destination success rate
3. Retry rate trend
4. DLQ depth by domain
5. Circuit breaker state map
6. API latency p50/p95/p99
7. Schema validation failure rate
8. Reconciliation mismatch percentage
9. Batch completion SLA timer
10. Token/auth error rate
11. Queue consumer lag
12. End-to-end processing lag

## Logging Standard
Mandatory fields:
- timestamp
- level
- correlation_id
- tenant_id
- domain
- source_system
- destination_endpoint
- status
- error_class
- retry_attempt
- latency_ms
- payload_hash

## Alerting Rules (15+)
- P1: destination success rate < 90% for 5m
- P1: DLQ depth > critical threshold
- P1: circuit breaker open on critical domains
- P2: retry rate > baseline by 3x
- P2: reconciliation mismatch > threshold
- P2: latency p95 exceeds SLA
- P3: token refresh anomalies
- P3: validation failures trending upward
- P4: low-severity config drift warnings
(plus domain-specific variants and escalation mappings)
