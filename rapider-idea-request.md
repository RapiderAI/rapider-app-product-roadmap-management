<!-- Rapider Official App SOW & Specification | App #108: Product Roadmap Management (product-roadmap-management) | Domain: DEV -->

# #108 Product Roadmap Management (`product-roadmap-management`) — Scope of Work (SOW)

- **App Number & Name:** `#108 Product Roadmap Management`
- **Proposed App Key:** `product-roadmap-management`
- **Domain / Suite & Model Prefix:** `DEV` (`Dev*`) — Category `11. Software Development & DevOps`
- **Representative Benchmark (`P1`):** `Aha!` (`Aha! Roadmaps` & `Aha! Ideas`)
- **Combined Feature Catalog:** [../combined-features/108-product-roadmap-management-features.md](../combined-features/108-product-roadmap-management-features.md)

---

## 1. Executive Outcome & Target Audience

**Product Roadmap Management (`product-roadmap-management`)** bridges customer discovery, strategic prioritization, and engineering execution inside the Rapider `DEV` suite—integrating seamlessly upstream of Rapider's built `planning` / `apm` apps (`ApmEpic`, `ApmIssue`, `ApmProjectPortfolio`). Instead of maintaining stale slide decks disconnected from engineering sprint boards and scattered customer requests in CRM/Support notes, product managers consolidate voice-of-the-customer evidence, quantify influenced ARR, rank initiatives objectively using RICE/WSJF `Decimal128` scorecards, promote winning roadmap items in one click into canonical `ApmEpic` delivery backlogs, and close the loop with customers through tailored portals and release changelogs.

- **SME & Startup Fast-Path:** A founder or PM captures feature ideas in `#/ideas`, drags validated `DevRoadmapItem` cards across `NOW / NEXT / LATER` on `<rapider-kanban>` (`#/roadmap`), applies the built-in `RICE` scorecard, and clicks **Promote to Planning Epic**—creating a linked `ApmEpic` whose live engineering completion percentage (`% Done`) automatically syncs back onto the roadmap card.
- **Enterprise Progressive Disclosure:** Multi-product portfolios unlock `DevStrategicTheme` investment mix targets tied to `HrGoal` / `ApmProjectPortfolio`, `CrmOpportunity` influenced-ARR rollups, multi-rater Priority Poker calibration, stage-gate `COMMITTED` approvals via shared Rapider Home `WorkItem`s, audience-segmented `DevRoadmapPortal` views (`INTERNAL_STAKEHOLDERS` vs. `PUBLIC`), and cross-functional `DevProductLaunch` GTM readiness checklists spanning `#105` flags, `#106` QA gates, `MKT` campaigns, and `SUP` knowledge articles.
- **Measurable Business & Engineering Outcomes:**
  1. Ensure **85%+ of committed engineering capacity** (`ApmEpic`) traces directly to quantified `DevStrategicTheme` objectives and customer-validated `DevFeedbackEvidence`.
  2. Eliminate **100% manual roadmap status deck updates** via automated bi-directional `deliveryProgressPercent` sync from `ApmEpic` / `ApmIssue` execution and `#105` feature-flag rollouts.
  3. Increase B2B renewal & expansion win rates by surfacing exact `Decimal128` influenced ARR (e.g., \$250,000.00 blocked pipeline) during quarterly prioritization.
- **Top 6 Global Benchmarks Synthesized (`P1`–`P6`):** `Aha! Roadmaps & Ideas` (`P1` — Representative Product), `Productboard` (`P2`), `Airfocus` (`P3`), `Atlassian Jira Product Discovery` (`P4`), `ServiceNow Strategic Portfolio Management` (`P5`), and `Monday.com Dev & Product Roadmaps` (`P6`).

---

## 2. In-Scope, Out-of-Scope & Suite Ownership Boundaries

### In-Scope
- Capturing, deduplicating, and triaging `DevProductIdea` requests and `DevFeedbackEvidence` records linked to `CrmAccount`, `CrmOpportunity`, and `SupTicket` (`PRM-001`–`PRM-004`, `PRM-023`).
- Defining `DevStrategicTheme` bets, configurable `DevScoringModel` frameworks (`RICE`, `WSJF`, custom weighted `Decimal128` formulas), Value-vs-Effort matrices, and Priority Poker calibration (`PRM-005`–`PRM-009`).
- Managing `DevRoadmapItem` horizons (`NOW`, `NEXT`, `LATER`, `ICEBOX`, `SHIPPED`), cross-item dependencies, Home `WorkItem` commitment approvals, and 1-click promotion + bi-directional progress sync with canonical `ApmEpic` & `ApmIssue` (`PRM-010`–`PRM-014`, `PRM-019`).
- Audience-tailored `DevRoadmapPortal` boards (with sanitized external copy and CAB voting budgets), `DevProductLaunch` cross-functional GTM readiness, customer changelogs, Notebook PRD links, and grounded AI discovery/release-note assistants (`PRM-015`–`PRM-018`, `PRM-020`–`PRM-022`, `PRM-024`–`PRM-028`).

