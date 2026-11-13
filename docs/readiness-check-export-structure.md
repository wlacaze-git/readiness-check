# SAP Readiness Check for SAP Cloud ALM — export structure (reference)

Reference derived from a real customer export analysed 2026-10-21 (SolMan 7.2). Used as input for the "Estimate from your Readiness Check" entry product in the service offering (artifact v0.3). No client data kept here.

## Files in the export ZIP
- `SAP Readiness Check for SAP Cloud ALM.docx` — full report, ~54 tables
- `Full Capabilities List for Implementation.xlsx` (~68 rows), `...Operations.xlsx` (~21), `...Service.xlsx` (~10), `...Administration.xlsx` (~7): columns SolMan Scenario | Capability | Availability Category | CALM Scenario | CALM Capability | Another SAP Solution | Link | Status (Relevant/Not) | Comments
- `ChangeReqManagement.xlsx`: Cycle Id | Description | Type (SMIM phase / SMAI continual) | Tracks | RfCs | Change Documents | Transport Requests | TR Owners | Retrofit | SolDoc Integration | Focused Build | Cross-Landscape Distribution | Repack | Cutover | ATC Integration

## Word report sections
1. Intro + header (SID, client, version, installation no., analysis date)
2. Usage in SolMan: ~110 capabilities, In use / Relevant / Collector status
3. Transition activities per area (Cross, Implementation, Operations, Service, Support): recommended activities + SAP setup effort in hours (tenant 1h, IAS 1h, roles 2h, landscape 1+1h, notifications 2h; optional integrations 1–3h each; Operations effort per system table). These are setup clicks, not project effort.
4. Availability of relevant capabilities (Available in CALM / Another SAP Solution / Roadmap / Vision / Only SolMan)
5. CALM capabilities with Used / Not used / Only in CALM, incl. per-solution Operations table (~387 rows)
6. SDT scope analysis: per solution and branch — counts + 6/12-month changes for process hierarchy types, libraries, processes/diagrams, documents/test cases/steps; LCGs; custom attributes with/without CALM equivalent
7. ChaRM insights: active cycles summary + per-cycle detail
8. Enhancements & extensions: ABAP Z objects, custom tables, AET fields, BSP, add-ons, transaction type modifications, custom cycles

## Not covered by the RC (must ask customer)
ITSM/service desk usage, users/roles, real approval flows, external tools, test automation, non-ABAP/cloud systems, compliance, roadmap-blocker tolerance, dates, history retention.

## Typical "ChaRM-only" profile seen in practice (anonymised)
Many active cycles (mix of phase and continual), few RfCs, thousands of change documents/transports, retrofit on break-fix cycles, many LCGs, CTMS in use; SolDoc/Test Suite/Projects unused; minimal Operations. Gaps typically flagged: Standard Change + Phase Cycle (roadmap), CSOL/Branch/Custom Code Library (vision), Sites/Quality Cockpit/Customizing Sync/License Data Distribution (only SolMan). AET fields on RfC holding an external ticket number hint at a Package 4 integration. → Band M, Packages 1 + 3, no SDT.
