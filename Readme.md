# Opportunity Finder

A structured skill that scans a market landscape, analyzes competitive dynamics, and identifies unmet needs — then matches opportunities to a team's unique strengths. Produces a single self-contained interactive HTML report (viewable in any browser) that assembles all phase outputs into a tabbed interface.

This skill sits **upstream** of idea validation. It answers "where should we play?" rather than "will this specific idea work?"

## ⚠️ Execution Rules (CRITICAL)

**These rules override all other behavior. Read them before starting.**

### Rule 1: Complete ALL 8 Phases — No Skipping

You MUST execute every single phase from Phase 1 through Phase 8, in order. Do NOT skip, merge, or abbreviate any phase. If a phase feels redundant based on the user's input — do it anyway. Each phase builds on the previous one, and skipping creates blind spots.

If the conversation is running long, tell the user "I need to continue in the next message" and keep going. Never say "I'll skip Phase X to save time" or "Phases Y and Z can be combined." They cannot.

**Checkpoint:** After completing each phase, explicitly state:
> ✅ Phase N complete. Moving to Phase N+1.

### Rule 2: Every Analysis Comes From THIS Conversation Only

Do NOT reference, recall, or assume information from any previous conversation, chat history, or prior session. Treat every execution of this skill as if it's the first time you've ever seen this user and this topic.

- If the user says "as we discussed before" → ask them to re-state the information here
- If the user's project files contain prior analysis → read them fresh, do not assume you "remember" them
- All web searches must be performed fresh — do not rely on cached knowledge from other sessions

### Rule 3: Go Deep Where It Matters

Spend the most effort on Phase 2 (market structure), Phase 3 (competitor deep-dive + VC thesis), Phase 4 (positioning), and Phase 5 (gap analysis). These are the analytical core — **there is no length limit on these phases**. Write as much as needed to be thorough. If a competitor profile takes 500 words, write 500 words. If a gap analysis lens yields 10 specific findings, list all 10. Do not truncate, summarize prematurely, or say "and more" — be exhaustive.

Phase 6 and 7 are synthesis — keep them concise and action-oriented, don't repeat analysis already done.

### Rule 4: Web Search is Mandatory, Not Optional

Phases 2, 3, 4, and 5 REQUIRE web search. Do not rely on training data alone. If web search fails, clearly mark all outputs as **[Knowledge-Based — verify independently]**.

### Rule 5: Always Explain the Business Logic

