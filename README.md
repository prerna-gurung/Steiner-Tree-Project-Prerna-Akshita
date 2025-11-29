# Steiner Tree Problem – Algorithms, Experiments, and Notebooks

This repository contains three Jupyter Notebook implementations of the **Steiner Tree Problem (STP)**.  
Each notebook is designed for a different scale of input graphs — **small**, **large**, and **real-world datasets** — and implements multiple algorithms such as:

- **Brute Force (Exact)**
- **KMB Approximation Algorithm (2-Approx)**
- **Greedy Heuristic (Shortest-Path Based)**

This README also summarizes theoretical foundations and the experimental findings from the project report.

---

## 📂 Repository Structure

| File | Description |
|------|-------------|
| **`Steiner_tree_small_graph.ipynb`** | Contains Brute Force, KMB Approximation, and Greedy Heuristic implementations. Designed for **small graphs (10–20 nodes)** where exact solutions are feasible. |
| **`final_Big_Data_Steiner_tree_new.ipynb`** | Optimized for **large graphs (50–2000 nodes)**. Runs KMB Approximation and Greedy Heuristic — Brute Force is omitted due to exponential complexity. |
| **`Steiner_tree_PACE.ipynb`** | Runs the KMB and Greedy algorithms on **real-world PACE 2018 Steiner Tree Challenge datasets**. Includes parsing, cost computation, and performance evaluation. |

---

# 🧩 Problem Statement

The **Steiner Tree Problem** is defined as:

> Given a weighted graph \( G=(V,E) \) and a set of required **terminal nodes** \( T \subseteq V \),  
> find a minimum-cost tree connecting all terminals, optionally using additional **Steiner nodes**.

- Objective:  
  \[
  \min_{F \subseteq E} \sum_{e \in F} w(e)
  \]
  such that the chosen edges connect all terminals.

- Output: A tree  
  \[
  (V^*, F^*),\quad V^* = T \cup S
  \]
  where \( S \) is the set of Steiner nodes.

📌 **The Steiner Tree Problem is NP-hard**, as proved in Garey & Johnson (1979).

---

# ⚙️ Algorithms Implemented

## 1. **Brute Force (Exact Algorithm) — Small Graphs**
- Enumerates all subsets of Steiner nodes.
- Computes MST for each subset.
- Guarantees **optimal** solution.
- Complexity: **Exponential (O(2^n))**, usable only up to ~20 nodes.

### Characteristics
- ✔ Full optimality  
- ✖ Very slow for larger graphs  

---

## 2. **Kou–Markowsky–Berman (KMB) Approximation — 2-Approx**
A classical approximation algorithm:

1. Compute all-pairs shortest paths between terminals.
2. Build a complete graph on terminals (metric closure).
3. Compute MST on this metric closure.
4. Expand MST edges back into original graph shortest paths.
5. MST again on final expanded edges → approximate Steiner Tree.

### Guarantees
\[
w(T_{KMB}) \le 2 \cdot OPT
\]

### Time Complexity
\[
O\left(|T|^2 (|E| + |V|\log|V|)\right)
\]

### Characteristics
- ✔ Near-optimal  
- ✔ Works well for medium and large graphs  
- ✖ Slower than the Greedy heuristic  

---

## 3. **Greedy Heuristic**
- Start from any terminal.
- Iteratively connect the nearest unconnected terminal using shortest paths.
- Optionally prune cycles using MST.

### Characteristics
- ✔ Fastest algorithm  
- ✔ Scales to very large graphs  
- ✖ No approximation guarantee  
- ✖ Often higher cost than KMB  

---

# 🧪 Experimental Setup

Experiments were performed across **multiple graph scales**:

| Scale | |V| | |T| | Algorithms |
|-------|-----|-----|------------|
| **Small** | 10–20 | 3–6 | Brute Force, KMB, Greedy |
| **Medium** | 50–200 | 8–20 | KMB, Greedy |
| **Large** | 500–2000 | 20–100 | KMB, Greedy |
| **Real-world** | PACE 2018 | varies | KMB, Greedy |

Graph Model: **Erdős–Rényi random graphs**  
Metrics collected:
- Total Tree Cost  
- Runtime  
- Approximation Factor  
- Number of Steiner Nodes  
- Memory usage  

Each setup was repeated **10 times** with different seeds.

---

# 📊 Key Results

## **Comparison 1 — Small Graphs (BF vs KMB vs Greedy)**

- All three methods (BF, KMB, Greedy) produced **identical optimal cost** on small graphs.
- **Brute Force** had extremely high runtime.
- **KMB** and **Greedy** were significantly faster.
- ✔ Confirms correctness of approximation/heuristic algorithms.

---

## **Comparison 2 — Medium & Large Graphs (KMB vs Greedy)**

### Cost:
- **KMB outperforms Greedy** consistently (lower cost, fewer Steiner nodes).

### Runtime:
- **Greedy is much faster**, especially above 500 nodes.
- KMB becomes slower due to repeated shortest-path computations.

### Trade-off:
- **KMB = better solution quality**  
- **Greedy = better scalability**

---

# 🌍 Real-World Dataset — PACE 2018

Using 20 real-world instances:

- **KMB** achieves much lower cost.
- **Greedy** runs significantly faster.
- Approximation factor varies, but stays close to 1.1–1.3.

---

# 📦 Requirements

Install dependencies:

```bash
pip install networkx numpy matplotlib pandas
