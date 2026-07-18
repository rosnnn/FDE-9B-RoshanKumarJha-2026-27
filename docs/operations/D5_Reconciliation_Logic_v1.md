# D5 Reconciliation Logic and Data Quality (Deliverable 5)

## Reconciliation Dimensions
1. Completeness: source count vs destination count.
2. Accuracy: amount-level and key-field correctness.
3. Timeliness: latency and freshness SLO compliance.
4. Consistency: cross-domain semantic alignment.

## Report Design
- Batch reconciliation report (domain-level summary + exceptions).
- Daily dashboard (trend view for mismatch categories).
- Monthly audit pack (control evidence and closure rates).

## Data Quality Rules (25+)
### Null/Presence
1. mandatory company code present
2. fiscal year present
3. posting date present
4. document id present
5. currency present

### Format
6. date format ISO-8601
7. currency ISO-4217
8. customer id pattern valid
9. vendor id pattern valid
10. account id numeric constraint

### Range
11. amount not NaN
12. amount precision <= 2 decimals
13. fiscal period in valid range
14. exchange rate > 0
15. quantity >= 0

### Referential Integrity
16. cost center exists in master
17. profit center exists in master
18. company code exists in config
19. ledger code exists
20. tax code reference valid

### Cross-Field and Business
21. debit/credit balance check
22. posting date within fiscal year
23. due date >= posting date
24. status and amount consistency
25. document type allowed for domain
26. reversal records linked to original
27. duplicate key check with hash fingerprint
