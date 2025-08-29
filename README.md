# Genetics — Genome Test with Punitive Decrease

Genetic Algorithm experiments with **adaptive punitive decrease** applied to the genome. The repository is designed for **easy execution**, **reproducibility**, and **clear evaluation** of results, following best practices valued by recruiters at **Amazon, B3, Google, Nubank**, and **Mercado Livre**.

> Main notebook: `Genetica_testeGenomaDiminuicaoPunitivaTeste.ipynb`

---

## Table of Contents

- [Overview](#overview)  
- [Why this project is relevant for recruiters](#why-this-project-is-relevant-for-recruiters)  
- [Run in 2 minutes](#run-in-2-minutes)  
  - [Option A: Docker](#option-a-docker)  
  - [Option B: Local with Python](#option-b-local-with-python)  
- [Notebook execution step by step](#notebook-execution-step-by-step)  
- [Genetic Algorithm parameters](#genetic-algorithm-parameters)  
- [Reproducibility and logs](#reproducibility-and-logs)  
- [Repository structure](#repository-structure)  
- [Quick tests and validation](#quick-tests-and-validation)  
- [Short roadmap](#short-roadmap)  
- [FAQ](#faq)  
- [License](#license)

---

## Overview

This project explores a variation of **adaptive punitive penalization** during the genetic algorithm evolution process. The key idea is to apply a **punitive decrease** to genes or individuals that violate constraints or lead to overfitting, reducing the likelihood of propagating poor solutions across generations.  

The experiment is implemented in a single **Jupyter Notebook** to ensure readability, straightforward execution, and rapid iteration.

Expected outcomes:
- Comparison between baseline GA and GA with adaptive punishment.  
- Fitness curves per generation, runtime, and stability.  
- Hyperparameter sensitivity analysis.

---

## Why this project is relevant for recruiters

- **Clarity and rigor**: reproducible execution, objective steps, measurable metrics.  
- **Product mindset**: focus on results, easy-to-follow documentation.  
- **Technical quality**: attention to reproducibility, experiments, and parameter tracking.  
- **Production readiness**: Docker-based isolated environment.  
- **Security and compliance**: dependencies listed and pinned.

---

## Run in 2 minutes

Choose one of the following options:

### Option A: Docker

Requirements:
- Docker installed

```bash
# 1. Clone the repository
git clone <YOUR_REPO_URL>.git
cd <REPO_FOLDER>

# 2. Run Jupyter Lab with SciPy notebook image
docker run -it --rm -p 8888:8888 -v "$PWD":/home/jovyan/work jupyter/scipy-notebook:latest
```

Then, open the link shown in the terminal, go to `work/`, and open `Genetica_testeGenomaDiminuicaoPunitivaTeste.ipynb`.

On Windows PowerShell:

```powershell
git clone <YOUR_REPO_URL>.git
cd <REPO_FOLDER>
docker run -it --rm -p 8888:8888 -v "${PWD}:/home/jovyan/work" jupyter/scipy-notebook:latest
```

### Option B: Local with Python

Requirements:
- Python 3.10 or 3.11  
- Updated `pip`

```bash
# 1. Clone
git clone <YOUR_REPO_URL>.git
cd <REPO_FOLDER>

# 2. Create and activate venv
python -m venv .venv
# Linux/macOS
source .venv/bin/activate
# Windows PowerShell
# .\.venv\Scripts\Activate.ps1

# 3. Install dependencies
python -m pip install --upgrade pip
pip install -r requirements.txt

# 4. Launch Jupyter
jupyter lab
# or
jupyter notebook
```

Suggested `requirements.txt`:

```txt
numpy>=1.26
pandas>=2.0
matplotlib>=3.8
scikit-learn>=1.4
tqdm>=4.66
ipywidgets>=8.1
jupyterlab>=4.0
```

---

## Notebook execution step by step

1. Open `Genetica_testeGenomaDiminuicaoPunitivaTeste.ipynb`.  
2. Select the Python kernel from your environment.  
3. Run configuration and import cells.  
4. Adjust **GA hyperparameters**.  
5. Run all cells (`Run All`).  
6. Check outputs:
   - Mean and best fitness curves.  
   - Execution time.  
   - Comparison between baseline and adaptive punishment.  
   - Logs and result tables.

---

## Genetic Algorithm parameters

- `seed`: reproducibility (e.g., `42`).  
- `population_size`: population size (e.g., `100`).  
- `n_generations`: number of generations (e.g., `200`).  
- `selection_method`: tournament, roulette, or rank.  
- `crossover_rate`: crossover probability (e.g., `0.8`).  
- `mutation_rate`: mutation probability per gene (e.g., `0.05`).  
- `elitism`: elite individuals preserved (e.g., `2`).  
- `penalty_mode`: enables adaptive punishment.  
- `penalty_factor`: initial penalty factor (e.g., `0.1`).  
- `penalty_decay`: penalty decay rate per generation (e.g., `0.98`).  
- `constraint_fn`: constraint function to penalize infeasible solutions.

---

## Reproducibility and logs

- Always set the `seed` at the beginning.  
- Save outputs in `results/`:
  - CSV with metrics per generation  
  - PNG plots  
  - JSON with parameters  

Example:

```python
import json, time, pandas as pd
ts = time.strftime("%Y%m%d-%H%M%S")
pd.DataFrame(history).to_csv(f"results/history_{ts}.csv", index=False)
with open(f"results/params_{ts}.json", "w") as f:
    json.dump(params, f, indent=2)
```

---

## Repository structure

```
.
├── Genetica_testeGenomaDiminuicaoPunitivaTeste.ipynb
├── requirements.txt
├── results/
│   ├── history_YYYYMMDD-HHMMSS.csv
│   ├── params_YYYYMMDD-HHMMSS.json
│   └── plots_YYYYMMDD-HHMMSS.png
└── README.md
```

---

## Quick tests and validation

- **Smoke test**: reduce `population_size` and `n_generations` to run quickly.  
- **Consistency**: run 3 times with the same `seed` to validate reproducibility.  
- **Sanity check**: compare results with `penalty_mode=off` vs `penalty_mode=on`.

---

## Short roadmap

- Extract GA into standalone Python module.  
- CLI runner: `python -m ga.run --config configs/base.yaml`.  
- Auto-generated HTML report with metrics and plots.  
- Systematic comparison of selection and crossover operators.  
- GitHub Actions integration for smoke tests.

---

## FAQ

**Why Jupyter instead of a pure Python script?**  
For rapid research and experimentation.

**Is Docker mandatory?**  
No. It is optional.  

**Does the project depend on external datasets?**  
No. Experiments are synthetic and self-contained.

---

## License

Choose one depending on your goals:
- **MIT** (simple, permissive).   
---

### Recruiter’s note

- Demonstrates ability to **formulate hypotheses**, **experiment**, **measure**, and **document** results.  
- Code is clean, reproducible, and easy to review.  
- Reflects strong technical foundations in optimization, research mindset, and engineering best practices.
