---
layout: post
title: Why the F-statistic is equivalent to the squared t-statistic for a two-group comparison
date: 2026-03-09
summary: The proof is in the pudding.
categories: statistics proof anova
---

Possibly the most horrifying seven words you can encounter when reading a textbook are the following: "The proof is left to the reader." When learning ANOVA (Analysis of Variance), it is common to encounter the fact that the F-statistic is equal to the squared t-statistic when you are only comparing two groups. Unfortunately, this sentence is often followed by the previously-mentioned proof hand-waving, which can leave readers confused, myself included. Thus, I am going to clearly and concisely demonstrate how the F-test reduces to a t-test under certain conditions.

Interestingly, this proof is quite elusive. In fact, while researching how to write this up, the only published proof I stumbled across was another blog post from a data scientist named [Juan Manuel](https://canovasjm.netlify.app/about/). Big shoutout to him for his post, which helped me double-check my results.

This proof assumes familiarity with the ANOVA and t-test framework.

### Setup

In the notation we'll be using,
* $SS_B$: Sum of Squares between groups due to treatment
* $SS_W$: Sum of Squares within groups due to error
* $MS_B$: Mean Sum of Squares between groups $=SS_B / k-1$
* $MS_W$: Mean Sum of Squares within groups $=SS_W / N-k$
* $N$: Total number of observations
* $n_i$: Number of observations in group $i$
* $k$: Number of groups
* $j$: Index of a single observation
* $\overline{y}$: The grand mean
* $\overline{y}_i$: Mean of group $i$

A few formulae are important for the following results:

$t=\frac{\overline{y_1}-\overline{y_2}}{SE_{\overline{y_1}-\overline{y_2}}}$

where $SE_{\overline{y_1}-\overline{y_2}}=s_p \sqrt{\frac{1}{n_1}+\frac{1}{n_2}}$.

Sample variance: $s_i^2=\frac{\sum_{j=1}^{n_i}(y_{ij}-\overline{y}_i)^2}{n_i-1}$ for group $i$.

Pooled sample variance for two groups: $s^2_p = \frac{s^2_1(n_1-1) \ + \ s^2_2(n_2-1)}{N-2}$.

$F = \frac{MS_{\text{B}}}{MS_{\text{W}}}$

with $MS_B= \frac{\sum_{i=1}^{k} n_i (\overline{y}_i - \overline{y})^2}{k-1}$

and $MS_{\text{W}} = \frac{ \sum_{i=1}^{k} \sum_{j=1}^{n_i} \left(y_{ij} - \overline{y}_i \right)^2 }{N-k}$.

This final $F$ equation is the one we need to reduce to obtain $t^2$.

### Simplifying Denominator

The first step is to figure out what the denominator of the expression simplifies to. With two groups, $MS_{W}=\frac{SS_{W}}{N-2}$.

Again, with two groups,

$SS_W= \sum_{i=1}^{k} \sum_{j=1}^{n_i} \left(y_{ij} - \overline{y}_i \right)^2=\sum_{j=1}^{n_1}(y_{1j}-\overline{y}_1) + \sum_{j=1}^{n_2}(y_{2j}-\overline{y}_2)$.

Thus, $MS_{W}= \frac{\sum_{i=1}^{k} \sum_{j=1}^{n_i} \left(y_{ij} - \overline{y}_i \right)^2}{N-k}=\frac{\sum_{j=1}^{n_1}(y_{1j}-\overline{y}_1)\ +\ \sum_{j=1}^{n_2}(y_{2j}-\overline{y}_2)}{N-2}$ for two groups.

The goal is to represent this equation in terms of something we recognize. We know that sample variance, $s^2_i$, is equal to $\frac{\sum_{j=1}^{n_i}(y_{ij}-\overline{y}_i)^2}{n_i-1}$ for group $i$. We might notice that the numerator of this equation shows up twice in our current $MS_{W}$ formula. We can make sample variance itself show up by multiplying both the numerator and denominator of $MS_W$ by $\frac{1}{(n_1-1)(n_2-1)}$.

$MS_W \cdot \frac{\frac{1}{(n_1-1)(n_2-1)}}{\frac{1}{(n_1-1)(n_2-1)}}=\frac{\sum_{j=1}^{n_1}(y_{1j}-\overline{y}_1)\ +\ \sum_{j=1}^{n_2}(y_{2j}-\overline{y}_2)}{N-2} \cdot \frac{\frac{1}{(n_1-1)(n_2-1)}}{\frac{1}{(n_1-1)(n_2-1)}} = \frac{\sum_{j=1}^{n_1}(y_{1j}-\overline{y}_1)/(n_1-1)(n_2-1)\ +\ \sum_{j=1}^{n_2}(y_{2j}-\overline{y}_2)/(n_1-1)(n_2-1)}{(N-2)/(n_1-1)(n_2-1)}=\frac{s^2_1 / (n_2-1) \ + \ s^2_2 / (n_1-1)}{(N-2)/(n_1-1)(n_2-1)}$.

This is starting to look a lot like the pooled variance estimator for two groups, $s^2_p = \frac{s^2_1(n_1-1) \ + \ s^2_2(n_2-1)}{N-2}$. If we multiply our current equation by $\frac{(n_1-1)(n_2-1)}{(n_1-1)(n_2-1)}$ we obtain exactly this formula:

$\frac{s^2_1 / (n_2-1) \ + \ s^2_2 / (n_1-1)}{(N-2)/(n_1-1)(n_2-1)} \cdot \frac{(n_1-1)(n_2-1)}{(n_1-1)(n_2-1)} = \frac{s^2_1(n_1-1) \ + \ s^2_2(n_2-1)}{N-2} = s^2_p$.

Thus, we have proven the denominator of the two-group $F$ formula is equal to the pooled variance estimator.

### Simplifying Numerator

The numerator, $MS_B$, is a little trickier. We know that $t=\frac{\overline{y_1}-\overline{y_2}}{s_p \sqrt{\frac{1}{n_1}+\frac{1}{n_2}}}$ and $t^2= \frac{(\overline{y_1}-\overline{y_2})^2}{s^2_p (\frac{1}{n_1}+\frac{1}{n_2})}$. If our denominator is equivalent to $s^2_p$, the numerator must equal $\frac{(\overline{y_1}-\overline{y_2})^2}{ (\frac{1}{n_1}+\frac{1}{n_2})}$ for our overall formula to equal $t^2$. Let's prove it.

$MS_B= \frac{\sum_{i=1}^{k} n_i (\overline{y}_i - \overline{y})^2}{k-1}$. For two groups, $k-1=1$ and this equation simplifies to $MS_B= n_1(\overline{y}_1 - \overline{y})^2\ + \ n_2(\overline{y}_2 - \overline{y})^2$ by expanding the sum for $k=2$.

We can represent the grand mean $\overline{y}$ as a weighted average $\overline{y}= \frac{n_1 \overline{y}_1 + n_2 \overline{y}_2}{N}$ with $N=n_1 + n_2$.

If we substitute it into our equation for two groups, we get $MS_B= n_1(\overline{y}_1 - \frac{n_1 \overline{y}_1 + n_2 \overline{y}_2}{N})^2 + n_2(\overline{y}_2 - \frac{n_1 \overline{y}_1 + n_2 \overline{y}_2}{N})^2$.

This equation consists of two similar effect terms, one for each group. We will now focus on one of these terms to simplify it, with the logic that the other term will simplify in the same manner. Let's examine $n_1(\overline{y}_1 - \frac{n_1 \overline{y}_1 + n_2 \overline{y}_2}{N})^2$.

We will now make a few algebraic steps. Each should be clear and followable.

$$
\begin{align*}
    n_1(\overline{y}_1 - \frac{n_1 \overline{y}_1 + n_2 \overline{y}_2}{N})^2 &= n_1(\frac{\overline{y}_1N}{N} - \frac{n_1 \overline{y}_1 + n_2 \overline{y}_2}{N})^2 \\
            &= n_1(\frac{n_1 \overline{y}_1+n_2 \overline{y}_1}{N} - \frac{n_1 \overline{y}_1 + n_2 \overline{y}_2}{N})^2 \ \ \ (\text{since} \ N=n_1+n_2) \\
            &= n_1(\frac{n_2 \overline{y}_1 - n_2 \overline{y}_2}{N})^2 \\
            &= n_1(\frac{n_2 (\overline{y}_1 - \overline{y}_2)}{N})^2 \\
            &= n_1(\frac{n_2^2 (\overline{y}_1 - \overline{y}_2)^2}{N^2}) \\
            &= \frac{n_1n_2^2}{N^2}(\overline{y}_1 - \overline{y}_2)^2.
\end{align*}
$$

Thus, our first term $n_1(\overline{y}_1 - \frac{n_1 \overline{y}_1 + n_2 \overline{y}_2}{N})^2$ is equivalent to $\frac{n_1n_2^2}{N^2}(\overline{y}_1 - \overline{y}_2)^2$. The same process can be repeated for the second term (switching the $n$'s and $\overline{y}'s$ as appropriate), which obtains $n_2(\overline{y}_2 - \frac{n_1 \overline{y}_1 + n_2 \overline{y}_2}{N})^2 = \frac{n_2n_1^2}{N^2}(\overline{y}_2 - \overline{y}_1)^2$.

So, our whole equation for $MS_B$ can be rewritten as $MS_B = n_1(\overline{y}_1 - \frac{n_1 \overline{y}_1 + n_2 \overline{y}_2}{N})^2 + n_2(\overline{y}_2 - \frac{n_1 \overline{y}_1 + n_2 \overline{y}_2}{N})^2 = \frac{n_1n_2^2}{N^2}(\overline{y}_1 - \overline{y}_2)^2 + \frac{n_2n_1^2}{N^2}(\overline{y}_2 - \overline{y}_1)^2$.

By definition, $(\overline{y}_1 - \overline{y}_2)^2 = (\overline{y}_2 - \overline{y}_1)^2$, so the entire equation simplifies to $[\frac{n_1n_2^2}{N^2} + \frac{n_2n_1^2}{N^2}](\overline{y}_1 - \overline{y}_2)^2$.

We will conduct one final sequence of algebraic steps:

$$
\begin{align*}
    [\frac{n_1n_2^2}{N^2} + \frac{n_2n_1^2}{N^2}](\overline{y}_1 - \overline{y}_2)^2 &= [\frac{n_1n_2^2+n_2n_1^2}{N^2}](\overline{y}_1 - \overline{y}_2)^2 \\
            &= [\frac{n_1n_2n_2+n_2n_1n_1}{N^2}](\overline{y}_1 - \overline{y}_2)^2 \\
            &= [\frac{n_1n_2(n_1+n_2)}{N^2}](\overline{y}_1 - \overline{y}_2)^2 \\
            &= [\frac{n_1n_2(n_1+n_2)}{(n_1+n_2)^2}](\overline{y}_1 - \overline{y}_2)^2 \\
            &= [\frac{n_1n_2}{(n_1+n_2)}](\overline{y}_1 - \overline{y}_2)^2 \\
            &= [\frac{1}{\frac{1}{n_2}+\frac{1}{n_1}}](\overline{y}_1 - \overline{y}_2)^2 \ \ \ (\text{since} \ \frac{\frac{1}{n_1n_2}}{\frac{1}{n_1n_2}} \cdot \frac{n_1n_2}{(n_1+n_2)}=\frac{1}{\frac{n_1+n_2}{n_1n_2}}=\frac{1}{\frac{n_1}{n_1n_2}+\frac{n_2}{n_1n_2}}=\frac{1}{\frac{1}{n_2}+\frac{1}{n_1}}) \\
            &= \frac{(\overline{y}_1 - \overline{y}_2)^2}{\frac{1}{n_2}+\frac{1}{n_1}}
\end{align*}
$$

Thus, for two groups our numerator $MS_B$ is equivalent to $\frac{(\overline{y}_1 - \overline{y}_2)^2}{\frac{1}{n_2}+\frac{1}{n_1}}$.

### Conclusion

The F-statistic is the ratio of $\frac{MS_B}{MS_W}$. We have shown that for two groups ($k=2$) this is equivalent to the ratio $\frac{(\overline{y}_1 - \overline{y}_2)^2}{s^2_p(\frac{1}{n_2}+\frac{1}{n_1})}$, which is exactly equal to $t^2$. 

And there you have it.

### P.S.

There are obviously multiple ways of proving this result. A much simpler version is in the general linear model framework where you can show that the test of the coefficient for a single-predictor (like group membership) model follows a $t$ distribution with $t_{obs}=\frac{b_1}{s_{b_1}}$. It can then be shown that squaring this is equivalent to the observed $F$ value. However, I wanted to highlight a method of proof that only requires familiarity with the ANOVA framework and some solid algebra skills. I hope this is helpful for anyone like me who was curious about this often-stated fact about hypothesis testing.