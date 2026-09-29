# Census of AI / Frontier-Model Partnerships across the 2026 Formula 1 Grid

*A hand-built, primary-source census of publicly disclosed artificial-intelligence, cloud, data, semiconductor, cybersecurity and enterprise-software partnerships held by the eleven 2026 Formula 1 teams (plus the driver-personal and F1-central landscape), each coded for whether the FIA cost cap's valuation machinery can price it.*

- **File:** `census_ai_f1_2026.csv` (UTF-8, pure ASCII, one row per arrangement)
- **Records:** 105 arrangements (94 team-cap; 5 driver-personal; 6 F1-central); 0 unsourced
- **Data version:** 1.5 (2026-08-01) — see `CHANGELOG.md`. **No row has changed since 2026-08-01.**
- **Documentation last revised:** 2026-09-29 (headings, the citation stub, the research-assistance statement in §0 and the provenance notes). **Documentation edits do not bump the data version**, because the CSV is untouched; every change to the data itself has a `CHANGELOG.md` entry.
- **Completeness:** this is a **floor on publicly disclosed arrangements, not an exhaustive enumeration.** Teams publish 25–56 partners each. The inclusion boundary is now **fixed and written down (§3.0)** and has been applied retroactively; what remains open is the ordinary residue of any hand-built census — arrangements never announced, or announced in language no search reaches. See §8.7.
- **Provenance:** hand-built from primary sources 2026-06-29; corrections 2026-07-02; R076 added 2026-07-10, adjudicated 2026-07-11; query-based refresh sweep 2026-07-30 adding `R077`–`R082`; official partner-page diff across all eleven teams 2026-07-30 adding `R083`–`R087`; inclusion rule fixed and applied 2026-08-01 adding `R088`–`R105`. The raw research transcripts cited in §8.5 are retained privately for provenance and are **not part of the public release**.
- **License:** **CC BY 4.0** — `LICENSE` carries the full official legal code. Copyright © 2026 Hanyu Wang.
  *Scope of the licence:* it covers **the compilation, the coding and the documentation**. The primary-source
  URLs recorded in the dataset point to third-party announcements and filings; **those pages remain the property
  of their respective owners and are not covered by this licence.**
- **DOI:** not yet minted. The Zenodo release is deliberately held until the companion paper is posted, so that the citable record of the dataset and of the paper appear together. Until then, cite the repository URL and the version number. Backfilled here and in `CITATION.cff` once assigned.

**How to cite:**
> Wang, H. (2026). *Census of AI / Frontier-Model Partnerships across the 2026 Formula 1 Grid* (v1.5) [Data set]. GitHub. https://github.com/hildahanyuwang/f1-ai-partnership-census *(Zenodo DOI to follow.)*

**Research assistance and AI use.** Stated here in one place rather than left to be discovered in footnotes.
**The coding scheme is the author's**: the inclusion rule (§3.0), the definition of the frontier tier (§3.1) and
the three properties (§3.2) were specified before any row was adjudicated, and are set out in full so that a
reader can apply them independently and disagree. **AI assistance was used for two things, both under that
scheme:** (i) *collection* — parallel search-and-retrieval agents gathered candidate arrangements and primary
source URLs, each of which was then verified against the cited page (§8.4–§8.6), and (ii) *application* — three
borderline rows (`R076`, `R077`, `R083`) were scored against the published rule by an AI assistant at the
author's request, with the reasoning recorded in the row note and in §8.2, **and the author reviewed and ratified
each call.** No tier in this dataset rests on an unreviewed machine judgement. Every classification, including
those three, is contestable from the primary source cited in the row.

**Companion paper.** The two-tier classification in this dataset — the `prop_bidirectional`,
`prop_no_clearing_price`, `prop_capability_drift` and `tier` columns — operationalises a three-property test
developed in:

> Wang, H. (2026). *Off the Ledger: A Three-Property Test for Inputs That Money-Metric Regulation Cannot Price.* Working paper, SSRN forthcoming.

This dataset is released ahead of that paper so that the census can be cited and contested independently. The
test itself, and the doctrinal analysis of the FIA Financial Regulations that motivates it, belong to the paper.

---

## 1. What this dataset is (and is not)

This is the empirical backbone of a study of the FIA Formula 1 cost cap and frontier AI. The cost cap secures competitive fairness by equalising team **spend**. The census asks a narrower, structural question of each AI-related partnership: **can the cap's valuation machinery ("Fair Value") actually price it?** Each arrangement is sorted into two tiers on that single axis, and — for the team-cap arrangements — related to a team-resource proxy so that the *distribution* of frontier-AI access can be examined.

It measures the **distribution of access**, not its effect on competitive outcomes. Whether any arrangement has altered a race result is not observable from public data and is **not** claimed here. No confidential or contractual material is used; the near-total absence of disclosed financial terms is itself treated as a finding (`source_primary_url` and terms are frequently undisclosed).

---

## 2. Scope

- **All eleven 2026-grid teams:** Williams, McLaren, Aston Martin, Alpine, Cadillac (new), Red Bull, Ferrari, Mercedes, Racing Bulls (VCARB), Haas (TGR Haas), Audi (took over Sauber/Kick Sauber).
- **Landscape rows, tagged and separable:** individual **driver-personal** deals (outside the team cost cap) and **F1-central / FOM** partnerships (the commercial-rights holder, not team cost-cap relevant). These carry `category = driver-personal` or `F1-central` and `cap_relevant = no`, and their tier/property columns are intentionally blank. **The cost-cap analysis uses only `category = team-cap` rows.**
- **Currency:** current arrangements as of the 2026 season, re-swept across all eleven teams on **2026-07-30** and extended under the fixed inclusion rule on **2026-08-01** (newest record: `R079` Haas–Exein, announced July 2026). Lapsed/legacy arrangements are generally excluded, with exceptions retained and **flagged in `since_detail`** rather than deleted, so that the record and its correction history stay visible: **Alpine–Microsoft/Azure** (`R042`, lapsed end-2025, moved to Mercedes — a clean natural experiment) and, from 2026-08-01, **Alpine–data.ai** (`R048`, lapsed; counterparty brand retired after the Sensor Tower acquisition). Two further rows carry an unresolved **currency-unconfirmed** flag — `R043` Alpine–KX and `R058` Haas–CSG, both absent from their teams' current official partner pages, both downgraded to `LOW`; absence from a partner page is not proof of termination, so neither was deleted. All four are `T1` and none bears on the Tier-2 population. Other lapsed deals named in the source census (e.g. Ferrari–Palantir, Red Bull–Arctic Wolf, Aston–SentinelOne, AlphaTauri-era SenseTime) are not included as rows.

---

## 3. Coding rulebook

*The **tier** rule (§3.1) was fixed in advance of coding. The **inclusion** rule (§3.0) was not: it was applied case by case through v1.4 and only written down on 2026-08-01, then applied retroactively to every existing row. That sequence is stated plainly here rather than presented as a prior design, and the consequences are recorded in Correction #11 and §8.7.*

### 3.0 Inclusion rule — what counts as a record

**A partnership enters the census if it transfers *computing or data technology* to the team**, where that means hardware, software, or an IT/data service whose function is to acquire, store, transmit, process, analyse, secure or automate decisions over information.