### Out-of-Scope (Strict Zero-Duplication Boundary with Built `APM` Suite)
- **Sprint Planning, Story Points, Subtasks & Engineering Kanban:** Strictly owned by Rapider `APM` (`planning` / `apm`: `ApmProject`, `ApmEpic`, `ApmSprint`, `ApmIssue`). `#108` NEVER creates shadow `Sprint`, `UserStory`, or `Bug` tables.
- **Resource Timesheets, Utilization & Project Capex/Opex Ledgers:** Owned by `APM` (`resources`: `ApmResourceProfile`, `time`: `ApmTimesheet`, `financials`: `ApmProjectFinancialPlan`).
- **CRM Pipeline Management & Support SLA Ticketing:** Owned by `CRM` (`CrmAccount`, `CrmOpportunity`) and `SUP` (`SupTicket`).
- **Standalone Rich-Text Document Storage:** PRDs and opportunity briefs reuse canonical Rapider Platform Notebooks.

### Cross-Suite Ownership & Integration Contract

| Domain / App | Owns (Canonical System of Record) | Integration Contract with `#108` (`product-roadmap-management`) |
| :--- | :--- | :--- |
| **`#108` (`product-roadmap-management`)** | `DevStrategicTheme`, `DevProductIdea`, `DevFeedbackEvidence`, `DevScoringModel`, `DevRoadmapItem`, `DevProductLaunch`, `DevRoadmapPortal` | Governs upstream product discovery, RICE prioritization, horizons, portals, and GTM launches; emits `dev.roadmap.item_committed.v1` and `dev.roadmap.launch_published.v1`. |
| **`APM` (`planning`, `apm`, `resources`, `financials`)** | `ApmProject`, `ApmEpic`, `ApmSprint`, `ApmIssue`, `ApmProjectPortfolio`, `ApmResourceProfile`, `ApmProjectFinancialPlan` | Promoting a `DevRoadmapItem` creates/links `linkedApmEpicId` (`ApmEpic`) and optional `linkedApmIssueIds` (`ApmIssue[]`); `#108` consumes `apm.epic.progress_updated.v1` to update `deliveryProgressPercent`. |
| **`CRM` (`crm`)** | `CrmAccount`, `CrmContact`, `CrmOpportunity` | `DevFeedbackEvidence` references `crmAccountId` and `crmOpportunityId` to roll up exact `Decimal128` `influencedArrAmount` on ideas and roadmap items. |
| **`SUP` (`support`)** | `SupCustomer`, `SupTicket`, `SupKnowledgeArticle` | `DevFeedbackEvidence` links `supTicketId` escalations; `DevProductLaunch` links `SupKnowledgeArticle` readiness; shipping an idea notifies linked `SupTicket` watchers. |
| **`#105` & `#106` & `#097`** | `DevFeatureFlag` (`#105`), `DevQualityGate` (`#106`), Analytics (`#097`) | `DevRoadmapItem` / `DevProductLaunch` displays live `#105` rollout %, `#106` release gate pass status, and `#097` post-launch adoption metric links. |
| **`HR` & `MKT` & Platform Core** | `HrGoal` (`performance`), `MktCampaign` (`campaigns`), Notebooks, Home `WorkItem`s, `projectChannelMessage` | `DevStrategicTheme` aligns to `HrGoal`; `DevProductLaunch` links `MktCampaign`; PRDs link Notebook pages; `COMMITTED` & `PUBLIC` approvals use Home `WorkItem`s; AI runs on `projectChannelMessage`. |

---

## 3. Primary Web Pages & Sidebar Navigation Architecture (12 Pages)

Every visible sidebar section strictly enforces the **Minimum 3 Items Rule** (`Strategy & Roadmaps` = 3 items, `Discovery & Prioritization` = 3 items, `Launches & Portals` = 3 items; detail and drawer routes set `displayOnMenu: false`).

