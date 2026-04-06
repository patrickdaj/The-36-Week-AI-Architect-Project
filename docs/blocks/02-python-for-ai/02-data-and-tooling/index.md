# 🐍 Block 2: Data & Tooling

[← Block 1: Stop Wasting Tokens](../../01-prompt-engineering/01-stop-wasting-tokens/index.md) | [Block 3: First AI Apps →](../../03-llm-apis/03-first-ai-apps/index.md)

> *"The model is only as good as the data you feed it. Most people never learn to look at data properly."*

**Quick Reference:** [→ Block 2 Quick Ref](quick-ref.md)

---

## Before You Start Block 2

Skim these — 20 minutes:

- 📖 [Pandas Getting Started — 10 Minutes to Pandas](https://pandas.pydata.org/docs/user_guide/10min.html) — official quick-start, covers everything you need for Session 9. Bookmark the full User Guide for reference later.
- 📖 [Real Python — Jupyter Notebook Tutorial](https://realpython.com/jupyter-notebook-introduction/) — skim if you haven't used Jupyter before, skip if you have

**Setup:**
```bash
mkdir -p ~/Development/ai-architect-builds/phase-1-log-analyzer
cd ~/Development/ai-architect-builds/phase-1-log-analyzer
pip install pandas numpy matplotlib jupyterlab
```

**Data:** Download the [CICIDS2017 dataset](https://www.unb.ca/cic/datasets/ids-2017.html) or [UNSW-NB15](https://research.unsw.edu.au/projects/unsw-nb15-dataset) — real network intrusion detection datasets with labeled attacks.

---

## Week 1 — Learn to See Your Data

### Session 9: DataFrames Are Your New Best Friend

**Skill:** Load, inspect, and manipulate tabular data with Pandas. This is the lingua franca of data work.

**Build:** Create a Jupyter notebook `01-data-exploration.ipynb`:
- Load the IDS dataset into a DataFrame
- Run `.head()`, `.info()`, `.describe()` — understand shape, types, missing values
- Filter: show only rows flagged as attacks
- Group by attack type, count occurrences, sort descending
- Answer: What are the top 5 attack types? What % of traffic is benign?

| Component | Task |
|-----------|------|
| Build | `01-data-exploration.ipynb` — IDS dataset exploration |
| Key Ops | load, filter, groupby, value_counts, sort |

> 📖 **Read:** [Pandas — 10 Minutes to Pandas](https://pandas.pydata.org/docs/user_guide/10min.html) — the official quickstart

---

### Session 10: Slicing, Filtering, and Aggregation

**Skill:** Advanced DataFrame operations — boolean indexing, multi-column groupby, aggregation functions, and the query syntax.

**Build:** Continue in `02-attack-analysis.ipynb`:
- Filter traffic by source IP, destination port, protocol
- Group by (source_ip, attack_type) — which IPs are launching what?
- Calculate: mean packet size per attack type vs. benign traffic
- Create a "top talkers" report — the 10 IPs generating the most traffic
- Find: time windows with anomalous traffic volume (>2 standard deviations from mean)

| Component | Task |
|-----------|------|
| Build | `02-attack-analysis.ipynb` — multi-dimensional attack analysis |
| Key Ops | boolean indexing, multi-groupby, agg, rolling window |

> 📖 **Read:** [Python Data Science Handbook — Data Manipulation with Pandas](https://jakevdp.github.io/PythonDataScienceHandbook/03.08-aggregation-and-grouping.html)

---

### Session 11: Visualization — Make Data Legible

**Skill:** Create meaningful charts from security data. Matplotlib for basic plotting, plus enough style to make outputs presentable.

**Build:** Create `03-visualizations.ipynb`:
- Bar chart: top 10 attack types by frequency
- Time series: traffic volume over time with attack windows highlighted
- Heatmap: source IP × destination port activity matrix
- Scatter: packet size vs. flow duration, colored by attack/benign
- Save all plots as PNGs for your report

| Component | Task |
|-----------|------|
| Build | `03-visualizations.ipynb` — 4+ security-relevant visualizations |
| Key Ops | bar, line, heatmap, scatter, savefig |

> 📖 **Read:** [Matplotlib — Tutorials](https://matplotlib.org/stable/tutorials/index.html) — official getting started

---

### Session 12: The CLI Tool — From Notebook to Production

**Skill:** Turn your notebook exploration into a reusable CLI tool. This is the transition from "exploring data" to "building tools."

**Build:** Create `log_analyzer.py`:
```python
# CLI tool that:
# 1. Takes a CSV/PCAP log file as input
# 2. Runs the analysis from Sessions 9-11 automatically
# 3. Generates an HTML report with:
#    - Executive summary (total flows, attack %, top threats)
#    - Top talkers table
#    - Anomaly windows
#    - All 4 visualizations embedded
# 4. Accepts flags: --top-n, --time-window, --output-format
```

Use `argparse` for CLI args. Use your notebooks as the reference implementation.

| Component | Task |
|-----------|------|
| Build | `log_analyzer.py` — CLI security log analysis tool with HTML report |
| Test | Run against the IDS dataset, verify HTML output |

> 📖 **Read:** [Real Python — Command-Line Interfaces with argparse](https://realpython.com/command-line-interfaces-python-argparse/)

---

### ⏰ Project 3: Analyze Something Real

Run your `log_analyzer.py` against a different dataset than you developed against. Options:
- [UNSW-NB15](https://research.unsw.edu.au/projects/unsw-nb15-dataset) (if you developed on CICIDS)
- Your own sanitized logs (if you have them)
- [CTU-13](https://www.stratosphereips.org/datasets-ctu13) — botnet traffic dataset

Document: What broke? What assumptions did your tool make about data format? Write findings in `reports/log-analyzer-service.md`.

---

## Optional: Go Deeper

- 📖 [Python Data Science Handbook — Chapter 4: Visualization with Matplotlib](https://jakevdp.github.io/PythonDataScienceHandbook/04.00-introduction-to-matplotlib.html)
- 📺 [Corey Schafer — Pandas Tutorial Series](https://www.youtube.com/playlist?list=PL-osiE80TeTsWmV9i9c58mdDCSskIFdDS) — excellent video walkthroughs
- 📖 [Polars Documentation](https://docs.pola.rs/) — the faster alternative to Pandas, worth knowing exists

---

[← Block 1: Stop Wasting Tokens](../../01-prompt-engineering/01-stop-wasting-tokens/index.md) | [Block 3: First AI Apps →](../../03-llm-apis/03-first-ai-apps/index.md)