Every analysis must answer "so what?" from a business perspective. Do NOT just describe — explain WHY it matters commercially:
- Phase 2: Don't just list sub-tracks — explain why value flows this way, where money concentrates, and where the economic bottleneck is
- Phase 3: Don't just profile companies — explain why each competitor's business model works (or doesn't), what makes their unit economics viable, why customers pay them specifically
- Phase 4: Don't just plot dots — explain why each quadrant represents a different business strategy, and why the empty zone is commercially viable (or not)
- Phase 5: Don't just list gaps — explain who would pay to fill each gap, how much, and why they can't solve it themselves
- Phase 6-7: Every recommendation must have a commercial rationale, not just a technical one

---

## How It Works

Two modes, same destination:

**Mode A — Direction-first:** The user already has a broad area of interest (e.g., "AI in healthcare", "cross-border e-commerce logistics"). Start from Phase 1 (light team profiling) then dive into market scanning.

**Mode B — Team-first:** The user has no direction yet. Start from Phase 1 (deep team profiling), then recommend 3-5 promising sectors before proceeding.

```
Mode A: Team Profile (light) → Market Scan → Competitor Analysis → Quadrant Map → Gap Analysis → Opportunity Ranking → Action Brief → HTML Report
Mode B: Team Profile (deep) → Sector Recommendation → [User picks 1-2] → Market Scan → ... same as Mode A
```

### Language

Detect the language of the user's first message and use it for all outputs. If the user switches language mid-conversation, follow their lead.

### Progress Tracking

If a session is interrupted mid-analysis, optionally create `PROGRESS.md` to track which phases are complete, so the next session can resume from the right point.

---

## Phase 1: Team Profile

Everything downstream depends on understanding who's doing the building. A brilliant opportunity for the wrong team is a trap.

### Mode Detection

If the user provides a market/industry direction in their opening message → **Mode A** (light profile).
If the user asks "what should we build" or has no clear direction → **Mode B** (deep profile).

### Interview (Mode A — Light)

Ask 3-5 questions in one round, covering:
- Team composition: who's on the team, what are the core skills?
- Domain expertise: what industries have you worked in?
- Resources: budget range, full-time or side project, timeline expectations?
- Constraints: anything you refuse to do? (e.g., no hardware, no regulated industries)

### Interview (Mode B — Deep)

This requires more nuance because you're using the answers to generate sector recommendations. Ask in 2-3 rounds:

**Round 1 — Capabilities**
- Technical strengths (specific: "React + Python + ML" not just "engineering")
- Non-technical strengths (sales, design, ops, domain knowledge)
- Past work experience — what industries, what roles, what problems did you solve?
- Unique assets: patents, datasets, partnerships, audience, distribution channels?

**Round 2 — Preferences & Patterns**
- What kind of work energizes you vs. drains you?
- B2B or B2C preference? Or no preference?
- Comfort with sales cycles? (enterprise = long, consumer = short but high volume)
- Geographic focus or advantage?
- What problems have you personally experienced and wished someone would solve?

**Round 3 — Constraints & Ambition**
- Budget and runway
- Risk tolerance (bootstrapping vs. seeking funding)
- Timeline: when do you need revenue?
- Hard no's: industries or business models you won't touch
- Scale ambition: lifestyle business or venture-scale?

After the interview, summarize the team profile back to the user for confirmation.

### Output

Present the team profile summary in the conversation for user confirmation. The summary must include:
- **Team roster**: Each member's role, technical background, relevant industry experience, and unique assets
- **Collective strengths**: What this team can do that most teams cannot (be specific)
- **Collective gaps**: What's missing — sales experience? Domain knowledge? Design capability?
- **Resource reality**: Full-time vs. part-time, runway estimate, timeline pressure
- **Constraints**: Hard no's and soft preferences
- **Target**: Accelerator goal, revenue target, or other success metric

For Mode B, after the profile is confirmed, recommend 3-5 sectors with a brief rationale for each (why this sector × this team is interesting). Use web search to validate that these sectors have real activity and aren't purely theoretical. Ask the user to pick 1-2 to explore. Then proceed to Phase 2 with the chosen sectors.

> ✅ After completing Phase 1, state: "Phase 1 complete. Moving to Phase 2: Market Scan."

---

## Phase 2: Market Scan

Define the playing field using a **zoom-in structure**: start from the broadest view, then progressively narrow down.

**🔑 Business logic focus:** Don't just map categories — explain where revenue concentrates in the value chain, where margins are highest, where switching costs create lock-in, and where the economic bottleneck sits. The user needs to understand the MONEY flow, not just the data flow.

### Step 1: Position the Main Track

First, place this market in context — where does it sit in the broader tech/industry landscape?

- **Name the main track** (e.g., "AI Document Intelligence", "DevOps Tooling", "FinTech Infrastructure")
- **Name 3-5 adjacent tracks** that this track borders or overlaps with (e.g., if the main track is "AI Document Intelligence", adjacent tracks might be "Enterprise Search", "RPA/IDP", "Data Integration/ETL", "RAG Frameworks")
- **Draw the relationship**: is this main track upstream (feeds into), downstream (consumes from), or parallel to each adjacent track?

Present this as a **landscape positioning map** — a simple diagram or structured description showing how the main track relates to its neighbors. This gives the user (and later, investors) an instant mental model of where the opportunity sits.

### Step 2: Sub-track Mapping (Value Chain View)

Within the main track, break it into sub-tracks organized by **how value flows** — not just as a flat list of categories. Think of it as a pipeline:

```
[Upstream] → [Midstream] → [Downstream]
Raw input      Processing     Application
```

For each sub-track:
- **Position in the flow**: Is it upstream (data ingestion, raw processing), midstream (platform, orchestration), or downstream (end-user application)?
- **What it feeds into / receives from**: Which other sub-tracks does it connect to?
- **Representative players**: 2-5 companies that exist here
- **Heat level**: How crowded and active is this sub-track? (1-5)

Also map sub-tracks along other relevant dimensions (pick 2-3):
- **Technology approach:** AI-native / SaaS / marketplace / hardware / hybrid
- **Customer size:** enterprise / SMB / developer
- **Open-source vs. commercial**
- **Geographic concentration**

The goal is that someone reading this immediately understands: "data flows from A → B → C, and the bottleneck is at B."

### Step 3: Market Sizing

For each meaningful sub-track, research:
- Estimated market size (TAM/SAM if available)
- Growth trajectory (growing / stable / declining)
- Funding activity (are VCs investing here?)
- Number of notable players
- Maturity level (nascent / growth / mature / declining)

### Web Search Requirements

Perform **5-8 web searches minimum** for this phase. Cross-reference findings across 2+ sources. Date all data and flag anything older than 18 months. Quantify where possible — "$4.2B at 12.3% CAGR" not "the market is growing."

### Output

Present in the conversation (ALL of the following — do not skip any):

**1. Landscape Positioning Map**
- Name the main track clearly
- List 3-5 adjacent tracks with their relationship (upstream/downstream/parallel)
- For each adjacent track, name 1-2 representative companies so the reader instantly understands what it is

**2. Value Chain Flow**
- Draw the upstream → midstream → downstream pipeline with named sub-tracks at each stage
- For each sub-track: position, what it feeds into, what it receives, 2-5 named companies, heat level (1-5)
- Explicitly identify where the bottleneck or weakest link is

**3. Market Sizing Table**
- One row per sub-track: name, TAM/SAM estimate, CAGR, funding activity level, player count, maturity stage
- Flag which numbers are [Data] vs [Estimate]

**4. Heat Assessment**
- Which sub-tracks are overcrowded (5+ well-funded players)?
- Which sub-tracks are sparse (0-1 notable players)?
- Which sub-tracks are growing fastest?

**5. Initial Observations**
- Any surprising gaps? Overcrowded zones? Structural bottlenecks?
- What would you tell a friend in 2 sentences about this market?

> ✅ After completing Phase 2, state: "Phase 2 complete. Moving to Phase 3: Competitor Deep-Dive."

---

## Phase 3: Competitor Deep-Dive

Now zoom in. Identify and analyze the key players across the landscape.

**🔑 Business logic focus:** For every competitor, explain the commercial engine — not just what the product does, but WHY customers pay, HOW they make money per unit, and WHAT makes the business defensible. The VC thesis section is where this matters most: investors bet on business logic, not features.

> **Reference:** Read `references/competitor-analysis.md` for the detailed analysis template, comparison matrix format, and future trajectory framework.

### Step 1: Identify Players

Compile a list of 8-15 relevant companies/products across the sub-tracks from Phase 2. Include:
- Direct competitors (solving the same problem for the same customer)
- Indirect competitors (solving the same problem differently, or a related problem)
- Adjacent players (could easily expand into this space)

Use web search extensively — don't rely on memory alone. Search for recent funding rounds, product launches, and industry reports.

### Step 2: Individual Profiles

For EACH company (not a subset — every single one identified in Step 1), research and document ALL of the following:

**Product & Market**
- Core product/service: what does it actually do? (describe fully, not buzzwords — explain the product as if the reader has never heard of it)
- How it works technically: what's the architecture? API-based? On-premise? Open-source core?
- Target customer: be hyper-specific (not "businesses" but "mid-size e-commerce brands doing $1-10M ARR who need to process 10K+ invoices/month")
- Pricing model: freemium? per-seat? per-page? usage-based? If public, include actual numbers.

**Company Status**
- Founded when? Where?
- Team size (approximate)
- Funding: stage, total amount, lead investors
- Revenue signals: any public ARR, customer count, or growth metrics?
- Recent moves in last 12 months: product launches, pivots, partnerships, key hires

**Strengths & Weaknesses**
- Key differentiator: what would THEY say makes them unique? (use their own language from website/blog)
- Observed weaknesses: search G2/Capterra reviews, Reddit complaints, HN threads, Twitter/X criticism
- What do customers wish it did better?

### Step 3: VC Investment Thesis (Critical)

This is what separates shallow analysis from actionable intelligence. For each funded competitor, research and explain:

**Origin Story** — How did this company start?
- Was it a pivot from something else? A weekend side project? A PhD research spinoff?
- What was the "aha moment" that revealed the opportunity?
- Search for founder interviews, podcast appearances, First Round Review-style articles, YC launch posts

**Secret Sauce** — What makes this company defensible?
- Is it a technical moat (proprietary model, unique dataset, system-level innovation)?
- Is it a distribution moat (open-source community, ecosystem integrations, government connections)?
- Is it a timing moat (first to market when a new technology became viable)?

**Why VCs Invested** — What thesis did the investor articulate?
- Search for investor quotes from funding announcements, press releases, blog posts
- What signal did the VC see that made them write the check? (e.g., "organic pull from YC batch-mates", "10x better accuracy than incumbents", "80% of enterprise data is untapped")
- Was it a bet on the team, the market, the technology, or the traction?

**What the team had at funding time** — What was the state of the product/company when money came in?
- Did they have revenue? Users? Just a prototype? Just a thesis?
- This reveals how early/late different investors are willing to bet in this space

Use web search to find GP quotes, investor blog posts, and press coverage. If no public information exists, mark as **[No public VC thesis found]** — the absence of information is itself a signal (stealth mode, or too early for coverage).

### Step 4: Comparison Matrix

Build a structured comparison table across ALL players. The table must include:
- Company name
- Sub-track position (from Phase 2)
- Funding total
- 3-5 numeric dimension scores (1-5 scale) — choose dimensions that matter most for THIS market (e.g., technical depth, language support, speed, enterprise-readiness, open-source strength)
- One-line differentiator

Name each dimension explicitly. These dimension scores become the axes candidates for Phase 4 quadrant charts.

### Step 5: Similarities & Differences Analysis

This is where insight happens — don't just list facts, find patterns:

**Similarities (The Consensus)**
- What are ALL these companies doing the same way?
- What assumptions do they all share?
- What customer segments do they all target?
- What technology choices do they all make?
- Critical question: **Is this consensus correct, or is it groupthink?** Explain why.

**Differences (Strategic Divergence)**
- Where do companies make fundamentally different bets?
- Pricing strategy differences and what they imply about market assumptions
- Technology approach differences (e.g., proprietary model vs. open-source vs. API wrapper)
- GTM strategy differences (sales-led vs. PLG vs. open-source community)
- What can we learn from the outliers — the companies doing something nobody else does?

### Step 6: Future Trajectory

For each major player (at least the top 5 by funding), project their likely next 1-2 years:
- Most probable expansion direction (upstream? downstream? new geo? new segment?)
- Likely product evolution based on current trajectory, blog posts, job postings, and hiring patterns
- Potential collision courses (which companies will start competing with each other?)
- Acquisition likelihood: who might get bought, and by whom?

### Output

Present in the conversation (ALL of the following):
- Individual competitor profiles with full VC investment thesis for each funded company
- Comparison matrix table with numeric dimension scores
- Similarities & differences analysis with the groupthink challenge
- Future trajectory projections for top 5+ players

> ✅ After completing Phase 3, state: "Phase 3 complete. Moving to Phase 4: Quadrant Map."

---

## Phase 4: Quadrant Map

The most visual and insight-dense deliverable. The goal is not just to plot companies — it's to reveal where the opportunities are.

**🔑 Business logic focus:** Each quadrant represents a different business strategy with different economics. When analyzing white space, don't just say "nobody is here" — explain whether a business in that zone would have viable unit economics, who would pay, and why incumbents haven't moved there (can't? won't? haven't noticed?).

> **Reference:** Read `references/quadrant-chart-template.md` for the HTML/JS component template and axis selection guide.

### Step 0: Determine Quadrant Strategy

Before choosing axes, decide how many quadrants are needed based on the competitive landscape:

**Case A — Single main track:** All competitors operate in the same main track (e.g., all are "Document AI" companies, just in different sub-tracks). Generate **one quadrant** that plots sub-track positions and reveals gaps within the track.

**Case B — Multiple main tracks:** Competitors span 2+ distinct main tracks (e.g., some are "Document AI", others are "Data Integration", others are "Enterprise Search"). Generate:
1. **One quadrant per main track** — showing sub-track positions within each track
2. **One cross-track quadrant** — zooming out to show how all main tracks relate, with opportunity zones at track intersections

Explain which case applies and why.

### Step 1: Select Axes

Choose the two dimensions that **best reveal strategic gaps** in this specific market. Don't default to lazy axes like "price vs. features."

Consider these dimension pairs (pick the most insightful for THIS market):
- Automation depth vs. Human touch
- Vertical specialization vs. Horizontal platform
- Self-serve vs. Sales-led
- Point solution vs. Full suite
- Incumbent-friendly vs. Disruptive
- Technical sophistication vs. Ease of use
- Current market vs. Emerging market
- Standardized vs. Customizable

For multi-track quadrants (Case B), each track-specific quadrant should use axes relevant to THAT track. The cross-track quadrant should use higher-level axes that differentiate across tracks.

**Explain your reasoning** for why these axes were chosen. What insight does this particular view unlock that other views wouldn't?

### Step 2: Plot Companies

Place each company from Phase 3 on the appropriate quadrant(s). For each placement, explain the reasoning — why this position and not somewhere else.

### Step 3: Identify White Space

For each empty or sparse quadrant:
- **Is it empty because nobody's tried?** → Potential opportunity
- **Is it empty because it's structurally impossible?** → Not an opportunity (explain why)
- **Is it empty because it's not valuable enough?** → Probably not an opportunity (but question whether market conditions have changed)
- **Is it sparsely populated with weak players?** → Potential opportunity to do it better

For cross-track quadrants (Case B): look specifically at **track intersection zones** — areas where capabilities from two tracks could combine into something new.

### Step 4: Prepare Chart Data

Structure each quadrant view as a JS data object for embedding in the final HTML report. Each view needs: title, axis labels, corner labels, dot positions (x/y 0-100), dot sizes, colors, and opportunity zone coordinates. The HTML report will render all views as switchable tabs.

### Output

Present in the conversation:
- Quadrant strategy explanation (Case A or B, and why)
- Axis rationale per quadrant
- Company placements with justifications
- White space analysis
- The quadrant data (views, dots, zones) for Phase 8 HTML embedding

> ✅ After completing Phase 4, state: "Phase 4 complete. Moving to Phase 5: Gap Analysis."

---

## Phase 5: Gap Analysis (Unmet Needs)

This is the core value of the entire skill. Systematically identify what's missing in the market.

**🔑 Business logic focus:** A gap is only an opportunity if someone would PAY to fill it. For every gap identified, answer: who is the buyer? What's their budget? Are they already spending money on a bad workaround (validated willingness to pay)? A painful problem with no budget is a charity project, not a startup.

> **Reference:** Read `references/gap-analysis-framework.md` for the 5-lens framework with examples and scoring criteria.

### The 5 Lenses

Analyze gaps through EACH lens — do not skip any lens. For each lens, provide at least 2-3 specific, named gaps with evidence. If a lens genuinely yields nothing, explain why (don't just skip it silently).

**Lens 1: User Pain Gaps**
What problems do current solutions fail to solve well?
- Mine user reviews on G2, Capterra, Product Hunt — focus on 2-3 star reviews (1 star = rage, 4-5 star = generic praise, the middle reveals real friction)
- Search Reddit, HN, Twitter/X for "[competitor name] alternative", "[problem] frustrating", "wish there was"
- Look for workarounds: people building spreadsheets, Zapier automations, or manual processes to compensate for tool gaps
- Identify "table stakes" features that are surprisingly missing or poorly executed
- Note recurring frustrations: slow support, bad UX, inflexible pricing, poor integrations
- **For each pain gap**: estimate Frequency (how many people mention it), Severity (inconvenience vs. business-critical), and how poorly served it is by current solutions

**Lens 2: Value Chain Gaps**
Where in the value chain is there no good solution?
- Map the FULL workflow from end to end (use the value chain from Phase 2)
- Identify specific handoff points where data is lost or processes break — name the tools on either side
- Look for steps that are still manual, expensive, or error-prone
- Consider: who is the underserved player in the value chain? (not the end user, but the distributor, the supplier, the service provider)
- **Common patterns to look for**: The Glue Gap (two great tools but connecting them is manual), The Translation Gap (data exists in wrong format), The Last Mile Gap (output needs heavy post-processing)

**Lens 3: Customer Segment Gaps**
Who is being ignored?
- The "sandwich segment": too big for tools built for individuals, too small for enterprise solutions
- Specific verticals underserved by horizontal platforms — name the verticals
- Emerging customer types (new job roles, new business models that didn't exist 3 years ago)
- Geographic markets where global players don't localize well — which regions, which languages?
- Non-obvious segments: "the customer's customer"
- **For each segment gap**: is this segment growing or shrinking? Do they have budget?

**Lens 4: Timing Gaps**
What's newly possible that wasn't before?
- New technology enablers: what specific AI/infra capability matured in the last 12-18 months?
- Regulatory changes creating new needs or removing barriers — cite specific regulations
- Behavioral shifts (post-pandemic, generational, cultural) — with evidence
- Market structure changes (consolidation, unbundling, platform shifts)
- **The "Why Now?" test**: for each timing gap, state (1) what specifically changed, (2) when it changed, (3) why incumbents haven't adapted yet. If you can't answer all three, it's not a real timing gap.

**Lens 5: Business Model Gaps**
Can the same problem be solved with a radically different model?
- Subscription where everyone charges per-seat
- Usage-based where everyone charges flat rate
- Marketplace where everyone sells direct
- Open-source where everything is proprietary
- Productized service where everything is pure software
- Reverse the revenue model: charge the other side of the transaction
- **For each model gap**: does this model align incentives better? Does it lower barriers to trying?

### Synthesis

After examining ALL 5 lenses, compile the most promising gaps into a ranked list. For EACH gap:
- **Name it clearly** (e.g., "SMB onboarding automation gap" — not "there's an opportunity")
- **Describe the unmet need** fully — what's broken, for whom, and what the current workaround is
- **Estimate severity**: How painful is this for affected users? (minor inconvenience → business-critical)
- **Estimate size**: How many people/companies are affected?
- **Note barriers**: What makes this gap hard to fill? (technology, regulation, unit economics, chicken-and-egg)
- **Tag which lenses** identified this gap (some gaps show up across multiple lenses — those are stronger signals)

### Output

Present the FULL gap analysis in the conversation:
- Analysis per lens (with specific named gaps, evidence, and scoring)
- Synthesized gap ranking table
- Flags section (red flags and yellow flags)

> ✅ After completing Phase 5, state: "Phase 5 complete. Moving to Phase 6: Opportunity Scoring."

---

## Phase 6: Opportunity Scoring

Quick scoring to rank the gaps from Phase 5. Don't overthink — this is a prioritization tool, not a thesis defense.

Score each gap on **Market Attractiveness** (problem severity, market size, timing, competition, monetization clarity) and **Team Fit** (technical match, domain match, resource match, passion, unfair advantage), both 1-10. Present as a table, highlight top 2-3, state the biggest risk for each.

> ✅ After completing Phase 6, state: "Phase 6 complete. Moving to Phase 7: Action Brief."

---

## Phase 7: Action Brief

For the top 2-3 opportunities, provide enough to start testing. Keep it short and concrete.

Per opportunity: one-line pitch, entry wedge (smallest thing to build), first 10 customers (who + how to reach them), MVP features (3-5 items), biggest risk as a testable hypothesis, 30-day validation plan (week-by-week).

End with a clear recommendation: which one to pursue first, 3 things to do this week, and what evidence would trigger a pivot to #2.

> ✅ After completing Phase 7, state: "Phase 7 complete. Moving to Phase 8: HTML Report."

---

## Phase 8: HTML Report

Generate a single self-contained HTML file that embeds all Phase 1-7 analysis. This is the only file output of the entire skill.

> **Reference:** Read `references/html-report-template.md` for the HTML template, CSS, and assembly instructions.

### Readability Requirements (CRITICAL)

The HTML report will be shared with teammates, mentors, and potentially investors. It must be **pleasant to read**, not just functional. Follow these rules:

**Typography**
- Use a professional font stack with good CJK support (e.g., Source Sans 3 + Noto Serif TC)
- Body text: 14-15px, line-height 1.7-1.8 — generous spacing for readability
- Headings: clear visual hierarchy (h1 > h2 > h3) with distinct sizes and weights
- Code/data: monospace font for numbers, metrics, and technical terms

**Layout**
- Max content width: 900px, centered — do not stretch to full screen
- Generous padding and whitespace between sections
- Tables must be well-formatted: alternating row hints, aligned columns, clear headers
- No wall-of-text — break content with headings, spacing, and visual separators

**Color & Contrast**
- Dark theme with high contrast text (not gray-on-gray)
- Use accent color sparingly for emphasis (headings, key metrics, links)
- Different visual treatment for: data points, estimates, warnings, opportunities

**Interactive Elements**
- Tab switching must be instant and smooth (CSS animation)
- Quadrant chart: dots must be hoverable with clear labels
- Tables should highlight rows on hover

### How It Works

1. **Collect all analysis content** from the conversation — everything presented in Phases 1-7.
2. **Structure it as tabbed content** — one tab per phase (or group related phases).
3. **Generate `opportunity-report.html`** with this structure:

```
HTML file:
├── marked.js (CDN) — renders markdown in browser
├── Inline CSS — dark theme + markdown typography (must follow readability rules above)
├── Tab bar — one button per phase
├── Tab pages:
│   ├── Tab: Team Profile → Phase 1 content as markdown
│   ├── Tab: Market Scan → Phase 2 content as markdown
│   ├── Tab: Competitors → Phase 3 content as markdown
│   ├── Tab: Quadrant Map → Phase 4 as interactive HTML/JS (not markdown)
│   ├── Tab: Gap Analysis → Phase 5 content as markdown
│   └── Tab: Opportunities & Action → Phase 6+7 content as markdown
└── Script — tab switching, marked.parse(), quadrant renderQ()
```

4. For each markdown tab: embed the analysis text (HTML-escaped) inside `<div class="md-content">`, let `marked.parse()` render it client-side.
5. For the quadrant tab: embed the data as JS objects and the rendering function directly.

### Output

Save to `/mnt/user-data/outputs/opportunity-report.html` and present to user. This is the only file produced by the skill.

> ✅ After completing Phase 8, state: "All 8 phases complete. Your opportunity report is ready."

---

## Honesty Protocol

This skill helps teams make good decisions, not feel validated. Follow these rules:

1. **Label everything.** Use **[Data]**, **[Estimate]**, **[Assumption]**, **[Opinion]** tags. Never present estimates as data.
2. **Surface risks.** Include a **Flags** section at the end of every phase output — red flags (serious concerns) and yellow flags (worth monitoring).
3. **Don't fabricate.** If you can't find data, say "no reliable data found" — don't guess and present it as fact.
4. **Challenge consensus.** If all competitors do something the same way, question whether that's smart or just inertia.
5. **Be direct.** If a market is overcrowded, too small, or poorly timed, say so clearly. The team can disagree, but they should have the honest assessment.

---

## Web Search Protocol

This skill relies heavily on web search for credible analysis.

- **Minimum searches per phase:** Phase 2 (5-8), Phase 3 (8-15), Phase 4 (2-3 for validation), Phase 5 (5-8)
- **Source quality:** Prefer industry reports, company blogs, Crunchbase, SEC filings, and analyst coverage. Use Reddit/forums specifically for customer pain mining in Phase 5.
- **Cross-reference:** Every major claim should be supported by 2+ independent sources.
- **Date everything:** Flag data older than 18 months. Prefer sources from the last 12 months.
- **Handle failure gracefully:** If web search is unavailable, fall back to training knowledge but clearly mark all outputs as **[Knowledge-Based — verify independently]** and reduce confidence ratings by one level.

---

## Reference Files

Read only the file relevant to the current phase.

| File | When to Read | Purpose |
|------|-------------|---------|
| `references/competitor-analysis.md` | Before Phase 3 | Detailed profile template, comparison matrix format, trajectory framework |
| `references/quadrant-chart-template.md` | Before Phase 4 | HTML/JS quadrant component template and axis selection guide |
| `references/gap-analysis-framework.md` | Before Phase 5 | 5-lens framework with examples and scoring rubric |
| `references/html-report-template.md` | Before Phase 8 | HTML shell template, CSS for markdown rendering, assembly instructions |