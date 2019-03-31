---
layout: post
title: Lifelong Learning with Low Regret
date: 2019-03-30 12:00
summary: Lifelong learning comes from online learning and multi-task learning. We face tasks and samples sequence by sequence as usual online learning settings. However, there are more than one task which makes learning more difficult.
categories: lifelong
author: Yi-Shan Wu
visible: False
---

# Introduction

Machine learning algorithms can now solve many problems even better than humans. However, machines are still far from being intelligent that they typically need to relearn when facing new tasks, while humans are able to learn new things efficiently by ultilizing learned knowledge. This motivates the study called lifelong learning (Thrun and Pratt, 1998), which aims to perform better over time by transferring information learned from previously tasks to later ones, under the belief that there are some commonalities across tasks.

<center class="half">
  <img src="/images/lifelong/Lifelong.png" width="780" height="200" />
</center>

In this paper, we face tasks and samples sequence by sequence as usual online learning settings. As introduced above, tasks are related as they share some common representation, but they are different as each requires a different predictor on top of the representation. We let $\mathcal{G}$ and $\mathcal{H}$ be the space of representation and predictor respectively. As learning the representations is typically much more costly than learning predictors in lifelong learning, we would like to understand if it is possible to learn them continuously through time across different tasks, instead of relearning them in different tasks.

# Notations and Settings

* representation space : $\mathcal{G}$ (usually very large)
* predictor space : $\mathcal{H}$
* number of tasks : $K$
* number of samples in each task : $T_k \forall k\in [K]$ and $\sum\limits_{k=1}^K=T$

For each task $k$ and each step $s$ in it, we need to choose a representation $g_{k,s}$ and an accompanying predictor $h_{k,s}$  which jointly provide a decision for us. After making this decision, we suffer some loss $\ell_{k,s}(g_{k,s}, h_{k,s})$ according to some loss function $\ell_{k,s}$, receive some feedback information, and then proceed to the next iteration.