| # | Route | Page Title | Sidebar Section | Menu Visible | Key Components & UX Standards |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | `dashboard` | Product Strategy Overview | `Strategy & Roadmaps` | `true` (Order 1) | KPI cards (`countSWR`/`findSWR`) for Committed `NOW` Items, Synced `ApmEpic` Completion %, Untriaged Ideas, Influenced ARR, and Upcoming Launches; theme allocation donut. |
| 2 | `roadmap` | Now / Next / Later Roadmap | `Strategy & Roadmaps` | `true` (Order 2) | `<rapider-kanban>` Horizon Board (`NOW`, `NEXT`, `LATER`, `SHIPPED`) + Quarterly Swimlane toggle; `#activeFilterTagsBar` with `Clear all`; live `ApmEpic` `%` & `#105` flag badges; clickable title (`roadmap-item-detail`). |
| 3 | `themes` | Strategic Themes & Mix | `Strategy & Roadmaps` | `true` (Order 3) | `DevStrategicTheme` list comparing target vs. actual `Decimal128` investment mix %, linked `HrGoal` / `ApmProjectPortfolio`, and child roadmap count. |
| 4 | `ideas` | Customer Ideas & Evidence | `Discovery & Prioritization` | `true` (Order 4) | Dual Table + `<rapider-kanban>` Idea Triage (`NEW`, `UNDER_REVIEW`, `PLANNED`, `SHIPPED`, `DECLINED`) showing vote count, `Decimal128` influenced ARR, `CrmAccount`/`SupTicket` badges, and clickable idea title (`idea-detail`). |
| 5 | `prioritization` | RICE & Weighted Scorecards | `Discovery & Prioritization` | `true` (Order 5) | Interactive `Decimal128` scoring grid (`Reach`, `Impact`, `Confidence`, `Effort` -> `priorityScore`) + Value-vs-Effort 2x2 quadrant view and **Promote to `ApmEpic`** action. |
| 6 | `scoring-models` | Scoring Models & Criteria | `Discovery & Prioritization` | `true` (Order 6) | `DevScoringModel` governance table (`RICE`, `WSJF`, Custom Weighted) with criterion weight validation (`sum == 100.00%`), `Edit` (icon + text) and `Delete` (icon-only). |
| 7 | `launches` | Product Launches & GTM | `Launches & Portals` | `true` (Order 7) | `DevProductLaunch` milestone tracker with cross-functional readiness pills (`ApmEpic`, `#106` QA, `#105` Flag, `MktCampaign`, `SupKnowledgeArticle`) and target launch dates. |
| 8 | `portals` | Stakeholder & Customer Portals | `Launches & Portals` | `true` (Order 8) | `DevRoadmapPortal` configuration (`INTERNAL_STAKEHOLDERS`, `DESIGN_PARTNERS`, `PUBLIC`), audience visibility filters, CAB voting point budgets, and safe external copy preview. |
| 9 | `changelog` | Published Release Notes | `Launches & Portals` | `true` (Order 9) | Chronological shipped changelog feed linking `DevProductLaunch` notes to fulfilled `DevProductIdea` items with Save-to-Notebook & portal publish controls. |
| 10 | `roadmap-item-detail` | Roadmap Initiative & Delivery Sync | *(Hidden)* | `false` | `Decimal128` scorecard breakdown, linked `ApmEpic` & `ApmIssue` live delivery progress table, dependencies (`BLOCKS`/`DEPENDS_ON`), PRD Notebook link, `DevFeedbackEvidence` list, and AI Copilot (`projectChannelMessage`). |
| 11 | `idea-detail` | Idea Evidence & ARR Rollup | *(Hidden)* | `false` | Customer feedback quotes, `CrmOpportunity` ARR & `SupTicket` links, duplicate merge selector, voter list, and **Promote to Roadmap Initiative** button. |
| 12 | `roadmap-item-drawer` | Create / Edit Roadmap Item | *(Hidden)* | `false` | Sliding form drawer for `DevRoadmapItem` creation/editing (theme, horizon, RICE inputs, sanitized portal summary, `ApmEpic` link); enforces `try/catch/finally`, SWR invalidation, and auto-close. |

**Mandatory Rapider UI Compliance across all 12 Pages:**
- Initial data loads exclusively invoke `window.rapiderApi.findSWR` and `countSWR` with zero redundant `isDeleted` filter clauses; local in-memory arrays filter `item.isDeleted !== true` and update optimistically on horizon move, score edit, or delete.
- Tables never render a standalone "View" button in `Actions`; primary identifiers (`itemCode`/`title`, `ideaCode`/`title`, `themeName`, `launchName`) navigate to detail views; `Edit` uses icon + text and `Delete` uses icon-only with `aria-label="Delete"`.
- Primary and destructive confirmation buttons enforce `#ffffff !important` text contrast; native `alert`/`confirm`/`prompt` dialogs are strictly banned.

---

## 4. Canonical Data Models (`Dev*` — 7 Models)

