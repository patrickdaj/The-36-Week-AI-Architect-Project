# ⚡ Block 2 Quick Reference — Data & Tooling

← [Back to Full Guide](index.md)

---

## Sessions

| Session | Build | Skill | Key Resource |
|---------|-------|-------|-------------|
| **Session 9** | `01-data-exploration.ipynb` | DataFrames, load/filter/groupby | [10 Minutes to Pandas](https://pandas.pydata.org/docs/user_guide/10min.html) |
| **Session 10** | `02-attack-analysis.ipynb` | Advanced filtering, aggregation, anomaly detection | [Pandas — Aggregation](https://jakevdp.github.io/PythonDataScienceHandbook/03.08-aggregation-and-grouping.html) |
| **Session 11** | `03-visualizations.ipynb` | Matplotlib charts for security data | [Matplotlib Tutorials](https://matplotlib.org/stable/tutorials/index.html) |
| **Session 12** | `log_analyzer.py` | CLI tool, notebook → production | [argparse Tutorial](https://realpython.com/command-line-interfaces-python-argparse/) |
| **Service 3** | `reports/log-analyzer-service.md` | Run tool against new dataset | — |

---

## Setup

```bash
mkdir -p ~/Development/ai-architect-builds/phase-1-log-analyzer
cd ~/Development/ai-architect-builds/phase-1-log-analyzer
pip install pandas numpy matplotlib jupyterlab
```

**Download data:** [CICIDS2017](https://www.unb.ca/cic/datasets/ids-2017.html) or [UNSW-NB15](https://research.unsw.edu.au/projects/unsw-nb15-dataset)

---

## Files

```
phase-1-log-analyzer/
├── 01-data-exploration.ipynb
├── 02-attack-analysis.ipynb
├── 03-visualizations.ipynb
├── log_analyzer.py
└── reports/
    └── log-analyzer-service.md
```
