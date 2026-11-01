# 🌍 Carbon-Aware AI Task Scheduler

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Research Status](https://img.shields.io/badge/Status-Completed-success.svg)]()

An empirical simulation framework and intelligent orchestration engine designed to minimize the carbon footprint and operational costs of artificial intelligence compute workloads by aligning execution windows with regional renewable energy peaks.

---

## 📊 Executive Summary & Key Results

Traditional AI orchestration pipelines execute computing jobs immediately upon submission, treating electrical grid carbon intensity as a static variable. This project demonstrates that **temporal workload shifting**—delaying flexible jobs to exploit renewable energy troughs—significantly mitigates emissions without violating task deadlines.

Evaluated over a rigorous 30-day simulation of the **British National Grid**:
* **Grid Volatility (CV):** $44.8\%$ (Mean Intensity: $107.82\ gCO_2/kWh$, $\sigma = 48.31$)
* **Total Cumulative Savings:** **$2,647.51\text{g } CO_2$** and **$2.85\text{ USD}$** across **145 task executions**.
* **Primary Impact Driver:** High-power, long-duration tasks (such as 7B LLM Fine-Tuning) yield the highest environmental return, averaging **$78.86\text{g } CO_2$** saved per run.

---

## 📈 System Visualization

The two-panel research figure below illustrates the optimization mechanism and task-specific efficiency:

![Carbon Curve & Optimization Analysis](assets/carbon_curve.png)
* **Panel A:** Demonstrates how an AI workload is dynamically delayed from a high-carbon fossil-fuel peak to an overnight/midday renewable energy trough within its deadline window.
* **Panel B:** Compares the average carbon reduction (in grams of $CO_2$) across 5 distinct AI hardware states over a 30-day mean.

---

## 🛠️ Workload Efficiency Breakdown

| Task Name | Hardware Profile | Estimated Runtime | Max Delay Window | Avg $CO_2$ Saved / Run |
| :--- | :--- | :--- | :--- | :--- |
| **Data Scraper** | CPU ($0.055\text{ kW}$) | $0.75\text{ hrs}$ | $12\text{ hrs}$ | **$2.42\text{ g}$** |
| **Vector Embedding Generation** | GPU ($0.120\text{ kW}$) | $0.50\text{ hrs}$ | $6\text{ hrs}$ | **$3.23\text{ g}$** |
| **7B LLM Fine-Tuning / LoRA** | GPU ($0.350\text{ kW}$) | $3.00\text{ hrs}$ | $18\text{ hrs}$ | **$78.86\text{ g}$** |
| **Batch Inference** | GPU ($0.250\text{ kW}$) | $1.00\text{ hr}$ | $2\text{ hrs}$ | **$5.49\text{ g}$** |
| **FAISS Vector Store Indexing** | CPU/RAM ($0.090\text{ kW}$) | $0.25\text{ hrs}$ | $8\text{ hrs}$ | **$1.30\text{ g}$** |

---

## 🗂️ Repository Structure

```text
├── assets/
│   └── carbon_curve.png       # Two-panel research visualization chart
├── research_data.csv          # 30-day simulation log (145 execution records)
├── carbon_scheduler.py        # Core simulation and scheduling engine
├── whitepaper.md              # Full academic research paper
└── README.md                  # Repository documentation
