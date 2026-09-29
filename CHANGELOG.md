# Changelog

All notable changes to the *Census of AI / Frontier-Model Partnerships across the 2026 Formula 1 Grid* dataset are documented here. Format loosely follows [Keep a Changelog]; versioning is date-anchored.

## [1.5] — 2026-08-01

The inclusion boundary left open by `[1.4]` was decided, written into the codebook as **README §3.0**, and applied **retroactively** — to the pending candidate list and to the existing rows alike. Two per-property adjudications and four currency resolutions were carried out in the same pass.

### Inclusion rule fixed (README §3.0)
- A partnership enters the census if it **transfers computing or data technology to the team** — hardware, software, or an IT/data service that acquires, stores, transmits, processes, analyses, secures or automates decisions over information. The unit is the technology partnership a team holds, sorted by whether the cap can price it, **not** "arrangements whose press release says AI."
- A narrower AI-only rule was considered and **rejected**: it would turn on the vocabulary of a release rather than on what is supplied, and would have forced the removal of nine enterprise-security rows whose classification is not in doubt.
- Four exclusion classes (brand-only; manufacturing/materials/mechanical/AV; apparel-beverage-finance-logistics-media; consultancy and talent) and one **mixed-supply convention** are stated in §3.0, with every boundary call named so a reader can reverse it.
- **Honesty note recorded in §3:** the tier rule was fixed in advance of coding; the inclusion rule was not. It is written down as of this version, not presented as a prior design.

### Added — eighteen on-ledger arrangements (`R088`–`R105`)
- **McLaren (7)** — `R088` Smartsheet, `R089` Medallia, `R090` Freshworks, `R091` Dropbox, `R092` Rubrik, `R093` Schneider Electric, `R094` Arrow Electronics.
- **Mercedes (2)** — `R095` Akkodis, `R096` Solera.
- **Ferrari (3)** — `R098` DXC Technology, `R099` Genesys, `R100` Riedel.
- **Racing Bulls (3)** — `R101` Siemens, `R102` RebelDot, `R103` **Octave**.
- **Haas (2)** — `R104` CommScope, `R105` Emburse.
- **Red Bull (1)** — `R097` **Hexagon** (metrology and digitalisation; `performance-critical`, `cap_relevant = yes`).

### Excluded under the rule, recorded by name
Red Bull–DMG Mori, Red Bull–Philips Professional Displays, Racing Bulls–Roboze, Audi–Camozzi (all manufacturing/mechanical/AV); Audi–Aleph (advertising services); Mercedes–BetterUp, Alpine–AtkinsRéalis (consultancy and talent). `R093` McLaren–Schneider Electric was **included** on the mixed-supply convention and is flagged `BORDERLINE` in its row.

### Classification rationale
- **All eighteen are `T1`, and no new Tier-2 arrangement was found anywhere on the grid — the third consecutive pass to return that result.**
- **The abstention finding was tested and strengthened.** This pass added technology partnerships at all three abstainers (Ferrari +3, Mercedes +2, Red Bull +1, one of them performance-critical) and found no frontier-model deal at any of them. Looking harder at the largest-resourced teams produced more on-ledger technology and zero off-ledger technology.

### Adjudicated
- `R077` **McLaren–Intel** — `T1` ratified, properties `1,0,0` → **1/3**. A = 1 (the release states the parties will "co-engineer solutions"); B = 0 (published list prices, deep market); C = 0 (delivered silicon does not drift within a reporting period).
- `R083` **McLaren–Groq** — `T1` ratified, properties `1,0,0` → **1/3**. A = 1 on branding alone, scored for consistency with `R076`; B = 0 (GroqCloud publishes per-token pricing); C = 0 (what is transferred is inference capacity at a published rate).
- **Both fail the all-three rule under the most generous available reading** (Property C = 1 gives 2/3), so the `T1` call rests on **Property B — the one property settled by a published price list rather than by judgment.**
- **Instrument note (README §3.2):** Property A now scores 1 in all ten adjudicated rows, in `R083` on sponsorship branding alone. Property A is doing little discriminating work; the sort is carried by Property B and the frontier gate. No classification depends on it. Stated here rather than left for a reviewer to find.

### Currency — all four `[1.4]` flags closed
- `R030` McLaren–Salesforce — **confirmed current**; the 07-30 flag was a page-capture artefact. `MED` → `MED-HIGH`.
- `R048` Alpine–data.ai — **lapsed**; absent from the partner page and the counterparty brand was retired after the March 2024 Sensor Tower acquisition. Flagged `LAPSED`, retained on the `R042` convention.
- `R043` Alpine–KX — **unresolved**, absent from the partner page, no renewal since 2021. Downgraded to `LOW`, retained (absence ≠ termination).
- `R058` Haas–CSG — **unresolved**, absent from the partner page, announcement scoped to a single race. Downgraded to `LOW`, retained.
- **No row was deleted.** IDs are never reused or renumbered; lapses are flagged in `since_detail`.