All models omit `projectId`, use backend-generated UUIDs (`00000000-xxxx-xxxx-xxxx-xxxxxxxxxxxx` in deterministic fixtures), enforce optimistic `version` checks, and store exact financial/scoring values as `Decimal128`.

| Model Name | Key Fields & Types | Relationships & External Refs | Invariants & Lifecycle |
| :--- | :--- | :--- | :--- |
| **`DevStrategicTheme`** | `id` (UUID), `code` (String, e.g., `THM-01`), `name` (String), `description` (String), `colorHex` (String), `targetAllocationPercent` (`Decimal128`), `fiscalPeriod` (String, e.g., `FY2026`), `status` (`ACTIVE` \| `ARCHIVED`), `version` (Integer) | Optional `linkedHrGoalId` (`HrGoal`), `linkedPortfolioId` (`ApmProjectPortfolio`), `ownerUserId` (Platform Identity) | `code` unique per workspace; active themes in the same `fiscalPeriod` validate target allocation percentages in `Decimal128` (`0.00`–`100.00`). |
| **`DevProductIdea`** | `id` (UUID), `ideaCode` (String, e.g., `IDEA-304`), `title` (String), `problemStatement` (String), `publicSanitizedSummary` (String?), `portalVisibility` (`PRIVATE` \| `PORTAL_VISIBLE`), `voteCount` (Integer), `evidenceCount` (Integer), `influencedArrAmount` (`Decimal128`), `currencyCode` (String), `status` (`NEW` \| `UNDER_REVIEW` \| `PLANNED` \| `IN_DELIVERY` \| `SHIPPED` \| `DECLINED`), `mergedIntoIdeaId` (UUID?), `version` (Integer) | Refs `submittedByUserId` / `crmContactId` (`CrmContact`), `promotedRoadmapItemId` (`DevRoadmapItem`), `threadChannelId` (`projectChannelMessage`) | Merging `Idea B` into `Idea A` sets `mergedIntoIdeaId`, transfers unique voters & `DevFeedbackEvidence` without double-counting duplicate `CrmOpportunity` ARR (`Decimal128`). |
| **`DevFeedbackEvidence`** | `id` (UUID), `ideaId` (UUID), `roadmapItemId` (UUID?), `sourceType` (`CRM_OPPORTUNITY` \| `SUPPORT_TICKET` \| `CUSTOMER_CALL` \| `PORTAL_SUBMISSION`), `verbatimQuote` (String), `urgency` (`CRITICAL_BLOCKER` \| `HIGH` \| `NICE_TO_HAVE`), `crmAccountId` (UUID?), `crmOpportunityId` (UUID?), `supTicketId` (UUID?), `attributedArrAmount` (`Decimal128`), `capturedAt` (DateTime), `version` (Integer) | Belongs to `DevProductIdea` (and optional `DevRoadmapItem`); refs canonical `CrmAccount`, `CrmOpportunity`, `SupTicket` | Validates foreign references on create; `attributedArrAmount` stored in `Decimal128` (`>= 0.00`). |
| **`DevScoringModel`** | `id` (UUID), `name` (String), `methodology` (`RICE` \| `WSJF` \| `VALUE_EFFORT` \| `CUSTOM_WEIGHTED`), `criteriaDefinitions` (JSON[] — `{ key, label, weightPercent: Decimal128, role: 'NUMERATOR'\|'DENOMINATOR' }`), `isDefault` (Boolean), `version` (Integer) | Referenced by `DevRoadmapItem` | `CUSTOM_WEIGHTED` criteria weights must sum to `100.0000` (`Decimal128`); denominator (`Effort` / `Job Size`) enforces `> 0` guard against division by zero. |
| **`DevRoadmapItem`** | `id` (UUID), `itemCode` (String, e.g., `RMP-112`), `title` (String), `publicPortalTitle` (String?), `themeId` (UUID), `scoringModelId` (UUID), `criterionInputs` (JSON), `priorityScore` (`Decimal128`), `effortEstimatePoints` (`Decimal128`), `influencedArrAmount` (`Decimal128`), `horizon` (`NOW` \| `NEXT` \| `LATER` \| `ICEBOX` \| `SHIPPED`), `targetQuarter` (String?), `commitmentStatus` (`PROPOSED` \| `PENDING_APPROVAL` \| `COMMITTED`), `dependsOnItemIds` (UUID[]), `linkedApmEpicId` (UUID?), `linkedApmIssueIds` (UUID[]), `deliveryProgressPercent` (`Decimal128`), `prdNotebookPageId` (UUID?), `linkedFlagId` (UUID?), `version` (Integer) | Belongs to `DevStrategicTheme` & `DevScoringModel`; refs canonical `ApmEpic`, `ApmIssue[]`, `#105` `DevFeatureFlag`, Platform Notebook page, Home `WorkItem` | Acyclic `dependsOnItemIds` graph; transitioning `horizon -> NOW` with `commitmentStatus = COMMITTED` requires approved Home `WorkItem` when portfolio governance is enabled; `deliveryProgressPercent` synced read-only from `ApmEpic` when linked. |
| **`DevProductLaunch`** | `id` (UUID), `launchCode` (String), `name` (String), `tier` (`TIER_1_MAJOR` \| `TIER_2_STANDARD` \| `TIER_3_MINOR`), `roadmapItemIds` (UUID[]), `targetLaunchDate` (Date), `readinessChecks` (JSON — `{ apmComplete, qaGatePassed, flagReady, docsReady, mktReady }`), `releaseNotesMarkdown` (String), `status` (`PLANNING` \| `READY_FOR_LAUNCH` \| `PUBLISHED`), `publishedAt` (DateTime?), `version` (Integer) | Refs `DevRoadmapItem[]`, optional `mktCampaignId` (`MktCampaign`), `supArticleId` (`SupKnowledgeArticle`), `qaGateRunId` (`#106` `DevTestRun`) | Publishing (`status -> PUBLISHED`) seals published changelog revision (subsequent edits create versioned changelog updates) and transitions linked `DevRoadmapItem` & `DevProductIdea` records to `SHIPPED`. |
| **`DevRoadmapPortal`** | `id` (UUID), `name` (String), `slug` (String), `audienceScope` (`INTERNAL_STAKEHOLDERS` \| `DESIGN_PARTNERS` \| `PUBLIC`), `includedThemeIds` (UUID[]), `allowIdeaSubmission` (Boolean), `votingPointBudgetPerUser` (Integer?), `requirePublishApproval` (Boolean), `isActive` (Boolean), `version` (Integer) | Governs filtered projection of `DevRoadmapItem`, `DevProductIdea`, and `DevProductLaunch` | `PUBLIC` and `DESIGN_PARTNERS` projections strip internal fields (`criterionInputs`, `influencedArrAmount`, `crmAccountId`, `linkedApmIssueIds`), exposing only `publicPortalTitle` / `publicSanitizedSummary`. |

