# Client B material waste and nesting pilot

## 1. What I propose and why

Start with a six-week pilot on one plate-cutting line and two active projects, keeping each project's stock separate. Compare manual nesting with the automatic option already available in Strumis, then test better stock selection if needed. Keep planner approval and existing cutting controls. Cross-project sharing is a later, conditional step, not the basis of the business case.

The client asked where AI could help across nesting, drawing revisions, yard storage, trailer loading and equipment use. The immediate need is a reliable measure of avoidable material loss and a practical way to use available stock. An AI model is not a prerequisite for either.

**What the calls establish:** 80,000 tonnes is stated capacity, not confirmed annual throughput. There are 10–15 projects. Plate wastage is reported at 20–25%, profiles at 5–10% and overall at 7–10%. Strumis and a PLM package support nesting; the company is moving towards Strumis as its main ERP. Planners say automatic nesting wastes more than manual nesting, but this has not been measured independently.

**Current process:** Business Development and Estimation bid → Planning schedules purchasing and delivery → Engineering releases drawings → Nesting plans cuts per project → Sizing cuts → Fabrication fits and welds → Coating → Dispatch. Purchases and rates belong to individual projects. Offcuts are already recorded and checked before new stock, but reuse effectiveness is uncertain. Revisions continue while budgets stay fixed; some jobs are on hold and needed steel can be buried in the yard.

### People who need to be involved

| Person or team | What they need from this proposal |
|---|---|
| Cost Control contact | A forwardable update this week and a defensible loss breakdown. The contact is not a confirmed budget owner or nesting expert. |
| Nesting planner | Feasible suggestions, less searching and the final say on each nest. |
| Engineering and quality | Correct revisions and traceability; separate client-change losses that may be claimed back from internal engineering errors. |
| Yard team | A short stock-check routine and remnants that can actually be found and moved. |
| Production and machine operator | No missed dates or unapproved changes to cutting instructions. |
| Management and Finance | Capped spend, fixed project budgets and fair transfer costing; acknowledge concern about extra trailer hire despite low utilisation. |
| IT or systems owner | Limited access, agreed data handling and no disruption to production systems. |

## 2. Five questions for the next call

| Rank | Question and why it matters | Assumption until answered |
|---|---|---|
| 1 | Can the nesting, yard, engineering and production leads walk us through one recent job, and who can approve a pilot? This tests the problem with the people doing the work. | Cost Control can convene them; the budget owner and operating owner still need confirmation. |
| 2 | Can planners reproduce a case where Strumis automatic nesting loses to manual, with the same inputs and settings? This tests the central claim before buying or building. | The planner's view is a hypothesis. Check version, module, settings, exports and machine rules; do not assume automation wins. |
| 3 | How is waste calculated, and can recent batches distinguish cutting loss, reusable returns, client revisions and internal errors? This establishes avoidable cost. | The quoted rates are provisional; 80,000 tonnes is capacity. Claimable losses are not automatically recovered cash. |
| 4 | Can Finance approve sharing a plate or transferring an offcut, and how would each project's rates and budget be adjusted? Can Yard locate the stock? | Keep project stock separate. Require an approved transfer record, valuation and traceability before any cross-project test. |
| 5 | Which released jobs can provide 20 batches despite holds and revisions, and who confirms the latest drawing before cutting? This protects delivery and the trial. | One plate line, two projects; held jobs are excluded. Engineering confirms release status and the operator supplies machine constraints. |

## 3. Options and the first decision

| Option | Assessment |
|---|---|
| Measure waste and improve stock records only | Necessary first step and the fallback if the data or reuse opportunity is weak. It may solve much of the problem without new software. |
| Configure Strumis automatic nesting | First technical test: compare against the planners' manual layouts. A second package is considered only if a demonstrated capability gap remains. |
| Add a small stock-matching and comparison tool | Build only where exports and existing software leave a demonstrated gap. It can filter eligible stock and compare candidate nests without replacing CAM. |
| Build a custom 1D/2D nesting platform or train an AI model | Defer. Too much development and validation before we know the constraints or opportunity. |

I recommend the measurement work followed by an existing-software trial, with a small matching tool only if needed. Plates are the starting hypothesis because their reported loss is higher; week one must also confirm enough eligible plate volume to matter. Commercial software is not ruled out on an unsupported claim that it cannot work across projects.

We would deliver discovery, configuration, any agreed small tool, training and the pilot report ourselves, not just a software shopping list. Trailer utilisation is a credible next option: reconcile existing CarTrack and booking records with paid hire and concurrent demand. Low idle-time utilisation alone does not prove spare capacity at the time it is needed. Do not replace these six-month-old systems before testing their data.

