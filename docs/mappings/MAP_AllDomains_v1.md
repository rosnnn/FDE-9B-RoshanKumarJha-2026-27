# D3 Data Transformation Specification

The table below contains 50 representative mappings across 10 domains.

| Mapping ID | Source Field | Target Field | Rule |
|---|---|---|---|
| MAP-001 | BKPF.BUKRS | journal.companyCode | Direct |
| MAP-002 | BKPF.BELNR | journal.documentNumber | Direct |
| MAP-003 | BKPF.GJAHR | journal.fiscalYear | Direct |
| MAP-004 | BSEG.HKONT | journal.glAccount | Trim leading zeros |
| MAP-005 | BSEG.DMBTR | journal.localAmount | Decimal(2) |
| MAP-006 | BKPF.WAERS | journal.currency | ISO 4217 validate |
| MAP-007 | BKPF.BUDAT | journal.postingDate | yyyy-mm-dd |
| MAP-008 | BSEG.KOSTL | journal.costCenter | Lookup CCA master |
| MAP-009 | BSEG.PRCTR | journal.profitCenter | Lookup PCA master |
| MAP-010 | BKPF.BLART | journal.docType | Code map |
| MAP-011 | LFA1.LIFNR | payable.vendorId | Pad-left 10 |
| MAP-012 | BSIK.ZFBDT | payable.dueDate | Direct |
| MAP-013 | BSIK.DMBTR | payable.openAmount | Decimal(2) |
| MAP-014 | BSIK.SHKZG | payable.debitCredit | Enum map |
| MAP-015 | LFA1.LAND1 | payable.vendorCountry | ISO country |
| MAP-016 | KNA1.KUNNR | receivable.customerId | Pad-left 10 |
| MAP-017 | BSID.DMBTR | receivable.openAmount | Decimal(2) |
| MAP-018 | BSID.FAEDT | receivable.dueDate | Direct |
| MAP-019 | KNB1.KLIMK | receivable.creditLimit | Decimal(2) |
| MAP-020 | KNB5.MAHNA | receivable.dunningLevel | Enum map |
| MAP-021 | CSKS.KOSTL | costCentre.id | Direct |
| MAP-022 | CSKT.LTEXT | costCentre.name | Trim |
| MAP-023 | CSKS.KHINR | costCentre.hierarchyNode | Flatten hierarchy |
| MAP-024 | CSKS.KOSAR | costCentre.type | Code map |
| MAP-025 | CSKS.BUKRS | costCentre.companyCode | Direct |
| MAP-026 | CEPC.PRCTR | profitCentre.id | Direct |
| MAP-027 | CEPCT.LTEXT | profitCentre.name | Trim |
| MAP-028 | CEPC.SEGMENT | profitCentre.segment | Direct |
| MAP-029 | CEPC.KOKRS | profitCentre.controllingArea | Direct |
| MAP-030 | CEPC.VDATU | profitCentre.validFrom | Date map |
| MAP-031 | CKMLHD.MATNR | materialLedger.material | Direct |
| MAP-032 | CKMLCR.STPRS | materialLedger.stdPrice | Decimal(4) |
| MAP-033 | CKMLCR.PEINH | materialLedger.priceUnit | Int |
| MAP-034 | CKMLCR.SALK3 | materialLedger.totalStockVal | Decimal(2) |
| MAP-035 | CKMLCR.VPRSV | materialLedger.priceControl | Enum |
| MAP-036 | EKKO.EBELN | purchaseOrder.id | Direct |
| MAP-037 | EKPO.MATNR | purchaseOrder.material | Direct |
| MAP-038 | EKPO.NETPR | purchaseOrder.netPrice | Decimal(2) |
| MAP-039 | EKPO.WERKS | purchaseOrder.plant | Direct |
| MAP-040 | EKPO.MENGE | purchaseOrder.quantity | Decimal(3) |
| MAP-041 | VBAK.VBELN | salesOrder.id | Direct |
| MAP-042 | VBAP.POSNR | salesOrder.itemNo | Direct |
| MAP-043 | VBAP.NETWR | salesOrder.netValue | Decimal(2) |
| MAP-044 | VBUP.LFSTA | salesOrder.deliveryStatus | Enum |
| MAP-045 | ANLA.ANLN1 | fixedAsset.assetId | Direct |
| MAP-046 | ANLC.NAFAG | fixedAsset.deprOrdinary | Decimal(2) |
| MAP-047 | FEBKO.KUKEY | bankStatement.statementId | Direct |
| MAP-048 | FEBEP.BETRG | bankStatement.amount | Decimal(2) |
| MAP-049 | GLT0.TSLVT | budgetActual.actual | Decimal(2) |
| MAP-050 | MARD.LABST | inventory.unrestrictedStock | Decimal(3) |