---

## 5. Core End-to-End User Journeys

1. **Discovery-to-Delivery (`DevProductIdea` -> RICE Score -> `ApmEpic` Sync):**
   - Customer Success links 3 `SupTicket` escalations and 2 `CrmOpportunity` deals totaling \$185,000.00 ARR (`Decimal128`) onto `IDEA-304: SSO SAML Group Mapping` (`#/idea-detail`).
   - PM clicks **Promote to Roadmap Initiative**, scores `RMP-112` on `#/prioritization` (`Reach=500, Impact=3.0, Confidence=90%, Effort=5 -> priorityScore = 270.0000`), and clicks **Promote to Planning Epic**.
   - `promoteToApmEpic` creates canonical `ApmEpic` `EPIC-77` in Rapider `planning`/`apm` and stores `linkedApmEpicId`. As engineers close child `ApmIssue` stories in `planning`, `apm.epic.progress_updated.v1` updates `RMP-112.deliveryProgressPercent` (`0% -> 40% -> 100%`) live on `#/roadmap`.
2. **Executive Horizon Commitment via Shared Home `WorkItem`:**
   - PM drags `RMP-112` into the `NOW` column on `<rapider-kanban>` (`#/roadmap`) and clicks **Request Commitment**.
   - `requestHorizonCommitment` transitions `commitmentStatus -> PENDING_APPROVAL` and dispatches a Rapider Home `WorkItem` to the VP of Product displaying RICE score, \$185,000.00 influenced ARR, `DevStrategicTheme` fit, and dependency checks. Approval marks `RMP-112` `COMMITTED`.
3. **Coordinated Tier-1 Product Launch & Closed-Loop Changelog:**
   - PM bundles `RMP-112` into `DevProductLaunch` `2026 Spring Enterprise Release` (`#/launches`), verifies `#106` QA Gate `PASSED`, `#105` flag `saml-group-sync`, `MktCampaign`, and `SupKnowledgeArticle` readiness, asks Rapider AI on `projectChannelMessage` to draft customer release notes (`PRM-027`), reviews/edits the Markdown, and clicks **Publish Launch**—updating `#/changelog` and notifying `IDEA-304` voters and `SupTicket` watchers.
4. **Sanitized External Portal Projection:**
   - Design Partner logs into portal `enterprise-cab` (`DESIGN_PARTNERS`), allocates 25 of their 100 CAB voting points to a `NEXT` card, and sees only `publicPortalTitle` and horizon—zero internal ARR figures or other customers' `CrmAccount` names are transmitted.
