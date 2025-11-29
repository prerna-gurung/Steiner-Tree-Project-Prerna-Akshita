# Steiner Tree Problem – Project Overview

This repository contains three Jupyter Notebooks implementing and comparing algorithms for the **Steiner Tree Problem (STP)** across small, large, and real-world datasets.

---

## 📂 Files

| Notebook | Purpose |
|---------|---------|
| **Steiner_tree_small_graph.ipynb** | Brute Force, KMB Approximation, and Greedy Heuristic on **small graphs (10–20 nodes)**. |
| **final_Big_Data_Steiner_tree_new.ipynb** | KMB + Greedy algorithms optimized for **large graphs (50–2000 nodes)**. |
| **Steiner_tree_PACE.ipynb** | Runs KMB + Greedy on **real PACE 2018 datasets**. |

---

## 🧩 Problem Summary

Given a weighted graph \(G = (V,E)\) and terminal set \(T\subseteq V\), the Steiner Tree Problem finds a minimum-cost tree that connects all terminals, possibly using additional **Steiner nodes**.

- STP is **NP-hard**.
- Applications: networks, VLSI, routing, infrastructure.

---

## ⚙️ Algorithms Implemented

### **1. Brute Force (Exact)**  
- Tests all subsets; optimal but exponential.  
- Used only for **small graphs**.

### **2. KMB Approximation (2-Approx)**  
- Builds metric closure on terminals → MST → expanded tree.  
- Good solution quality.

### **3. Greedy Heuristic**  
- Iteratively connects nearest terminal via shortest paths.  
- Fastest, scalable; no guarantee.

---

## 🧪 Experiments

Graph scales tested:

- **Small:** 10–20 nodes → BF vs KMB vs Greedy  
- **Medium & Large:** 50–2000 nodes → KMB vs Greedy  
- **Real-world:** PACE 2018 dataset

### Key Findings
- **Brute Force** gives the exact solution but is slow.  
- **KMB** achieves lower cost; slower for large graphs.  
- **Greedy** is fastest; slightly higher cost.  

---

## 📦 Requirements

Install dependencies:

```bash
pip install networkx numpy matplotlib pandas