The unit is therefore **the technology partnership a team holds**, sorted by whether the cap can price it — *not* "arrangements whose announcement uses the word AI." A narrower AI-only rule was considered and rejected: it would turn on the marketing vocabulary of a press release rather than on what is supplied, and would have required dropping nine enterprise-security rows whose classification is not in doubt (see §8.2, `R078`).

**Excluded, even where the counterparty is a technology company:**

- **(i) Brand-only arrangements** that transfer no technology to the team. Where the counterparty is itself an AI or technology firm, the row is *recorded* for landscape completeness but coded `cap_relevant = no`, `activity = Marketing`, and excluded from the performance analysis — e.g. `R087` Williams–Zoox.
- **(ii) Physical manufacturing, materials, mechanical and plant equipment** — machine tools, additive manufacturing, pneumatics, industrial automation, AV/display hardware.
- **(iii) Apparel, beverage, finance, logistics, hospitality, travel, healthcare, staffing, media and advertising services**, and the rest of the ordinary sponsorship field.
- **(iv) Consultancy and talent arrangements** whose deliverable is people, training or advice rather than a technology — e.g. an engineering academy or a secondment programme.

**Mixed-supply convention.** Where a partner supplies both an excluded and an included category, the arrangement is **included if the information-processing component is named in the team's or the provider's own description of the deal**, and excluded otherwise. This is the only place the rule requires judgment, and every row decided by it is flagged `BORDERLINE` in its `notes` (as of v1.5: `R093` McLaren–Schneider Electric).

**Boundary calls recorded at the 2026-08-01 application** (named so that a reader who disagrees can reverse them): **excluded** — Red Bull–DMG Mori (machine tools, (ii)), Red Bull–Philips Professional Displays ((ii)), Racing Bulls–Roboze (additive manufacturing, (ii)), Audi–Camozzi (industrial automation, (ii)), Audi–Aleph (digital advertising enablement, (iii)), Mercedes–BetterUp (coaching, (iv)), Alpine–AtkinsRéalis (engineering academy and consultancy, (iv)). **Included on the mixed-supply convention** — McLaren–Schneider Electric. All eight would be `T1` if the rule were drawn more widely, so none of them can move a headline.

### 3.1 The two tiers

An arrangement is coded **off-ledger (Tier 2 / `T2`)** only if it satisfies **all three** of the following properties; anything lacking one or more is **on-ledger (Tier 1 / `T1`)**.

1. **Bidirectional value flow** (`prop_bidirectional`) — the recipient returns data, expert feedback and/or prestige to the provider, so value does not flow one way for cash.
2. **No clearing price** (`prop_no_clearing_price`) — there is no single market price; the price surface is discriminated across roughly 1–2 orders of magnitude. *(This property was previously named "near-zero marginal cost"; it was renamed to "no clearing price" in the 2026-07-02 correction, which is the operative definition here.)*
3. **Capability drift** (`prop_capability_drift`) — the capability changes materially within a single reporting period.

In practice the `T2` rule isolates **frontier general-purpose models supplied as an organisation-wide partnership and used in performance work.**

- **"Frontier" = the current top capability tier of general-purpose models** — the latest Claude-, Gemini- or GPT-class systems. It is a moving definition tied to the capability frontier of the day, not a fixed model list.
- **Priced-resale-channel rule:** a frontier model reached through a *priced resale channel* — Azure OpenAI / Microsoft Copilot, AWS Bedrock, Oracle OCI generative AI — is **on-ledger (`T1`)**. A clearing price exists (Property 2 fails) and there is no bidirectional lab partnership (Property 1 fails), so metered access to a top-tier model does not by itself make a team Tier 2.
- **In-house capability** (salaried staff, owned compute, booked R&D) is on-ledger by construction and is not a channel measured here.

### 3.2 Where the properties are coded per-record

The three property flags and `prop_count` are populated **only for the arrangements adjudicated explicitly under the current scheme**: the six `T2` records (all coded `1,1,1` → count 3) and four borderline-adjudicated `T1` records — Racing Bulls–Neural Concept (`1,0,1` → 2, recoded 2026-07-02); Mercedes–G42 (`1,0,1` → 2, adjudicated 2026-07-11); **McLaren–Intel `R077` (`1,0,0` → 1) and McLaren–Groq `R083` (`1,0,0` → 1), both adjudicated 2026-08-01**. Ten rows in total.

**Note on Property A, surfaced by the 2026-08-01 adjudication.** Property A (bidirectional value flow) now scores `1` in all ten adjudicated rows, and in `R083` it scores `1` on sponsorship branding alone — the Groq release names no data return, no expert feedback and no co-development. Since branding flows back in essentially every sponsorship, **Property A is doing little discriminating work; the sort is carried by Property B and the frontier gate.** This is a property of the instrument, not of any one row, and it is better stated in the paper than left for a reviewer to find. It does not change any classification: no row's tier turns on Property A.

For all other `T1` records the property flags are **left blank rather than fabricated** — the source census classifies these at the tier level (they fail the "all three" test) but does not publish an adjudicated per-property vector for each. The `tier` column carries the coding for those rows. This is a deliberate accuracy-over-completeness choice.

### 3.3 Confidence coding

`confidence` reflects source strength for the *existence and classification* of the arrangement, not the (mostly undisclosed) financial terms:
- `HIGH` — census assigns HIGH (the T2 set, except Alpine) or the arrangement is a well-attested flagship/borderline coded call.
- `MED-HIGH` — Alpine–Indra (hedged "probable" per the correction) and well-documented title partnerships with a captured primary URL.
- `MED` — a publicly announced current partnership from the census whose primary-source URL was not present in the provided materials (`source_primary_url = TBA`).
- `LOW` — the census flags weak/secondary sourcing (e.g. Red Bull–AT&T, Williams–Brillio), or the arrangement is exploratory/branding-only.

---

## 4. Correction history (vs the pre-census draft / old grid)

These corrections are **authoritative** and are reflected in the CSV. Where the older census prose and `analysis/grid_classification_table.md` *(project working file, not in this repository)* differed, the classification table (latest) governs.

