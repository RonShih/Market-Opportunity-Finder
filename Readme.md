# Opportunity Finder

A skill for Claude that scans market landscapes, maps competitive dynamics, and identifies unmet needs — then matches the best opportunities to your team's unique strengths.

This is the **upstream** exploration tool. Use it *before* you have a startup idea to figure out **where to play**. Once you've picked a direction, hand off to [startup-design](https://github.com/ferdinandobons/startup-skill) to validate and plan.

## Goal

Most founders start with an idea and then look for a market. This skill reverses that. It starts with the market — who's playing, how they're positioned, what's missing — and works backward to find the opportunities that fit your team.

It's built for:
- **Teams exploring a sector** — "We're interested in AI + healthcare. Where are the gaps?"
- **Teams with no direction yet** — "We're three engineers with fintech experience. What should we build?"
- **Anyone doing competitive landscape analysis** — mapping players, finding white space, spotting timing windows

## How It Works

### Two Modes

**Mode A — Direction-first**
You already have a broad area of interest. The skill dives straight into scanning that market.

```
Team Profile (light) → Market Scan → Competitor Analysis → Quadrant Map → Gap Analysis → Opportunity Ranking → Action Brief
```

**Mode B — Team-first**
You don't have a direction yet. The skill interviews your team deeply, then recommends 3-5 promising sectors to explore.

```
Team Profile (deep) → Sector Recommendations → [You pick 1-2] → Market Scan → ... same flow
```

### Seven Phases

| Phase | What Happens | Output |
|-------|-------------|--------|
| 1. Team Profile | Interview to capture skills, experience, resources, constraints, and preferences | `00-team/team-profile.md` |
| 2. Market Scan | Define the arena, map sub-segments, size each one, identify hot vs. cold zones | `01-landscape/market-map.md` |
| 3. Competitor Deep-Dive | Profile 8-15 players, build comparison matrix, analyze consensus vs. divergence, project future trajectories | `01-landscape/competitor-profiles.md` `01-landscape/comparison-matrix.md` `01-landscape/trajectory-analysis.md` |
| 4. Quadrant Map | Auto-select the most insightful axes, plot all players, highlight empty zones, generate interactive React chart | `02-analysis/quadrant-analysis.md` `02-analysis/quadrant-chart.jsx` |
| 5. Gap Analysis | Scan through 5 lenses — user pain, value chain, customer segment, timing, business model | `02-analysis/unmet-needs.md` |
| 6. Opportunity Scoring | Score each gap on market attractiveness × team fit, rank and recommend top 2-3 | `03-opportunities/opportunity-scorecard.md` |
| 7. Action Brief | Entry wedge, MVP sketch, first 10 customers, 30-day validation plan per opportunity | `03-opportunities/action-brief.md` |

### The 5-Lens Gap Analysis

This is the core of the skill — a systematic scan for what's missing:

1. **User Pain Gaps** — What do current solutions fail to solve? Mine reviews, forums, and social media for complaints and workarounds.
2. **Value Chain Gaps** — Where in the workflow is there no good tool? Find the broken handoffs, manual steps, and data loss points.
3. **Customer Segment Gaps** — Who is nobody building for? The "sandwich" segments, vertical orphans, emerging personas, geographic outsiders.
4. **Timing Gaps** — What's newly possible? New AI capabilities, regulatory shifts, behavioral changes, platform disruptions.
5. **Business Model Gaps** — Can the same problem be solved with radically different economics? Subscription → usage-based, direct → marketplace, software → productized service.

### Interactive Quadrant Chart

Phase 4 generates a React component with:
- Company dots plotted on strategically chosen axes
- Hover tooltips with company details
- Highlighted opportunity zones in empty quadrants
- Multiple axis-pair views for different perspectives

### Honesty Protocol

Every output labels claims as **[Data]**, **[Estimate]**, **[Assumption]**, or **[Opinion]**. Each phase ends with red/yellow flags. If a market is overcrowded or poorly timed, the skill says so directly.

## What You Get

A complete set of markdown files organized by phase:

