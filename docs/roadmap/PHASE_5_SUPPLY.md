### Phase 5 — Supply Chain, IoT Cold-Chain, MICHELIN Key Compliance (Months 13–15)
- **Month 13:** Reservation-driven par-level procurement; FEFO dispatch; OCR supplier invoice parsing.
- **Month 14:** Live GPS tracking for air-freighted luxury imports; instant mobile-bank payouts for local foragers and small organic farms.
- **Month 15:** Continuous MICHELIN Key QA Audit Tracker; Bluetooth HACCP thermal probe logging; predictive appliance failure diagnostics.

---

## Supplemental implementation guidance retained from the review

The following material supplements the exact chat roadmap above; the phase/month deliverables above remain the roadmap baseline.

### Phase 5 — Supply, IoT and Venue Operations
Window: Months 13–15 (original target 2027-Q4; provisional). Goal: traceable procurement/receiving and selected monitoring.

## Work
- Model suppliers, purchase orders, deliveries, lots, provenance, expiry and receiving exceptions.
- Prototype reservation/menu-based par suggestions; staff approve. FEFO only with reliable lot/expiry data.
- Evaluate invoice OCR on real representative documents; human review, confidence thresholds, correction and source linkage required.
- Evaluate cold-chain/dry-aging sensors, calibration, offline buffer, alert routing, maintenance and export.
- Define HACCP capture/export with jurisdiction and food-safety review.
- Add GPS tracking only for confirmed freight use and available provider data.
- Treat mobile-bank payouts as a separate regulated third-party integration requiring demand/provider and finance/legal review.
- Make MICHELIN Key QA configurable; verify criteria and brand/program claims with authoritative sources.
- Defer appliance diagnostics until telemetry and maintenance partner exist.

## Exit evidence
Trace selected goods through a recall-style lookup; measure OCR accuracy/correction time by document type; test sensor calibration, disconnect, clock drift, low battery and recovery; document market-specific compliance evidence.

Gate: partner demonstrates traceability and reliable records with manual fallback/export.



## Technology fit update (supplementary; exact roadmap bullets above are unchanged)
- FEFO requires reliable lot and expiry data at receiving; start with scan/capture, alerts, traceability and manual override before automated dispatch.
- Invoice OCR must retain source documents, line-level confidence, human correction and supplier/tax/total reconciliation; integrate accounting/AP tools where feasible.
- HACCP records support the food operator’s procedures; software does not itself make a venue compliant. Evaluate available temperature probe/logging systems, calibration, offline buffers, corrective actions and export.
- MICHELIN Keys are qualitative awards, not a compliance checklist. Describe this as configurable hospitality QA without implying MICHELIN endorsement.
- Use carrier feeds before custom freight GPS; use authorized payment providers for payouts; defer predictive maintenance until equipment telemetry and a maintenance workflow are available.
- Map NF525, German TSE and PCI DSS by jurisdiction and payment/cash-register functions after deciding whether the product handles payments or integrates with a separate provider.