Do not build autonomous cutting, a custom CAD parser, yard computer vision, trailer planning, equipment monitoring or automatic drawing revision management in this pilot. Do not pool all 10–15 projects. Do not retain offcuts simply to make the waste metric look better.

## 4. How it works

### Minimum inputs

| Input and owner | Required fields or checks |
|---|---|
| Released parts from Engineering | Project, part ID, revision, quantity, approved geometry, grade, thickness and required date. Use project + part ID + revision as the key. |
| Stock and remnants from Yard | Unique stock ID, measured usable shape and dimensions, grade, thickness, heat or certificate reference, location, availability and reservation status. |
| Cutting rules from planner and operator | Bed limits, approved kerf and spacing, orientation restrictions, trim, process limitations and handling rules. |
| Actual results from Production and Cost Control | Issued steel, accepted parts, returns, scrap, rework, time and prices; loss reason, revision reference, client/internal cause and claim status. |

**Daily routine:**

1. Import approved Strumis/PLM exports into a controlled comparison register. Confirm export fields with IT; do not assume an API. Reject missing revisions, quantities, units or material identifiers. Strumis remains the operational record.
2. Start with existing offcut records. Yard confirms location, usable shape and retrieval effort. Exclude buried stock that cannot be retrieved within the plan, held jobs and incompatible or reserved material. Keep each project's allocation unless Finance approves a transfer.
3. Filter by grade, thickness, certification, dates and machine constraints. Use the existing nesting engine to compare feasible layouts on verified remnants and new plate. Rank by estimated material cost after scrap recovery, plus handling and cutting effort; do not chase utilisation alone.
4. Show the planner the current plan and proposed alternative, with stock IDs, expected material use and reasons for exclusions. The planner can reject or adjust it. Engineering/quality resolves exceptions; no automatic material substitution.
5. Before release, recheck revision and stock availability and record the reservation in the existing operating process. A revision change cancels the proposal until reviewed. The approved CAM process generates and validates machine instructions; the pilot tool does not send code to a machine.
6. Record actual parts, scrap and measured returns in the existing offcut process. Log losses as cutting, client revision, internal error or unknown, with evidence and an owner. Cost Control tracks claims separately from nesting savings; do not count the same loss twice.

Start with file exports and manual approved updates, not a live ERP integration. Agree access, storage and retention with IT; keep confidential files within the approved environment. A missed import or bad record falls back to normal planning. No language model is needed for geometry, eligibility or release decisions.

## 5. How we decide whether it worked

**Baseline:** in weeks 1–2, reconcile at least 10 recent comparable batches and observe current planning. Separate plate from profiles and record the denominator. The reported 20–25% plate loss is context, not the acceptance baseline.

Use a material balance for every measured batch: issued steel = accepted parts + verified reusable returns + scrap/process loss + unexplained difference. Investigate an unexplained difference above 2% of issued weight before using that batch as evidence.

**Primary metric:** material cost per tonne of accepted parts. For each plan, calculate `(issued stock value − verified return value − scrap proceeds) / accepted part tonnes`, using the same agreed valuation rules. Credit a returned remnant only if its shape, grade, traceability and location are verified and a specific use is identified within 30 days; otherwise value it at scrap. Run a sensitivity check with all unused remnants valued at scrap.

**Trial:** for 20 distinct batches across two projects over at least two weeks, freeze demand, revisions, stock and constraints. Compare A: current manual nesting, B: existing automatic nesting and, if needed, C: configured automatic nesting or improved stock selection. Give each the same agreed planning-time budget; record settings and all failures. Keep project stock separate. Include urgent jobs and batches without usable remnants. Extend the window if there are too few eligible batches.

**Success threshold:** B or C achieves at least 3% lower aggregate material cost per accepted tonne than A, with no increase in combined planning and handling time or pilot-caused missed dates. Aggregate costs and tonnes, not batch percentages. Report B versus A and C versus B separately. If B works, configure the existing option; do not claim custom-tool value for savings already available in Strumis.

The nesting lead records the paired plans, the yard lead checks stock, Production records results, and Cost Control owns the calculation. Execute at least five approved candidate batches through the existing CAM process. Those batches must confirm usable parts, traceability and a positive saving after extra handling/cutting costs. Paper comparisons alone do not justify rollout.

**Stop or narrow the work:** pause immediately for an unsafe suggestion reaching release, wrong revision, grade or traceability failure. Stop expansion if reconciled inputs are unavailable by week two, if the 20-run result is below 3%, or if operational costs erase the benefit. Investigate poor results; do not quietly exclude them. A six-week pilot provides a decision, not a proven annual saving.

## 6. Delivery plan and client commitments

