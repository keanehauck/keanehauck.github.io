---
layout: post
title: Proving the Central Limit Theorem for Dummies
date: 2026-06-07
summary: Characteristic functions, moment generating functions, pull up at the functions.
categories: statistics proof mathematics
---

A frequently-mentioned concept in quantitative psychology is the [Central Limit Theorem](https://en.wikipedia.org/wiki/Central_limit_theorem), which states that the sampling distribution of the sample mean approaches a normal distribution as $n$ gets large (typically $\geq30$). This theorem has important implications for typical hypothesis testing in psychological research. For example, if we are attempting to determine if two groups have significantly different means, we can use a t-test even if the groups have non-normal distributions in the population, because the CLT ensures that the distribution of the sample mean will approximate a normal distribution. Thus, we can compare the difference in observed means to a theoretical t distribution and calculate associated p-values. 

This concept gets taught in many introductory statistics classes. In fact, I learned it in the intermediate statistics class taught by Samantha Anderson. However, in the psych world, understanding a rigorous proof of the CLT requires mathematical ability *much* more advanced than what is typically expected of students (myself included). So a proof of the CLT is typically glossed over.

In this post, I am going to try and unpack a typical proof of the Central Limit Theorem. Much of the math here is new to me, so I will describe everything that I had to learn in order to understand the mechanisms going on under the hood.

### Some definitions

If you are not familiar with more advanced probability (I am not), it will be helpful to cover some of the tools which will be helpful as we try to tackle this proof. First is the concept of *moments*.

Moments, in probability, are defined as the expected value of an exponentiated random variable. More precisely, the *n*th moment of a random variable is equal to $E[X^n]$. There are also central moments, where the *n*th central moment of a random variable $X$ is defined as $E[(X-E[X])^n]$. Moments are useful because they map to very important concepts in statistics. The 1st moment, $E[X]$, is the mean of $X$. The second central moment is the variance, the third standardized moment is the skewness, and the fourth standardized central moment is the kurtosis. Helpful indeed.

Following from this, another important concept is *moment-generating functions* (MGFs). They are functions of random variables defined as $$M_X(t)=E[e^{tX}].$$

A moment-generating function allows us to calculate all of the moments of $X$. In addition, a MGF contains the same "information" as a probability density function (PDF) in the sense that if we know a variable's characteristic function, we know its probability density function. This means that two variables with the same MGFs have the same underlying distribution. Moment-generating functions index over $t$, not the random variable $X$ itself, but we can recover the moments of the original PDF of $X$ from them. 

Do you remember your Taylor series? I certainly didn't. Here is one example of how they can be applied. The Taylor series expansion for $e^x$ is 

$$e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots = \sum_{k=0}^{\infty} \frac{x^k}{k!}.$$ 

Because the MGF of $X$ is defined as $E[e^{tX}]$, we can show 

$$M_X(t)=E[e^{tX}]=\sum_{k=0}^{\infty} E[X^k] \frac{t^k}{k!}.$$

The *k*th moments of $X$ are equal to the coefficient of $ \frac{t^k}{k!}$ in the Taylor series expansion. 

There are two more important functions to know. A *cumulant generating function* (CGF) is defined as $K_X(t)=\ln [M_X(t)]$. The derivatives of the CGF at $0$ are called cumulants, and the cumulants recover the moments (the first cumulant is $E[X]$, the second cumulant is the variance, etc). Similarly, we also have characteristic functions (CFs). Characteristic functions work very similarly to MGFs, but they are defined everywhere. However, they may involve complex numbers. They are represented with the notation $\phi(t)$ and are defined as $\phi_X(t)=E[e^{itX}]$ where $i$ is the imaginary unit. Again, a lot of this math is over my head, so I don't totally understand why these functions involve imaginary numbers.

All of these functions basically contain the same "information." If you know a random variable's MGF, you also know its CGF, CF, PDF, and thus underlying distribution.

One really important property of MGFs and CFs is that they allow you to sum random variables. They have the property $\phi_{X+Y}(t) =\phi_X(t)\phi_Y(t)$.


### The proof

A typical proof structure starts with stating the moment generating functions of a variable and then builds up to an application of the characteristic function of a normally distributed random variable. I am going to reverse the direction of the proof and provide the material starting from the endpoint. The purpose is twofold. For one reason, having knowledge of where we're trying to go helps understand why certain concepts are defined the way they are. Additionally, this will not be a completely formal representation, so this presentation allows for more fluidity in description.

One important caveat: for the following math, all variables are assumed to be mean-centered at $0$. Similarly, the random variables $X_1+\cdots+X_n$ are assumed to be independent.

We start with the end goal. Consider the following statement:

$$ \phi_{\frac{X_1+\cdots+X_n}{\sqrt{n}}}(t)=\left(1-\frac{\sigma^2}{2n}t^2+O\!\left(\frac{t^3}{n^{3/2}}\right)\right)^n\longrightarrow e^{-\frac{\sigma^2}{2}t^2}. $$

This is the final step of proving the Central Limit Theorem. What is going on here?

We see $\phi$, so we know we have characteristic functions. The overall equation here is notable because it is an application of Lévy's Continuity Theorem, which states that if we have a sequence of characteristic functions $\phi_n(t)$ which converge to some function $\phi(t)$, then if $\phi(t)$ is continuous at $t=0$ then $\phi(t)$ is the characteristic function of a random variable $X$ *and* the distributions of the sequence of random variables $X_n$ and the distribution represented by the characteristic function on the right-hand side of the equation converge. In other words, if on one side of the equation we have a sequence of characteristic functions for $X_n$ and on the other side we have the characteristic function for $X$, they will converge. 

So, because we know that the right-hand side is the characteristic function for a normally-distributed variable, if the left hand side is a sequence of characteristic functions for $X_n$ (which it is), we can use Lévy's Continuity Theorem to prove that the sequence of characteristic functions and $X$ converge to the same normal distribution.

Ok, so how does the math work in that equation? It still seems like a jumble of numbers. Well, the first thing I was confused about is what that $O$ meant. Remember Big-O notation from computer science, where it described the time complexity of a function? *Apparently*, in applications like this it refers to the size of the errors without having to specify the exact formula. So, because we are using a Taylor series expansion, instead of writing out all of the terms after the 2nd one we can just provide an "upper bound" with $O$ notation and call it a day. So, when we are conducting the limit, we can treat it as a single term.

Due to some limit math behind the scenes, it is the case that the expression indeed converges to the result we are interested in. This math works out IF the characteristic function for a a random variable $X_i$ is equal to $\phi_{X_i}(t) = 1 - \frac{\sigma^2}{2}t^2 + O(t^3).$ So, the problem becomes, why is that the characteristic function for $X_i$?

It comes from a Taylor expansion of the characteristic function. Remember that the characteristic function is defined as $\phi_X(t)=E[e^{itX}]$. If we expand the exponential, we get 

$$e^{itX}=1+itX-\frac{t^2X^2}{2}+\cdots$$

We can then take expectations. Remember that $E[X^2]=\sigma^2$. So, the expectation of the Taylor series is $1-\frac{\sigma^2}{2}t^2+\cdots$. Because all higher-order terms involve $t^3$, we can represent them using the $O$ notation discussed earlier, and group them together like so:

$$\phi_{X_i}(t) = 1 - \frac{\sigma^2}{2}t^2 + O(t^3).$$

Which recovers our original hope for what the characteristic function for a random variable $X_i$ would be equal to. So, we have actually done most of what is required—it just needed a lot of definitions of what characteristic functions are and how they work.

### Recap

Now we can reverse my jumble of words and recap the process in order. We want to prove that the distribution of sample means will converge to the normal distribution as $n$ gets large. Using our new knowledge, we recognize that if we have a normalized sum of random variables $S_n=\frac{X_1+\cdots+X_n}{\sqrt n}$ then we can represent the characteristic function for a given $X_i$ as $\phi_{X_i}(t) = 1 - \frac{\sigma^2}{2}t^2 + O(t^3)$.

If this is our characteristic function, we can represent the sequence of characteristic functions for all $X$ in our set as 

$$\phi_{\frac{X_1+\cdots+X_n}{\sqrt{n}}}(t)=\left(1-\frac{\sigma^2}{2n}t^2+O\!\left(\frac{t^3}{n^{3/2}}\right)\right)^n.$$

Then, we can perform some limit math to discover that it converges to the characteristic function for the normal distribution. Applying Lévy's Continuity Theorem tells us that the distributions of the sequence of random variables $X_n$ and the distribution represented by the characteristic function on the right-hand side of the equation converge. Thus, we have proven that our normalized sum of random variables (sampling distribution) converges to the normal distribution.

### Conclusion

This is probably the most hand-waving I've ever done while writing about a stats topic. There was obviously a lot of glossing over the mathy steps in the proof. If you want to point fingers, blame the fact that the proof I was reading was exactly $1$ step: it just defined the characteristic functions for independent random variables $X_i$ and for a normal distribution. But now we know! (Kind of.)