### Completeness
- `R103` Racing Bulls–Octave **was not on the 24-name pending list compiled by the 07-30 diff** — it surfaced only when that list was itself re-checked against the live team page. A miss inside a completeness audit, recorded rather than absorbed; it is the honest measure of what this method guarantees. See README §8.7.
- The floor caveat stands and is now better supported: three passes, three methods, **zero missed Tier-2 arrangements and twenty-nine missed Tier-1 ones.** The error runs systematically in the argument's favour, because frontier-model deals are the loudest and easiest records on the grid to find.

### Counts
- Total records 87 → **105** (team-cap 76 → **94**; driver-personal 5 and F1-central 6 unchanged). Record range now `R001`–`R105`. **Tier-2 unchanged at 6.** 0 `TBA`. Adjudicated per-property vectors 8 → **10**.
- Per-team team-cap: McLaren 18, Mercedes 12, Aston Martin 10, Alpine 9, Red Bull 9, Ferrari 7, Haas 7, Racing Bulls 7, Williams 7, Audi 5, Cadillac 3.
- CSV re-validated: 105 unique IDs, 20 fields per row, pure ASCII.

## [1.4] — 2026-07-30

Official partner-page diff, run immediately after `[1.3]` because that sweep was still query-shaped and therefore blind to partners whose announcements do not use the word "AI". All eleven teams' official partner pages were fetched and compared line by line against the file.

### Added
- `R083` **McLaren–Groq** (`T1`) — Official Partner, announced 26 Sep 2025, branding on the rear wing from the Singapore GP, terms undisclosed. Custom Language Processing Unit inference compute supporting "analysis, development and real-time insight" in race-weekend decision-making. `performance-critical`, `cap_relevant = yes`.
- `R084` **Mercedes–Vercel** (`T1`) — multi-year strategic partnership announced 1 Jul 2026, branding from the British GP, expanding from 2027. Agentic/web infrastructure platform plus migration of the team's digital estate. `operational`, `partial`.
- `R085` **Racing Bulls–Dynatrace** (`T1`) — Official Observability and Performance Analytics Technology Partner, announced 14 Jan 2025. AI-powered observability across vehicle dynamics, driver performance and race optimisation. `performance-critical`, `cap_relevant = yes`.
- `R086` **Alpine–Arctic Wolf** (`T1`) — Official Cybersecurity Partner, announced 11 Feb 2025. Aurora security-operations platform ("Alpha AI") across the team's global infrastructure. `peripheral`, `partial`. Distinct from the lapsed Red Bull–Arctic Wolf arrangement the source census excluded.
- `R087` **Williams–Zoox** (`T1`) — Official Regional Partner (US races), announced 13 Nov 2024. An AI company sponsoring a team with **no technology transferred to the team**; recorded for landscape completeness and coded `activity = Marketing`, `cap_relevant = no`, so it is excluded from the performance analysis.

### Classification rationale
- All five are on-ledger. `R083` and `R085` are priced, severable capacity/analytics products; `R084` is priced web infrastructure; `R086` is a priced managed-security product; `R087` transfers nothing to the team at all.
- **Again no new Tier-2 anywhere on the grid.** `R084` Vercel sits at Mercedes but is digital-estate infrastructure and branding, not frontier-model performance work, so the abstention finding is untouched.
- `R083` **Groq joins `R077` Intel as the census's sharpest on-ledger edge case** — a dedicated AI supplier, sponsored, race-weekend-relevant, terms undisclosed. Both remain `T1` because the rule keys on what is transferred: priced, quotable capacity rather than an unpriceable partnership. Flagged in README §8.2.

### Completeness
- The diff established that this census is a **floor on publicly disclosed arrangements, not an exhaustive enumeration** — teams publish 25–56 partners each, and ~24 further named technology suppliers remain un-entered pending an explicit inclusion rule (all would be `T1`; none is a frontier-model partnership). Full list, reasoning and four currency flags (`R030`, `R043`, `R048`, `R058`) in README §8.7. The header now states the floor caveat, and the paper skeleton carries a matching `[HEDGE]` beat.

### Counts
- Total records 82 → **87** (team-cap 71 → 76; driver-personal 5 and F1-central 6 unchanged). Record range now `R001`–`R087`. Tier-2 unchanged at **6**. 0 `TBA`; 8 adjudicated per-property vectors, unchanged.

## [1.3] — 2026-07-30