| Timing | Deliverable | Client dependency |
|---|---|---|
| Week 1 | Forwardable management update, walkthrough and trial scope | Access to planner, yard, engineering, production and budget owner. |
| Week 2 | First measured result: baseline, loss breakdown and manual versus automatic comparison | Job records, stock checks and valuation rules. Stop/go review before further build. |
| Weeks 3–4 | Configure existing software; add only necessary import/matching logic; start paired trials | Usable exports, software access and operator-approved constraints. |
| Weeks 5–6 | Finish 20 comparisons and at least five controlled executions; present measured result and rollout decision | Eligible jobs, planner time, release approvals and actual cutting records. |

The six-week clock starts after the required people and sample files are available. No forced rollout follows the pilot. Any wider deployment gets a separate scope and quote. Client delays or missing batch volume move the finish date; scope and budget changes require agreement.

## 7. Cost and value

All figures below are proposal assumptions in USD, not verified local prices or market quotes. Confirm currency and actual material values with Finance.

**Our delivery cost:** FDE, 18 days × $700 = $12,600; integration engineer, 12 days × $600 = $7,200; nesting specialist, 4 days × $800 = $3,200. Labour totals $23,000. Add $1,000 for pilot compute/tools and $2,000 contingency: **$26,000 estimated delivery cost** for 34 person-days across six weeks.

**Client price:** a **$35,000 fixed-fee pilot**, paid $10,500 at kickoff, $14,000 after baseline review and approval to continue, and $10,500 on delivery of the trial report. The final payment buys the completed evaluation, not a guaranteed positive result. If the week-two gate fails, stop with only the kickoff payment due and hand over the findings. Our downside is delivery effort already spent. At full scope, the estimated contribution is $35,000 − $26,000 = **$9,000**, before company overhead and tax.

The price includes the pilot tooling allowance. Travel, tax and any new commercial CAM licence are excluded and require a separate approved quote before purchase. Budget roughly 4 hours/week for the planner, 2 for Yard, 2 for Cost Control and 2 shared across Engineering, Production and IT: **60 client staff-hours** over six weeks, to confirm at kickoff.

After a successful pilot, optional support for the same limited scope is **$1,000/month**, comprising an assumed $250 hosting/tools + $500 support labour + $250 contribution. This excludes wider rollout and third-party CAM subscriptions. There is no annual platform commitment.

**Illustrative value at unchanged finished output:** assume the eligible scope currently consumes 10,000 tonnes/year. A measured improvement that avoids 2% of those purchases saves 200 tonnes. At an assumed $900/tonne purchase cost and $300/tonne scrap recovery, the net material benefit is `200 × ($900 − $300) = $120,000/year`. Deduct $10,000 additional annual handling/cutting cost and $12,000 support: **$98,000 annual operating benefit**. Deduct the $35,000 pilot once: **$63,000 in the first full year of operation including the pilot fee**, before client staff cost, tax and excluded items.

This is a scenario, not a forecast or the 3% pilot acceptance metric. Payback on the pilot fee would be `$35,000 / ($98,000 / 12) = 4.3 operating months` after savings begin; it excludes the pilot period. At only 1% purchase avoidance, annual operating benefit falls to $38,000 and the same first-year benefit to $3,000. At zero, there is no payback. Confirm eligible tonnage and measured purchase avoidance before annualising anything; do not apply plate results to all 80,000 tonnes.

## 8. Main risks and limits

- **Inventory is wrong:** a good digital nest uses an offcut nobody can find. Require physical confirmation and reservation before release; otherwise use normal stock.
- **Reported waste mixes scrap and reusable returns:** reconcile weights and definitions before estimating savings. The quoted plate, profile and overall rates cannot establish a weighted baseline without the material mix.
- **The savings exist only on paper:** count handling, cutting and scrap revenue; check actual executions and later remnant use. Avoid double-counting recovered stock and reduced purchases.
- **Cross-project reuse is restricted:** project-specific rates and cost loading are confirmed. No sharing until Finance approves how both budgets and stock ownership change. The core pilot works within each project.
- **The operating teams do not adopt the routine:** involve them from week one and record rejection reasons. Do not impose yield targets that reward storing unusable offcuts.
- **Manual may already be better:** the nesting team's claim is unverified, not false. Test it fairly; keep manual planning if it wins. Strumis is confirmed, but its configuration, exports and machine constraints are not.
- **Revisions and holds distort the result:** invalidate stale plans, log change-driven losses separately and exclude unreleased demand. A recovered client claim is not a nesting saving.

The notes also quote 7,000–8,000 tonnes/month against 80,000 tonnes/year capacity; these do not reconcile as a simple annual average. Obtain actual eligible throughput rather than annualising capacity. This proposal is based on both discovery calls; machine details and financial inputs remain assumptions.

The next decision is whether the baseline and feasible opportunity justify completing this small pilot. It is too early to promise a percentage reduction across the whole factory.
