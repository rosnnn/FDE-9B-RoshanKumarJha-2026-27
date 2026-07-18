# D4 Error Handling and Retry Framework (Deliverable 4)

## Error Taxonomy
- TRANSIENT: network timeout, temporary service unavailability, token refresh race.
- PERMANENT: invalid auth scope, unsupported endpoint, policy violation.
- DATA_QUALITY: malformed field, enum mismatch, referential integrity failure.
- SYSTEM: connector failure, queue pressure breach, storage outage.

## Retry Strategy
Formula: wait = min(cap, random(base, base * 2^attempt))
- Critical: fast first retries + bounded cap.
- Non-critical: widened intervals to protect downstream stability.

## Circuit Breaker
States: CLOSED -> OPEN -> HALF_OPEN -> CLOSED
Signals:
- error_rate > threshold
- timeout_rate > threshold
- success_probe_count in HALF_OPEN

## Dead Letter Queue
- Retention: 30 days
- Metadata: error class, payload hash, domain, correlation id, first/last failure timestamp
- Operations: inspect, replay, discard with reason code

## Notification Matrix
- P1: SYSTEM and critical TRANSIENT (Pager + incident room)
- P2: repeated DATA_QUALITY spikes (email + dashboard)
- P3: non-critical retry saturation (ticket backlog)
