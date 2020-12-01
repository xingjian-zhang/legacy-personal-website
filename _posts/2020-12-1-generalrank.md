---
layout:     post
title:      Generalized Rank-Breaking
subtitle:   Computation and Statistical Tradeoffs
date:       2020-12-1
author:     JIM
header-img: img/post-bg-desk.jpg
mathjax: true
catalog: true
tags:
    - Foreseer
    - ML
    - Paper
    - Notes
	- Learning-to-Rank
	- Plackett-Luce Model
	- Rank Aggregation

---

## Resource

Khetan, A. and Oh, S. (2018). Generalized rank-breaking: computational and statistical trade-offs. *The Journal of Machine Learning Research*, 19(1):983–1024.

## Abstract

> For massive and heterogeneous modern datasets, it is of fundamental interest to provide guarantees
> on the accuracy of estimation when computational resources are limited. In the application of rank
> aggregation, for the Plackett-Luce model, we provide a hierarchy of rank-breaking mechanisms or-
> dered by the complexity in thus generated sketch of the data. This allows the number of data points
> collected to be gracefully traded off against computational resources available, while guaranteeing
> the desired level of accuracy. Theoretical guarantees on the proposed generalized rank-breaking
> implicitly provide such trade-offs, which can be explicitly characterized under certain canonical
> scenarios on the structure of the data. Further, the proposed generalized rank-breaking algorithm
> involves set-wise comparisons as opposed to traditional pairwise comparisons. The maximum like-
> lihood estimate of pairwise comparisons is computed efficiently using the celebrated minorization
> maximization algorithm (Hunter, 2004). To compute the pseudo-maximum likelihood estimate of
> the set-wise comparisons, we provide a generalization of the minorization maximization algorithm
> and give guarantees on its convergence.
>
> **Keywords:**  Rank aggregation, Plackett-Luce model, Sample and Computational tradeoff.

## Core Concepts

### Rank Aggregation

In many applications such as election, policy making, polling, and recommendation systems, we want to aggregate individual preferences to produce a global ranking that best represents the collective social preference. We assume that the data comes from a parametric family of choice models, and learns the parameters that determine the global ranking.

### Traditional Structures of Revealed Preference

* **Pairwise Comparison** e.g. Sports and chess matches.
* **Best-out-of-$\kappa$ comparison** e.g. Historical purchase data.
*  **$\kappa$-way Coparison** e.g. Elections and surveys.

### Modern Structures of Revealed Preference

Contrary to traditional structures of revealed preference, modern datasets are unstructured and heterogeneous, leading to significant increase in computation complexity. In the most general case, the preference relations are expressed in the form of *partially ordered set (poset)*. Furthermore, under *the PL model*, a poset can be represented as a *directed acyclic graph (DAG)*.

### Generalized Rank-Breaking

The generalized rank-breaking a hierarchy of estimators ordered in increasing computational complexity and achieving increasing accuracy. **The key idea is to break down the heterogeneous revealed preferences into simpler pieces of ordinal relations, and apply an estimator tailored for those simple structures treating each piece as independent.**

### Algorithmic Weakening & Time-Data Tradeoff

In classical statistics, one is interested in the tradeoff between the sample size and the accuracy, with little considerations to the computational complexity or time. As more computations are typically required with increasing availability of data, the computational resources are often the bottleneck. Recently, a novel idea known as “algorithmic weakening” has been investigated to overcome such a bottleneck, in which a hierarchy of algorithms is proposed to allow for faster algorithms at the expense of decreased accuracy. When guided by sound theoretical analyses, this idea allows the statistician to achieve the same level of accuracy and save time when more data is available. This is radically different from classical setting where processing more data typically requires more computational time.

### ...

## Problem Formulation