5. **Search, Active Filter Tags, Click-Through & Back Restoration:**
   - On `#/roadmap`, PM filters `Theme: Enterprise Security` + `Horizon: NOW` and types `"SAML"`. `#activeFilterTagsBar` displays dismissible chips and `Clear all`.
   - Clicking `RMP-112` opens `#/roadmap-item-detail?id=...` cleanly; clicking `#btnGoBack` returns to `#/roadmap` with filter chips and `<rapider-kanban>` state intact.

---

## 6. Consolidated Feature Priorities & Work Packages

### `P0` Foundation (MVP Release-Ready Core)
- **WP-P0-1: Ideas, CRM/Support Evidence & Sanitized Portals (`PRM-001`–`PRM-003`, `PRM-014`):** `DevProductIdea`, `DevFeedbackEvidence`, `DevRoadmapPortal` schemas, deduplicated `Decimal128` ARR rollup from `CrmOpportunity`/`SupTicket`, `#activeFilterTagsBar`, `#/ideas`, `#/idea-detail`, `#/portals`.
- **WP-P0-2: Strategic Themes & `Decimal128` RICE/Weighted Prioritization (`PRM-005`–`PRM-007`):** `DevStrategicTheme` & `DevScoringModel` engines, Value-vs-Effort 2x2 matrix, `#/dashboard`, `#/themes`, `#/prioritization`, `#/scoring-models`.
- **WP-P0-3: Horizon `<rapider-kanban>`, `ApmEpic` Sync & Home `WorkItem` Commitments (`PRM-010`–`PRM-013`):** `DevRoadmapItem`, `roadmap-item-drawer`, `#/roadmap`, `#/roadmap-item-detail`, acyclic dependency validator, 1-click `ApmEpic`/`ApmIssue` promotion + progress listener, and Home `WorkItem` commitment workflow.
- **WP-P0-4: Product Launches & Customer Changelogs (`PRM-015`, `PRM-016`):** `DevProductLaunch` GTM readiness tracker (`#/launches`) and Markdown release changelog (`#/changelog` + Notebook export).

### `P1` Enterprise Portfolio & Cross-Suite GTM
- **WP-P1-1: Priority Poker, Investment Mix & Scenario Snapshots (`PRM-008`, `PRM-009`, `PRM-019`):** Multi-rater calibration, `ApmResourceProfile`/`ApmProjectFinancialPlan` envelope comparison, and quarterly baseline snapshots.
- **WP-P1-2: Closed-Loop Notifications, `#105`/`#097` Links, PRDs & Import/Export (`PRM-004`, `PRM-017`, `PRM-018`, `PRM-020`–`PRM-022`):** Voter/CRM/Support status notifications, `#105` flag rollout badges, `#097` adoption metric links, audience-specific date-free views, Notebook PRD linking, and CSV/Markdown import/export.

### `P2` Adjacent Discovery & Grounded AI Copilot
- **WP-P2-1: Competitive Signal Tags & CAB Point Budgets (`PRM-023`, `PRM-024`):** Competitive win/loss tagging on `DevFeedbackEvidence` and bounded voting point budgets on `DevRoadmapPortal`.
- **WP-P2-2: Grounded AI Product Copilot (`PRM-025`–`PRM-028`):** Feedback theme clustering & merge suggestions, Notebook PRD drafter, release-note generator, and dependency risk advisor over `projectChannelMessage`.

---

## 7. Roles, Permissions & Field-Level Governance

| Role | Permitted Actions | Restricted / Field-Level Boundaries |
| :--- | :--- | :--- |
| **Product Manager** | Create/edit `DevProductIdea`, `DevFeedbackEvidence`, `DevRoadmapItem`, `DevProductLaunch`; score items; promote to `ApmEpic`; request `COMMITTED` / `PUBLIC` approvals; invoke AI Copilot on `projectChannelMessage`. | Cannot self-approve `COMMITTED` horizon locks or `PUBLIC` portal publications when 4-eyes portfolio governance is enabled. |
| **VP Product / Portfolio Lead** | All PM actions + configure `DevStrategicTheme` targets and `DevScoringModel` weights, approve/reject Home `WorkItem` horizon commitments & public portal launches, and lock quarterly baseline snapshots. | Audited on all commitment approvals and scoring model weight changes. |
| **Engineering / QA Lead** | View full internal roadmap, dependencies, PRDs, and scores; link existing `ApmEpic` / `ApmIssue` / `#105` / `#106` records; participate in Priority Poker effort scoring. | Cannot publish external customer changelogs or alter `CrmOpportunity` ARR attributions. |
| **Sales / Customer Success Contributor** | Submit `DevProductIdea` and attach `DevFeedbackEvidence` (`CrmAccount`, `CrmOpportunity`, `SupTicket`); view internal stakeholder roadmap and launch notes. | Cannot mutate RICE weights, move `COMMITTED` items across horizons, or delete roadmap initiatives. |
| **External Portal Visitor / CAB Member** | View `PORTAL_VISIBLE` items (`publicPortalTitle`, `publicSanitizedSummary`, horizon) and cast votes within `votingPointBudgetPerUser`. | **Strict Field Isolation:** Zero access to `influencedArrAmount`, `criterionInputs`, `crmAccountId`, `supTicketId`, `linkedApmEpicId`, or internal threads. |

