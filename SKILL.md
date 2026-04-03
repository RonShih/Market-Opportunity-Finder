---
name: market-opportunity-finder
description: Scan a market landscape, analyze competitors, map positioning gaps, and find unmet needs to identify startup opportunities matched to a team's strengths. Use this skill when someone wants to explore a market before committing to a specific idea, needs competitive landscape analysis, wants to find white space or blue ocean opportunities, asks for a quadrant/positioning map, says things like "where should we start a business", "what opportunities exist in X", "help me find a startup direction", "analyze the competitive landscape for X", or wants to understand market gaps. Also trigger when someone has a team and wants to figure out what to build, or wants to compare players in a space to find underserved areas. This skill is the "upstream" exploration tool — use it BEFORE startup-design, which validates a specific idea.
---

# Market Opportunity Finder

A structured skill that scans a market landscape, analyzes competitive dynamics, and identifies unmet needs — then matches opportunities to a team's unique strengths. Produces markdown analysis files and an interactive React quadrant chart.

This skill sits **upstream** of idea validation. It answers "where should we play?" rather than "will this specific idea work?"

## How It Works

Two modes, same destination:

**Mode A — Direction-first:** The user already has a broad area of interest (e.g., "AI in healthcare", "cross-border e-commerce logistics"). Start from Phase 1 (light team profiling) then dive into market scanning.

**Mode B — Team-first:** The user has no direction yet. Start from Phase 1 (deep team profiling), then recommend 3-5 promising sectors before proceeding.

```
Mode A: Team Profile (light) → Market Scan → Competitor Analysis → Quadrant Map → Gap Analysis → Opportunity Ranking → Action Brief
Mode B: Team Profile (deep) → Sector Recommendation → [User picks 1-2] → Market Scan → ... same as Mode A
```

### Language

Detect the language of the user's first message and use it for all outputs. If the user switches language mid-conversation, follow their lead.

### Progress Tracking

Create `PROGRESS.md` at the project root after Phase 1. Update after each phase. If a session is interrupted, check for `PROGRESS.md` on resume and pick up from the last completed phase.

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

Save to `{project-name}/00-team/team-profile.md`.

For Mode B, after the profile is confirmed, recommend 3-5 sectors with a brief rationale for each (why this sector × this team is interesting). Use web search to validate that these sectors have real activity and aren't purely theoretical. Ask the user to pick 1-2 to explore. Then proceed to Phase 2 with the chosen sectors.

Create `PROGRESS.md` with project name, date, mode, language, and phase checklist.

---

## Phase 2: Market Scan

Define the playing field. The goal is to see the full landscape before zooming into competitors.

### Step 1: Define the Arena

Start by clearly defining:
- **The big market** (the broadest category, e.g., "HR Tech")
- **The problem space** (the specific pain area, e.g., "employee onboarding")
- **Adjacent spaces** that could be relevant (e.g., "LMS", "internal comms tools")

### Step 2: Sub-segment Mapping

Break the market into sub-segments along multiple dimensions. Use web search to validate these aren't just theoretical categories — real companies or products should exist (or notably NOT exist) in each.

Dimensions to consider (pick the 3-4 most relevant):
- **Service target:** B2B / B2C / B2B2C / B2G
- **Value chain position:** upstream (infrastructure) / midstream (platform) / downstream (application)
- **Technology approach:** AI-native / SaaS / marketplace / hardware / hybrid
- **Customer size:** enterprise / SMB / consumer / prosumer
- **Geographic scope:** local / regional / global
- **Maturity:** established players / emerging / greenfield

### Step 3: Market Sizing

For each meaningful sub-segment, research:
- Estimated market size (TAM/SAM if available)
- Growth trajectory (growing / stable / declining)
- Funding activity (are VCs investing here?)
- Number of notable players
- Maturity level (nascent / growth / mature / declining)

### Web Search Requirements

Perform **5-8 web searches minimum** for this phase. Cross-reference findings across 2+ sources. Date all data and flag anything older than 18 months. Quantify where possible — "$4.2B at 12.3% CAGR" not "the market is growing."

### Output

Save to `{project-name}/01-landscape/market-map.md`:
- Arena definition
- Sub-segment map (table format with dimensions as columns)
- Market sizing summary per sub-segment
- Heat map: which sub-segments are hot (lots of activity) vs. cold (sparse)
- Initial observations: any surprising gaps or overcrowded zones?

Update PROGRESS.md.

---

## Phase 3: Competitor Deep-Dive

Now zoom in. Identify and analyze the key players across the landscape.