Eleven-team refresh sweep. Triggered by the author spotting an AI-security sponsor (Okta) on a McLaren asset that the census did not contain; the whole grid was then re-checked rather than the single case.

### Added
- `R077` **McLaren–Intel** (`T1`) — Official Compute Partner, announced 14 May 2026, multi-year, terms undisclosed. Xeon / Core Ultra silicon for CFD, aerodynamic analysis, vehicle-dynamics simulation, race-strategy analytics, digital twins and trackside edge compute. `performance-critical`, `cap_relevant = yes`.
- `R078` **McLaren–Okta** (`T1`) — Official Partner, announced 28 Jan 2025, multi-year, terms undisclosed. Identity and access management; branding on both cars and driver overalls. **The announcement names no AI component** — see the inclusion caveat below.
- `R079` **Haas–Exein** (`T1`) — "Official Physical AI Security Partner", announced July 2026, effective from the 2026 Belgian Grand Prix, multi-year. Runtime device security. Newest record in the census.
- `R080` **Haas–Ruckus Networks** (`T1`) — Official Networking Partner, announced 21 Jan 2026 (expansion of an existing relationship). Trackside, factory and hospitality connectivity.
- `R081` **Audi–Perk** (`T1`) — Official Work Automation Partner, announced 1 Dec 2025, multi-year. AI-driven back-office automation (travel, expenses, invoices, approvals).
- `R082` **Racing Bulls–Confluent** (`T1`, `MED-HIGH`) — real-time data-streaming platform connecting car, pit wall and factory; announced Oct 2025, multi-year, still listed as a current partner in 2026.

### Classification rationale
- **All six are on-ledger (`T1`)**, each coded against an existing precedent rather than a new rule: `R077` on `R027` Dell (compute); `R079` on `R038` Zscaler / `R053` Keeper (security); `R080` on `R059` Extreme Networks (networking); `R081` on `R032` Workday / `R047` Businessolver (back-office); `R082` on `R043` KX / `R052` VAST Data (data infrastructure); `R078` on the enterprise-security class generally.
- **No new Tier-2 arrangement was found anywhere on the grid**, and none at Mercedes, Red Bull or Ferrari — their 2026 AI deals remain Microsoft/Azure, Oracle/OCI and AWS, already coded as priced-resale or applied-agent channels. The Tier-2 population (`R001`–`R006`) is unchanged.
- **Effect on the analysis: the distribution finding is unchanged; the on-ledger denominator grows.** Six more priceable, severable arrangements make the "large majority are on-ledger" statement stronger, not weaker, and the abstention of the largest-resourced teams is untouched.
- **Two open caveats** (README §8.2, not adjudicated): `R077` is the census's strongest on-ledger edge case (sponsored, performance-critical, undisclosed terms, at a team that also holds a Tier-2 deal); `R078` names no AI component and stands or falls with the seven enterprise-security rows already in the census, not on its own.

### Not added (checked and excluded)
- Extensions and expansions of arrangements **already** in the census — Cisco–McLaren (7 Jul 2026), Oracle–Red Bull (26 Feb 2026), Salesforce–Racing Bulls Agentforce 360 (22 Jun 2026), Salesforce–Formula 1 (Mar 2026), Cognizant–Aston Martin "Global AI Services Partner" (30 Apr 2026), Cohere–Aston Martin (4 Mar 2026) — these update existing rows' timing, not the record count.
- Non-technology sponsorships surfaced by the sweep (Alpine–Skip, Aston Martin–Celsius, Ferrari–Whoop, McLaren–Puma and similar).
- The 2026 power-unit in-car energy-deployment software, which remains out of scope by the 2026-07-23 scope decision (procured under the separate Power Unit Financial Regulations, not partnered; and not established on the public record to be machine learning).

### Counts
- Total records 76 → **82** (team-cap 65 → 71; driver-personal 5 and F1-central 6 unchanged). Record range now `R001`–`R082`. Tier-2 unchanged at **6**. All 82 rows carry a verified primary-source URL (0 `TBA`); 8 rows carry adjudicated per-property vectors, unchanged.

## [1.2] — 2026-07-11

