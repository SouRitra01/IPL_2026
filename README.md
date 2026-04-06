# IPL 2026 — Match Intelligence Pipeline

An end-to-end sports analytics data product: live match ingestion → feature engineering → ML scoring models → LLM-powered narrative generation → social media assets.

Built as a side project to apply production data engineering and ML patterns to a high-frequency, event-driven domain. The same pipeline architecture mirrors real-world operational intelligence systems.

---

## Why This Exists

Cricket match data is a useful stress-test for production ML pipeline patterns:

- **High-frequency events** — ball-by-ball data, 300+ events per match
- **Mixed data sources** — historical JSON (Cricsheet) + live scraping (Cricinfo)
- **Real-time scoring** — models must update after every ball, not just end of match
- **Contextual narrative** — decision-makers want insight, not raw tables

The same architecture applies directly to supply chain event streams, operational monitoring, and any domain where the goal is: raw events → structured features → model scores → human-readable decisions.

---

## Pipeline Architecture

```
Raw Data (Cricsheet JSON + live Cricinfo scrape)
                    |
            Ingestion & Cleaning
                    |
         Feature Engineering
         (ball-level, over-level, match-level)
                    |
          ML Scoring Models
          - Expected Runs Model
          - Impact Score / Win Probability
          - Surge Detection
                    |
          Context Builder
          (match state + historical comparisons)
                    |
      LLM Insight Generator (Google Gemini)
      - Match summaries
      - Player narratives
      - Strategic analysis
                    |
          Output Layer
          - Charts & visualizations
          - LinkedIn posts
          - Instagram reels
```

---

## ML Models

**Expected Runs Model**

Predicts ball-by-ball expected runs given match context: batsman, bowler, venue, over number, wickets in hand. Delta between actual and expected = performance signal above/below baseline.

**Impact Score Model**

Quantifies player contribution via win probability shift — how much did this ball or over change the match outcome? Directly analogous to EPA (Expected Points Added) in NFL analytics.

**Surge Detection**

Identifies run rate inflection points across an innings. Answers: where did momentum shift, and what caused it? Used for both in-match alerts and post-match storytelling.

---

## LLM Integration

Uses Google Gemini 1.5 Flash for context-aware narrative generation over structured match data — the same RAG-style pattern used in production operational intelligence systems:

- Match context assembled as structured prompt input
- Model generates summaries, player spotlights, strategic analysis, and social media narratives
- Output calibrated per audience: technical analysis vs LinkedIn post vs Instagram reel

---

## Project Structure

```
IPL_2026/
├── config/
│   └── config.yaml               # Data paths, model params, match IDs
├── data/
│   ├── raw/                      # Cricsheet JSONs, scraped match data
│   └── processed/                # Ball-level + match-level feature CSVs
├── src/
│   ├── ingestion/                # Cricsheet JSON loader, Cricinfo scraper
│   ├── processing/               # Data cleaning, feature engineering
│   ├── models/                   # Expected runs, impact, win probability
│   ├── analysis/                 # Insights, surge, zone, comparisons
│   ├── visualization/            # Charts, pitch maps, run rate graphs
│   └── utils/                    # Match selector, helpers
├── scripts/
│   ├── build_historical_dataset.py   # Build training CSV from historical JSONs
│   ├── run_pipeline.py               # Full match analysis pipeline
│   └── test_scraper.py               # Data source validation
├── outputs/
│   ├── charts/                   # Generated visualizations
│   ├── linkedin_assets/          # Social media content
│   └── reels_ready/              # Video-ready assets
├── Match1_analysis.ipynb         # Exploratory analysis notebook
└── requirements.txt
```

---

## Quickstart

```bash
# Clone and install
git clone https://github.com/SouRitra01/IPL_2026.git
cd IPL_2026
pip install -r requirements.txt

# Set API key for LLM insights
export GOOGLE_API_KEY=your_google_api_key

# Build historical training dataset from Cricsheet JSONs
python scripts/build_historical_dataset.py

# Run full match analysis pipeline
python scripts/run_pipeline.py

# Validate data scraping
python scripts/test_scraper.py
```

---

## Design Decisions

**Why ball-by-ball features rather than match-level aggregates?**

Aggregates lose the temporal structure of a match. Impact models need to know *when* in the match a run was scored — a six in over 1 has a different win probability delta than a six in over 19. Fine-grained features are what separate a real impact model from a box score summary.

**Why LLM narrative generation instead of templates?**

Template-based summaries break down across match contexts — a collapse, a record chase, and a rain-affected game all need fundamentally different framing. LLM generation handles contextual variation that rule-based templates cannot scale to.

**Why config-driven architecture?**

Match IDs, data paths, and model parameters change every match day. Hardcoding any of these creates fragile pipelines that need code changes to run a new match. Config-driven design makes the pipeline reusable across an entire season without touching source code.

---

## Transferable Patterns

The architecture here maps directly to production ML pipelines in operational domains:

| Sports Analytics | Supply Chain / Ops |
|---|---|
| Ball-by-ball event stream | Shipment / scan event stream |
| Expected runs model | Demand forecast model |
| Win probability shift | SLA risk score |
| Surge detection | Anomaly detection |
| LLM match narrative | LLM operational decision support |
| Social media output | Leadership dashboard |

---

## Related Projects

- [THANOS Network Optimization](https://github.com/SouRitra01/thanos-network-optimization-demo) — Monte Carlo simulation for supply chain network planning
- [Middle-Mile Forecasting Simulator](https://github.com/SouRitra01/middle-mile-forecasting-simulator) — XGBoost/LightGBM demand forecasting with event signals
- [Email Task Assignment](https://github.com/SouRitra01/email-task-assignment) — BERT-based NLP pipeline for operational task routing

---

## Requirements

```
pandas
numpy
scikit-learn
xgboost
google-generativeai
requests
beautifulsoup4
matplotlib
seaborn
pyyaml
jupyter
```

---

*Same patterns, different domain.*
