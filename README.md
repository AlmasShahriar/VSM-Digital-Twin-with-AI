# VSM Digital Twin
### with AI Copilot — IE Flagship Portfolio Project

> A production-grade Value Stream Mapping tool with real-time discrete-event simulation and an AI-powered IE Copilot. Built to demonstrate end-to-end mastery of Lean, Supply Chain, Quality Engineering, and modern software tooling.

---

## Overview

**VSM Digital Twin** is an interactive web application that models a manufacturing value stream, runs a discrete-event simulation, computes live KPIs, and queries an AI copilot (Claude by Anthropic) for Lean analysis and kaizen recommendations.

- **Zero dependencies** — single HTML file, no build step, no backend
- **Deployable in 2 minutes** via GitHub Pages
- **AI-powered analysis** — Claude identifies wastes, bottlenecks, and future-state recommendations automatically after each simulation run

---

## Platform Architecture

This project is Module 04 of a 6-module Smart Manufacturing Operations Platform:

| # | Module | Key Technique | Tools |
|---|--------|---------------|-------|
| 01 | Demand Forecasting | ARIMA + XGBoost + Prophet | Python, Dash, SAP MM |
| 02 | Inventory Optimizer | EOQ, ROP, Monte Carlo DES | SciPy, Pandas |
| 03 | SPC Automation | X̄-R charts, Western Electric rules | Python, Plotly |
| **04** | **VSM Digital Twin ★** | **SimPy DES + AI Copilot** | **JS, Anthropic API** |
| 05 | Supplier Scorecard | OTIF, defect rate, LT variance | Pandas, SAP QM/MM |
| 06 | Unified Ops Dashboard | Full-stack integration | Streamlit, Docker |

---

## Features

### VSM Canvas
- Supplier → process steps → customer flow with push arrows
- WIP triangles between stations (amber = near limit, red = exceeded)
- OEE progress bar inside each process box
- Bottleneck detection with ⚠ red highlight
- Production timeline (sawtooth) with CT blocks

### Simulation Engine
Real-time discrete-event-inspired simulation:

```
Effective CT     = CT_i / (OEE_i / 100)
Bottleneck       = argmax(ECT_i)
Throughput       = min(shift_s / ECT_bottleneck, demand)
Lead Time        = WIP / throughput_rate        [Little's Law]
Value-Added %    = ΣCT_i / (total_effective_time + queue_time)
```

### KPIs Computed Live
| KPI | Definition | World-Class Target |
|-----|------------|--------------------|
| Lead Time | Days from raw to delivery | < 3 days |
| Value-Added % | VA time / total lead time | > 40% |
| OEE | Availability × Performance × Quality | > 85% |
| Throughput | Units / shift | = Demand |
| Total WIP | Units in system | < WIP limit |

### AI Copilot (Claude)
- **Auto-analysis** after every simulation run — top 3 wastes, kaizen opportunity, future state recommendation
- **Free chat** — ask anything: takt time, SMED, kanban sizing, OEE benchmarks, DMAIC, anything
- Grounded with live simulation state injected into every message

---

## Quick Start

```bash
# Clone
git clone https://github.com/your-username/vsm-digital-twin.git
cd vsm-digital-twin

# Open (no server needed)
open vsm-digital-twin.html       # macOS
start vsm-digital-twin.html      # Windows
```

### Deploy to GitHub Pages
1. Push to `main`
2. Go to **Settings → Pages → Source → main branch**
3. Live at `https://your-username.github.io/vsm-digital-twin`

### AI Copilot Setup
Add your Anthropic API key to the `Authorization` header in the `fetch()` call:
```javascript
headers: {
  "Content-Type": "application/json",
  "x-api-key": "sk-ant-your-key-here",
  "anthropic-version": "2023-06-01"
}
```
Without a key the app uses built-in fallback analysis.

---

## IE Concepts Demonstrated

| Lean / IE Theory | Six Sigma / Quality | Operations Research |
|-----------------|---------------------|---------------------|
| Value Stream Mapping | OEE (A × P × Q) | Little's Law |
| Takt time calculation | SPC control limits | Discrete-event simulation |
| 8 Wastes (TIMWOODS) | Cpk / Ppk indices | Bottleneck analysis |
| SMED / Changeover | Western Electric rules | EOQ / ROP models |
| Kanban sizing | FMEA risk priority | Monte Carlo methods |
| Kaizen burst analysis | DMAIC framework | Multi-echelon inventory |

---

## Tech Stack

```
Frontend     Pure HTML / CSS / JS — zero framework
Fonts        Syne (display) · DM Mono (data) · Inter (body)
Rendering    Programmatic SVG from simulation state
AI Layer     Anthropic claude-sonnet-4-20250514
Deploy       Single .html · GitHub Pages
```

---

## Roadmap

- [ ] Module 02: Inventory Optimizer with stochastic demand
- [ ] Module 03: SPC Automation with SMTP alerting
- [ ] Module 05: Supplier Scorecard (SAP QM/MM export pipeline)
- [ ] Module 06: Unified Ops Dashboard (Streamlit + Docker)
- [ ] Future state VSM comparison view
- [ ] PDF report export from AI Copilot

---

## About

Built as a flagship IE portfolio project combining Lean Manufacturing, Operations Research, and modern AI tooling. Designed to be a **real tool**, not just a demonstration.

**License:** MIT