> **Reference:** Read `references/competitor-analysis.md` for the detailed analysis template, comparison matrix format, and future trajectory framework.

### Step 1: Identify Players

Compile a list of 8-15 relevant companies/products across the sub-segments from Phase 2. Include:
- Direct competitors (solving the same problem for the same customer)
- Indirect competitors (solving the same problem differently, or a related problem)
- Adjacent players (could easily expand into this space)

Use web search extensively — don't rely on memory alone. Search for recent funding rounds, product launches, and industry reports.

### Step 2: Individual Profiles

For each company, research and document:
- Core product/service and how it works
- Target customer (be specific: not "businesses" but "mid-size e-commerce brands doing $1-10M ARR")
- Business model (how they make money, pricing if public)
- Funding stage and amount (if available)
- Team size / company maturity
- Key differentiator (what they'd say makes them unique)
- Observed weaknesses or complaints (from reviews, forums, social media)
- Recent moves (product launches, pivots, partnerships in last 12 months)

### Step 3: Comparison Matrix

Build a structured comparison table across all players with columns for the most relevant dimensions. This table is the foundation for the quadrant chart in Phase 4.

### Step 4: Similarities & Differences Analysis

This is where insight happens — don't just list facts, find patterns:

**Similarities (The Consensus)**
- What are ALL these companies doing the same way?
- What assumptions do they all share?
- What customer segments do they all target?
- Critical question: **Is this consensus correct, or is it groupthink?**

**Differences (Strategic Divergence)**
- Where do companies make fundamentally different bets?
- Pricing strategy differences and what they imply
- Technology approach differences
- GTM strategy differences
- What can we learn from the outliers?

### Step 5: Future Trajectory

For each major player, project their likely next 1-2 years:
- Most probable expansion direction (upstream? downstream? new geo? new segment?)
- Likely product evolution based on current trajectory and hiring patterns
- Potential collision courses (which companies will start competing with each other?)
- Acquisition targets or acquirers

### Output

- `{project-name}/01-landscape/competitor-profiles.md` — individual profiles
- `{project-name}/01-landscape/comparison-matrix.md` — structured comparison table
- `{project-name}/01-landscape/trajectory-analysis.md` — future path projections

Update PROGRESS.md.

---

## Phase 4: Quadrant Map

The most visual and insight-dense deliverable. The goal is not just to plot companies — it's to reveal where the opportunities are.

> **Reference:** Read `references/quadrant-chart-template.md` for the React component template and axis selection guide.

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

**Explain your reasoning** for why these two axes were chosen. What insight does this particular view unlock that other views wouldn't?

### Step 2: Plot Companies

Place each company from Phase 3 on the quadrant. For each placement, provide a brief justification.

### Step 3: Identify White Space

For each empty or sparse quadrant:
- **Is it empty because nobody's tried?** → Potential opportunity
- **Is it empty because it's structurally impossible?** → Not an opportunity (explain why)
- **Is it empty because it's not valuable enough?** → Probably not an opportunity (but question whether market conditions have changed)
- **Is it sparsely populated with weak players?** → Potential opportunity to do it better

### Step 4: Generate Interactive Chart

Create an interactive React component (saved as `.jsx` file) that:
- Plots all companies as labeled dots on a 2D quadrant
- Highlights empty quadrants with a subtle overlay
- Shows company details on hover (name, one-line description, funding, key differentiator)
- Allows axis labels to be visible
- Marks the "opportunity zones" identified in Step 3
- Uses clean, professional styling

If multiple axis pairs are insightful, generate 2-3 chart variants the user can compare.

### Output

- `{project-name}/02-analysis/quadrant-analysis.md` — axis rationale, company placements, white space analysis
- `{project-name}/02-analysis/quadrant-chart.jsx` — interactive React component

Update PROGRESS.md.

---

## Phase 5: Gap Analysis (Unmet Needs)

This is the core value of the entire skill. Systematically identify what's missing in the market.

> **Reference:** Read `references/gap-analysis-framework.md` for the 5-lens framework with examples and scoring criteria.

### The 5 Lenses

Analyze gaps through each lens. Not every lens will yield insights for every market — spend time where the opportunities are richest.

**Lens 1: User Pain Gaps**
What problems do current solutions fail to solve well?
- Mine user reviews, Reddit, forums, social media for complaints
- Look for workarounds people build (spreadsheets, manual processes, duct-tape solutions)
- Identify "table stakes" features that are surprisingly missing or poorly executed
- Note recurring frustrations: slow support, bad UX, inflexible pricing, poor integrations

**Lens 2: Value Chain Gaps**
Where in the value chain is there no good solution?
- Map the full workflow from end to end
- Identify handoff points where data is lost or processes break
- Look for steps that are still manual, expensive, or error-prone
- Consider: who is the underserved player in the value chain? (not the end user, but the distributor, the supplier, the service provider)

**Lens 3: Customer Segment Gaps**
Who is being ignored?
- Too small for enterprise solutions, too complex for consumer tools
- Specific verticals underserved by horizontal platforms
- Emerging customer types (new job roles, new business models)
- Geographic markets where global players don't localize well
- Non-obvious segments: "the customer's customer"

**Lens 4: Timing Gaps**
What's newly possible that wasn't before?
- New technology enablers (AI capabilities, API ecosystems, infrastructure cost drops)
- Regulatory changes creating new needs or removing barriers
- Behavioral shifts (post-pandemic, generational, cultural)
- Market structure changes (consolidation, unbundling, platform shifts)
- Ask: "Why now?" — if there's no good answer, it's probably not a timing gap

**Lens 5: Business Model Gaps**
Can the same problem be solved with a radically different model?
- Subscription where everyone charges per-seat
- Usage-based where everyone charges flat rate
- Marketplace where everyone sells direct
- Open-source where everything is proprietary
- Productized service where everything is pure software
- Reverse the revenue model: charge the other side of the transaction

### Synthesis

After examining all 5 lenses, compile the most promising gaps. For each:
- Name it clearly (e.g., "SMB onboarding automation gap")
- Describe the unmet need in 2-3 sentences
- Estimate the severity (how painful is this for the affected users?)
- Estimate the size (how many people/companies are affected?)
- Note any barriers to filling this gap

### Output

Save to `{project-name}/02-analysis/unmet-needs.md`.

Update PROGRESS.md.

---

## Phase 6: Opportunity Scoring

Match the gaps found in Phase 5 against the team profile from Phase 1. The best opportunity is where market need and team capability intersect.

### Scoring Framework

For each promising gap, score on two axes (1-10 each):

**Market Attractiveness**
- Problem severity: How painful is this? (1 = minor annoyance, 10 = hair-on-fire)
- Market size: How many potential customers? (1 = niche, 10 = massive)
- Timing: Is this the right moment? (1 = too early/late, 10 = perfect window)
- Competition: How defensible is entry? (1 = Red Ocean, 10 = Blue Ocean)
- Monetization clarity: Is willingness to pay obvious? (1 = unclear, 10 = proven)

**Team Fit**
- Technical match: Can this team build it? (1 = totally outside skillset, 10 = perfect fit)
- Domain match: Does the team understand this space? (1 = zero context, 10 = deep expertise)
- Resource match: Can they afford to pursue it? (1 = way beyond means, 10 = well within reach)
- Passion match: Would this team enjoy working on this? (1 = dread, 10 = obsessed)
- Unfair advantage: Does the team have something unique? (1 = nothing special, 10 = strong moat)

### Output

Save to `{project-name}/03-opportunities/opportunity-scorecard.md`:
- Scoring table with all opportunities ranked
- Top 2-3 opportunities highlighted with detailed rationale
- For each top opportunity: why it scores high, what the biggest risk is, what would need to be true for it to work
- Visual: a simple 2×2 of Market Attractiveness vs. Team Fit with opportunities plotted

Update PROGRESS.md.

---

## Phase 7: Action Brief

For each of the top 2-3 opportunities, produce a concise action brief. This is not a business plan — it's a "just enough to start testing" document.

### Per Opportunity

- **One-line pitch:** What is this, for whom, and why now?
- **Entry wedge:** What's the smallest version you could build to test demand?
- **First customers:** Who are the first 10 customers and how do you reach them?
- **MVP sketch:** What does the minimum viable product look like? (features, NOT a product spec)
- **Biggest risk:** What's the single assumption that, if wrong, kills this?
- **30-day test:** How would you validate this in 30 days with minimal spend?
- **Startup-design handoff note:** If validated, what information from this analysis carries forward into deeper planning

### Final Recommendation

End with a clear, opinionated recommendation:
- Which opportunity to pursue first and why
- What to do this week (3 concrete actions)
- What would make you pivot to opportunity #2 instead

### Output

Save to `{project-name}/03-opportunities/action-brief.md`.

Mark all phases complete in PROGRESS.md.

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
| `references/quadrant-chart-template.md` | Before Phase 4 | React component template and axis selection guide |
| `references/gap-analysis-framework.md` | Before Phase 5 | 5-lens framework with examples and scoring rubric |