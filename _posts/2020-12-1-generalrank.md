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

### Setup

We assume there are $n$ users and $d$ items. We denote the set of $n$ users by $[n]=\{1,...,n\}$ and the set of $d$ items by $[d]$. We assume that each user $j\in [n]$ is presented with a subset of items $S_j\subset [d]$, and independently provides her ordinal preference in the form of *poset*, where the ordering is drawn from the *Plackett-Luce (PL) model*. Let $\mathcal{G}_j$ denote the DAG of the poset provided by the user $j$ over $S_j$ according to the PL model with weights $\theta^*$. 

### Task

The task is to learn $\widehat\theta$,  an estimate of the true weights (i.e. utilities) $\theta^*$.

### Plackett-Luce Model

Plackett-Luce Model is a special case of *random utility models*, where each item $i$ is parametrized by a latent true *utility/weight* $\theta_i\in\mathbb{R}$. When offered with $S_j\subset[d]$, the user **samples** the perceived utility $U_i$ for each item $i$ independently according to $U_i=\theta_i+Z_i$, where $Z_i$s are i.i.d. noise. In particular, the PL model assumes $Z_i$ follow the *standard Gumbel distribution*. The observed poset is a partial observation of the ordering according to this perceived utilities.

#### statistical equivalence

Consider a (full) ranking as a map $\sigma_j:[|S_j|]\to S_j$. It can be shown that the PL model is **generated** by first independently assigning each item $i\in S_j$ an unobserved value $Y_i$, exponentially distributed with mean $e^{-\theta_i}$, and the resulting ranking $\sigma_j$ is inversely given by $Y_i$ so that $Y_{\sigma_j(1)}\leq Y_{\sigma_j(2)}\leq ...\leq Y_{\sigma_j(|S_j|)}$. *(Q: In reality, does the exponential distribution make sense?)*

#### property of sequential choices

$P_\theta(i_3\prec i_2\prec i_1)=P_\theta(\{i_3, i_2\}\prec i_1)P_\theta(i_3\prec i_2)$

Thus,

$$\displaystyle P_{\theta}[\sigma_j]=\prod_{i=1}^{|S_j|-1}\dfrac{\exp(\theta_{\sigma_j(i)})}{\sum_{i'=i}^{|S_j|}\exp(\theta_{\sigma_j(i')})}$$

### Maximum Likelihood Esitimate (MLE) of DAG

Probability of observing a DAG is the sum of probabilities of all possible rankings that are consistent with it. i.e.

$\displaystyle P_\theta[\mathcal{G}_j]=\sum_{\sigma\in\mathcal{G}_j}P_{\theta}[\sigma]$

where the notation $\mathcal{G_j}$ is slightly abused to denote the set of all permitting rankings that are consistent with the DAG $\mathcal{G_j}$. The maximum likelihood estimate maximizes log-likelihood of observing $\mathcal{G_j}$ for each $j$:

$$\displaystyle \widehat\theta\in\arg\max_{\theta\in\Omega_b}\left\{\sum_{j=1}^n\log P_\theta[\mathcal{G_j}] \right\}$$

where $\Omega_b$ is a designed bounded set of $\theta$.

### Gumbel Distribution

#### cumulative distribution function

${\displaystyle F(x;\mu ,\beta )=e^{-e^{-(x-\mu )/\beta }}\,}$

#### standard gumbel distribution

The standard Gumbel distribution is the case where ${\displaystyle \mu =0}$ and ${\displaystyle \beta =1}$ with cumulative distribution function

${\displaystyle F(x;\mu ,\beta )=e^{-e^{-x}}}$

#### merits

* log-concave PDF
* memoryless