# Steiner Tree Project – README

This repository contains three Python (Jupyter Notebook) implementations of the **Steiner Tree Problem**, each designed for different dataset scales and purposes.

---

## 📁 Files Overview

### 1. `Steiner_tree_small_graph.ipynb`
**Purpose:** Implementation designed for **small graphs**.  
**Use case:** Suitable for testing, debugging, and educational understanding.  
**Features:** Step‑by‑step algorithm explanation and simple visualizations.

---

### 2. `final_Big_Data_Steiner_tree_new.ipynb`
**Purpose:** Optimized for **large graphs / big‑data scenarios**.  
**Use case:** Works efficiently for high node/edge counts.  
**Features:** Performance‑oriented structures, scalable heuristics, and memory‑aware handling.

---

### 3. `Steiner_tree_PACE.ipynb`
**Purpose:** Designed for **real‑world datasets**, including standardized formats such as PACE Challenge sets.  
**Use case:** Experimental evaluation, benchmarking, reproducible research.  
**Features:** Dataset parsers, runtime and solution cost reporting.

---

## 📦 Requirements

All notebooks require:

- Python 3.x  
- Jupyter Notebook / JupyterLab  
- Libraries:
  - networkx  
  - numpy  
  - matplotlib  
  - pandas (optional, dataset handling)

Install dependencies:

```bash
pip install networkx numpy matplotlib pandas
```

---

## 🚀 How to Run

1. Start Jupyter:
   ```bash
   jupyter notebook
   ```
2. Choose the appropriate notebook:
   - Small graph → `Steiner_tree_small_graph.ipynb`
   - Large graph → `final_Big_Data_Steiner_tree_new.ipynb`
   - Real dataset → `Steiner_tree_PACE.ipynb`

3. Run all cells to generate outputs.

---

## 📘 Notes
Feel free to modify the notebooks for further experiments, visualizations, or integration into your own research pipeline.

