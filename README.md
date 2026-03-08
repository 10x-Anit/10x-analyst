# 10x Analyst — Agentic Analysis Swarm

> Built with [10x-Skill-Builder](https://10x.in) — Production-quality AI skills for every platform.

A multi-agent Claude Code plugin that transforms raw data into insights, reports, and interactive dashboards. Five specialist agents coordinate through an orchestrator to deliver end-to-end data analysis automation.

## Input / Output

```
10x-analyst/
├── input/                      # PUT YOUR DATA HERE
│   └── shopify-data/           # Example dataset (included)
│       ├── customers.csv
│       ├── orders.csv
│       ├── order_items.csv
│       ├── products.csv
│       └── price_changes.csv
│
└── output/                     # ALL RESULTS GO HERE (auto-created)
    └── shopify-data/           # One folder per dataset
        ├── report.md
        ├── dashboard.html
        ├── data-profile.md
        ├── cleaning-log.md
        ├── insights.json
        ├── cleaned-data/
        └── charts/
```

**To analyze new data:** drop your folder into `input/` and run the command with the folder name.

## Agent Swarm

| Agent | Specialty | Model Tier |
|-------|-----------|-----------|
| Data Engineer | Ingest, profile, clean, transform | Haiku (fast) |
| Statistician | EDA, correlations, RFM, KPIs | Sonnet (balanced) |
| Visualizer | Charts, plots, HTML dashboards | Haiku (fast) |
| Reporter | Markdown reports with findings | Sonnet (balanced) |
| Strategist | Business recommendations & priorities | Sonnet (balanced) |

## Commands

```bash
/10x-analyst:analyze   shopify-data                  # Full pipeline
/10x-analyst:profile   shopify-data                  # Data profiling only
/10x-analyst:clean     shopify-data                  # Cleaning only
/10x-analyst:query     shopify-data "Top products?"  # Ask a question
/10x-analyst:visualize shopify-data "revenue trend"  # Generate charts
/10x-analyst:report    shopify-data                  # Markdown report
/10x-analyst:dashboard shopify-data                  # HTML dashboard
```

Every command reads from `input/<dataset>/` and writes to `output/<dataset>/`.

## Model Compatibility

Designed to work across all Claude model sizes:

| Model | Best For | Why |
|-------|----------|-----|
| Haiku | `:profile`, `:clean`, `:visualize` | Fast, token-efficient — follows explicit scripts |
| Sonnet | `:analyze`, `:report`, `:dashboard`, `:query` | Balanced reasoning for EDA + report writing |
| Opus | Complex `:query`, deep `:analyze` | Maximum reasoning for hard business questions |

All instructions are explicit and step-by-step — smaller models follow the scripts, larger models add deeper reasoning on top.

## Plugin Structure

```
10x-analyst/
├── .claude-plugin/plugin.json     # Plugin metadata
├── CLAUDE.md                      # Orchestrator — routes commands to agents
├── README.md                      # This file
├── input/                         # Data input directory
│   └── shopify-data/              # Demo dataset
├── output/                        # Analysis output directory
├── agents/                        # 5 specialist subagents
│   ├── data-engineer.md
│   ├── statistician.md
│   ├── visualizer.md
│   ├── reporter.md
│   └── strategist.md
├── skills/                        # 7 slash commands
│   ├── analyze/SKILL.md
│   ├── profile/SKILL.md
│   ├── clean/SKILL.md
│   ├── query/SKILL.md
│   ├── visualize/SKILL.md
│   ├── report/SKILL.md
│   └── dashboard/SKILL.md
├── references/                    # Shared knowledge base
│   ├── analysis-patterns.md
│   ├── chart-styles.md
│   └── data-quality.md
└── scripts/                       # Reusable Python utilities
    ├── profiler.py
    ├── data_cleaner.py
    ├── chart_generator.py
    └── dashboard_template.py
```

## Requirements

- Python 3.8+
- pandas, matplotlib, seaborn (auto-installed if missing)
- openpyxl (for .xlsx), xlrd (for .xls)
- Chart.js CDN (for dashboard interactivity)

## Supported Data

- **CSV** (.csv) — pandas read_csv
- **Excel** (.xlsx, .xls) — pandas read_excel
- **JSON** (.json) — pandas read_json / json_normalize

---
*Developed by [10x.in](https://10x.in) | 10x-Analyst v1.0.0*
