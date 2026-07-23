---
layout: post
title: What is Quantitative Psychology?
date: 2026-07-22
summary: What I do, explained simply.
categories: statistics quantitative psychology
---

![quant meme](/images/posts/quant-psych/quantmeme.png)

It's a running joke for those in the quant world that it's really hard to describe what we do. When someone asks what we study and we respond with "quantitative psychology", the near-universal response is either "What?" or "Oh, psychology? Can you read my mind?" That is—if they respond at all. The mere mention of anything statistics-related seems to evoke a trauma response (usually nausea or fear) in many people outside the field. 

When someone asks what I do, I say I study statistics in the field of psychology. I think this is a succinct description of the research I conduct, but it certainly isn't all-encompassing. Many individuals in my life have asked for a more expansive description of what I do, so the purpose of this blog post is to be an introduction to what exactly it is that I'm doing with my time in Arizona.

### So, can I read your mind?

For many laypeople, the term "psychologist" evokes images of a therapist or counselor, not someone who conducts research. This is the first big clarification that needs to be made: the field of psychology is extremely broad, and research is only a piece of a huge psych pie. Common types of psychologists include clinical psychologists, cognitive psychologists, developmental psychologists, forensic psychologists, I-O (industrial-organizational psychologists), sports psychologists, and more. Individuals who work in the psych field who aren't specifically psychologists can include psychiatrists (medical doctors who prescribe medications), therapists, counselors, social workers, and others. As you can see, many of these positions do not conduct research.

As a quantitative psychologist, I do. I am in the subset of psychologists (typically academics) whose primary focus is research, not applying psychological methods. In addition, the term *quantitative* reflects the fact that I study the statistical modeling methods themselves, not certain substantive topics in the field of psychology. As Mike Edwards (one of the quant faculty at ASU) puts it, "I'm not one of the psychologists who cares about people. I care about numbers."

### What is a quantitative psychologist?

A quantitative psychologist, simply put, is someone who studies research methods and design in the field of psychology. In other words, we assess methods of measuring, modeling, and predicting human behavior. This area of focus is contrasted with *substantive* psychologists: researchers who study a specific facet of human behavior. In empirical psychological work, these foci work in tandem to produce quality research. For example, someone who studies child development may conduct research through student surveys in a certain schooling district to try and understand how an intervention program can increase feelings of social acceptance. If a substantive researcher and a quantitative researcher were both working on the project, the substantive psychologist would be the expert in understanding the different dimensions of social acceptance in children, what risk factors may be prudent to ask about in a survey, and what types of interventions are theorized to be the most effective. On the other hand, the quantitative psychologist would be the expert in designing the survey in order to ensure they are measuring the topic of interest, understanding what methods of statistical analysis work best with the type of data collected, and running/interpreting the results of said analyses.

Alongside conducting statistical analyses in applied research, quantitative researchers also strive to make contributions to the field of psychology through studying the statistical methods themselves. For example, in assessing the impact of an intervention with two-wave data, two commonly used methods are an autoregressive model and a difference model (don't worry if you're not totally familiar). Research into the effectiveness of these two competing methods could include mathematical derivations of certain parameters (coefficients) in the models or simulating data from a certain model to assess the resulting estimates. Research topics such as these are the main focus of study for most quantitative psychologists.

| Autoregressive model | Difference model |
| --- | --- |
| $y_{2i} = a_0 + a_1y_{1i} + a_2x_i + e_i$ | $\Delta_i = b_0 + b_1x_i + e_i$ |

The quantitative methods used in quant psych are also commonly used in many other fields, including biostats, finance, and machine learning. As a result, the skills we learn are ubiquitous to many areas of study, and individuals who graduate with a PhD in quantitative psychology often find work as biostatisticians, econometricians, or other niche positions.

### What are the specific subfields of quantitative psychology?

Now we're getting into the specifics of what I study. Broadly speaking, work in quantitative psychology can be categorized into a variety of subfields. Two of the most prominent are psychometrics and statistical modeling.

#### Psychometrics

Psychometrics, at its core, is the area of quantitative psychology relating to *measurement*. An important thing to note about statistics in psychology is that they are almost always latent variable statistics. When we are interested in a psychological *construct* (i.e., a theoretical concept like depression), we are unable to observe it directly. We cannot (unfortunately) open someone's head and pull out a number representing that person's level of depression, anxiety, life satisfaction, etc. So, we must come up with methods of measuring these constructs. 

This leads to a whole host of intricacies. If we have a scale measuring depression like the Center for Epidemiologic Studies Depression Scale (CES-D), there are **many** questions relating to measurement we can ask. For example:

* How much can we trust a score from one single measurement occasion? Do people tend to get the same result if we give the test multiple times? In other words, how *reliable* is the score? 
* How well does the scale represent the underlying construct? If we care about all dimensions of depression, are there test questions that tap all of these dimensions? How *valid* is the score?
* If different questions measure different parts of depression (like sleep, emotional affect, appetite, social withdrawal, etc.), how should the test be scored? Should we weight all of these items equally?
* Which questions seem to discriminate (filter) between levels of the underlying construct the best? Are there some questions that everyone answers "yes" to? Are there some questions that everyone answers "no" to? How should we handle these items?
* Are there certain patterns of answering that are evoked? Do certain groups of items seem to "cluster" together? (i.e., are there different observable factors of depression?)
* Do all of the items function similarly across different populations? For example, are men and women interpreting the question "I cry easily" in the same way? What about across different cultures? Different times?

