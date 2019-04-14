---
layout: post
title:  "Basic notions of Probability"
categories: stats
tags: data-science probability notes
---
Some personal notes on basic notions of probability.

# Probability vs Statistics?
When studying something, there is usually (1) a perfect mental model, so perfect that it doesn't exist in the real world; and (2) use the perfect mental model to reason about phenomena in the real world. Some examples:
- Geometry. 
	- Shapes as perfect as circles, spheres, etc doesn't quite exist - for example you can't draw a perfect circle on paper if you have a magnifying glass of sufficient power. 
	- But these perfect shapes are good enough models to reason about things. Treating the Sun as a perfect sphere is perfectly okay if you are trying to deduce something coarse (such as estimating the distance from the Sun to the Earth)
- Physics.
	- Classical equations are often based on a perfect model. For example, heat equation is derived from constant mass density. (Yeah, you can get rid of that probably - I just meant the very first version of it)
	- But it's already good enough to deduce something.

In this case, probability theory is the study of the perfect mental model; statistics is everything else. For example, we collected some real data. How can we fit these data to a mental model (or a family of it) that we have? Is the fitting real - are we collecting enough data? Data collection comes with a cost, can we get the same "strength" of conclusion by collecting less data? We want to make conclusions/inference from these real data, even though we only have a rough mental model. How confident are we about our conclusions? Et cetera.

# Notions 

# Probability space
## Definitions
- Probability space
	- The space of all possible outcomes.
	- Formally, $(\Omega, \mathcal{F}, \mu)$ - a set $\Omega$, a $\sigma$-algebra $\mathcal{F}$ on $\Omega$, and a probability measure $\mu$ on $\mathcal{F}$.
- Events
	- An element of $\mathcal{F}$ - i.e. a set of outcomes that can be measured.
- Probability measure
	- Size/measure of all measurable set of outcomes.
- Why isn't $\mathcal{F} \subset 2^{\Omega}$?
	- Assigning probability measure is the game of measuring sets, and being able to measure all subsets of outcome consistently is actually hard. 
	- For example, on $\mathbb{R}$, we "know" that $m((a,b)) = b-a$. But if we want translational invariance + countable additivity as well, then we can't measure all subsets of $\mathbb{R}$ if we believe in Axiom of Choice. C'est la vie.
		- (This was an example of an infinite probability measure, but the point stands in general - or maybe just repeat the same story for Lebesgue measure on $[0,1]$)

## Independence of events
- Independence of events
	- Two events $A, B$ are independent of each other if $P(A \cap B) = P(A) P(B)$.

## Conditional probability
- Conditional probability
	- We have tow events $A$ and $B$. Then the probability of $A$ happening given $B$ is 
$$P(A | B)  = \frac{P(A \cap B)}{P(B)}$$
- Bayes theorem
	- $$P(A | B) = \frac{P(A \cap B)}{P(B)} = \frac{P(B|A) P(A)}{P(B)}$$
	- Philosophically, you can relate $P(A | B)$ and $P(B | A)$. 
		- Important if you think of the case where $P(prior | data)$. This is the Bayesian way of thinking about probability: given new data, update your prior probability distribution. This is then related to $P(data | prior)$ (which is tractable) by Bayes' theorem.

# Random Variables
- Random Variable
	- A measurable function from probability space to a measurable space.
	- Common choices of the image:
		- Finite set with discrete measure (Discrete case)
		- $\mathbb{R}^n$ with Lebesgue measure. More generally, any Borel measurable space.
		
## Discrete random variable
- Probability mass function (pmf)
	- Let $X: \Omega \to S$ be a random variable, $S$ being discrete. 
	- We usually care about integral of random variables (e.g. expectations). The particular outcomes that lie in the event space doesn't matter so much.
	- For integration, knowing $s \to P(X^{-1}(s))$ is sufficient. This is the probability mass function.

## Continuous random variable
- Cumulative distribution function (cdf)
	- Let $X: \Omega \to \mathbb{R}$ be a random variable.
	- We usually care about integral of random variables (e.g. expectations). The particular outcomes that lie in the event space doesn't matter so much.
	- For integration, knowing $P(X^{-1}(A))$ for Lebesgue measurable $A$ is sufficient.
	- By approximation results, this is equivalent to knowing $P(X^{-1}((a,b)))$ for any $a,b$ - or even just $P(X^{-1}((-\infty, x))$.
	- The function $x \to P(X^{-1}((-\infty, x)) = P(X \leq x)$ is the cumulative distribution function (cdf).
- Probability density function (pdf)
	- Again, for purpose of integration, we care about the pushforward measure $A \to P(X^{-1}(A))$.
	- In nice cases, this is absolutely continuous wrt to Lebesgue measure. In other words, $P(X^{-1}(A)) = P(X \in A) = \int_A f(x) dx$ for some Lebesgue measurable $f$, if $dx$ is the Lebesgue measure.
	- If $P(X \in A) = \int_A f(x) dx$, we call $f(x)$ the probability density function (pdf).
	- In particular, $P(X \in (a,b)) = \int_a^b f(x) dx$.
- (?) What does probability distribution mean usually?

## Bivariate distributions
- Joint distribution
	- Let $X, Y$ be two random variables.
		- Does it have to be same probability space?
	- (?) The joint distribution is the probability density of the random variable $X \times Y$ on $\Omega_1 \times \Omega_2$
		- (?) Analogue of probability density
- (?) Marginal distribution

## Independence of random variables
- Independent random variables

## Conditional distributions

## Multivariate distributions
- i.i.d. samples

# Expectation of random variable
- Expectation
- Variance, Covariance
- Conditional expectation

# Inequalities
- Tail bound
	- Markov
	- Chebyshev
	- Hoeffding's inequality/VC dimension?

# Convergence of Random Variable
- Type of convergence
- Convergence theorems
   - Law of large numbers
   - Central limit theorem
