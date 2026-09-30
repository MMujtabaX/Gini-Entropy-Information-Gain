# 🌳 Decision Trees — Gini, Entropy & Information Gain

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/MMujtabaX/gini/blob/main/gini_entropy_information_gain_(1).ipynb)
![Python](https://img.shields.io/badge/Python-3.x-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange)

A step-by-step walkthrough of **how decision trees choose where to split**. Every calculation is done by hand on a tiny 5-row dataset, then visualized and verified against scikit-learn.

## 📊 The Dataset: Will a Person Buy a Laptop?

| # | Age | Income | Buys Laptop? |
|---|-----|--------|--------------|
| 1 | Young | High | Yes |
| 2 | Young | Low | No |
| 3 | Old | High | Yes |
| 4 | Old | Low | Yes |
| 5 | Young | Low | No |

Small enough to calculate everything by hand: **3 Yes, 2 No** at the root.

## 📐 Concepts Covered

| Concept | Formula | Meaning |
|---------|---------|---------|
| **Gini Impurity** | $1 - \sum p_i^2$ | How "mixed" a node is (0 = pure, 0.5 = max for 2 classes) |
| **Entropy** | $-\sum p_i \log_2 p_i$ | Disorder, from information theory (0 = pure, 1 = max for 2 classes) |
| **Information Gain** | $H(\text{parent}) - \sum \frac{n_k}{n} H(\text{child}_k)$ | How much a split reduces entropy; the tree picks the highest |

## 🧮 Results

| Split | Weighted Gini | Weighted Entropy | Information Gain |
|-------|---------------|------------------|------------------|
| Root (no split) | 0.4800 | 0.9710 | — |
| Income | 0.2667 | 0.5510 | **0.4200** |
| Age | 0.2667 | 0.5510 | **0.4200** |

**The two features tie.** Splitting on Income gives the same child class distributions as splitting on Age: one pure node (2 Yes, 0 No) and one mixed node (1 Yes, 2 No). The rows themselves land in different groups, but the impurity comes out identical.

## 📈 Key Takeaways

- Gini and entropy have **nearly identical curves**, and in practice they almost always pick the same split.
- **Gini is faster** because it has no logarithm, which is why it's scikit-learn's default (`criterion='gini'`).
- Entropy comes from information theory and feeds directly into **information gain**.
- Both criteria produce the **same tree structure** in scikit-learn for this dataset.

## 🏋️ Practice Exercises

The notebook ends with exercises: break the tie by adding rows, prove that pure nodes have zero impurity, explain why the maximum binary Gini is 0.5, and add a third feature.

## 🚀 Run It

Click the **Open in Colab** badge above, or run it locally:

```bash
pip install numpy pandas matplotlib scikit-learn jupyter
jupyter notebook "gini_entropy_information_gain_(1).ipynb"
```

## 👤 Author

**Muhammad Mujtaba Khan Suri** — CS @ UBIT, University of Karachi
[GitHub](https://github.com/MMujtabaX)