1. **Mercedes–Meta AI: frontier → on-ledger (`T1`, marketing).** It is a fan-facing marketing assistant, not a Llama frontier-compute deal — no Mercedes source names "Llama." The earlier "Mercedes = Meta-AI + Microsoft within-team natural experiment" framing was wrong.
2. **Red Bull–Oracle: frontier → on-ledger (`T1`).** Commodity cloud (OCI) + an applied "AI Strategy Agent" — priceable and severable; a clearing price exists.
3. **Racing Bulls–Neural Concept: → on-ledger (`T1`).** Specialised engineering-AI / digital-twin aero (a CFD complement), not a general-purpose LLM thinking-partner; scores only 2 of 3 properties, so it fails the fixed "all three" rule. Excluded from the Tier-2 count.
4. **Cadillac–TWG AI: `T2` but a related-party captive transfer**, not arm's-length sponsorship (TWG co-owns the team). `related_party = Y`; **excluded from the sponsored-channel count**; it belongs to the RPT / in-kind (widely-reported "TD45") analysis.
5. **Alpine–Indra: hedged `T2`, `MED-HIGH`, "probable."** IndraMind is a bespoke platform from a defence/tech integrator, not a top-tier general-purpose model — treated as a likely instance, not confirmed.
6. **Williams–Airia: real, re-added** (`R051`). The earlier note that it was "dropped as a Gemini error" was wrong; it has a williamsf1.com primary source (URL not captured in the provided materials — see GAPS).
7. **Mercedes–G42: on-ledger (`T1`), added 2026-07-10** (`R076`). A multi-year Mercedes AI partner since Feb 2023 that the earlier census had missed. G42 supplies *specialised* big-data / predictive analytics (its Presight.ai omni-analytics platform) for broad operational optimisation — "marginal gains, on and off the track" — with no financial terms disclosed. Coded `T1` by the same fixed rule as `R054` Neural Concept: it is not a top-tier *general-purpose* model, so it fails the frontier gate, and a bespoke analytics deliverable is severable and in principle priceable. Entered as a **borderline** call (the undisclosed terms plus a direct, non-resale AI partnership at a big-three team is the uncomfortable edge); **adjudicated and ratified 2026-07-11** — properties scored `1,0,1` → 2/3 per the R054 precedent, so it fails the all-three rule independently of the frontier gate; see §8.2 (Resolved) and `CHANGELOG.md` [1.2]. Its significance is that it makes the abstention finding *robust to the obvious objection*: even Mercedes's one direct AI partnership is specialised analytics, not an off-ledger frontier thinking-partner — so Mercedes remains a frontier-LLM abstainer on the record, not merely for want of looking.
8. **Property B renamed** from "near-zero marginal cost" to **"no clearing price"** — the operative definition in this dataset.
9. **Refresh sweep 2026-07-30 — six on-ledger arrangements added** (`R077`–`R082`; 76 → 82 records, team-cap 65 → 71). An eleven-team re-check of publicly announced partnerships found six current arrangements the 2026-06-29 build had missed: `R077` McLaren–Intel (Official Compute Partner, announced 14 May 2026), `R078` McLaren–Okta (identity and access management, 28 Jan 2025), `R079` Haas–Exein ("Official Physical AI Security Partner", July 2026), `R080` Haas–Ruckus Networks (networking, 21 Jan 2026), `R081` Audi–Perk (work automation, 1 Dec 2025) and `R082` Racing Bulls–Confluent (real-time data streaming, Oct 2025). **All six are `T1`**, coded against existing precedents (Dell `R027`; Zscaler `R038` / Keeper `R053`; Extreme Networks `R059`; Workday `R032`; KX `R043` / VAST Data `R052`). The sweep found **no new Tier-2 arrangement anywhere on the grid**, and none at Mercedes, Red Bull or Ferrari: the frontier-model deals reported for those three remain Microsoft/Azure, Oracle/OCI and AWS respectively, all already coded as priced resale or applied-agent channels. **The Tier-2 population and the distribution finding are therefore unchanged; only the on-ledger denominator grows.** Two rows carry caveats worth reading before use — `R077` (performance-critical sponsored compute with undisclosed terms, the strongest on-ledger counterpart to the Tier-2 set) and `R078` (no AI component is named in its announcement; it is included on the same basis as the seven enterprise-security rows already in the census, and would have to be reviewed together with them under any stricter AI-only rule). See §8.2.

