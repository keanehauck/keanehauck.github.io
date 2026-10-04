---
layout: post
title: Why sphericity is important in RM-ANOVA
date: 2026-09-12
summary: Why is it even called sphericity?
categories: statistics longitudinal anova
---

Sphericity is an important assumption for Repeated Measures Analysis of Variance (RM-ANOVA), and also for being [Violet Beauregarde](https://tenor.com/view/charlie-and-the-chocolate-factory-violet-beauregarde-gif-14253451951019764007). Unfortunately, many papers and texts describing the sphericity assumption treat it in a manner similar to the following:

>RM-ANOVA uses the F-statistic to determine statistical significance, and this requires, among other assumptions, normality and sphericity. Previous Monte Carlo simulation studies have indicated that the Type I error and power of the F-test are not altered by the violation of normality when sphericity is fulfilled. For example, Blanca et al. (2023) carried out an extensive study, examining a wide variety of conditions that might be encountered in real research situations. They manipulated the number of repeated measures (3, 4, 6, and 8), sample size (from 10 to 300), and distribution shape (slight, moderate, and severe departure from the normal distribution), and considered both equal and unequal distributions in each repeated measure. The results showed that RM-ANOVA is robust under non-normality when the sphericity assumption is met with distributions having skewness and kurtosis values as large as 2.31 and 8, respectively, and also that empirical power did not decrease with the violations of normality tested in the study.

>In one-way repeated measures designs, the sphericity assumption is met when the variances of the population difference scores for all pairs of treatment levels are homogeneous (Kirk, 2013) (for a definition in terms of the covariance matrix, see Kirk, 2013, pp. 306–310, and Langenberg et al., 2023). Sphericity is usually examined with the Mauchly test, whose null hypothesis states that the variances of the differences are equal. As recommended in some books (e.g., Gamst et al., 2008), applied researchers usually perform the Mauchly test as a preliminary analysis and then, depending on the results, decide on the subsequent analytic strategy. However, early simulation studies showed that the Mauchly test does not control Type I error under non-normality, and neither is it sensitive to small departures from sphericity (Huynh and Mandeville, 1979; Keselman et al., 1980), thus calling into question its usefulness as a preliminary test.

This excerpt is from a paper by Blanca et al. (2023) titled "Repeated measures ANOVA and adjusted F-tests when sphericity is violated: which procedure is best?" Stated differently, this is a paper explicitly aimed at describing and examining the sphericity assumption in RM-ANOVA. Still, it lacks an intuitive explanation for why sphericity is important. The authors do a fantastic job explaining the impact of violated sphericity, the context behind RM-ANOVA, and the methods of their analysis. So why does it lack the justification for sphericity?

I even asked AI—it didn't give me a good answer either. Here's what ChatGPT v5.5 spit out:

>Why does RM-ANOVA need this assumption?

>Repeated measurements from the same person are naturally correlated. RM-ANOVA accounts for this correlation, but its F-statistic is only exact if the covariance structure satisfies sphericity.

>If sphericity is violated: the denominator of the F statistic is estimated incorrectly, the degrees of freedom are too large, the F distribution no longer matches the theoretical distribution, p-values become artificially small, increasing the chance of a Type I error (finding a significant effect when none exists).

>In other words, violating sphericity makes RM-ANOVA too liberal.

Well, it's definitely been trained on human data. It's interesting how difficult it is to actually find in the literature a description of why sphericity is needed for the math to work out.

### Unraveling the mystery

First it is prudent to revisit the goals of RM-ANOVA. The point of RM-ANOVA is to extend the ANOVA framework to longitudinal data and answer the question: "Do differences exist between the means of our outcome variable at each timepoint?" Typically, RM-ANOVAs work by analysis of longitudinal data in the wide format with a between-subjects factor of person and a within-subjects factor of time. In this way, each individual person contributes a factor effect that removes stable between-person variability from the residual error.

Example data are given below:

$$
\begin{array}{c|ccc}
  ID & Time_1 & Time_2 & Time_3 \\
  1 & 1 & 3 & 4 \\
  2 & 3 & 5 & 6 \\
  3 & 1 & 2 & 2 \\
  4 & 2 & 2 & 3
\end{array}
$$

From this setup, an $F$ statistic is calculated as the ratio of Mean Square Between (MSB) to Mean Square Within (MSW) as a means of expressing the variance between groups (timepoints) relative to the variance within each person. If you're familiar with ANOVA, this makes sense—by creating a "person" factor and a "time" factor, we answer the questions: "Do person means differ overall?" and "Do timepoint means differ overall?"

Less clear is how sphericity then comes into play. It is clear that our setup violates the independence of cases typically assumed in the general linear model, as one of our factors literally represents the same individual across levels of the other. But how does incorporating the sphericity assumption help skirt the independence assumption? I found a [lovely article](https://www.tqmp.org/RegularArticles/vol12-2/p114/p114.pdf) by David M. Lane at Rice University which laid it out in terms of linear algebra.

First, consider that the sphericity assumption is normally stated as the assumption that the variances of the differences between any arbitrary pairs of conditions to be equal. So, with three timepoints, $Var(T_1-T_2)=Var(T_1-T_3)=Var(T_2-T_3)$. Equivalently, sphericity can also be defined in terms of orthogonal contrasts where the variances of the orthogonal contrasts are all equal and that the correlations among the contrasts are 0. To see why consider the following orthogonal contrasts: 

$$\Psi_1 = (1, -1, 0)$$ $$\Psi_2 = (-1, -1, 2)$$

These two contrasts are orthogonal because they satisfy $\Sigma {c_1c_2}=0$. Furthermore, they represent all pairs of differences, because the first contrast represents the difference between the first and second group, and the differences between the other pairs can be represented by a linear combination of the two contrasts. So, equality of variances of the differences between any arbitrary pair of conditions is equivalent to the equality of variances of these orthogonal contrasts. Generally this holds.

For any set of conditions $k$ we have $k-1$ orthogonal contrasts whose individual sum of squares add to compose the overall sum of squares for the omnibus test. For two orthogonal contrasts $1$ and $2$ for a set of three groups, $SS_B=SS_1+SS_2$. Furthermore, the $F$ for each contrast will average to the omnibus $F$. These observations will be relevant later.

### Matrix algebra

For a raw data matrix $X$, linear contrasts can be calculated as $L=XC$ where $C$ is a $k \cdot (k-1)$ matrix with contrast coefficients as columns. $L$ will be a $N \cdot (k-1)$ matrix representing the observed contrast scores for each individual. In calculating the $F$ test for each contrast, the numerator consists of the mean squares for that contrast and the denominator consists of a pooled mean square error. The numerator, $MS_c$, is calculated as $N \cdot m_c$ where $m_c$ is the mean for all participants on that contrast. The denominator, $MS_e$, is calculated as the mean of the variances of all contrasts.

Thus, two assumptions are evoked. To have the property hold that the $F$ for the omnibus test will equal the average of all contrast $F$ tests (and to ensure that the calculation of $MS_e$ is valid), it necessitates the assumption that each mean square error is estimating the same population variance. If the population variance for each contrast was different, the calculation for the denominator wouldn't be valid. Furthermore, the assumption is necessitated that the contrasts have correlation of $0$. This is because the degrees of freedom are added in both the numerator and denominator, which only makes sense if the contrasts each provide an independent estimate. 

So, once we have the observed contrast matrix $L$, the covariance matrix between contrasts can be given by $\Sigma^*=C'\Sigma C$ where $\Sigma$ is the data covariance matrix. 

We know our assumptions hold if $\Sigma^*$ has equal values on the principal diagonal and $0$ on the off-diagonal. This occurs when our data covariance matrix $\Sigma$ has equality between all off-diagonal elements and equality between elements on the principal diagonal. This corresponds exactly to our assumption of sphericity.

### An additional perspective

Talk about how MDK treats/explains sphericity


### Conclusion

The omnibus F test in RM-ANOVA is built by combining $k-1$ independent one-degree-of-freedom contrast tests. That combination is only mathematically valid if every contrast estimates the same error variance. Sphericity is the condition that guarantees this.