As you can see, a seemingly simple questionnaire can actually hold a wealth of more interesting measurement questions. 

The shocking thing is that most of these questions need addressing *even before* we run formal statistical methods on our data. This is why psychometrics is such a cool and theoretical field: there is a lot of philosophical pondering about the nature of measurement. Some of the most common frameworks for psychometricians include Classical Test Theory and Item Response Theory. Classical Test Theory is the class of psychometrics that attempts to represent each individual's observed score as the sum of two parts: their true level of the latent construct (true score; e.g., someone's expected observed level of depression) and error (non-structural components of the score; e.g., daily fluctuations in how they're feeling). Item Response Theory is the area of psychometrics concerned with item-level analysis. It allows us to formally represent the difficulty and discrimination (filter-ability) of each item in a scale.

In 1946, S. S. Stevens defined measurement as "the assignment of numerals to objects or events according to some rule." Now in the 21st century, we are still discovering new ways of how the idea of measurement impacts how we think about psychological concepts.

#### Statistical modeling

Statistical modeling in psychology is a vast field. At its core, it seeks to model and predict human behavior. For example, imagine that you are a researcher and have the theory that young children, over time, learn new vocabulary words at a very slow rate at an early age, followed by an explosion of vocabulary increases at toddler age, finally tapering off logarithmically as children reach adolescence. How in the world can you test this? 

As it turns out, there are modeling techniques that would allow you to test the accuracy of this claim. In fact, modeling techniques exist for a *massive* breadth of possible hypotheses, leading to different subfields even within the area of modeling. Some of these specialized areas include:

* Longitudinal modeling: How can we assess change over time?
* Mixture modeling: How can we assess data with specific subgroups of participants?
* Regression techniques: How can we predict an outcome from an observed predictor variable?
* Structural equation modeling: How can we represent complex theorized networks in our data and test their accuracy?
* Multilevel modeling: How can we best analyze data that may be clustered (e.g., patients nested within hospitals)?
* Nonlinear modeling: How can we model data that are nonlinear (e.g., data that follow exponential/logarithmic patterns)?
* Survival analysis: How can we predict data that are characterized by the onset of one specific event?
* Time-series modeling: How can we assess data that have intensive, densely repeated observations?

And many others. There are obviously significant overlaps between many of these topics, and projects in statistical modeling draw from several of these areas as foundational frameworks. Researchers who work in these areas typically develop and analyze the current statistical techniques used in the field of psychology to contribute to better science.

In addition to psychometrics and statistical modeling are myriad other subfields in quantitative psychology. These include, but are not limited to: causal inference, metascience, mediation, Bayesian methods, estimation techniques, and machine learning. The common denominator tying all of these areas together is that they are all focused on assessing and improving the statistical methods utilized in the field of psychology and other social sciences. 

### What I do

Currently, my work is most accurately characterized as **longitudinal** work situated in the **structural equation modeling** framework. So, I assess, improve, and create methods for the assessment of data measured at multiple timepoints. For instance, I have recently been conducting a project proposing a new method for the analysis of *panel data*: longitudinal data characterized by the measurement of multiple variables per participant at each timepoint. As an example, imagine that you have a measure of life satisfaction and a measure of workplace acceptance at multiple timepoints for a sample of 500 individuals. You want to determine how these two variables interact with each other over time. Does a higher level of workplace acceptance result in higher life satisfaction? Does this pattern hold both at large and for a specific individual? How can we test this?

There are a few common methods of assessing multivariate change over time when you have panel data, including the Random-Intercepts Cross-Lagged Panel Model (RI-CLPM) and the Latent Curve Model with Structured Residuals (LCM-SR). These methods attempt to separate between-person effects (do people who generally feel more accepted than others also report greater life satisfaction?) from within-person effects (during periods when a particular person feels more accepted than usual, do they also feel more satisfied than usual?). I propose a new method, the First Difference Model, that is a method of assessing within-person effects that is less *parametric* (defined by specific coefficients) than the other common techniques. For more information, feel free to check out [my research]({{ site.baseurl }}/research).

If you don't totally understand what that means, that's OK! The point is that I conduct research on the *methods themselves* that are commonly used in psychological research.

### Why all of this matters

Distinctions between "types of effects" might sound technical and overly pedantic, but they can meaningfully change the conclusions researchers draw. If we confuse differences between people with changes within a person, we might conclude that increasing workplace acceptance will improve life satisfaction when the data do not actually support that claim. That's why it's really important to model these effects as accurately as possible.

In general, what seem like statistical minutiae can seriously impact real-world events. Consider a mental health screening aimed at determining whether or not they're fit to fly a plane. You'd better make damn sure it's as reliable, valid, and statistically-supported as possible. Psychometrics can help you answer the question "does this really measure mental health?" Statistical modeling can help you answer the question "how can we predict and model different levels of mental health among pilots?" Quantitative psychology works to constantly improve these methods of analysis.

### Conclusion

I hope this was helpful to those of you who were somewhat unfamiliar with what "quantitative psychology" was. Many of the different subfields I described all overlap and interact with each other in really intriguing and motivating ways: psychometricians often situate their work in the structural equation modeling world, machine learning researchers often compare their results to established modeling techniques, causal inference people need to consider the reliability/validity of their models, Bayesians have their own version of just about every method on the planet. 

I'll probably keep telling people I sit next to on flights that I study statistics in the field of psychology. Now, you can judge for yourself whether this is an accurate description or not ;)