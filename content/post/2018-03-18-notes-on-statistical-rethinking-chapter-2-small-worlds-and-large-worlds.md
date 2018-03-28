---
title: Notes on Statistical Rethinking (Chapter 2 - Small Worlds and Large Worlds)
author: José Roberto Ayala Solares
date: '2018-03-18'
categories:
  - StatisticalRethinking
tags:
  - bayesian
  - notes
slug: notes-on-statistical-rethinking-chapter-2-small-worlds-and-large-worlds
header:
  caption: ''
  image: ''
summary: Notes for Chapter 2 of [Statistical Rethinking](http://xcelab.net/rm/statistical-rethinking/)
---

> All statistical modeling has two frames: the small world of the model itself and the large world we hope to deploy the model in.

> The small world is the self-contained logical world of the model. Within the small world, all possibilities are nominated. There are no pure surprises. Within the small world of the model, it is important to be able to verify the model’s logic, making sure that it performs as expected under favorable assumptions. Bayesian models have some advantages in this regard, as they have reasonable claims to optimality: **No alternative model could make better use of the information in the data and support better decisions, assuming the small world is an accurate description of the real world.**

> The large world is the broader context in which one deploys a model. In the large world, there may be events that were not imagined in the small world. Moreover, the model is always an incomplete representation of the large world, and so will make mistakes, even if all kinds of events have been properly nominated. The logical consistency of a model in the small world is no guarantee that it will be optimal in the large world.

## 2.1. The garden of forking data
> In order to make good inference about what actually happened, it helps to consider everything that could have happened. A Bayesian analysis is a garden of forking data, in which alternative sequences of events are cultivated. As we learn about what did happen, some of these alternative sequences are pruned. In the end, what remains is only what is logically consistent with our knowledge.

> Principle of Indifference: when there is no reason to say that one conjecture is more plausible than another, weigh all of the conjectures equally. The issue of choosing a representation of “ignorance” is surprisingly complicated. The principle of indifference results in inferences very comparable to mainstream non-Bayesian approaches, most of which contain implicit equal weighting of possibilities. For example a typical non-Bayesian confidence interval weighs equally all of the possible values a parameter could take, regardless of how implausible some of them are.

## 2.2. Building a model
> Designing a simple Bayesian model benefits from a design loop with three steps:

> 1. Data story: Motivate the model by narrating how the data might arise.
2. Update: Educate your model by feeding it the data.
3. Evaluate: All statistical models require supervision, leading possibly to model revision.

### 2.2.2. Bayesian updating
> There is a widespread superstition that 30 observations are needed before one can use a Gaussian distribution. Why? In non-Bayesian statistical inference, procedures are often justified by the method’s behavior at very large sample sizes, so-called asymptotic behavior. As a result, performance at small samples sizes is questionable. In contrast, **Bayesian estimates are valid for any sample size.** This does not mean that more data isn’t helpful — it certainly is. Rather, the estimates have a clear and valid interpretation, no matter the sample size. But the price for this power is dependency upon the initial estimates, the prior. If the prior is a bad one, then the resulting inference will be misleading. **There’s no free lunch, when it comes to learning about the world. A Bayesian golem must choose an initial plausibility, and a non-Bayesian golem must choose an estimator.** Both golems pay for lunch with their assumptions.

### 2.2.3. Evaluate
> The model’s certainty is no guarantee that the model is a good one. Models of all sorts — Bayesian or
not — can be very confident about an estimate, even when the model is seriously misleading.
This is because the estimates are conditional on the model. What your model is telling you
is that, given a commitment to this particular model, it can be very sure that the plausible
values are in a narrow range. Under a different model, things might look differently.

> The goal model checking is not to test the truth value of the model’s assumptions. We know the model’s assumptions are never exactly right, in the sense of matching the true data generating process. **Therefore there’s no point in checking if the model is true.** Failure to conclude that a model is false must be a failure of our imagination, not a success of the model. **Moreover, models do not need to be exactly true in order to produce highly precise and useful inferences.** All manner of small world assumptions about error distributions and the like can be violated in the large world, but a model may still produce a perfectly useful estimate. This is because models are essentially information processing machines, and there are some surprising aspects of information that cannot be easily captured by framing the problem in terms of the truth of assumptions.

## 2.3. Components of the model
* Likelihood: a mathematical formula that specifies the plausibility of the data. What this means is that the likelihood maps each conjecture onto the relative number of ways the data could occur, given that possibility.
* Parameters: they are adjustable inputs and represent the different conjectures for causes or explanations of the data.
* Prior: it is an initial plausibility assignment for each possible value of a parameter.
* Posterior: the relative plausibility of different parameter values, conditional on the data.

> No one is required to swear an oath to the assumptions (likelihoods, parameters and priors) of a model, and no set of assumptions deserves our obedience.

## 2.4. Making the model go
Conditioning engines are numerical techniques for computing posterior distributions. Common ones are:

1. Grid approximation
2. Quadratic approximation
3. Markov chain Monte Carlo (MCMC)

### 2.4.1 Grid approximation
No practical. It scales very poorly, as the number of parameters increases.

### 2.4.2 Quadratic approximation
> Under quite general conditions, the region near the peak of the posterior distribution will be nearly Gaussian in shape. This means the posterior distribution can be usefully approximated by a Gaussian distribution. A Gaussian distribution is convenient, because it can be completely described by only two numbers: the location of its center (mean) and its spread (variance). The procedure contains two steps:

> 1. Find the posterior mode. This is usually accomplished by some optimization algorithm.
2. Once you find the peak of the posterior, you must estimate the curvature near the
peak. This curvature is sufficient to compute a quadratic approximation of the
entire posterior distribution. In some cases, these calculations can be done analytically,
but usually your computer uses some numerical technique instead.

The `rethinking` package has the `map` function. MAP stands for Maximum A Posteriori, which is just a fancy Latin name for the mode of the posterior distribution. To use `map`, you provide a formula, a list of data, and a list of start values for the parameters. The formula defines the likelihood and prior.

### 2.4.3 Markov chain Monte Carlo
> There are lots of important model types, like multilevel (mixed-effects) models, for which neither grid approximation nor quadratic approximation is always satisfactory. Markov chain Monte Carlo (MCMC), which is a family of conditioning engines capable of handling highly complex models. Instead of attempting to compute or approximate the posterior distribution directly, MCMC techniques merely draw samples from the posterior. You end up with a collection of parameter values, and the frequencies of these values correspond to the posterior plausibilities. You can then build a picture of the posterior from the histogram of these samples.

## References
McElreath, R. (2016). *Statistical rethinking: A Bayesian course with examples in R and Stan.* Chapman & Hall/CRC Press.

Kurz, A. S. (2018, March 9). *brms, ggplot2 and tidyverse code, by chapter*. Retrieved from https://goo.gl/JbvNTj
