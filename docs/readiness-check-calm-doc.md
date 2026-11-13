# Running the SAP Readiness Check for SAP Cloud ALM

Oct 22, 2026 · @Wence

Answer the 10 questions below with **Yes** or **No** in the Answer column. If every answer is Yes, you are ready to run the SAP Readiness Check for SAP Cloud ALM; follow Part 2. Any No tells you exactly what to fix first.

The check analyses how you use SAP Solution Manager 7.2 and shows which capabilities have an equivalent in SAP Cloud ALM. It collects usage metadata only, and takes about 1–2 hours of Basis work plus background job runtime.

## Part 1 — Are you ready?

### A. Your system

| # | Question | Answer | If No, do this |
| --- | --- | --- | --- |
| 1 | Do you run **SAP Solution Manager 7.2**? | Yes | The check only runs on SolMan 7.2. Contact us to discuss alternatives. |
| 2 | Can you run it in the **production** SolMan system, in the **productive client**? |  | Arrange access to production. Results from a dev or test SolMan do not reflect real usage. |
| 3 | Do you have a user who can use **SNOTE, PFCG, SA38, SM37 and SM59** in that client? |  | Ask your Basis team to run the steps, or to grant these transactions. |

### B. Data collector

| # | Question | Answer | If No, do this |
| --- | --- | --- | --- |
| 4 | Is SAP Note **3236443** implemented in its **latest version**? (Check its status in SNOTE.) |  | Implement or update it in SNOTE, or update ST-PI to SP21 or higher. Re-check before every new run. |
| 5 | Can you implement the note and the role through your **change process** this week? |  | Book a change window first; both are changes to Solution Manager. |

### C. Authorizations and connectivity

| # | Question | Answer | If No, do this |
| --- | --- | --- | --- |
| 6 | Has the **template role** attached to note 3236443 been imported in PFCG and assigned to the user who will run the collection? |  | Download the role from the note, upload and copy it in PFCG, generate it, assign it. The background job runs under this user. |
| 7 | Does RFC destination **WEBADMIN** exist and pass the connection test in SM59? |  | Create or repair it. Without it, the collector program short-dumps. |

### D. Uploading to SAP

| # | Question | Answer | If No, do this |
| --- | --- | --- | --- |
| 8 | Do you have an **S-user** for your customer number? |  | Ask your SAP super-administrator to create one. |
| 9 | Can that S-user open the SAP Readiness Check app at [me.sap.com/readinesscheck](https://me.sap.com/readinesscheck)? |  | Ask your super-administrator for the Readiness Check authorization in SAP for Me. |
| 10 | Does your security policy allow uploading the usage data to SAP? |  | The downloaded ZIP is human-readable: let your security team review it before upload. |

**All 10 = Yes?** Go to Part 2. **Any No or Not sure?** Fix that row first, or send us this page and we will help.

## Part 2 — Run the check

Tick each step as you complete it.

- [ ] Log on to the productive client of production SolMan with the user from question 6.
- [ ] In **SA38**, run program `/SDF/RC_ALM_COLLECT_DATA`.
- [ ] Choose **Schedule Analysis**. This starts the master background job.
- [ ] In **SM37**, wait until all collection jobs have finished.
- [ ] Back in the program, choose **Display Analysis Log** and confirm no collector ended in error.
- [ ] Choose **Download Analysis Data** and save the ZIP file.
- [ ] Open [me.sap.com/readinesscheck](https://me.sap.com/readinesscheck) and choose **Start New Analysis**.
- [ ] Enter an analysis name (for example `<SID> CALM RC <date>`), select the ZIP, accept the Terms of Use and choose **Create**.
- [ ] Wait until the status changes from **In Preparation** to **Available** (usually minutes, up to 1 hour), then open the dashboard.

Running it again later? Choose **Delete Buffered Analysis Data** in the program before scheduling a new analysis.

## Part 3 — Send us the results

- [ ] In the Readiness Check dashboard, download the results (Word report plus the Excel capability lists).
- [ ] Send the files to your SOLMAN365 consultant, together with this page with your answers.

We use them to map your Solution Manager usage to SAP Cloud ALM and to estimate your transition.

## Sources

- [SAP Note 3236443 — SAP Readiness Check for SAP Cloud ALM](https://me.sap.com/notes/3236443)
- [SAP Community: Steps to generate SAP Readiness Check report for SAP Cloud ALM](https://blogs.sap.com/2023/05/17/steps-to-generate-sap-readiness-check-report-for-sap-cloud-alm/)
- [SAP Technical Guru: SAP Readiness check for Cloud ALM](https://saptechnicalguru.com/?p=9363)
- [SAP Learning: Using the Tool Readiness Check](https://learning.sap.com/courses/implementing-with-sap-cloud-alm/using-the-tool-readiness-check_c0c7ac7b-8cdb-4459-952d-7067b2ecda02)
