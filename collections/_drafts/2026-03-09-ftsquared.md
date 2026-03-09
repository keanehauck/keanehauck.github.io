---
layout: post
title: A short proof of why F = t^2 for a two-group comparison
date: 2026-03-09
summary: The proof is in the pudding.
categories: statistics proof anova
---

One method of proof with equal n

### Setup

we can represent t as

$t=\frac{\overline{Y_1}-\overline{Y_2}}{SE_{\overline{Y_1}-\overline{Y_2}}}$

where $SE_{\overline{Y_1}-\overline{Y_2}}=S_p \sqrt{\frac{1}{n_1+1}+\frac{1}{n_2+1}}$

An anova formula: $F = \frac{MS_{\text{Between}}}{MS_{\text{Within}}}$

with $MS_{\text{Within}} = \frac{ \sum_{i=1}^{k} \sum_{j=1}^{n_i} \left(Y_{ij} - \overline{Y}_i \right)^2 }{N-k}$

In the notation we'll be using,
* $N$: Total number of observations
* $n_i$: Number of observations in group $i$
* $k$: Number of groups
* $j$: Index of a single observation

### Simplifying Denominator

The first step is to figure out what the denominator of the expression simplifies to. With two groups, $MS_{W}=\frac{SS_{W}}{N-2}$.

Again, with two groups,

$SS_W= \sum_{i=1}^{k} \sum_{j=1}^{n_i} \left(Y_{ij} - \overline{Y}_i \right)^2=\sum_{j=1}^{n_1}(Y_{1j}-\overline{Y}_1) + \sum_{j=1}^{n_2}(Y_{2j}-\overline{Y}_2)$.

Thus, $MS_{W}= \frac{\sum_{i=1}^{k} \sum_{j=1}^{n_i} \left(Y_{ij} - \overline{Y}_i \right)^2}{N-k}=\frac{\sum_{j=1}^{n_1}(Y_{1j}-\overline{Y}_1) + \sum_{j=1}^{n_2}(Y_{2j}-\overline{Y}_2)}{N-2}$ for two groups.

The goal is to represent this equation in terms of something we recognize. We know that sample variance, $s^2_i$, is equal to $\frac{\sum_{j=1}^{n_i}(Y_{ij}-\overline{Y}_i)^2}{n_i-1}$ for group $i$. We might notice that the numerator of this equation shows up twice in our current $MS_{W}$ formula. We can make sample variance itself show up by multiplying both the numerator and denominator of $MS_W$ by $\frac{1}{(n_1-1)(n_2-1)}$.

$MS_W \cdot \frac{\frac{1}{(n_1-1)(n_2-1)}}{\frac{1}{(n_1-1)(n_2-1)}}=\frac{\sum_{j=1}^{n_1}(Y_{1j}-\overline{Y}_1) + \sum_{j=1}^{n_2}(Y_{2j}-\overline{Y}_2)}{N-2} \cdot \frac{\frac{1}{(n_1-1)(n_2-1)}}{\frac{1}{(n_1-1)(n_2-1)}} = \frac{\sum_{j=1}^{n_1}(Y_{1j}-\overline{Y}_1)/(n_1-1)(n_2-1) + \sum_{j=1}^{n_2}(Y_{2j}-\overline{Y}_2)/(n_1-1)(n_2-1)}{N-2}$