```
{project-name}/
├── PROGRESS.md
├── 00-team/
│   └── team-profile.md
├── 01-landscape/
│   ├── market-map.md
│   ├── competitor-profiles.md
│   ├── comparison-matrix.md
│   └── trajectory-analysis.md
├── 02-analysis/
│   ├── quadrant-analysis.md
│   ├── quadrant-chart.jsx
│   └── unmet-needs.md
└── 03-opportunities/
    ├── opportunity-scorecard.md
    └── action-brief.md
```

The final deliverable is an **action brief** for each top opportunity — not a business plan, but enough to start testing within 30 days.

## Usage

Start a conversation with Claude and describe your situation:

```
We're a team of 3 — two full-stack engineers and one product designer.
We have experience in fintech and e-commerce.
We're interested in exploring opportunities in cross-border payments for SMBs in Southeast Asia.
Help us find where the gaps are.
```

Or if you don't have a direction:

```
We're three engineers with backgrounds in ML and data infrastructure.
We have about $50K to bootstrap and can go full-time.
Help us figure out what to build.
```

The skill picks up the mode automatically and guides you through.

### Resuming a Session

If a session is interrupted, just say:

```
Resume from checkpoint
```

The skill reads `PROGRESS.md` and continues from the last completed phase.

### Connecting to startup-design

Once you've picked a direction, you can take your analysis into [startup-design](https://github.com/ferdinandobons/startup-skill) for full validation:

```
I want to validate the "AI-powered follow-up for solo real estate agents" opportunity.
Here's my previous analysis: [paste from opportunity-scorecard.md]
```

## Installation

### Claude Code CLI

```bash
npx skills add {your-github-username}/opportunity-finder
```

### Manual Install

```bash
git clone https://github.com/{your-github-username}/opportunity-finder.git
cp -r opportunity-finder/.agents/skills/opportunity-finder ~/.agents/skills/
```

## Repository Structure

```
opportunity-finder/
├── SKILL.md                                    # Main skill (7 phases, ~420 lines)
└── references/
    ├── competitor-analysis.md                  # Profile template, comparison matrix, trajectory framework
    ├── quadrant-chart-template.md              # React component template, axis selection guide
    └── gap-analysis-framework.md               # 5-lens methodology with scoring rubrics
```

## License

MIT

---

# Opportunity Finder（繁體中文）

一個 Claude 技能，用來掃描市場格局、分析競爭態勢、找出未被滿足的需求，然後將最佳機會與你團隊的獨特優勢做匹配。

