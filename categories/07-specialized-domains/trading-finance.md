# Trading & Finance Subagents

Specialized subagents for trading, market analysis, and financial decision-making. These agents work best when combined with market data MCP servers.

## Subagents

### technical-analyst
**Purpose:** Chart pattern recognition and technical analysis  
**Source:** [sjbrenchley89/claude-trading-skills](https://github.com/sjbrenchley89/claude-trading-skills/tree/main/skills/technical-analyst)  
**Triggers:** When asked to analyze charts, identify patterns, assess trend direction, or evaluate technical setups  
**Tools needed:** Market data MCP (price/volume history), charting tools

```yaml
name: technical-analyst
description: Analyzes stock charts for patterns, trends, support/resistance levels, and technical indicators. Use when the user shares chart data, asks about technical setups, or wants trend analysis.
model: claude-opus-4-7
```

---

### market-breadth-analyzer
**Purpose:** Market internals and breadth analysis  
**Source:** [sjbrenchley89/claude-trading-skills](https://github.com/sjbrenchley89/claude-trading-skills/tree/main/skills/market-breadth-analyzer)  
**Triggers:** When asked about market health, advance/decline ratios, new highs/lows, or overall market conditions  
**Tools needed:** Market data MCP (index and breadth data)

```yaml
name: market-breadth-analyzer
description: Evaluates overall market health through breadth indicators, advance/decline data, new high/low ratios, and McClellan oscillator. Use when assessing overall market conditions or risk environment.
model: claude-sonnet-4-6
```

---

### portfolio-risk-manager
**Purpose:** Portfolio construction and risk management  
**Source:** [sjbrenchley89/claude-trading-skills](https://github.com/sjbrenchley89/claude-trading-skills/tree/main/skills/portfolio-manager)  
**Triggers:** When asked to review portfolio allocations, assess concentration risk, or optimize position sizing  
**Tools needed:** Portfolio data access

```yaml
name: portfolio-risk-manager
description: Analyzes portfolio construction, sector concentration, correlation risk, and position sizing. Use when reviewing portfolio health, planning new positions, or stress-testing allocations.
model: claude-opus-4-7
```

---

### earnings-trade-analyst
**Purpose:** Earnings event analysis and trade planning  
**Source:** [sjbrenchley89/claude-trading-skills](https://github.com/sjbrenchley89/claude-trading-skills/tree/main/skills/earnings-trade-analyzer)  
**Triggers:** When asked about upcoming earnings, implied moves, or historical earnings reactions  
**Tools needed:** Options data MCP, earnings history data

```yaml
name: earnings-trade-analyst
description: Analyzes earnings events for trading opportunities — historical reaction patterns, implied move vs actual, and pre/post earnings positioning strategies. Use before earnings announcements.
model: claude-sonnet-4-6
```

---

### canslim-stock-screener
**Purpose:** IBD-style growth stock identification  
**Source:** [sjbrenchley89/claude-trading-skills](https://github.com/sjbrenchley89/claude-trading-skills/tree/main/skills/canslim-screener)  
**Triggers:** When asked to find growth stocks, evaluate CANSLIM criteria, or screen for leadership stocks  
**Tools needed:** Fundamental data MCP, market data MCP

```yaml
name: canslim-stock-screener
description: Screens and evaluates stocks using IBD CANSLIM criteria: EPS growth, sales acceleration, new highs, institutional sponsorship, and market leadership. Use when searching for high-quality growth stocks.
model: claude-sonnet-4-6
```

---

### macro-regime-analyst
**Purpose:** Economic regime and macro trend analysis  
**Source:** [sjbrenchley89/claude-trading-skills](https://github.com/sjbrenchley89/claude-trading-skills/tree/main/skills/macro-regime-detector)  
**Triggers:** When asked about economic cycles, Fed policy impact, yield curve signals, or inflation regimes  
**Tools needed:** Economic data MCP, bond market data

```yaml
name: macro-regime-analyst
description: Classifies current economic regime (expansion/contraction, inflation/deflation) and assesses macro impact on asset classes. Use for top-down market analysis and asset allocation decisions.
model: claude-opus-4-7
```

---

## Related Packages

- **Full trading skills collection:** [sjbrenchley89/claude-trading-skills](https://github.com/sjbrenchley89/claude-trading-skills) — 54 skills
- **Market data MCP:** [sjbrenchley89/claude-trading-skills](https://github.com/sjbrenchley89/claude-trading-skills) includes Crypto.com MCP integration
- **Aggregated package:** [sjbrenchley89/source-build-au](https://github.com/sjbrenchley89/source-build-au)

## Usage Pattern

These subagents work best in a multi-agent pipeline:

```
User Query
    ↓
market-breadth-analyzer (is the market environment favorable?)
    ↓
canslim-stock-screener (find candidates)
    ↓
technical-analyst (evaluate chart setups)
    ↓
portfolio-risk-manager (size positions, check concentration)
```