### Changed
- `R076` **Mercedes–G42** — borderline flag **resolved: `T1` ratified** (scored against the published rule by an AI assistant at the author's request; reviewed and ratified by the author — see `README.md` §0, Research assistance and AI use). Three grounds: (1) properties scored from the primary announcement per the `R054` precedent — bidirectional=1, no-clearing-price=0 (bespoke analytics platform, severable and benchmarkable), drift=1 → **2/3, fails the all-three rule independently of the frontier gate**; (2) the 2023–2026 record re-checked (web pass 2026-07-11): the arrangement remains the Presight.ai analytics platform with no expansion into a general-purpose frontier-model deployment, and Mercedes's frontier access remains the metered Microsoft resale channel; (3) the coding rule keys on the **technology transferred**, not the counterparty's portfolio — G42 group's own LLM assets (Jais/Core42) are not part of what this arrangement conveys. CSV `notes` updated (BORDERLINE → ADJUDICATED), property fields filled (`1,0,1,2`), README §8.2 entry moved to "Resolved," §8.3 exception note added.

## [1.1] — 2026-07-10

### Changed
- `R002` **McLaren–Google/Gemini** — `notes` field updated after re-verifying both official pages (mclaren.com 2025 extension + blog.google Gemini-3 post) on 2026-07-10. Only **creative** uses are concretely documented (Piastri helmet via Gemini image tools; Sphere real-time livery restyle); the **engineering leg is company-asserted**, no named tool or race-weekend workflow, and neither a regulations-search tool nor a live telemetry interface appears on either page. **Kept in Tier-2 with an explicit caveat** (author decision) as the tier's weakest member; the distribution finding turns on the abstention of Mercedes/Red Bull/Ferrari and does not depend on R002. Full detail in `census/AUDIT_McLaren_Google_2026-07-10.md` *(project working file, not in this repository)*. Draft §3.3/§3.4 softened accordingly.

### Added
- `R076` **Mercedes–G42** (`T1`, on-ledger). A multi-year Mercedes AI partner since February 2023, missed by the initial census. G42 supplies specialised big-data / predictive analytics (its Presight.ai omni-analytics platform) for broad operational optimisation — "marginal gains, on and off the track" — with no financial terms disclosed. Sourced to the g42.ai partnership announcement.

### Classification rationale
- Coded `T1` by the same fixed rule as `R054` Neural Concept: G42 is not a top-tier *general-purpose* model, so it fails the frontier gate, and a bespoke analytics deliverable is severable and in principle priceable. Logged as a **borderline** call in README §8.2 (undisclosed terms + a direct, non-resale AI partnership at a big-three team is the uncomfortable edge).
- Effect on the analysis: **strengthens, does not alter, the distribution finding.** Even Mercedes's one direct AI partnership is specialised analytics, not an off-ledger frontier thinking-partner, so Mercedes remains a frontier-LLM abstainer on the record — closing the most obvious "you missed a deal" objection.

### Counts
- Total records 75 → **76** (team-cap 64 → 65). Record range now `R001`–`R076`. All 76 rows carry a verified primary-source URL (0 `TBA`).

## [1.0] — 2026-07-02

Initial public release, assembled from the corrected hand-built census.

### Added
- `census_ai_f1_2026.csv` — 75 arrangements (64 team-cap, 5 driver-personal, 6 F1-central), one row each, machine-readable UTF-8, with the two-tier (T1/T2) classification, three-property coding for the Tier-2 and borderline records, depth/activity, since-year, confidence, related-party flag, cap-relevance, category, primary-source URL (or `TBA`), and notes.
- `README.md` — codebook: scope, coding rulebook (three properties with Property B renamed to "no clearing price"; the "all three" T1/T2 rule; the "frontier = current top-tier general-purpose model" definition; the priced-resale-channel rule), correction history, column definitions, provenance, Companies House team-resource panel, GAPS, and citation stub.
- `CHANGELOG.md` — this file.

### Corrections baked into v1.0 (vs the pre-census draft / old grid)
- Mercedes–Meta AI reclassified frontier → on-ledger (T1, fan-facing marketing; not a Llama compute deal).
- Red Bull–Oracle reclassified frontier → on-ledger (T1, commodity cloud + applied agent).
- Racing Bulls–Neural Concept recoded on-ledger (T1; scores 2 of 3 properties; specialised engineering-AI, not a general-purpose LLM thinking-partner) and excluded from the Tier-2 count.
- Cadillac–TWG AI kept Tier-2 but flagged `related_party = Y` and excluded from the sponsored-channel count (captive / RPT in-kind transfer).
- Alpine–Indra hedged to a "probable" Tier-2 at `MED-HIGH` confidence.
- Williams–Airia re-added (earlier "dropped as a Gemini error" note was wrong).
- Property B renamed from "near-zero marginal cost" to "no clearing price."

### Known gaps (see README §8)
- 67 of 75 records have `source_primary_url = TBA`, including four load-bearing Tier-2 rows (Aston–Cohere, Aston–Cognition, Cadillac–TWG, Alpine–Indra). Resolving these is the priority before public release, since SSAC requires an open-source data repository.
- Per-property flags are populated for Tier-2 and the one borderline record only; Tier-1 records are coded at the tier level.
- License (CC-BY-4.0 suggested), author, and Zenodo DOI are placeholders to be finalised at release.