10. **Partner-page diff 2026-07-30 — five further arrangements added** (`R083`–`R087`; 82 → 87 records, team-cap 71 → 76). The 07-30 query sweep (#9) was still query-shaped, so every one of the eleven teams' **official partner pages** was then fetched and diffed against the file. Added: `R083` McLaren–Groq (AI-inference LPU compute, 26 Sep 2025), `R084` Mercedes–Vercel (agentic/web infrastructure, 1 Jul 2026), `R085` Racing Bulls–Dynatrace (AI observability and performance analytics, 14 Jan 2025), `R086` Alpine–Arctic Wolf (AI-assisted security operations, 11 Feb 2025), `R087` Williams–Zoox (autonomous-vehicle *brand* partner — no technology transferred to the team; `cap_relevant = no`, `activity = Marketing`). **All five are `T1`; again no new Tier-2 anywhere, and the Mercedes/Red Bull/Ferrari abstention is untouched** (`R084` Vercel is web-deployment infrastructure and branding, not frontier-model performance work). `R083` Groq now joins `R077` Intel as the sharpest on-ledger edge cases — see §8.2. **The diff also established that this census is a floor, not an enumeration — see §8.7.**

11. **Inclusion rule fixed and applied retroactively, 2026-08-01 — eighteen further on-ledger arrangements added** (`R088`–`R105`; 87 → 105 records, team-cap 76 → 94). The boundary left open by #10 was decided (§3.0: the unit is an arrangement that transfers computing or data technology), written into the codebook, and applied to the pending candidate list *and* to the existing rows. Added: McLaren — Smartsheet, Medallia, Freshworks, Dropbox, Rubrik, Schneider Electric, Arrow Electronics (7); Mercedes — Akkodis, Solera (2); Ferrari — DXC Technology, Genesys, Riedel (3); Racing Bulls — Siemens, RebelDot, Octave (3); Haas — CommScope, Emburse (2); Red Bull — Hexagon (1). Seven candidates were **excluded** and eight boundary calls recorded by name in §3.0. **All eighteen are `T1`. No new Tier-2 arrangement anywhere, for the third consecutive pass.** Two consequences worth reading:
    - **The abstention finding is strengthened, not threatened.** This pass added technology partnerships at all three abstainers — Ferrari (+3), Mercedes (+2), Red Bull (+1), including a *performance-critical* one at Red Bull (`R097` Hexagon metrology, credited by the parties with enabling over 20,000 design changes a season). Each is priced, severable and on-ledger. The three largest-resourced teams now hold visibly more on-ledger technology in the census and still hold **zero** off-ledger frontier-model partnerships. The gap the paper describes is not an artefact of having looked harder at the midfield.
    - **`R103` Racing Bulls–Octave was not on the 07-30 pending list at all.** It surfaced only when that list was itself re-checked against the live team page. A second-order miss inside a completeness audit is the sharpest available evidence for the floor caveat — recorded rather than quietly absorbed. See §8.7.

    Also in this pass: property vectors adjudicated for `R077` and `R083` (§3.2); the four currency flags from #10 resolved or downgraded (§8.7).

**Net effect on the headline:** correcting (1) and (2) removes the only two cases that would have put deep frontier AI at the biggest-spending teams, producing the genuine Tier-2 population — **Williams–Anthropic, McLaren–Google/Gemini, Aston Martin–Cohere, Aston Martin–Cognition**, plus **Alpine–Indra** (probable), with Cadillac–TWG a related-party variant. That population sits in the midfield/new-entrant/champion band; three of the four historically biggest spenders (Ferrari, Mercedes, Red Bull) hold none. Access through the off-ledger sponsored channel does not track team budget.

---

## 5. Column definitions

| Column | Meaning / allowed values |
|---|---|
| `record_id` | Stable ID `R001`–`R105`. IDs are never reused or renumbered; rows found to have lapsed are flagged in `since_detail`, not deleted. |
| `team` | Team the arrangement belongs to. For driver rows: `<Team> (driver: <Name>)`. For central rows: `Formula 1 (central)`. |
| `constructor_entity` | The team's operating/legal entity where known (verified via Companies House for the UK teams — see §7); descriptive name otherwise. `n/a - driver personal deal` / `Formula One Management (FOM)` for landscape rows. |
| `provider` | The technology/AI provider. |
| `technology` | Short description of what is supplied. |
| `tier` | `T2` (off-ledger / unpriceable) or `T1` (on-ledger / priceable). **Blank** for driver-personal and F1-central rows (the tier axis applies to team-cap arrangements). |
| `prop_bidirectional` | `1`/`0` — Property 1. Populated for T2 + the one borderline row only (§3.2); blank elsewhere. |
| `prop_no_clearing_price` | `1`/`0` — Property 2 (renamed from "near-zero marginal cost"). Same population rule. |
| `prop_capability_drift` | `1`/`0` — Property 3. Same population rule. |
| `prop_count` | `0`–`3`, sum of the three properties. Populated only where the flags are. |
| `depth` | `peripheral` / `operational` / `performance-critical`. |
| `activity` | `F1` (performance/engineering) / `Marketing` (fan/brand) / `Mixed`. |
| `since_year` | Start year where stated; blank if not in the source materials. |
| `since_detail` | Free-text timing note (e.g. "extended 2025", "LAPSED end-2025"). |
| `confidence` | `LOW` / `MED` / `MED-HIGH` / `HIGH` — see §3.3. |
| `related_party` | `Y`/`N` — ownership tie between provider and team relevant to RPT/Fair-Value treatment. |
| `cap_relevant` | `yes` (F1/performance activity within team spend) / `partial` (back-office/cyber/HR; within spend but non-performance) / `no` (pure marketing, or driver/central rows outside the team cap). |
| `category` | `team-cap` / `driver-personal` / `F1-central`. **Analysis uses `team-cap` only.** |
| `source_primary_url` | Primary/press source URL where available in the provided materials; **`TBA`** where not (never fabricated). |
| `notes` | Coding rationale, corrections, caveats. |

---

## 6. Provenance

Hand-built by six parallel primary-source research agents on **2026-06-29**, consolidating official team/provider announcements, corporate filings (Companies House) and specialist reporting; corrections adjudicated and applied **2026-07-02** from `analysis/grid_classification_table.md` *(project working file, not in this repository)*. Source project files: `census/CENSUS_AI_F1_2026-06-29.md` *(project working file, not in this repository)*, `analysis/grid_classification_table.md` *(project working file, not in this repository)*, `analysis/grid_partnerships.csv` *(project working file, not in this repository)*. The full per-record source-URL task-output files referenced in the census header were not available when this package was assembled; captured primary URLs come from the project's works-cited materials, and all others are marked `TBA` (see GAPS).

---

## 7. Team-resource proxy (Companies House technical/R&D headcount)

Provided for the distribution analysis (team-level, not per-arrangement; verified in the source census/`grid_partnerships.csv`). Technical / R&D-and-design headcount from each UK operating entity's latest statutory accounts:

| Team | Legal entity | Companies House no. | Technical/R&D headcount | FY |
|---|---|---|---|---|
| Mercedes | Mercedes-Benz Grand Prix Limited | 00787446 | ~998 | 2025 |
| McLaren | McLaren Racing Limited | 01517478 | ~835 (group, upper bound) | 2024 |
| Alpine | Alpine Racing Limited | 01806337 | ~724 | 2024 |
| Red Bull | Red Bull Technology Limited | 05202976 | ~697 | 2024 |
| Aston Martin | AMR GP Limited | 11496673 | ~673 | 2024 |
| Williams | Williams Grand Prix Engineering Limited | 01297497 | ~660 | 2024 |
| Haas | (UK arm only) | — | ~156 | — |

Caveats: Ferrari files in Italy (no Companies House entity); Cadillac and Audi are new entrants; the McLaren figure is a group upper bound; the Haas figure covers its UK arm only. **Note on what that coverage means (added 2026-08-10).** This proxy is available only where a team's operating entity files UK statutory accounts, so its coverage is set by the **company-law disclosure regime of each team's domicile** — not by the sport, not by the cost cap, and not by any limit of this census. The cost cap is a single FIA instrument applying identically to all eleven teams whatever their domicile, so nothing in the *regulatory* treatment varies with incorporation; only *observability* does. Users comparing teams across the table should read a missing row as "not published in a comparable form," never as "not measured." The distribution finding turns on the *abstention of the largest filing teams* (Mercedes ~998, Red Bull ~697 hold no Tier-2 sponsored deal), which the data record directly. **Re-tested 2026-08-01:** the inclusion-rule pass added on-ledger technology partnerships at both (Mercedes +2, Red Bull +1, the latter performance-critical) and no frontier-model arrangement at either — so the abstention is not an artefact of thinner coverage at the top of the resource table. Mercedes's one direct (non-resale) AI partnership, G42 (`R076`), is coded `T1` specialised analytics, so the abstention holds even against its closest counter-example.

---

## 8. Known limits, and the audit trail behind them

*Heading and lede corrected 2026-09-28. This section was written while the dataset was still being built and was
titled "GAPS — must resolve before publication", with a lede calling missing primary-source URLs "the priority
blocker". **Both statements were obsolete**: §8.1 records that all 105 records carry a verified primary URL, and
the inclusion boundary was fixed and applied retroactively on 2026-08-01. Nothing below is an unfinished task.*

**What this section is.** The limits of a hand-built census, stated so a reader can test them: which records are
low-confidence and why (§8.2), what would need primary sourcing to go further (§8.3), the source-recovery logs
(§8.4–§8.6), and the completeness argument, including four currency flags and why retaining them is the
conservative choice (§8.7).

**Two of those flags remain unresolved and are retained deliberately** — `R043` Alpine–KX and `R058` Haas–CSG,
both absent from their team's current partner page. They are downgraded to `LOW` and kept, because **absence from
a partner page is not proof of termination**. Both are Tier-1, both are `cap_relevant = no`, and **neither touches
the Tier-2 population the analysis turns on.** Deleting them would assert a termination no source states.

### 8.1 Source URLs (`source_primary_url = TBA`) — 0 of 105 records
**All 105 records** now carry a captured, individually-verified primary URL (up from 8, then 18, then 54, then 75; `R076` Mercedes–G42 added 2026-07-10 already sourced to its g42.ai announcement; `R077`–`R087` added 2026-07-30 and `R088`–`R105` added 2026-08-01, each sourced to an official team or provider release at the point of entry) after three 2026-07-02 source-recovery passes — see §8.4 (web-search re-verification, 10 records), §8.5 (archived agent-transcript recovery, 36 records) and §8.6 (fresh web-search pass on the remaining 21 records, 2026-07-02) below for the full logs. The original 8 were: `R001` (Williams–Anthropic), `R002` (McLaren–Google), `R007` (Red Bull–Oracle), `R034` (Aston–Arm), `R049` (Williams–Atlassian), `R065` (Hamilton–Perplexity), `R070` (F1–AWS), `R071` (F1–Lenovo). **0 records remain `TBA`.**
- All four previously-highest-priority load-bearing Tier-2 rows are now sourced: `R003` Aston–Cohere, `R004` Aston–Cognition, `R005` Cadillac–TWG, `R006` Alpine–Indra.
- Both priority corrections are now sourced and **confirmed to hold up** against primary sources: `R020` Mercedes–Meta (confirmed fan-facing marketing, no "Llama" mention) and `R054` Racing Bulls–Neural Concept (confirmed engineering/digital-twin aero, not a general-purpose LLM).
- `R051` Williams–Airia — located directly on williamsf1.com as the census predicted.
- The §8.5 pass (2026-07-02) recovered nearly all remaining T1 rows for the six teams originally researched by the archived census agents (Red Bull, Ferrari, Mercedes, McLaren, Aston Martin, Alpine).
- **Caveat on two of the 2026-08-01 additions.** `R096` Mercedes–Solera and `R101` Racing Bulls–Siemens are sourced to their teams' **official partner pages** rather than to a dated release: currency is directly confirmed, the original announcement was not located. Both are coded `MED` and both leave `since_year` blank rather than carry an inferred date. Three further rows (`R097`, `R099`, `R100`) leave `since_year` blank for the same reason — the relationship is documented but its start date is not. No date in this dataset is inferred from an approximation.
- The 21 rows that were still `TBA` after §8.4/§8.5 — concentrated in teams/records the three archived transcripts never covered: Williams (`R050`, `R052`, `R053` — Brillio, VAST Data, Keeper Security), Racing Bulls (`R055` Salesforce), Haas (`R056`–`R058`), Audi/Sauber (`R059`–`R062`), Cadillac (`R063`–`R064`), four driver-personal rows (`R066`–`R069`), and four F1-central rows (`R072`–`R075`) — were **all resolved in the fresh web-search pass of 2026-07-02** (§8.6). None remain `TBA`.

### 8.4 Source recovery log (2026-07-02)

Verification protocol: web-search → WebFetch the candidate page → confirm the page itself names both parties and the partnership (never trust a search snippet alone) → prefer team site > provider press release > reputable trade press. No URL below was fabricated or guessed; any record that could not be confirmed this way was left `TBA`.

| Record (team–provider) | URL | Publisher | Date | Confirming detail | Status |
|---|---|---|---|---|---|
| `R003` Aston Martin–Cohere ("North") | https://www.astonmartinf1.com/en-GB/news/announcement/cohere-joins-aston-martin-aramco-as-official-generative-ai-partner | astonmartinf1.com (team site) | 2026-03-04 | "All team members" get access to North, Cohere's agentic AI platform, org-wide | VERIFIED |
| `R004` Aston Martin–Cognition (Devin) | https://www.astonmartinf1.com/en-GB/news/announcement/aston-martin-aramco-signs-cognition | astonmartinf1.com (team site) | 2026-02-09 | Multi-year deal; Cognition joins as Global Partner to "perform software development tasks autonomously" | VERIFIED — caveat: the primary page does not itself use the name "Devin" (sourced from trade press only); autonomous-coding-agent nature is directly confirmed |
| `R005` Cadillac–TWG AI | https://www.sportspro.com/news/cadillac-f1-twg-ai-sponsorship-february-2026/ | SportsPro (trade press) | 2026-02-05 | "Primary and exclusive AI partner"; TWG AI and Cadillac F1 share TWG Global as parent (related-party confirmed) | VERIFIED — trade press only; page describes broad "operational intelligence," not explicit sim/aero/driver specifics |
| `R006` Alpine–Indra/IndraMind | https://media.alpinecars.com/bwt-alpine-formula-one-team-announces-technological-partnership-with-indra-group/?lang=eng | Alpine (team media site) | 2026-01-23 | IndraMind = "sovereign AI platform" for real-time race-weekend data/strategy | VERIFIED — page does not itself confirm the "replaces lapsed Azure backbone" detail |
| `R019` Mercedes–Microsoft/Azure | https://news.microsoft.com/source/2026/01/22/microsoft-and-mercedes-amg-petronas-f1-team-unite-to-drive-innovation-from-factory-to-circuit/ | news.microsoft.com | 2026-01-22 | Azure AI supports "simulation workloads, performance analysis, race strategy modeling" | VERIFIED |
| `R020` Mercedes–Meta AI | https://www.mercedesamgf1.com/news/meta-ai-joins-as-official-team-partner | mercedesamgf1.com (team site) | 2025-10-17 | Fans use Meta AI to "analyse race strategies, share predictions...create and remix race day images and videos" via Facebook/Instagram/WhatsApp/Messenger; no "Llama" mention anywhere on the page | VERIFIED — confirms the census's on-ledger/marketing correction; no evidence of an engineering/Llama-compute deal |
| `R017` Ferrari–IBM watsonx | https://newsroom.ibm.com/2025-05-01-ibm-and-scuderia-ferrari-hp-debut-reimagined-mobile-app-to-supercharge-global-formula-1-fan-experience | newsroom.ibm.com | 2025-05-01 | "Racing Insights" fan app built with IBM watsonx; LLMs on watsonx turn data into narratives | VERIFIED — confirms fan-facing/marketing class |
| `R015` Ferrari–AWS | https://press.aboutamazon.com/2021/6/ferrari-selects-aws-as-its-official-cloud-provider-to-power-innovation-on-the-road-and-track | press.aboutamazon.com | 2021-06 | Ferrari names AWS "Official Cloud, Machine Learning, and Artificial Intelligence Provider"; SageMaker named | VERIFIED — note: original deal dates to 2021, not solely 2025 |
| `R051` Williams–Airia | https://www.williamsf1.com/articles/c4e8db90-41fb-4c5c-be57-560ffa4718a1/atlassian-williams-racing-partnership-airia | williamsf1.com (team site) | 2025-05-01 (Miami GP) | "Enables organisations to orchestrate, deploy and manage AI solutions securely and at scale"; branding debuted on FW47 | VERIFIED — the predicted williamsf1.com primary source, located |
| `R054` Racing Bulls–Neural Concept | https://www.neuralconcept.com/post/visa-cash-app-racing-bulls-vcarb-formula-one-tm-team-accelerates-racing-car-design-with-neural-concepts-engineering-ai | neuralconcept.com (provider site) | 2025-06-04 | Complements CFD with "high-speed predictive simulations"; digital twins evaluate design variants under multi-physics track conditions | VERIFIED — confirms engineering/digital-twin-aero classification, not a general-purpose LLM |
| `R007` Red Bull–Oracle (re-verification) | https://www.oracle.com/news/announcement/oracle-red-bull-racing-extends-title-partnership-with-oracle-2026-02-26/ | oracle.com (content confirmed via mirror: redbullracing.com) | 2026-02-26 | "OCI and Oracle AI underpinning...hybrid power unit"; "AI-powered strategy agent"; Oracle Fusion Cloud Apps for finance/HR/marketing | VERIFIED (content) — oracle.com blocks automated fetch (HTTP 403); identical text confirmed on redbullracing.com/int-en/oracle-extends-title-partnership-in-multi-year-deal. Supports the on-ledger/commodity-cloud-plus-applied-agent reading; confidence raised MED-HIGH → HIGH |

**Net result:** all four highest-priority load-bearing Tier-2 rows (Aston–Cohere, Aston–Cognition, Cadillac–TWG, Alpine–Indra) are now sourced; both priority corrections (Mercedes–Meta, Racing Bulls–Neural Concept) are sourced and their classifications hold up unchanged against primary sources; Williams–Airia is sourced; three abstainer/resale-channel records (Mercedes–Microsoft, Ferrari–IBM, Ferrari–AWS) and Red Bull–Oracle are sourced/re-verified. No fabricated or guessed URLs were inserted; nothing was force-matched to an unconfirmed page.

### 8.5 Source recovery from archived agent transcripts (2026-07-02)

The three original census-building research agents (launched 2026-06-29, before URL capture was standardised) left full JSONL transcripts of their web research, archived at `raw_agent_transcripts/census_agent_1.jsonl` (Red Bull, Ferrari, Mercedes), `census_agent_2.jsonl` (FIA TD45 / PSG-QTA fact-checking — not team-partnership data, contributed no rows here), and `census_agent_3.jsonl` (McLaren, Aston Martin, Alpine). These transcripts contain the per-partnership primary/official URLs the original agents had already located and cited but which were not carried through into the CSV at the time.

This pass extracted those URLs directly from the archived transcripts (no new web search performed) and matched them to CSV rows by team + provider, confirming from the surrounding transcript text that each URL was tied to that specific deal before assigning it. **36 rows were filled this way**, all from the six teams the two relevant transcripts covered:

| Team | Rows filled |
|---|---|
| Red Bull | `R008` Siemens, `R009` Ansys, `R010` HPE, `R011` CDW, `R012` 1Password, `R013` Neat, `R014` AT&T |
| Ferrari | `R016` HP Inc., `R018` Bitdefender |
| Mercedes | `R021` CrowdStrike, `R022` SAP, `R023` AMD, `R024` HPE, `R025` TeamViewer, `R026` Qualcomm |
| McLaren | `R027` Dell, `R028` Cisco, `R029` Splunk, `R030` Salesforce, `R031` Alteryx, `R032` Workday, `R033` Iron Mountain |
| Aston Martin | `R035` CoreWeave, `R036` Cognizant, `R037` NetApp, `R038` Zscaler, `R039` ServiceNow, `R040` UKG, `R041` Xerox |
| Alpine | `R042` Microsoft/Azure, `R043` KX, `R044` Cato Networks, `R045` SEALSQ, `R046` Avature, `R047` Businessolver, `R048` data.ai |

Notes:
- `R014` Red Bull–AT&T: the transcript itself flags this as its weakest find — "no official RBR press release located"; the URL used (sportskhabri.com) is a minor trade-press aggregator, not an official source. Filled because it is the only URL the original research produced, but the existing `LOW` confidence coding is unchanged and should be treated cautiously.
- No contradictions were found between any recovered URL and its row's existing coding (tier, depth, activity, notes) — the transcript descriptions of each deal's disclosed uses are consistent with how the CSV already classifies it.
- Rows for Williams, Racing Bulls, Haas, Audi, Cadillac, driver-personal, and F1-central were **not** covered by any of the three archived transcripts (those teams were researched in separate, non-archived sessions) and remain `TBA` — see §8.1.

### 8.6 Fresh web-search recovery of the final 21 records (2026-07-02)

The 21 rows never covered by the archived transcripts (Williams, Racing Bulls, Haas, Audi/Sauber, Cadillac, four driver-personal, four F1-central) were web-sourced on **2026-07-02** by six parallel research agents under the same protocol as §8.4 (web-search → WebFetch the candidate page → confirm the page itself names both parties and the deal → prefer team site > provider press release > reputable trade press; never a bare homepage; leave `TBA` if unconfirmable). **All 21 were verified and filled** — 0 remain `TBA`.

| Record (team–provider) | URL | Publisher | Date | Status / note |
|---|---|---|---|---|
| `R050` Williams–Brillio | https://www.williamsf1.com/articles/79bf7c67-377c-4dba-bac1-ce4799691ea7/atlassian-williams-racing-partnership-brillio | williamsf1.com (team) | 2025-03-13 | VERIFIED — "Official Digital Transformation Partner"/"Official Data and AI Services Partner". **Upgrades the row's prior "secondary source" flag to a primary team source** (existing `LOW` confidence/note left unchanged) |
| `R052` Williams–VAST Data | https://www.williamsf1.com/posts/b605b3be-ffb2-44dd-9134-ec110b1f44a0/williams-racing-vast-data-official-partner | williamsf1.com (team) | 2024-02-02 | VERIFIED — "Official Partner and technology vendor". NB: verified start = 2024 (CSV `since_year` blank; left unchanged per edit-scope) |
| `R053` Williams–Keeper Security | https://www.williamsf1.com/articles/fce0ff58-774b-431e-8109-063f548aeb33/williams-racing-cybersecurity-partnership-keeper-security | williamsf1.com (team) | 2024-04-30 | VERIFIED — "Official Password Security Partner". NB: verified start = 2024 (CSV `since_year` blank; left unchanged) |
| `R055` Racing Bulls–Salesforce (Agentforce/TORO) | https://www.salesforce.com/news/press-releases/2026/06/22/vcarb-salesforce-partnership-announcement/ | salesforce.com (provider) | 2026-06-22 | VERIFIED (content) — salesforce.com blocks automated fetch (403); identical release text confirmed via StockTitan mirror, which names VCARB + Salesforce, Agentforce 360 and "TORO" AI agent. Same convention as `R007` |
| `R056` Haas–Mphasis | https://www.haasf1team.com/news/moneygram-haas-f1-team-welcomes-mphasis-partnership | haasf1team.com (team) | 2024-11-21 | VERIFIED — "Official Digital Partner" (Data/Automation/Analytics/Cyber/AI). NB: deal announced 2024 (multi-year into 2026); "TGR Haas" is the 2026 rebrand |
| `R057` Haas–Infobip (RaceMate) | https://www.infobip.com/haas-f1-team-partnership | infobip.com (provider) | 2026-04-30 | VERIFIED — "TGR Haas F1 Team RaceMate powered by Infobip", AI conversational fan companion; also confirmed on a Business Wire release of the same date |
| `R058` Haas–CSG | https://www.haasf1team.com/news/moneygram-haas-f1-team-and-csg-partner-accelerate-innovation-2025-us-grand-prix | haasf1team.com (team) | 2025-10-14 | VERIFIED — CSG (NASDAQ: CSGS) customer-experience partner (Ascendon). NB: announced 2025 |
| `R059` Audi/Sauber–Extreme Networks | https://www.extremenetworks.com/resources/at-a-glance/extreme-networks-and-f1 | extremenetworks.com (provider) | — | VERIFIED — names the Sauber/Audi F1 team + Extreme Networks cloud networking |
| `R060` Audi/Sauber–ElevenLabs | https://elevenlabs.io/blog/we-are-on-the-grid | elevenlabs.io (provider) | 2025 | VERIFIED — ElevenLabs voice AI, content/marketing with the team |
| `R061` Audi/Sauber–NinjaOne | https://www.ninjaone.com/press/audi-revolut-f1-team/ | ninjaone.com (provider) | — | VERIFIED — NinjaOne IT-ops/endpoint management for the Audi Revolut F1 Team |
| `R062` Audi/Sauber–JigSpace | https://www.audif1.com/en/partners | audif1.com (team) | — | VERIFIED — JigSpace named as an official AR/3D supplier on the team partners page |
| `R063` Cadillac–Core Scientific | https://investors.corescientific.com/news-events/press-releases/detail/129/cadillac-formula-1-team-joins-forces-with-core-scientific-as-official-data-center-partner | investors.corescientific.com (provider) | 2026-03-10 | VERIFIED — "Official Data Center Partner"; Indianapolis AI-HPC hub (described as upcoming/under development) |
| `R064` Cadillac–IFS | https://www.cadillacf1team.com/news/cadillac-formula-1-r-team-partners-with-ifs-ahead-of-the-teams-debut-season | cadillacf1team.com (team) | 2026-01-07 | VERIFIED — IFS founding technology partner, ERP (finance/procurement/supply chain/production/engineering) |
| `R066` Leclerc–Eight Sleep | https://www.eightsleep.com/blog/charles-leclerc-joins-eight-sleep/ | eightsleep.com (provider) | 2025-02-18 | VERIFIED — Leclerc as "Athlete Ambassador and Investor" (confirms personal deal + equity angle) |
| `R067` Piastri–Dubber | https://www.dubber.net/learn/blog-posts/oscar-piastri-becomes-global-ambassador-for-dubber/ | dubber.net (provider) | 2023-03-29 | VERIFIED — Piastri "Global Ambassador"; explicitly personal, not a McLaren team deal |
| `R068` Albon–Domo | https://www.stocktitan.net/news/DOMO/domo-and-formula-1-driver-alex-albon-join-forces-to-showcase-the-g9aahbhqj692.html | StockTitan (verbatim Business Wire reprint) | 2025-11-20 | VERIFIED (content) — domo.com/Business Wire originals would not render (JS/bot-blocked); StockTitan reprint names Domo + Alex Albon as an individual-driver deal. This mirror was the only fetchable copy |
| `R069` Colapinto–Globant | https://www.globant.com/news/globant-sponsorship-franco-colapinto-f2-championship | globant.com (provider) | 2023-11-24 | VERIFIED (with caveat) — Globant's own release sponsoring Colapinto personally; NB this is his 2023 F2-debut announcement, not a fresh 2026 Alpine-era re-announcement (no dedicated 2026 primary located; continuity attested only by secondary sources). Distinct from the Williams team-level Globant deal and the FOM Globant deal |
| `R072` FOM–Salesforce | https://investor.salesforce.com/news/news-details/2026/Formula-1-and-Salesforce-Deepen-Partnership-Expanding-Agentforce-to-Grow-Fan-Connection-Worldwide/default.aspx | investor.salesforce.com (provider) | 2026-03-03 | VERIFIED — F1 + Salesforce Agentforce fan-companion agent on F1.com (corp.formula1.com copy 475'd; salesforce.com/news 403'd) |
| `R073` FOM–Tata Communications | https://www.prnewswire.com/news-releases/formula-1-and-tata-communications-announce-multi-year-strategic-collaboration-301505021.html | PR Newswire (official joint release) | 2022-03-17 | VERIFIED — Tata Communications "Official Broadcast Connectivity Provider of Formula 1" |
| `R074` FOM–Globant | https://www.globant.com/news/globant-formula-1-partnership | globant.com (provider) | 2024-05-02 | VERIFIED — league-level FOM digital/AI partnership (PitWall, race-day app), distinct from the Williams and Colapinto Globant deals. NB release states term "until 2026" — currency into 2026+ should be re-checked |
| `R075` FOM–PwC | https://www.formula1.com/en/latest/article/formula-1-welcomes-pwc-as-official-consulting-partner.jLK5v2MLA3QKOFtwcHLN8 | formula1.com (official site) | 2025-04-29 | VERIFIED — PwC "Official Consulting Partner" from 2025 Miami GP |

**Net result (as of the 2026-07-10 state, 76 rows):** the census is fully sourced — every one of the 76 rows then in the file (including `R076` Mercedes–G42, added 2026-07-10) carries an individually web-verified primary or official-mirror URL, none fabricated. *(The six rows added by the 2026-07-30 sweep, `R077`–`R082`, were each sourced to an official team or provider release at the point of entry, so the file remains 82/82 sourced — see §8.1.)* Two rows (`R055`, `R068`) rely on faithful mirrors of official releases whose canonical pages block automated fetch, following the `R007` precedent. No recovered source contradicted its row's tier/activity/nature coding; the only flags raised are date-precision notes (`R052`/`R053`/`R056`/`R058` announced earlier than 2026) and a currency question on the FOM–Globant term (`R074`, stated "until 2026") — none of which were auto-applied, per the edit scope (URL field only).

### 8.2 Low-confidence / borderline records
- `LOW` confidence: `R014` Red Bull–AT&T (weak source), `R050` Williams–Brillio (secondary), `R045` Alpine–SEALSQ (exploratory), `R048` Alpine–data.ai (branding; **lapsed** as of 2026-08-01), `R062` Audi–JigSpace, `R067` Piastri–Dubber (currency uncertain), `R075` F1–PwC, and — downgraded 2026-08-01 on currency — `R043` Alpine–KX and `R058` Haas–CSG.
- `MED` confidence on **what is supplied**, as distinct from whether the arrangement exists: `R094` McLaren–Arrow Electronics (F1-side supply not itemised; Arrow is title partner of the IndyCar team), `R098` Ferrari–DXC Technology (much of the announced scope concerns Ferrari road cars, not the race team), `R096` Mercedes–Solera and `R101` Racing Bulls–Siemens (sourced to partner pages, announcements not located). Each caveat is carried in the row's own `notes`.
- **Borderline classification calls to double-check:** `R006` Alpine–Indra (`T2` hedged "probable"), `R054` Racing Bulls–Neural Concept (`T1`, scores 2/3), `R005` Cadillac–TWG (`T2` but related-party, excluded from sponsored count).
- **`R083` McLaren–Groq and `R077` McLaren–Intel — ADJUDICATED 2026-08-01** (scored against the published rule in §3.1–§3.2 by an AI assistant at the author's request; reviewed and ratified by the author — see §0, Research assistance and AI use). Both `T1` **ratified**, with explicit vectors scored from the primary releases per the `R076` precedent:
  - `R083` **Groq** — `1,0,0` → **1/3**. A dedicated AI-inference supplier (custom LPU) feeding "real-time insight" into race-weekend decision-making, sponsoring the team, logo on the rear wing, terms undisclosed: **the census's hardest on-ledger call.** A = 1 on *branding alone* (the release names no data return, no expert feedback, no co-development) — scored 1 only for consistency with `R076`; see the Property A note in §3.2. B = 0: GroqCloud publishes per-token inference pricing. C = 0: what is transferred is inference capacity at a published rate.
  - `R077` **Intel** — `1,0,0` → **1/3**. A = 1 on firmer ground than Groq: the release states the companies "will co-engineer solutions." B = 0: Xeon and Core Ultra carry published list prices in a deep market. C = 0: delivered silicon performs identically across a reporting period; a product-line refresh is a new purchase, not drift in the capability supplied.
  - **Why the adjudication is worth having.** Both rows fail the all-three rule **on the most generous available reading**: score Property C as 1 for either and the total is 2/3, still short. The `T1` call therefore rests on **Property B — the single most externally verifiable of the three, since it is settled by a published price list rather than by judgment.** That is the reply if a reviewer attacks the Tier-1/Tier-2 line here, which is where they will attack it. The deeper point stands unchanged: the rule keys on *what is transferred*. Priced inference capacity and priced silicon are severable and quotable; a frontier thinking-partner relationship is not.
  - **Second-order value:** both sit at McLaren, which *also* holds a Tier-2 arrangement. Identical sponsor structure, identical branding, undisclosed terms in every case — and the cap can price two of the three. The distinction the paper draws does visible work inside a single team's portfolio.
  - `R078` McLaren–Okta — **resolved 2026-07-30 (author decision): retained.** Identity and access management; **the announcement names no AI component**. It is in the census on the same basis as the eight comparable enterprise-security rows (`R012`, `R018`, `R021`, `R038`, `R044`, `R053`, `R061`, `R079`): the census's unit is the *technology partnership* held by a team, sorted by whether the cap can price it, not "arrangements whose press release says AI." All nine are on-ledger either way, so no headline depends on the choice; the author elected to keep them rather than narrow the inclusion rule mid-dataset.
  - `R082` Racing Bulls–Confluent is coded `MED-HIGH` rather than `HIGH` only on 2026 currency (announced in the 2025 season, still listed on the team partner page).
- **Resolved:** `R076` Mercedes–G42 — flagged BORDERLINE on entry (2026-07-10); **adjudicated 2026-07-11** (scored against the published rule in §3.1–§3.2 by an AI assistant at the author's request; reviewed and ratified by the author — see §0, Research assistance and AI use): `T1` ratified. Properties scored per the `R054` precedent (1,0,1 → 2/3 — fails the all-three rule independently of the frontier gate); 2023–2026 record re-checked with no expansion into a general-purpose frontier-model deployment; the rule keys on the technology transferred (Presight analytics), not the counterparty's portfolio (G42 group's Jais/Core42 LLM assets are not part of this arrangement). See Correction #7 and the row note.

### 8.3 Other items to confirm
- `constructor_entity` for non-UK / new teams (Ferrari, Racing Bulls, Haas, Audi, Cadillac) uses descriptive names, not verified legal-registration strings — verify exact entity names if precise entity attribution is needed.
- Per-property flags for Tier-1 records are intentionally blank (§3.2); if the analysis or reviewers require them, they must be adjudicated from primary sources, not inferred. Two `T1` rows carry adjudicated scores as exceptions: `R054` (scored during its T2→T1 recode) and `R076` (scored during its 2026-07-11 borderline adjudication).

### 8.7 Completeness — the floor caveat, and what is now closed

Three successive completeness passes have been run against this file: a keyword sweep (2026-07-30, `R077`–`R082`), a line-by-line diff against all eleven teams' **official partner pages** (2026-07-30, `R083`–`R087`), and the retroactive application of a fixed inclusion rule (2026-08-01, `R088`–`R105`). What they established:

**Now closed — the boundary problem.** The residual gap identified on 07-30 was a *boundary* problem, not a search problem: 24 named technology partners sat un-entered because the project had never written down what counts as a record. §3.0 now fixes that rule, and it has been applied to the pending list and to the existing rows alike. Seventeen of the 24 were admitted, seven excluded, and every boundary call is named in §3.0 so a reader who disagrees can reverse it. **All eighteen additions (the 24 minus exclusions, plus `R103` Octave) are `T1`.**

**Still open — the ordinary residue.** What no procedure can close:

- **Teams publish 25–56 partners each.** McLaren's own Groq announcement called it the team's *56th partner*. This census now holds 18 McLaren rows; the remainder are apparel, beverage, finance, logistics and hospitality, excluded by §3.0(iii).
- **`R103` Racing Bulls–Octave was not on the 07-30 pending list.** It was found only when that list was itself re-checked against the live team page on 2026-08-01. A completeness audit missed something, and the audit *of* the audit caught it. Recorded here rather than quietly absorbed, because it is the honest measure of what this method can and cannot guarantee.
- **There is no partnership registry in F1.** A team's own partner page is the best available universe, and it is not a complete one: it omits arrangements that were never publicised and lists some that have quietly lapsed (see the four currency flags below). A census built this way can only prove what it found.

**Currency flags from the 07-30 diff — all four now resolved or downgraded** (2026-08-01):

| Row | Status |
|---|---|
| `R030` McLaren–Salesforce | **Confirmed current.** The 07-30 flag was a page-capture artefact; McLaren maintains a live Salesforce partner page. Confidence raised `MED` → `MED-HIGH`. |
| `R048` Alpine–data.ai | **Lapsed.** Absent from the partner page *and* the counterparty brand itself was retired after the March 2024 Sensor Tower acquisition. Flagged `LAPSED`, retained on the `R042` convention. |
| `R043` Alpine–KX | **Unresolved.** Absent from the partner page, no renewal announced since 2021. Downgraded to `LOW`, retained — absence is not proof of termination. |
| `R058` Haas–CSG | **Unresolved.** Absent from the partner page; the announcement is framed around a single event (2025 US GP) and names no term. Downgraded to `LOW`, retained. |

All four are `T1`; three are `cap_relevant = no`. None touches the Tier-2 population.

**Why the analysis survives all of this — and is now better supported than before.** Completeness is load-bearing only for the *off-ledger* tier, because the Tier-2 claim is an absence ("Ferrari, Mercedes and Red Bull hold none"). Three independent passes, using three different methods, have now searched for exactly that absence:

- **Not one turned up a missed Tier-2 arrangement.** Together they turned up **twenty-nine** missed Tier-1 ones.
- **The direction of the error is systematic and runs in the argument's favour.** Frontier-model partnerships are announced loudly and covered widely; they are the *easiest* arrangements on the grid to find. Enterprise networking, expense software and metrology contracts are the hardest. A census that is admittedly a floor is a floor **on precisely the category the argument does not depend on.**
- **The 08-01 pass tested this directly and passed.** It added technology partnerships at all three abstainers — Ferrari +3, Mercedes +2, Red Bull +1, one of them performance-critical — and still found no frontier-model deal at any of them. Looking harder at the biggest teams produced more on-ledger technology and zero off-ledger technology. That is the finding, reproduced under a harder test.

The on-ledger count should be read as a floor, and the paper should say so — then say why the floor is in the right place.

---

## 9. Citation stub

> Wang, H. (2026). *Census of AI / Frontier-Model Partnerships across the 2026 Formula 1 Grid* (Version 1.5) [Data set]. Zenodo. DOI: [minted on first Zenodo release]. Licensed CC-BY-4.0.

*Until the Zenodo DOI exists, cite the GitHub repository URL and the version number. The DOI is deliberately
withheld rather than missing: the Zenodo release follows the companion paper's posting, so that the citable
record of the dataset and the paper appear together.*
