# App demonstration and Task history evidence

Use this contract when planning an Environment, implementing an App, and reviewing its delivery. Proposal review checks the **plan**; completed screenshots, integration runs and history-count reports belong to delivery review. Record the policy revision alongside the approved scope. For an already approved proposal, agree and record any added delivery work rather than silently changing its scope.

## 1. GUI: reference, implementation and workflow sequence

For every required GUI workflow, provide an evidence index in the App README or a linked `evidence/README.md`. Keep screenshots in that directory or in stable PR attachments. Review evidence is separate from runtime assets and is not part of the App's media-bundle budget.

| Evidence | Required content |
| --- | --- |
| Reference-product screenshots | Screenshots of the original product's relevant pages/states, with source URL, capture/publication date and the workflow illustrated. Use public documentation or authorized captures; redact personal data. Explain inaccessible references and obtain a reviewed alternative, rather than inventing an original-product screenshot. |
| Corresponding implementation screenshots | Identify the matching implemented page/state, App commit, Host/browser version, viewport and synthetic run/account. Explain intentional functional or layout differences. A reference is a workflow comparison, not a requirement to copy branding or match pixels. |
| Ordered demonstration | For each core GUI workflow: starting state → actual control/action → intermediate/confirmation state where applicable → visible outcome. Include relevant edit/cancel, invalid/denied and stale/conflicting cases. Annotate actions and expected versus observed results, not just a gallery of unrelated pages. |
| State and test evidence | Link the sequence to its browser test or reproducible manual steps, MCP/API calls, persisted record/version and relevant receipt. Check reload and an independent update through the public interface. Retain App-only business and real MCP tests; screenshots do not replace either. |

The contributor supplies this comparison and sequence; the reviewer opens the artifacts and reproduces key flows in a real browser. Screenshots alone cannot establish that controls work. Report GUI, MCP/API and business-test outcomes separately. An approved MCP-only scope has no GUI screenshot requirement; record that scope explicitly. A promised GUI cannot be reclassified as MCP-only by omitting its implementation.

## 2. Demonstrate declared App dependencies

Cover **every integration claimed as implemented**, including required connections, delivered optional connections, separate Agent calls to personal Apps, and Messaging. Future/deferred connections stay explicitly outside the delivered scope. Use the real pinned dependency through its public tools/receive contract, not only a fake client or a private copy of its state.

For each workflow, record:

1. Source and destination App revisions, exact interface/contract, caller/direction, synthetic account binding and initial states.
2. Runnable command or demonstration steps, actual requests/results and correlation IDs. If the flow starts from a required GUI, include that GUI action and the destination's visible result when a destination GUI is available; otherwise use its real MCP/API result.
3. Result in the dependency: exact recipient/account, record IDs, state/version and, for files, immutable source version, received bytes/hash and accessibility. For read dependencies, show that the source record/version was actually read and used by the downstream action.
4. Relevant missing/denied dependency, incompatible contract/version, retry/duplicate and unknown-result behavior. Check both Apps for unintended changes. Do not infer automatic cross-App rollback.

Distinguish **local send/commit**, **receiver delivery/commit** and **recipient/business confirmation**. A successful publisher return or a delivery receipt does not prove the last of these. Keep App-only test doubles for unit tests, but label them correctly. Reviewers rerun the integration and inspect the dependency's actual state, not only the author's screenshots or test count. See [App integrations](app-integrations.md).

## 3. History: at least 300 distinct dates

Each Task's supplied historical dataset must cover **at least 300 distinct calendar dates within 2025-01-01 through 2026-12-31, inclusive**. Count the union across the Task's historical sources/Apps, not 300 per App. Multiple records, fields or Apps on one date count once; a 300-day elapsed span or 300 records is insufficient. The dates need not be consecutive and neither endpoint must contain a record.

Declare one IANA time zone for counting. Convert offset-bearing timestamps to that zone before taking their date. A date-only record is already a date in that zone. Use the authoritative historical occurrence/receipt date for each record, not its file modification, dataset-generation or export time. Do not count scheduled future events, rollout actions, date lists, empty placeholders or duplicated content fabricated solely to meet the count. Reviewers must judge that records are plausible, populated, task-relevant history; arithmetic alone cannot establish quality.

History must precede the first session. Date-only records on the first-session date need an actual time to establish this ordering. The existing rule that external-platform tasks start on or after **2026-01-01** remains. Task sessions and scenario events stay within the supported window ending **2026-12-31**. Older text-only personal background can still be retained under the existing policy, but dates outside the coverage window do not count toward the 300-date requirement.

**Ownership:** Task authors supply or select the historical dataset and count it. App authors provide seed/import, retrieval and date-dependent behavior that can load and use that history; an App delivering a historical corpus also supplies its coverage evidence. An App's minimal smoke-test fixture need not contain 300 dates. Environment proposals identify the historical fields/generation support and who supplies Task-specific history; Task proposals specify the date-coverage plan. Do not lengthen a Task's execution to 300 days just to satisfy a history requirement.

### Reproducible count

The contributor supplies a script, query or documented reproducible calculation over the **actual historical records** used to populate the Task. No new App schema or platform-specific file format is required. Include:

- Source files/dataset revisions and hashes, stable record IDs, the authoritative date field in each source, and any exclusions with reasons. For an export, explain how it maps to the records actually loaded into the Apps.
- The counting time zone, first-session cutoff and treatment of missing, invalid, out-of-window and future dates. Such records do not count; unresolved errors must be reported rather than silently hidden.
- Exact calculation/reproduction steps, total record count, per-source distinct-date counts, the **global deduplicated count**, earliest/latest counted dates and the date list or per-date breakdown.
- Representative content and a history-loading/query demonstration, so reviewers can check realism and that the counted data are actually available through the claimed App interfaces.

Reviewers rerun the supplied calculation against the delivered records, compare hashes and totals, and inspect representative content. Fewer than 300 valid distinct dates fails the coverage requirement. A hand-entered count, copied passing report, 300-day span or arithmetic over a fabricated date list is insufficient. Counting alone does not certify realism or prove that the records were loaded successfully.

At proposal stage, state the intended window, time zone, historical sources/date fields, planned distinct-date count and generation/export/check method. Do not claim that planned data have already passed verification.

## Delivery evidence index

| Workflow / requirement | Scope and pinned versions | Reference screenshots | Implemented sequence / actions | Business and MCP tests | Dependency result / files / receipts | Date report / source mapping | Verdict and remaining gap |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Name the actual workflow | Required, delivered optional, or deferred | Link or justified N/A | Ordered links and observed outcomes | Commands and reports | Inspect the actual dependency | Link when supplying Task history | Passed / failed / not run / N/A with reason |

Keep the four [implementation review sections](review/app-implementation-checklist.md) and the D1–D8 proposal checklist. These evidence requirements strengthen the relevant sections; they do not create a second approval process or replace maintainer review.