這是一個**上游探索工具**。在你有具體創業點子之前使用，幫你找出「應該往哪裡走」。選定方向後，可以銜接 [startup-design](https://github.com/ferdinandobons/startup-skill) 進行深度驗證和規劃。

## 目標

大多數創業者先有點子，再去找市場。這個 skill 反過來：先看市場——誰在玩、怎麼定位、缺了什麼——再反推出適合你團隊的機會。

適合以下情境：
- **有方向想深入的團隊** —— 「我們對 AI + 醫療有興趣，哪裡有缺口？」
- **還沒方向的團隊** —— 「我們三個工程師有金融科技經驗，該做什麼？」
- **需要競爭格局分析的人** —— 畫象限圖、找白色空間、發現時機窗口

## 怎麼做

### 兩種模式

**模式 A —— 方向先行**
你已有大方向，skill 直接掃描那個市場。

```
團隊簡介（輕量）→ 市場掃描 → 競爭者分析 → 象限圖 → 缺口分析 → 機會排序 → 行動建議
```

**模式 B —— 團隊先行**
你還沒有方向。Skill 會深度訪談團隊，推薦 3-5 個有潛力的賽道讓你選。

```
團隊深度盤點 → 賽道推薦 → [你選 1-2 個] → 市場掃描 → …後續相同
```

### 七個階段

| 階段 | 做什麼 | 產出 |
|------|--------|------|
| 1. 團隊盤點 | 訪談蒐集技能、經驗、資源、限制、偏好 | `00-team/team-profile.md` |
| 2. 市場掃描 | 定義賽道邊界、拆解子賽道、估算規模、標記冷熱區 | `01-landscape/market-map.md` |
| 3. 競爭者深度分析 | 分析 8-15 家公司的 profile、比較矩陣、共識 vs 分歧、未來路徑推演 | `01-landscape/competitor-profiles.md` `01-landscape/comparison-matrix.md` `01-landscape/trajectory-analysis.md` |
| 4. 象限圖 | 自動選最有洞察力的軸、標注所有玩家、高亮空白區、生成互動式 React 圖表 | `02-analysis/quadrant-analysis.md` `02-analysis/quadrant-chart.jsx` |
| 5. 缺口分析 | 五個透鏡掃描——用戶痛點、價值鏈、客群、時機、商業模式 | `02-analysis/unmet-needs.md` |
| 6. 機會評分 | 市場吸引力 × 團隊適配度評分，推薦 Top 2-3 方向 | `03-opportunities/opportunity-scorecard.md` |
| 7. 行動建議 | 每個機會的切入點、MVP 輪廓、前 10 個客戶、30 天驗證計畫 | `03-opportunities/action-brief.md` |

### 五透鏡缺口分析

這是整個 skill 的核心——系統性地掃描市場裡「缺了什麼」：

1. **用戶痛點缺口** —— 現有方案沒解決或解決得差的問題。從評論、論壇、社群媒體挖掘抱怨和土法煉鋼的替代方案。
2. **價值鏈缺口** —— 工作流程中哪個環節沒有好工具？找出斷裂的交接點、手動步驟、資料遺失處。
3. **客群缺口** —— 誰被忽略了？「三明治」客群、垂直孤兒、新興角色、地理邊緣市場。
4. **時機缺口** —— 什麼事情剛剛才變得可行？新 AI 能力、法規變動、行為改變、平台震盪。
5. **商業模式缺口** —— 同樣的問題能否用完全不同的經濟模型解決？訂閱制→用量制、直銷→市集、軟體→產品化服務。

### 互動式象限圖

第 4 階段產出一個 React 元件：
- 根據策略性選擇的軸繪製公司位置
- Hover 顯示公司詳細資訊
- 空白象限標記為機會區域
- 支援切換不同軸組合，看到不同視角

### 誠實協議

每份產出都會標注 **[Data]**、**[Estimate]**、**[Assumption]**、**[Opinion]**。每個階段結尾都有紅旗/黃旗警示。如果市場過度擁擠或時機不對，skill 會直接說出來。

## 產出什麼

一整套按階段組織的 markdown 文件：

```
{project-name}/
├── PROGRESS.md
├── 00-team/
│   └── team-profile.md
├── 01-landscape/
│   ├── market-map.md
│   ├── competitor-profiles.md
│   ├── comparison-matrix.md
│   └── trajectory-analysis.md
├── 02-analysis/
│   ├── quadrant-analysis.md
│   ├── quadrant-chart.jsx
│   └── unmet-needs.md
└── 03-opportunities/
    ├── opportunity-scorecard.md
    └── action-brief.md
```

最終交付物是每個 Top 機會的**行動建議**——不是商業計畫書，而是足以在 30 天內開始驗證的具體方案。

## 使用方式

開啟 Claude 對話，描述你的情況：

```
我們團隊三個人——兩個全端工程師、一個產品設計師。
有金融科技和電商經驗。
想探索東南亞中小企業跨境支付的機會。
幫我們找出缺口在哪裡。
```

或者沒有方向的情況：

```
我們三個工程師，背景是 ML 和資料基礎設施。
有大約 5 萬美金可以 bootstrap，可以全職投入。
幫我們想想該做什麼。
```

Skill 會自動判斷模式，引導你完成流程。

### 中斷恢復

如果對話中斷，只需要說：

```
從上次進度繼續
```

Skill 會讀取 `PROGRESS.md`，從最後完成的階段接著做。

### 銜接 startup-design

選定方向後，把分析結論帶入 [startup-design](https://github.com/ferdinandobons/startup-skill) 做完整驗證：

```
我想驗證「AI 自動跟進工具 for 獨立房仲」這個方向。
這是我之前的分析：[貼上 opportunity-scorecard.md 內容]
```

## 安裝方式

### Claude Code CLI

```bash
npx skills add {your-github-username}/opportunity-finder
```

### 手動安裝

```bash
git clone https://github.com/{your-github-username}/opportunity-finder.git
cp -r opportunity-finder/.agents/skills/opportunity-finder ~/.agents/skills/
```

## License

MIT