---

## 8. Technical APIs, Guarded Commands, Events & `requiredWorkflows`

### Guarded Domain Commands
All state-changing commands enforce RBAC, `idempotencyKey`, `correlationId`, and `expectedVersion`:
- `attachFeedbackEvidence(ideaId, sourceType, foreignRefId, verbatimQuote, urgency, idempotencyKey)` -> Validates `CrmAccount`/`CrmOpportunity`/`SupTicket` access and recalculates deduplicated `Decimal128` `influencedArrAmount`.
- `mergeProductIdeas(targetIdeaId, sourceIdeaIds[], expectedVersion, idempotencyKey)` -> Re-parents evidence and unique votes without double-counting shared `CrmOpportunity` IDs.
- `scoreRoadmapItem(roadmapItemId, criterionInputs, expectedVersion, idempotencyKey)` -> Computes exact `Decimal128` `priorityScore` using assigned `DevScoringModel` (rejecting zero/negative denominator).
- `promoteToApmEpic(roadmapItemId, apmProjectId, epicPayload, expectedVersion, idempotencyKey)` -> Creates or links canonical `ApmEpic` in `planning`/`apm` and initializes bi-directional sync.
- `requestHorizonCommitment(roadmapItemId, targetHorizon, justification, expectedVersion, idempotencyKey)` / `decideHorizonCommitment(...)` -> Manages governed Home `WorkItem` approval.
- `publishProductLaunch(launchId, portalIds[], expectedVersion, idempotencyKey)` -> Validates readiness checks, publishes sanitized changelog, marks linked items `SHIPPED`, and emits closed-loop notifications.

### Kafka Domain Events (Published & Consumed)
- **Published:** `dev.roadmap.idea_promoted.v1`, `dev.roadmap.item_committed.v1`, `dev.roadmap.epic_promotion_requested.v1`, `dev.roadmap.launch_published.v1`, `dev.roadmap.idea_shipped.v1`.
- **Consumed:** `apm.epic.progress_updated.v1` & `apm.issue.status_changed.v1` (updates `DevRoadmapItem.deliveryProgressPercent`), `crm.opportunity.amount_updated.v1` (refreshes `influencedArrAmount`), `dev.flag.toggled.v1` (`#105` rollout badge), `dev.test.quality_gate_passed.v1` (`#106` launch readiness).

### `requiredWorkflows` in `app.manifest.json`
1. `dev-roadmap-apm-delivery-sync-wf` (Synchronizes `ApmEpic` / `ApmIssue` completion percentages and status transitions onto `DevRoadmapItem` in `Decimal128`).
2. `dev-roadmap-arr-rollup-wf` (Recomputes deduplicated `influencedArrAmount` across `DevProductIdea` and `DevRoadmapItem` when `DevFeedbackEvidence` or `CrmOpportunity` values change).
3. `dev-roadmap-launch-and-notification-wf` (Coordinates Home `WorkItem` approvals for commitments/launches and sends closed-loop `SHIPPED` updates to `SupTicket` / `CRM` subscribers).
4. `dev-roadmap-ai-discovery-copilot-wf` (Grounded AI feedback clustering, Notebook PRD drafter, and release-note generator on `projectChannelMessage`—never merging ideas, committing horizons, or publishing externally without human confirmation).

---

## 9. Security, Privacy, Compliance & Non-Functional Requirements

- **External Portal Data Sanitization & Multi-Customer Confidentiality (STRICT):** Public and Design-Partner `DevRoadmapPortal` APIs enforce a server-side projection allowlist (`publicPortalTitle`, `publicSanitizedSummary`, `horizon`, `voteCount`), guaranteeing `0` leakage of private customer names (`CrmAccount`), deal sizes (e.g., \$250,000.00 ARR), internal engineering blockers, or verbatim support transcripts.
- **Markdown & XSS Sanitization:** Release notes (`releaseNotesMarkdown`) and feedback quotes are sanitized structurally before rich rendering and escaped (`escapeHtml()`) in filter chips and tables.
- **GDPR / CCPA Voter & Contact Privacy:** External portal votes and `CrmContact` attributions honor workspace retention and right-to-erasure requests while preserving anonymized aggregate `voteCount`.
- **Accessibility & Responsive Parity:** WCAG 2.2 AA compliant across `390px`, `768px`, and `1440px` (`light`/`dark` themes), including keyboard-accessible `<rapider-kanban>` horizon movement and scorecard inputs; `findSWR` initial renders `< 150ms` p95.

---

## 10. Deterministic Acceptance Criteria

1. **Zero `projectId` & Zero `APM` Shadow Models:** Inspecting schemas confirms zero `projectId` fields, backend-generated UUIDs (`00000000-...` in fixtures), and zero duplicate `Sprint`/`Epic`/`Bug` tables—delivery execution links strictly to canonical `ApmEpic` and `ApmIssue`.
2. **Exact `Decimal128` RICE Scoring & ARR Deduplication:** Scoring `(Reach=1000 * Impact=2.5 * Confidence=0.80) / Effort=4.0` yields exact `Decimal128` `priorityScore = 500.0000`; merging two ideas citing the same `CrmOpportunity` (\$50,000.00) yields `influencedArrAmount = 50000.00` (never \$100,000.00).
3. **Bi-Directional `ApmEpic` Progress Sync:** Promoting `RMP-112` sets `linkedApmEpicId`; consuming `apm.epic.progress_updated.v1` (`completedIssues: 3, totalIssues: 4`) updates `deliveryProgressPercent` to `75.0000%` on `#/roadmap` and `#/roadmap-item-detail`.
4. **Dependency Conflict Warning & Acyclic Graph:** Linking `Item A dependsOn Item B` where `Item A` is in `NOW` and `Item B` is in `LATER` surfaces a deterministic dependency-conflict warning; circular dependencies (`A -> B -> A`) are rejected on save.
5. **External Portal Field Isolation:** Querying a `PUBLIC` `DevRoadmapPortal` endpoint returns sanitized titles/horizons and `0` occurrences of `influencedArrAmount`, `crmAccountId`, `supTicketId`, or `criterionInputs`.
6. **Home `WorkItem` Commitment & Launch Governance:** Requesting `COMMITTED` status on a gated `NOW` initiative creates a shared Rapider Home `WorkItem`; self-approval is rejected when 4-eyes governance is active.
7. **Sidebar Minimum 3 Items Rule:** All 3 visible sidebar sections (`Strategy & Roadmaps`, `Discovery & Prioritization`, `Launches & Portals`) each contain 3 visible items (`displayOnMenu: true`), while `roadmap-item-detail`, `idea-detail`, and `roadmap-item-drawer` set `displayOnMenu: false`.
8. **SWR Clean Query & Optimistic Updates:** All pages load via `findSWR`/`countSWR` with zero `isDeleted` filter clauses; moving a horizon card on `<rapider-kanban>`, editing a RICE input, or deleting a draft idea updates in-memory state optimistically, clears SWR cache, and rolls back on error.
9. **Table Actions, Contrast & Dialog Ban:** Zero tables show a "View" button in `Actions`; primary identifiers navigate to detail routes; `Edit` renders icon + text; `Delete` renders icon-only with `aria-label="Delete"`; primary/danger buttons enforce `#ffffff` text; zero `alert`/`confirm`/`prompt` calls exist.
10. **Active Filter Tags & Clear All:** Filtering `#/roadmap` or `#/ideas` renders `#activeFilterTagsBar` with HTML-escaped dismissible chips and `Clear all`, synchronously updating Table and `<rapider-kanban>` views.
11. **Drawer Auto-Close & `finally` Reset:** Saving or cancelling `roadmap-item-drawer` closes the drawer, broadcasts `RECORD_CREATED`/`RECORD_UPDATED`, and restores the Save button state inside `finally`.
12. **Click-Through Navigation & Back State Restoration:** Clicking `RMP-112` on `#/roadmap` navigates cleanly to `#/roadmap-item-detail?id=...` without `<base href>` 404 diversion, and `#btnGoBack` restores `#/roadmap` with active filter tags intact.
13. **Grounded AI Safety:** AI clustering, Notebook PRD drafts, and changelog drafts post onto `projectChannelMessage` citing stored `DevFeedbackEvidence` IDs and never auto-merge ideas or auto-publish portals without human confirmation.
14. **Theme & Responsive Validation:** Automated light/dark `validate_theme` and `390px`/`768px`/`1440px` layout checks pass with zero contrast or overflow defects.
