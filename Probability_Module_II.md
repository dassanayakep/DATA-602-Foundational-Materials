**© [2026] [Placida Dassanayake]. All Rights Reserved.**

This notebook and its contents are protected by copyright. Unauthorized reproduction, distribution, or transmission of any part of this work, in any form or by any means, without the prior written permission of the copyright holder, is strictly prohibited.

# Module II: Random Variables
**Learning Objectives**

When you have completed this module, you should be able to:


*   Distinguish between discrete and continuous random variables
*   Identify characteristics of a probability distribution and compute mean, variance, and standard deviation of a variable using its probability distribution


*   Compute mean, variance, and standard deviation of a linear transformation of a variable
*   Describe and compute probabilities of three discrete probability distributions: Binomial, Hypergeometric, and Poisson.


*   Describe and compute probabilities of two continuous probability distributions: Exponential and Normal.
*   Describe and compute probabilities for Standard Normal Distribution.
*  Utilize programming language R to compute complex probabilities.




## 2.1. Random Variables and Probability Distribution of a Random Variable


In any random experiment, outcomes occur unpredictably. While we can list all possible outcomes, only one will actually happen. For example, when tossing a coin twice, the possible outcomes are *HH*, *HT*, *TH*, and *TT*. This randomness leads us to the concept of random variables, which help quantify outcomes in such experiments.


A random variable is a numerical value determined by the outcome of a random experiment.


In other words, a random variable assigns a numerical value to each possible outcome in a sample space, allowing us to analyze and calculate probabilities. Random variables can be classified into two types:


1.	**Discrete Random Variable**: Takes on a finite or countable number of values, often associated with scenarios where outcomes are distinct and separate (e.g., number of customer calls received by a support center in an hour).
2.	**Continuous Random Variable**: Takes on an infinite number of values within a range, associated with measurements that vary smoothly (e.g., the amount of time a customer spends on a call with support).
We use upper case letter as labels for random variables (X, Y, and Z) and lower case of the letter to indicate any possible value of that variable (*x*, *y* and *z*)   

Let us explore the following examples:

For each experiment below, identify the random variable, list the possible values it can take, and classify it as discrete or continuous.


1.	Experiment: Counting the number of emails received in a day.

  Random Variable X -

  Possible values x -

  Classification:

2.	Experiment: Timing how long a car takes to travel between two cities.

  Random Variable Y -  

  Possible Values y -  

  Classification:

3.	Experiment: Counting the number of students present in a class on a given day.

  Random Variable W -  

  Possible Values w -  

  Classification:

4.	Experiment: Tossing three coins and counting the number of Heads tossed.

  Random Variable V -

  Possible Values v -

  Classification:


## 2.2. Probability Distribution of a Discrete Random Variable

In the preceding experiments, each random variable was characterized by a well-defined set of possible values. By systematically assigning probabilities to these values using the principles developed in the previous module, we construct the *probability distribution* of the random variable.

Formally, a probability distribution specifies the complete probabilistic behavior of a random variable by associating every possible outcome with its corresponding probability. For a discrete random variable \(X\), the distribution can be represented as the collection

$$
\{(x_i, P(X=x_i))\},
$$

where each $x_i$ denotes a possible realization of $X$, and $P(X=x_i)$ denotes the probability that the variable assumes that value.

The fundamental properties of a probability distribution are summarized below:

1. **Non-negativity and Boundedness**  
   For every possible outcome $x_i$,

   $$
   0 \leq P(X=x_i) \leq 1.
   $$

   Hence, each probability is constrained to lie within the interval $[0,1]$.

2. **Mutual Exclusivity of Outcomes**  
   The outcomes in the distribution are mutually exclusive, implying that the occurrence of one outcome precludes the occurrence of any other outcome simultaneously.

3. **Exhaustiveness (Normalization Condition)**  
   The set of outcomes is collectively exhaustive; therefore, the total probability over all possible outcomes must equal unity:

   $$
   \sum_i P(X=x_i) = 1.
   $$
Together, these properties ensure that a probability distribution provides a mathematically consistent framework for modeling uncertainty and quantifying the likelihood of different outcomes of a random phenomenon.


For a discrete random variable, the probability distribution can be represented either in tabular form or via a probability mass function graph. In rigorous probabilistic modeling, the distribution fully characterizes the stochastic behavior of the variable and serves as the foundation for inference and decision-making.

We now revisit selected canonical examples to formalize the construction of probability distributions.



## Example 1: Coin Toss Experiment (Bernoulli Trials Aggregation)

**Experiment:** A fair coin is tossed three times.

The sample space is:

$$
S = \{HHH, HHT, HTH, HTT, THH, THT, TTH, TTT\}
$$

Let the random variable \(X\) denote the number of heads observed in the three trials.

Thus, \(X\) maps each outcome to a numerical value:

- \(HHH to 3\)
- \(HHT, HTH, THH to 2\)
- \(HTT, THT, TTH to 1\)
- \(TTT to 0\)

Hence, the support of \(X\) is:

$$
x \in \{0,1,2,3\}
$$



### Probability Mass Function Construction

We compute probabilities by aggregating equally likely outcomes:

$$
P(X=0) = P(TTT) = \frac{1}{8}
$$

$$
P(X=1) = P(HTT, THT, TTH) = \frac{3}{8}
$$

$$
P(X=2) = P(HHT, HTH, THH) = \frac{3}{8}
$$

$$
P(X=3) = P(HHH) = \frac{1}{8}
$$



### Probability Distribution Table

| x | P(X=x)  |
|----:|----------:|
| 0   | 0.125     |
| 1   | 0.375     |
| 2   | 0.375     |
| 3   | 0.125     |
| **Total** | **1** |




## Example 2: Multiple Choice Guessing Model (Binomial Structure)

**Experiment:** A student randomly guesses answers to three multiple-choice questions, each with four options and exactly one correct answer.

Define:
- \(C\): correct guess
- \(W\): incorrect guess

The sample space is:

$$
S = \{CCC, CCW, CWC, CWW, WCC, WCW, WWC, WWW\}
$$

Let \(Y\) denote the number of correct guesses.

Thus:

$$
y \in \{0,1,2,3\}
$$



### Probability Computation

Assuming independent trials with:

- P(C) = $\frac{1}{4}$
- P(W) = $\frac{3}{4}$



#### Zero correct guesses

$$
P(Y=0) = P(WWW) = \left(\frac{3}{4}\right)^3 = 0.421875
$$



#### Exactly one correct guess

$$
P(Y=1) = P(CWW + WCW + WWC)
$$

$$
= \frac{1}{4}\left(\frac{3}{4}\right)^2 + \frac{3}{4}\cdot\frac{1}{4}\cdot\frac{3}{4} + \left(\frac{3}{4}\right)^2\cdot\frac{1}{4}
$$

$$
= 0.421875
$$



#### Two and three correct guesses

$$
P(Y=2) = 0.140625
$$

$$
P(Y=3) = 0.015625
$$



### Probability Distribution Table

| $y$ | P(Y=y) |
|----:|----------:|
| 0   | 0.421875  |
| 1   | 0.421875  |
| 2   | 0.140625  |
| 3   | 0.015625  |
| **Total** | **1** |



## Example 3: Empirical Discrete Distribution (Baseball Performance Data)

Consider a dataset from the 2007 baseball season in which a player participates in 74 games, each consisting of exactly four at-bats.

Let \(X\) denote the number of hits in a given game.

We are given a partially observed empirical distribution of \(X\), which must be completed using the normalization condition:

$$
\sum_x P(X=x) = 1
$$

### Required Tasks

1. Complete the probability distribution table for \(X\) using empirical frequency normalization.
2. Compute the probability that the player achieves fewer than two hits in a game:

$$
P(X < 2) = P(X=0) + P(X=1)
$$



## Summary Statistics of a Discrete Random Variable

Beyond describing outcome likelihoods, probability distributions provide a foundation for deriving key statistical functionals, notably the expected value and measures of dispersion.



## Expected Value (Mean)

The expected value of a discrete random variable \(X\), denoted \(E(X)\) or \(\mu\), is defined as:

$$
\mu = E(X) = \sum_{i=1}^{n} x_i \, P(X=x_i)
$$

This represents a probability-weighted average of all possible realizations and corresponds to the long-run mean under repeated sampling.



## Variance and Standard Deviation

The variance quantifies dispersion around the mean:

$$
\sigma^2 = \mathrm{Var}(X) = \sum_{i=1}^{n} (x_i - \mu)^2 P(X=x_i)
$$

An equivalent computational identity is:

$$
\sigma^2 = E(X^2) - \mu^2
$$

The standard deviation is the square root of variance:

$$
\sigma = \sqrt{\mathrm{Var}(X)}
$$



These measures jointly provide a complete second-order characterization of a discrete random variable, capturing both central tendency and variability within a probabilistic framework.

# Example 1(re-visit): Coin Toss (3 Independent Bernoulli Trials)

Let \(X\) be the number of heads in three fair coin tosses.

The probability distribution is:

| x | P(X=x) |
|------:|-----------:|
| 0 | 1/8 |
| 1 | 3/8 |
| 2 | 3/8 |
| 3 | 1/8 |



## Expected Value \(E(X)\)

$$
E(X) = \sum x P(X=x)
$$

$$
E(X) = 0\cdot\frac{1}{8} + 1\cdot\frac{3}{8} + 2\cdot\frac{3}{8} + 3\cdot\frac{1}{8}
$$

$$
E(X) = \frac{0 + 3 + 6 + 3}{8} = \frac{12}{8} = 1.5
$$



## Variance ($\mathrm{Var}(X)$)

First compute:

$$
E(X^2) = 0^2\cdot\frac{1}{8} + 1^2\cdot\frac{3}{8} + 2^2\cdot\frac{3}{8} + 3^2\cdot\frac{1}{8}
$$

$$
E(X^2) = \frac{0 + 3 + 12 + 9}{8} = \frac{24}{8} = 3
$$

Now:

$$
\mathrm{Var}(X) = E(X^2) - [E(X)]^2
$$

$$
\mathrm{Var}(X) = 3 - (1.5)^2 = 3 - 2.25 = 0.75
$$



## Standard Deviation

$$
SD(X) = \sqrt{0.75} \approx 0.866
$$





```R
# Probability distribution
x <- c(0,1,2,3)
p <- c(1/8, 3/8, 3/8, 1/8)

# Expected value
EX <- sum(x * p)

# E(X^2)
EX2 <- sum((x^2) * p)

# Variance and SD
VarX <- EX2 - EX^2
SDX <- sqrt(VarX)

EX
VarX
SDX
```


1.5



0.75



0.866025403784439


# Example 2
You draw **3 cards from a standard 52-card deck**.

Let:

   X = winnings in dollars

Payoff structure:

- 0 Kings → $0

- 1 King → $10

- 2 Kings → $20

- 3 Kings → $30  



We assume all 3-card hands are equally likely. Compute the expected winnings and standard deviation.

---
# Quick Review: Counting Rules - Combinations

In probability problems involving selection *without regard to order*, we use combinations.

The number of ways to choose \(r\) objects from \(n\) distinct objects is:

$$
\binom{n}{r} = \frac{n!}{r!(n-r)!}
$$

Key interpretation:

- Order does **not** matter
- Used for counting selections from decks, lotteries, and sampling problems

Example:
- Number of ways to choose 3 cards from 52 with out replacement:
$$
\binom{52}{3} = \frac{52 \cdot 51 \cdot 50}{3 \cdot 2 \cdot 1} = 22100
$$

---


# Total Sample Space

Each outcome corresponds to selecting any 3 cards:

$$
|\Omega| = \binom{52}{3} = 22100
$$


We now compute each case using counting arguments.


## Case 1: 0 Kings

Choose all 3 cards from the 48 non-Kings:

$$
\text{Favorable outcomes} = \binom{48}{3} = 17296
$$

$$
P(X=0) = \frac{17296}{22100} \approx 0.7829
$$


## Case 2: 1 King

Choose:

- 1 King from 4: $\binom{4}{1}$
- 2 non-Kings from 48: $\binom{48}{2}$

$$
\text{Favorable outcomes} = \binom{4}{1}\binom{48}{2}
$$

$$
= 4 \cdot 1128 = 4512
$$

$$
P(X=10) = \frac{4512}{22100} \approx 0.2042
$$


## Case 3: 2 Kings

$$
\binom{4}{2}\binom{48}{1} = 6 \cdot 48 = 288
$$

$$
P(X=20) = \frac{288}{22100} \approx 0.0130
$$


## Case 4: 3 Kings

$$
\binom{4}{3}\binom{48}{0} = 4
$$

$$
P(X=30) = \frac{4}{22100} \approx 0.000181
$$



# Probability Distribution Table

| Winnings \(X\) | Probability |
|----------------:|------------:|
| 0  | 17296 / 22100 ≈ 0.7829 |
| 10 | 4512 / 22100 ≈ 0.2042 |
| 20 | 288 / 22100 ≈ 0.0130 |
| 30 | 4 / 22100 ≈ 0.000181 |



# Expected Value \(E(X)\)

$$
E(X) = \sum x P(X=x)
$$

$$
E(X) =
0 \cdot \frac{17296}{22100}
+ 10 \cdot \frac{4512}{22100}
+ 20 \cdot \frac{288}{22100}
+ 30 \cdot \frac{4}{22100}
$$

Numerically:

$$
E(X) \approx 2.04
$$



# Second Moment \(E(X^2)\)

$$
E(X^2) = \sum x^2 P(X=x)
$$

$$
E(X^2) =
100 \cdot \frac{4512}{22100}
+ 400 \cdot \frac{288}{22100}
+ 900 \cdot \frac{4}{22100}
$$

$$
E(X^2) \approx 24.98
$$



# Variance and Standard Deviation

## Variance

$$
\mathrm{Var}(X) = E(X^2) - [E(X)]^2
$$

$$
\mathrm{Var}(X) \approx 24.98 - (2.04)^2
$$

$$
\mathrm{Var}(X) \approx 20.82
$$



## Standard Deviation

$$
SD(X) = \sqrt{20.82} \approx 4.56
$$



# Final Summary

| Quantity | Value |
|----------|------:|
| Expected Value \(E(X)\) | 2.04 |
| Variance \(Var(X)\) | 20.82 |
| Standard Deviation \(SD(X)\) | 4.56 |


# Interpretation

The distribution is heavily concentrated at zero payoff, with a long right tail driven by rare high-value outcomes (multiple Kings). This produces:

- Low expected return (~$2)
- High variance (~20+)
- High risk relative to reward

From a probabilistic decision-making perspective, the game is characterized by **high dispersion and rare-event dominance**, making it unfavorable under risk-neutral evaluation.

# Linear Transformations of Random Variables


# Introduction

In probability theory and statistical inference, it is often necessary to study a random variable that is obtained through a transformation of another random variable. Among the most important transformations are **linear transformations**, which preserve much of the underlying probabilistic structure while altering location and scale characteristics.

A linear transformation of a random variable \(X\) is any transformation of the form

$$
Y = aX + b
$$

where:

- $a$ and $b$ are constants,
- $a$ controls scaling,
- $b$ controls translation (location shift).

Understanding how expected value and variance behave under linear transformations is fundamental in statistical modeling, estimation theory, regression analysis, stochastic processes, and standardization techniques.


# Expected Value and Variance Under Linear Transformations

Let \(X\) be a random variable with:

$$
E(X) = \mu
$$

and

$$
\mathrm{Var}(X) = \sigma^2
$$

Then the following properties hold.



# Theorem 1: Scaling Property of Expectation

For any constant \(a\),

$$
E(aX) = aE(X)
$$


## Proof

By definition of expected value for a discrete random variable:

$$
E(X) = \sum_x xP(X=x)
$$

Consider the transformed variable \(Y=aX\).

Then:

$$
E(aX)
= \sum_x (ax)P(X=x)
$$

Since \(a\) is constant, it may be factored outside the summation:

$$
E(aX)
= a\sum_x xP(X=x)
$$

Hence,

$$
E(aX)=aE(X)
$$


# Theorem 2: Translation Property of Expectation

For any constant \(b\),

$$
E(X+b)=E(X)+b
$$



## Proof

Using the definition of expectation:

$$
E(X+b)
=
\sum_x (x+b)P(X=x)
$$

Distribute the summation:

$$
=
\sum_x xP(X=x)
+
\sum_x bP(X=x)
$$

Since \(b\) is constant:

$$
=
E(X)
+
b\sum_x P(X=x)
$$

Because probabilities sum to 1:

$$
\sum_x P(X=x)=1
$$

Therefore,

$$
E(X+b)=E(X)+b
$$



# General Linear Transformation Rule

Combining the previous two results:

$$
E(aX+b)=aE(X)+b
$$

This shows that expectation is a **linear operator**.



# Theorem 3: Scaling Property of Variance

For any constant \(a\),

$$
\mathrm{Var}(aX)=a^2\mathrm{Var}(X)
$$


## Proof

Recall:

$$
\mathrm{Var}(X)=E[(X-\mu)^2]
$$

Let \(Y=aX\).

Then:

$$
E(Y)=a\mu
$$

Hence,

$$
\mathrm{Var}(aX)
=
E[(aX-a\mu)^2]
$$

Factor \(a\):

$$
=
E[a^2(X-\mu)^2]
$$

Since \(a^2\) is constant:

$$
=
a^2E[(X-\mu)^2]
$$

Thus,

$$
\mathrm{Var}(aX)=a^2\mathrm{Var}(X)
$$



# Theorem 4: Translation Property of Variance

For any constant \(b\),

$$
\mathrm{Var}(X+b)=\mathrm{Var}(X)
$$


## Proof

Variance measures spread around the mean. Adding a constant shifts all observations equally without changing relative dispersion.

Formally:

$$
\mathrm{Var}(X+b)
=
E[(X+b-E(X+b))^2]
$$

Using:

$$
E(X+b)=E(X)+b
$$

we obtain:

$$
=
E[(X+b-(E(X)+b))^2]
$$

Simplifying:

$$
=
E[(X-E(X))^2]
$$

Hence,

$$
\mathrm{Var}(X+b)=\mathrm{Var}(X)
$$



# Variance of a Constant

Let \(c\) be a constant random variable.

Since constants do not vary:

$$
\mathrm{Var}(c)=0
$$



## Proof

By definition:

$$
\mathrm{Var}(c)
=
E[(c-E(c))^2]
$$

Since:

$$
E(c)=c
$$

we obtain:

$$
=
E[(c-c)^2]
=
E(0)
=
0
$$

Thus,

$$
\mathrm{Var}(c)=0
$$



# Expectation of a Constant

For any constant \(c\),

$$
E(c)=c
$$



## Proof

A constant random variable always assumes the same value with probability 1.

Therefore:

$$
E(c)=c(1)=c
$$



# Summary of Linear Transformation Rules

| Property | Result |
|---|---|
| $$E(aX)$$ | $$aE(X)$$ |
| $$E(X+b)$$ | $$E(X)+b$$ |
| $$E(aX+b)$$ | $$aE(X)+b$$ |
| $$\mathrm{Var}(aX)$$ | $$a^2\mathrm{Var}(X)$$ |
| $$\mathrm{Var}(X+b)$$ | $$\mathrm{Var}(X)$$ |
| $$E(c)$$ | $$c$$ |
| $$\mathrm{Var}(c)$$ | $$0$$ |



# Interpretation

Linear transformations affect random variables in two fundamentally different ways:

- Multiplication by a constant changes both the center and the spread.
- Addition of a constant changes only the center while preserving dispersion.

Specifically:

- Scaling by \(a\) multiplies expectation by \(a\),
- Scaling by \(a\) multiplies variance by \(a^2\),
- Translation leaves variance invariant.

These properties are foundational in:

- standardization,
- z-score transformations,
- regression analysis,
- statistical estimation,
- signal processing,
- stochastic modeling.



# Example

Suppose:

$$
E(X)=5
$$

and

$$
\mathrm{Var}(X)=4
$$

Define:

$$
Y=3X+2
$$

Then:


## Expected Value

$$
E(Y)=E(3X+2)
$$

$$
=3E(X)+2
$$

$$
=3(5)+2=17
$$



## Variance

$$
\mathrm{Var}(Y)=\mathrm{Var}(3X+2)
$$

$$
=3^2\mathrm{Var}(X)
$$

$$
=9(4)=36
$$



## Standard Deviation

$$
SD(Y)=\sqrt{36}=6
$$

---




```R
# Original summaries
EX <- 5
VarX <- 4

# Linear transformation
a <- 3
b <- 2

# Transformed expectation
EY <- a * EX + b

# Transformed variance
VarY <- (a^2) * VarX

# Standard deviation
SDY <- sqrt(VarY)

EY
VarY
SDY
```


17



36



6


# 2.3 Essential Models in Discrete Probability:
# Binomial, Negative Binomial, Poisson, and Hypergeometric Distributions


# Introduction

In many probabilistic experiments, constructing probability distributions directly from the sample space becomes computationally prohibitive as the complexity of the experiment increases.

For small experiments, one may enumerate outcomes using:

- tree diagrams,
- counting principles,
- explicit sample spaces.

However, as the number of experimental outcomes grows, such approaches become impractical due to combinatorial explosion.

To address this challenge, probability theory introduces **parametric probability models**. These models emerge from identifying structural properties of the experiment, including:

- independence,
- replacement versus non-replacement,
- fixed versus random stopping criteria,
- constant success probabilities,
- finite versus infinite populations.

Once the probabilistic structure is identified, generalized analytical formulas allow efficient computation of:

- probabilities,
- expectations,
- variances,
- likelihoods,
- inferential quantities.

Among the most important discrete probability models are:

1. Binomial Distribution
2. Negative Binomial Distribution
3. Poisson Distribution
4. Hypergeometric Distribution

These distributions form the foundation of modern statistical inference, stochastic processes, reliability engineering, actuarial science, epidemiology, machine learning, and quantitative risk analysis.



# Bernoulli Trials

Many discrete distributions originate from repeated execution of a simple experiment called a **Bernoulli trial**.



## Definition

A Bernoulli trial is a random experiment satisfying:

1. Exactly two possible outcomes,
2. One outcome labeled success,
3. One outcome labeled failure,
4. Constant probability of success:

$$
P(\text{Success})=p
$$

5. Probability of failure:

$$
P(\text{Failure})=1-p
$$



## Examples

| Experiment | Success | Failure |
|---|---|---|
| Coin toss | Heads | Tails |
| Medical treatment | Recovery | Non-recovery |
| Manufacturing inspection | Defective | Non-defective |
| Loan application | Approved | Rejected |


# Bernoulli Process

A sequence of repeated Bernoulli trials forms a **Bernoulli process** if:

1. Trials are independent,
2. Success probability remains constant,
3. Trials are identically distributed.

Different probability models emerge depending on how the process is observed.



# Binomial Distribution



# Definition

Suppose an experiment consists of:

- \(n\) independent Bernoulli trials,
- each with success probability \(p\).

Define:

$$
X=\text{number of successes in }n\text{ trials}
$$

Then:

$$
X\sim B(n,p)
$$



# Conditions for a Binomial Model

A random variable is Binomial if:

1. Number of trials is fixed,
2. Trials are independent,
3. Two outcomes per trial,
4. Constant probability of success,
5. Variable counts successes.



# Binomial Probability Mass Function

For:

$$
X\sim B(n,p)
$$

the probability of exactly $x$ successes is:

$$
P(X=x)=\binom{n}{x}p^x(1-p)^{n-x}
$$

where:

$$
x=0,1,2,\dots,n
$$



# Derivation of the Binomial PMF

To obtain exactly $x$ successes:

1. Select which $x$ trials are successful:

$$
\binom{n}{x}
$$

2. Probability of any specific arrangement:

$$
p^x(1-p)^{n-x}
$$

Multiplying:

$$
P(X=x)=\binom{n}{x}p^x(1-p)^{n-x}
$$



### Mean and Variance

For:

$$
X\sim B(n,p)
$$



### Expected Value

$$
E(X)=np
$$



### Variance

$$
\mathrm{Var}(X)=np(1-p)
$$



## Standard Deviation

$$
SD(X)=\sqrt{np(1-p)}
$$



# Proof of the Mean

Express:

$$
X=X_1+X_2+\cdots+X_n
$$

where each \(X_i\) is a Bernoulli variable.

Since:

$$
E(X_i)=p
$$

then:

$$
E(X)=\sum_{i=1}^{n}E(X_i)=np
$$



# Proof of the Variance

Because Bernoulli trials are independent:

$$
\mathrm{Var}(X)
=
\sum_{i=1}^{n}\mathrm{Var}(X_i)
$$

For a Bernoulli variable:

$$
\mathrm{Var}(X_i)=p(1-p)
$$

Thus:

$$
\mathrm{Var}(X)=np(1-p)
$$



# Example: Reliability Engineering

A semiconductor manufacturing process produces defective chips with probability:

$$
p=0.02
$$

Suppose 15 chips are independently selected.

Define:

$$
X=\text{number of defective chips}
$$

Then:

$$
X\sim B(15,0.02)
$$



Probability of Exactly Two Defective Chips:

$$
P(X=2)
=
\binom{15}{2}(0.02)^2(0.98)^{13}
$$

$$
\approx 0.0323
$$



Probability of No Defective Chips:

$$
P(X=0)
=
(0.98)^{15}
\approx0.7386
$$

Probability of less than two Defective Chips:

$$
P(X< 2)
= P(X = 0) + P(X = 1)
 = (0.98)^{15} + \binom{15}{1}(0.02)^1(0.98)^{14}
 = 0.7386 + 0.2261
 = 0.9658
$$



```R
# P(X=2)
dbinom(2,15,0.02)
# P(X = 0)
dbinom(0,15,0.02)
# P(X < 2)
pbinom(1, 15,0.02)

```


0.0322989403489244



0.738569102645404



0.964661685087875


# Question: Overbooking and Capacity Risk in Taxi Fleet Operations (Advanced Binomial Model)

A taxi company operates a fleet of **30 taxis** available each evening. Based on historical data, the company observes that **18% of customers who reserve a taxi cancel their booking** independently of others.

To increase utilization, the company accepts **35 reservations** for a given evening.

a) Compute the probability that the fleet is sufficient to serve all customers.

b) Compute the expected number of customers who show up

c) Interpret this probability in terms of **service reliability and overbooking risk**

First try to attempt it before looking in to the answer.



**Answer**

Let:

$$
X = \text{number of customers who do NOT cancel their reservation}
$$

Assume each reservation behaves independently with probability of showing up:

$$
p = 0.82
$$

Thus:

$$
X \sim B(35, 0.82)
$$

### (a) Capacity Feasibility Probability


$$
P(X \leq 30)
$$

Interpret this probability in terms of **service reliability and overbooking risk**.

Use R to compute the value.


### (b) Expected Demand

$$
E(X)
$$

Interpret the result in terms of average nightly system load.



### (c) Overcapacity Risk Variable
Define:

$$
D = X - 30
$$

1. Express \(P(D > 0)\) in terms of \(X\)
2. Compute \(P(D > 0)\)
3. Interpret this probability as a system risk measure.



### Policy Change Scenario
Suppose the company increases reservations to **38 customers**.

Let:

$$
X' \sim B(38, 0.82)
$$

Compare:

$$
P(X \leq 30) \quad \text{vs} \quad P(X' \leq 30)
$$

and discuss the operational trade-off.



```R
#part a
pbinom(30,35,0.82)
```


0.780359091669752


# Negative Binomial Distribution



# Motivation

The Binomial distribution fixes the number of trials and counts successes.

The Negative Binomial distribution reverses this perspective:

- the number of successes is fixed,
- the number of trials becomes random.

It models waiting-time phenomena.



# Definition

Let:

$$
X=\text{number of trials required to obtain }r\text{ successes}
$$

Then:

$$
X\sim NB(r,p)
$$

where:

- $r$ = required number of successes,
- $p$ = probability of success per trial.



# Interpretation

The process continues until the $r^{th}$ success occurs.

Thus:

- the final trial must be a success,
- the total number of trials is random.




# Negative Binomial PMF

For:

$$
X\sim NB(r,p)
$$

the probability that the $r^{th}$ success occurs on trial $x$ is:

$$
P(X=x)
=
\binom{x-1}{r-1}
p^r(1-p)^{x-r}
$$

where:

$$
x=r,r+1,r+2,\dots
$$



# Derivation of the PMF

To end on trial $x$:

1. The first $x-1$ trials must contain exactly $r-1$ successes.
2. Trial $x$ must be a success.



## Number of arrangements

$$
\binom{x-1}{r-1}
$$


## Probability of each arrangement

$$
p^{r-1}(1-p)^{x-r}
$$

Final success contributes another factor of $p$.

Thus:

$$
P(X=x)
=
\binom{x-1}{r-1}
p^r(1-p)^{x-r}
$$



## Expected Value and Variance

For:

$$
X\sim NB(r,p)
$$



### Expected Value

$$
E(X)=\frac{r}{p}
$$



### Variance

$$
\mathrm{Var}(X)=\frac{r(1-p)}{p^2}
$$



### Standard Deviation

$$
SD(X)=\sqrt{\frac{r(1-p)}{p^2}}
$$


# Example: Clinical Screening Process

Suppose:

- probability a blood sample tests positive:

$$
p=0.08
$$

- testing continues until 4 positive cases are detected.

Define:

$$
X=\text{number of tests required to obtain 4 positives}
$$

Then:

$$
X\sim NB(4,0.08)
$$



Probability That the 4th Positive Occurs on Test 20:

$$
P(X=20)
=
\binom{19}{3}(0.08)^4(0.92)^{16}
$$


### Computation

$$
\binom{19}{3}=969
$$

$$
(0.08)^4=0.00004096
$$

$$
(0.92)^{16}\approx0.263
$$

Thus:

$$
P(X=20)
\approx
969(0.00004096)(0.263)
\approx0.0105
$$



### Expected Number of Tests

$$
E(X)=\frac{4}{0.08}=50
$$



### Variance

$$
\mathrm{Var}(X)
=
\frac{4(1-0.08)}{(0.08)^2}
=
575
$$



### Standard Deviation

$$
SD(X)=\sqrt{575}\approx23.98
$$



# Relationship Between Binomial and Negative Binomial Models

| Binomial Distribution | Negative Binomial Distribution |
|---|---|
| Fixed number of trials | Fixed number of successes |
| Random number of successes | Random number of trials |
| Counts successes | Counts waiting time |
| Support: $0,\dots,n$ | Support: $r,r+1,\dots$ |




```R
# Binomial Example
dbinom(2, size = 15, prob = 0.02)

# Negative Binomial Example
dnbinom(20 - 4, size = 4, prob = 0.08)

# Mean and variance
4 / 0.08
4 * (1 - 0.08) / (0.08^2)
```


0.0322989403489244



0.0104541556646095



50



575


## Hypergeometric and Poisson Distributions


# Hypergeometric Probability Distribution



## Conceptual Motivation

In the Binomial framework, a central assumption is **independent Bernoulli trials with constant success probability**, typically justified by sampling with replacement or from an effectively infinite population.

However, in finite-population sampling contexts, this assumption is violated. When sampling is performed **without replacement**, each draw alters the composition of the remaining population, inducing dependence across trials.

This leads to the **Hypergeometric distribution**, which explicitly models finite-population sampling without replacement.


## Experimental Structure

Consider a finite population of size:

$$
N
$$

containing:

- $S$ successes,
- $N-S$ failures.

A sample of size \(n\) is drawn without replacement.

Define:

$$
X = \text{number of successes in the sample}
$$

Then:

$$
X \sim \text{Hypergeometric}(N,S,n)
$$



## Probability Mass Function

$$
P(X=x)
=
\frac{\binom{S}{x}\binom{N-S}{n-x}}{\binom{N}{n}}
$$

with support:

$$
x \in \left\{\max(0,n-(N-S)),\dots,\min(n,S)\right\}
$$


## Expectation and Variance

### Expected Value

$$
E(X)=n\frac{S}{N}
$$



### Variance

$$
\mathrm{Var}(X)
=
n\frac{S}{N}\left(1-\frac{S}{N}\right)\frac{N-n}{N-1}
$$

The factor:

$$
\frac{N-n}{N-1}
$$

is the **finite population correction (FPC)**, capturing reduced variability due to sampling dependence.



## Interpretation

Compared to the Binomial model:

- variance is reduced due to negative dependence,
- success probability evolves dynamically across draws,
- sampling fraction governs deviation from Binomial behavior.



## R Implementation

- Probability mass function: `dhyper(x, S, N-S, n)`
- Cumulative distribution: `phyper(x, S, N-S, n)`


## Example: Knowledge-Constrained Sampling

An assignment consists of:

- $N=15$ problems,
- $S=8$ solvable without external reference,
- $7$ requiring external assistance.

A student randomly selects:

$$
n=4
$$

problems without replacement.

Define:

$$
X = \text{number of solvable problems in the selection}
$$

Then:

$$
X \sim \text{Hypergeometric}(15,8,4)
$$



### (a)

Compute:

$$
P(X=4)
$$

Interpretation: probability that all selected problems are solvable without assistance.

### (b) Compute:
$$
P(X \geq 2)
$$
Interpretation: probability that at least half of selected problems are solvable without external assistance.

### (c) Compute:

$$ P(X≥3∣X≥1) $$

This expresses conditional reliability under non-trivial selection events.


```R
#part a
dhyper(4, 8, 7, 4)
# part b
1 - phyper(1,8,7,4)
# part c
# P(X >= 3 | X >= 1) = P(X >= 3 and X >= 1)/P(X >= 1) = P(X >= 3)/ P(X >= 1)
(1-phyper(2,8,7,4))/(1-phyper(0,8,7,4))
```


0.0512820512820513



0.769230769230769



0.347368421052631


# Poisson Probability Distribution


# Conceptual Motivation

The Poisson distribution models the occurrence of random events over a continuous domain such as:

- time intervals,
- spatial regions,
- linear or planar domains.

It is appropriate when events satisfy the following structural assumptions:

1. Events occur independently.
2. The average event rate is constant over the interval.
3. Two events cannot occur simultaneously in an infinitesimally small interval.
4. The probability of an event occurring in a small interval is proportional to the length of that interval.

These conditions define a **Poisson process**, a fundamental object in stochastic process theory.



# Poisson Random Variable

A discrete random variable \(X\) is Poisson distributed if:

$$
X \sim \text{Poisson}(\lambda)
$$

where:

- \(\lambda > 0\) is the expected number of events in a fixed interval.



# Probability Mass Function

The Poisson probability mass function is given by:

$$
P(X=x)=\frac{e^{-\lambda}\lambda^x}{x!}, \quad x=0,1,2,\dots
$$

where:

- \(e\) is Euler’s constant,
- \(\lambda^x\) scales the intensity,
- \(x!\) normalizes combinatorial arrangements.


R Implementation

- Probability mass function, $P(X = x)$ : `dpois(x, λ)`
- Cumulative distribution, $P(X \leq x)$: `phyper(x,λ)`
# Structural Derivation (Limit of Binomial)

The Poisson distribution arises as a limiting case of the Binomial distribution.

Let:

$$
X_n \sim B(n,p_n)
$$

where:

$$
np_n \to \lambda
$$

Then:

$$
\lim_{n \to \infty} P(X_n = x)
=
\frac{e^{-\lambda}\lambda^x}{x!}
$$



## Sketch of Derivation

Start with:

$$
P(X_n=x)=\binom{n}{x}p_n^x(1-p_n)^{n-x}
$$

Substitute $p_n = \lambda/n$:

- Use approximation:

$$
\left(1-\frac{\lambda}{n}\right)^n \to e^{-\lambda}
$$

- Expand combinatorial term asymptotically:

$$
\binom{n}{x} \sim \frac{n^x}{x!}
$$

Combining terms yields:

$$
P(X=x)=\frac{e^{-\lambda}\lambda^x}{x!}
$$



# Mean and Variance

For:

$$
X \sim \text{Poisson}(\lambda)
$$



## Expected Value

$$
E(X)=\lambda
$$



## Variance

$$
\mathrm{Var}(X)=\lambda
$$



## Standard Deviation

$$
SD(X)=\sqrt{\lambda}
$$

A key implication is:

> The Poisson distribution is equidispersed (mean equals variance), a property frequently violated in empirical data (leading to over-dispersion models such as Negative Binomial).



# Reparameterization of $\lambda$

If $\lambda$ is defined per unit interval, scaling to a different interval requires linear adjustment.


## General Rule

If:

- rate is $\lambda$ per unit interval,
- interval length is $t$,

then:

$$
\lambda_t = t\lambda
$$



## Interpretation

This scaling property reflects the **stationarity of increments** in Poisson processes.



# Example 1: Queueing System with Tail Risk Analysis

A server receives requests at an average rate:

$$
\lambda = 4.5 \text{ requests per second}
$$

Let:

$$
X = \text{number of requests in a 2-second interval}
$$

Then:

$$
X \sim \text{Poisson}(9)
$$



### (a) Tail Probability (System Overload Risk)

Compute:

$$
P(X \ge 12)
$$

### Reformulation

$$
P(X \ge 12)=1-P(X \le 11)
$$

### (b) Compute

$$P(X≥12∣X≥8)$$

# Example 2: Spatial Poisson Process - Agriculture

Let:

X ∼ Poisson(5.5)

represent weed counts per acre.

#### (a) First Two Moments

E(X)=5.5

Var(X)=5.5


### (b) Probability of Rare Event

Compute: P(X=2)

### (c) Scaling to Subregion

For half-acre: λ=2.75

Compute: P(X=2)

# Example 3:  Call Center Load

Let:

X ∼ Poisson(7.5)

represent calls per shift.

### (a) Compute:

P(X=6)

### (b) Service Overload Probability

P(X≥9)


### (c) Policy Change Scenario


If system redesign yields: λ=5

Compute: P(X=6)


```R
# Example 1
# part a
print("Example 1 part a")
1 - ppois(11, 9)

# part b
# P(X >= 12 | X >= 8) = P(X >= 12 and X >= 8) / P(X >=8) = P(X >= 12)/P(X>=8)
print("Example 1 part b")
(1-ppois(11,9))/(1-ppois(7,9))

# Example 2
# part b
print("Example 2 part b")
dpois(2, 5.5)
# part c
print("Example 2 part c")
dpois(2, 2.75)

# Example 3
#part a
print("Example 3 part a")
dpois(6, 7.5)
# part b
print("Example 2 part b")
1 - ppois(8, 7.5)
# part c
print("Example 2 part c")
dpois(6, 5)

```

    [1] "Example 1 part a"
    


0.196991617470658


    [1] "Example 1 part b"
    


0.291363308656736


    [1] "Example 2 part b"
    


0.061812418006769


    [1] "Example 2 part c"
    


0.241727225187863


    [1] "Example 3 part a"
    


0.136718243353194


    [1] "Example 2 part b"
    


0.338032880858517


    [1] "Example 2 part c"
    


0.146222808139876





## Structural Interpretation

The Poisson distribution is characterized by:

independence of increments,
stationarity of event rate,
rare-event asymptotics,
infinite divisibility.

It is the canonical model for:

queueing theory,
spatial statistics,
reliability systems,
stochastic process modeling.

Final Insight:

* The Poisson distribution occupies a central role in discrete stochastic modeling as it bridges:

* Binomial finite-trial systems, continuous-time event processes, and limiting rare-event behavior.

It is therefore not merely a distribution, but a structural limit of probabilistic counting systems.

# 2.4 Continuous Probability Distributions  
## Mathematical Models for Continuous Random Variables



# Introduction to Continuous Random Variables

In previous sections, we studied **discrete random variables**, whose probability distributions were represented through probability mass functions (PMFs). Discrete variables assume countable values, and probabilities are assigned directly to individual outcomes.

Many phenomena encountered in scientific, engineering, biological, and economic systems, however, are inherently continuous. Measurements such as time, distance, mass, voltage, temperature, and concentration vary over intervals rather than isolated points. Such variables are modeled using **continuous probability distributions**.


## Definition: Continuous Random Variable

A random variable \(X\) is said to be **continuous** if it may assume any value within an interval of the real line.

Examples include:

- lifetime of a semiconductor device,
- oxygen consumption during athletic exertion,
- temperature fluctuations in industrial systems,
- waiting time between customer arrivals,
- blood pressure measurements in medical studies.

Unlike discrete variables, continuous variables possess infinitely many possible realizations within any interval.



# Probability Density Functions

For continuous variables, probabilities are not assigned to isolated points. Instead, probabilities are determined over intervals using a **probability density function (PDF)**.

The density function is denoted by:

$$
f(x)
$$

and satisfies:

$$
f(x) \ge 0
\quad \text{for all } x
$$



## Fundamental Property

Because a continuous variable has infinitely many possible values,

$$
P(X=x)=0
$$

for every individual value \(x\).



## Consequence

Only interval probabilities are meaningful:

$$
P(a \le X \le b)
$$

or equivalently,

$$
P(a < X < b)
$$

since boundary probabilities vanish.

Thus,

$$
P(a \le X \le b)=P(a<X<b)
$$


# Probability Computation via Integration

Probabilities are computed as areas under the density curve.

## General Formula

If \(X\) has density \(f(x)\), then:

$$
P(a \le X \le b)
=
\int_a^b f(x)\,dx
$$



## Total Probability Condition

The density must satisfy:

$$
\int_{-\infty}^{\infty} f(x)\,dx =1
$$



## Geometric Interpretation

Probabilities correspond to areas under the curve:

- larger area \(\Rightarrow\) larger probability,
- total area under the density equals 1.









# Exponential Probability Distribution



# 4.1 Motivation

The Exponential distribution models **waiting times** between occurrences in a Poisson process.

Typical applications include:

- waiting time between earthquakes,
- inter-arrival times in queueing systems,
- time between machine failures,
- duration between customer arrivals,
- survival analysis and reliability modeling.
# Exponential Random Variable

A random variable \(X\) is exponentially distributed with parameter \(\beta>0\) if:

$$
X \sim \text{Exp}(\beta)
$$

with probability density:

$$
f(x)=\frac{1}{\beta}e^{-x/\beta},
\quad x>0
$$

and:

$$
f(x)=0, \quad x \le 0
$$



# Verification of Total Probability

To verify that \(f(x)\) is a valid density:

$$
\int_0^\infty \frac{1}{\beta}e^{-x/\beta}dx
$$

Let:

$$
u=-x/\beta
$$

Then:

$$
du=-\frac{1}{\beta}dx
$$

Hence:

$$
\int_0^\infty \frac{1}{\beta}e^{-x/\beta}dx
=
\int_0^{-\infty} -e^u du
$$

which becomes:

$$
\int_{-\infty}^0 e^u du
=
\left[e^u\right]_{-\infty}^0
=1
$$

Thus, the exponential density is properly normalized.



# Mean and Variance

For:

$$
X \sim \text{Exp}(\beta)
$$



## Expected Value

$$
E(X)=\beta
$$



## Variance

$$
Var(X)=\beta^2
$$



## Standard Deviation

$$
SD(X)=\beta
$$



# Probability Computation

For any \(b>0\):

$$
P(X\le b)
=
\int_0^b \frac{1}{\beta}e^{-x/\beta}dx
$$

Evaluating:

$$
=
\left[-e^{-x/\beta}\right]_0^b
$$

Thus,

$$
P(X\le b)=1-e^{-b/\beta}
$$



# Example: Waiting Time for a Bus

Suppose waiting time for a bus follows:

$$
X \sim \text{Exp}(21)
$$

where \(X\) is measured in minutes.



## (a) Probability of Waiting Longer Than 15 Minutes

Compute:

$$
P(X>15)
$$

Using complements:

$$
P(X>15)=1-P(X\le15)
$$

Hence,

$$
P(X>15)=e^{-15/21}
$$


### R Computation

```r
1 - pexp(15, 1/21)
```



## (b) Probability of Waiting Between 10 and 15 Minutes

Compute:

$$
P(10 \le X \le 15)
$$

Using integration:

$$
=
\int_{10}^{15}\frac{1}{21}e^{-x/21}dx
$$

Thus,

$$
=
e^{-10/21}-e^{-15/21}
$$



### R Computation

```r
pexp(15,1/21) - pexp(10,1/21)
```



## (c) Quantile Interpretation

Find \(x\) such that:

$$
P(X>x)=0.90
$$

Equivalently:

$$
P(X\le x)=0.10
$$



### R Computation

```r
qexp(0.10, 1/21)
```



# Memoryless Property

The Exponential distribution is the only continuous distribution possessing the **memoryless property**.

The memoryless property of an exponential random variable is one of its key characteristics. It essentially means that the probability of an event occurring in the future is independent of the past. In simpler terms, the distribution "forgets" how much time has already passed, and the process starts fresh from the current time.
If you are waiting for something to happen (e.g., a bus, a phone call, a machine failure), and the waiting time follows an exponential distribution, the memoryless property tells you that:

  **The probability of waiting for a certain additional amount of time does not depend on how much time you've already waited.**


## Theorem

If:

$$
X \sim \text{Exp}(\beta)
$$

then:

$$
P(X>s+t \mid X>s)=P(X>t)
$$



## Proof

By conditional probability:

$$
P(X>s+t \mid X>s)
=
\frac{P(X>s+t)}{P(X>s)}
$$

Using survival probabilities:

$$
P(X>x)=e^{-x/\beta}
$$

Therefore:

$$
=
\frac{e^{-(s+t)/\beta}}{e^{-s/\beta}}
$$

Simplifying:

$$
=e^{-t/\beta}
$$

Hence:

$$
P(X>s+t \mid X>s)=P(X>t)
$$





## Example:

At a bus stop, the waiting time for the next bus is modeled by an exponential distribution with an average waiting time of 10 minutes. A student has already been waiting for 8 minutes, and the bus has still not arrived. What is the probability that the student will need to wait more than 5 additional minutes for the bus to arrive?

**Answer**

For an exponential random variable:

$$P(X>s+t∣X>s)=P(X>t)$$

Using:

Mean = 10 minutes
$ β = 10 $


We compute:

$P(X>5)=e
−λ(5)
=e
−0.5$

So,

$P(X>13∣X>8)=P(X>5)=e
−0.5$

$≈0.6065$

There is approximately a 60.65% chance the student waits more than 5 additional minutes.

# Normal Probability Distribution



# Importance of the Normal Distribution

The Normal distribution occupies a foundational role in probability theory and statistical inference due to:

- the Central Limit Theorem,
- asymptotic properties of estimators,
- Gaussian error modeling,
- prevalence in natural and social systems.

Many inferential procedures assume approximate normality.



# Definition

A random variable \(X\) is normally distributed if:

$$
X \sim N(\mu,\sigma^2)
$$

with density:

$$
f(x)=
\frac{1}{\sigma\sqrt{2\pi}}
\exp\left(
-\frac{(x-\mu)^2}{2\sigma^2}
\right)
$$

where:

- \(\mu\) is the population mean,
- \(\sigma\) is the population standard deviation.



# Structural Characteristics

The normal distribution is:

- symmetric,
- bell-shaped,
- unimodal,
- asymptotic to the horizontal axis.

Furthermore:

$$
\text{Mean}=\text{Median}=\text{Mode}
$$



# Mean and Variance

For:

$$
X\sim N(\mu,\sigma^2)
$$



## Expected Value

$$
E(X)=\mu
$$



## Variance

$$
Var(X)=\sigma^2
$$



# Probability Computation

Probabilities are computed via integration:

$$
P(a\le X\le b)
=
\int_a^b
\frac{1}{\sigma\sqrt{2\pi}}
\exp\left(
-\frac{(x-\mu)^2}{2\sigma^2}
\right)dx
$$

This integral has no elementary closed form and is evaluated numerically.



# Example: IQ Distribution

Suppose IQ scores follow:

$$
X\sim N(100,15^2)
$$



## (a) Probability of IQ Less Than 105

Compute:

$$
P(X<105)
$$



```R
pnorm(105,100,15)
```


0.630558659818236


## (b) Probability Between 80 and 105

Compute:

$$
P(80\le X\le105)
$$



```R
pnorm(105,100,15)-pnorm(80,100,15)
```


0.539347440092368


## (c) 90th Percentile

Find $x$ such that:

$$
P(X\le x)=0.90
$$


```R
qnorm(0.90,100,15)
```


119.223273483169


# Standard Normal Distribution



# Definition

The standard normal distribution is:

$$
Z\sim N(0,1)
$$

with density:

$$
f(z)=\frac{1}{\sqrt{2\pi}}e^{-z^2/2}
$$



# Standardization

Any normal random variable may be transformed into a standard normal variable using:

$$
Z=\frac{X-\mu}{\sigma}
$$

This transformation measures distance from the mean in units of standard deviation.



# Interpretation of Z-Scores

- $Z=1$: one standard deviation above mean,
- $Z=-2$: two standard deviations below mean,
- $Z=0$: exactly at mean.





# Example Computations

## (a)

Compute:

$$
P(Z>2.15)
$$


```R
1-pnorm(2.15)
```


0.0157776073910905



## (b)

Compute:

$$
P(0\le Z\le1.96)
$$


```R
pnorm(1.96)-pnorm(0)
```


0.47500210485178


## (c)

Compute:

$$
P(-1.52\le Z\le1.96)
$$



```R
pnorm(1.96)-pnorm(-1.52)
```


0.910746617032844


## (d)

Find $z_0$ such that:

$$
P(Z>z_0)=0.90
$$

Equivalently:

$$
P(Z\le z_0)=0.10
$$



```R
qnorm(0.10)
```


-1.2815515655446


# Final Perspective

Continuous probability distributions provide mathematical models for phenomena evolving over continuous domains.

The:

- Exponential distribution models waiting times,
- Normal distribution models aggregated variation,
- Standard normal distribution provides the computational foundation for statistical inference.

Together, these distributions form the analytical basis for advanced probability theory, stochastic modeling, and inferential statistics.

# Exercise Sheet — Probability Models and Statistical Distributions


## Exercise 1

A cybersecurity analyst monitors the number of unauthorized login attempts detected during a one-minute interval. Suppose that during a particular monitoring protocol, the analyst independently evaluates whether each of four access requests is malicious.

Let

$$
X = \text{number of malicious login attempts among the four requests}
$$

Assume each request is independently malicious with probability:

$$
p=0.25
$$

1. Construct the complete probability distribution of \(X\).

2. Verify formally that the distribution satisfies the axioms of a probability distribution.

3. Represent the distribution:
   - in tabular form,
   - graphically using a probability mass function plot.

4. Compute:

$$
P(X\ge2)
$$

5. Determine:

$$
E(X),\quad Var(X),\quad SD(X)
$$

---

## Exercise 2

A pharmaceutical laboratory randomly selects three chemical samples without replacement from a batch containing:

- 5 contaminated samples,
- 7 uncontaminated samples.

Let:

$$
Y=\text{number of contaminated samples selected}
$$

1. Determine the support of \(Y\).

2. Construct the probability distribution of \(Y\).

3. Verify that:

$$
\sum_y P(Y=y)=1
$$

4. Compute:

$$
P(Y\le1)
$$

5. Determine:

$$
E(Y),\quad Var(Y),\quad SD(Y)
$$

---

## Exercise 3

An investment analyst models the daily profit (in thousands of dollars) of a speculative portfolio using the following probability distribution:

| \(x\) | -8 | -2 | 4 | 10 |
|---|---|---|---|---|
| \(P(X=x)\) | 0.10 | 0.35 | 0.40 | 0.15 |

1. Verify that the distribution is valid.

2. Compute:

$$
E(X)
$$

3. Compute:

$$
Var(X)
$$

4. Compute:

$$
SD(X)
$$

5. Determine the coefficient of variation:

$$
CV=\frac{SD(X)}{E(X)}
$$

and interpret its meaning.

---

## Exercise 4

A biotechnology company develops a treatment with a success probability of:

$$
p=0.68
$$

Suppose 20 patients independently receive the treatment.

Let:

$$
X=\text{number of successful treatment responses}
$$

1. Compute:

$$
P(X=15)
$$

2. Compute:

$$
P(X\ge16)
$$

3. Compute:

$$
P(10\le X\le18)
$$

4. Determine:

$$
E(X),\quad Var(X),\quad SD(X)
$$

5. Approximate:

$$
P(X\ge16)
$$

using a normal approximation with continuity correction.

---

## Exercise 5

A cloud computing company estimates that a server independently fails during peak operation with probability:

$$
0.04
$$

Suppose 120 servers are monitored.

Let:

$$
X=\text{number of failed servers}
$$

1. Compute:

$$
P(X=0)
$$

2. Compute:

$$
P(X\le5)
$$

3. Determine:

$$
E(X)
$$

and

$$
Var(X)
$$

4. Compute the probability that the number of failures exceeds the mean by at least two standard deviations.

---

## Exercise 6

A manufacturing engineer tests electronic components sequentially. Each component independently functions correctly with probability:

$$
p=0.92
$$

Let:

$$
X=\text{number of tested components required to observe the fifth defective component}
$$

1. Compute:

$$
P(X=18)
$$

2. Compute:

$$
P(X\le25)
$$

3. Determine:

$$
E(X)
$$

and

$$
Var(X)
$$

4. Compute the probability that more than 30 tests are required.

---

## Exercise 7

An online retailer estimates that each website visitor independently makes a purchase with probability:

$$
0.12
$$

Let:

$$
Y=\text{number of visitors required to obtain the 8th purchase}
$$

1. Compute:

$$
P(Y=50)
$$

2. Compute:

$$
P(Y<60)
$$

3. Determine:

$$
E(Y),\quad Var(Y),\quad SD(Y)
$$

4. Explain why the probability of success remains constant across trials.

---

## Exercise 8

A shipment contains:

- 18 defective microchips,
- 82 non-defective microchips.

A quality-control analyst selects 10 chips without replacement.

Let:

$$
X=\text{number of defective chips selected}
$$

1. Compute:

$$
P(X=2)
$$

2. Compute:

$$
P(X\le3)
$$

3. Compute:

$$
P(X\ge1)
$$

4. Determine:

$$
E(X),\quad Var(X),\quad SD(X)
$$

5. Explain mathematically why independence does not hold in this experiment.

---

## Exercise 9

A financial auditor reviews 12 files selected without replacement from a collection of 80 files, among which 15 contain reporting errors.

Let:

$$
Y=\text{number of erroneous files selected}
$$

1. Compute:

$$
P(Y=0)
$$

2. Compute:

$$
P(Y\ge4)
$$

3. Determine:

$$
E(Y),\quad Var(Y)
$$

4. Compare this experiment with one involving independent trials.

---

## Exercise 10

Emergency-room arrivals occur at an average rate of:

$$
\lambda=6.5
$$

patients per hour.

Let:

$$
X=\text{number of arrivals during one hour}
$$

1. Compute:

$$
P(X=4)
$$

2. Compute:

$$
P(X\ge8)
$$

3. Compute:

$$
P(3\le X\le7)
$$

4. Determine:

$$
E(X),\quad Var(X),\quad SD(X)
$$

5. Compute the probability that no patients arrive in a 20-minute interval.

---

## Exercise 11

A telecommunications network experiences packet failures at an average rate of:

$$
1.8
$$

per minute.

1. Compute the probability of exactly 5 failures in a 3-minute interval.

2. Compute the probability of fewer than 2 failures in a 30-second interval.

3. Compute the probability of at least one failure in a 10-second interval.

4. Explain the assumptions necessary for the probability model to remain valid.

---

## Exercise 12

The time (in hours) between failures of a server system follows a continuous probability distribution with mean:

$$
18
$$

hours.

Let:

$$
X=\text{time until the next system failure}
$$

1. Derive the probability density function.

2. Compute:

$$
P(X>20)
$$

using integration.

3. Compute:

$$
P(10<X<25)
$$

4. Compute the median waiting time.

5. Compute the 95th percentile.

6. Verify:

$$
P(X>30\mid X>10)=P(X>20)
$$

---

## Exercise 13

The waiting time between customer arrivals at a service center has mean:

$$
12
$$

minutes.

1. Compute:

$$
P(X<5)
$$

2. Compute:

$$
P(X>20)
$$

3. Compute:

$$
P(8<X<15)
$$

4. Determine:

$$
Var(X),\quad SD(X)
$$

5. Compute:

$$
P(X>18\mid X>10)
$$

---

## Exercise 14

Graduate aptitude scores are normally distributed with:

$$
\mu=540,\quad \sigma=110
$$

Let:

$$
X=\text{graduate aptitude score}
$$

1. Compute:

$$
P(X<600)
$$

2. Compute:

$$
P(450<X<700)
$$

3. Determine the 90th percentile.

4. Determine the interquartile range.

5. Standardize the value:

$$
X=725
$$

6. Interpret the resulting standardized score.

---

## Exercise 15

The diameter of machine components follows a normal distribution with:

$$
\mu=25,\quad \sigma=0.8
$$

millimeters.

1. Compute:

$$
P(X>26)
$$

2. Compute:

$$
P(24.5<X<25.8)
$$

3. Determine the probability that a randomly selected component lies within two standard deviations of the mean.

4. Find the 5th percentile.

5. Determine the cutoff value corresponding to the upper 1% of component diameters.

---

## Exercise 16

For each scenario below, identify the most appropriate probability model and justify your selection mathematically.

1. Number of insurance claims filed in a week.

2. Number of defective products selected without replacement from a shipment.

3. Time until the next earthquake.

4. Number of successful DNA replications among 50 trials.

5. Number of customer arrivals before the 10th sale occurs.

6. Distribution of sample means for sufficiently large sample sizes.

---

## Exercise 17

Provide a rigorous comparison between the following pairs of probability models:

1. Sampling with replacement versus sampling without replacement.

2. Event counts over fixed trials versus event counts over continuous intervals.

3. Waiting-time models versus event-count models.

4. Discrete distributions versus continuous distributions.

Your discussion should include:
- assumptions,
- support,
- probability functions,
- expected values,
- variances,
- limiting relationships.

---

## Exercise 18

Suppose:

$$
X_1,X_2,\dots,X_n
$$

are independent Bernoulli random variables with:

$$
P(X_i=1)=p
$$

Define:

$$
S_n=\sum_{i=1}^n X_i
$$

1. Derive:

$$
E(S_n)
$$

2. Derive:

$$
Var(S_n)
$$

3. Show that:

$$
\frac{S_n}{n}
$$

is an unbiased estimator of \(p\).

4. Derive the variance of:

$$
\frac{S_n}{n}
$$

5. Explain how the Central Limit Theorem applies to:

$$
\frac{S_n}{n}
$$

for large \(n\).

---

## Exercise 19

Suppose a continuous random variable has probability density function:

$$
f(x)=\frac{1}{\beta}e^{-x/\beta},
\quad x>0
$$

1. Verify that:

$$
\int_0^\infty f(x)\,dx=1
$$

2. Derive:

$$
E(X)
$$

using integration by parts.

3. Derive:

$$
Var(X)
$$

4. Derive the cumulative distribution function.

5. Prove the memoryless property.

---

## Exercise 20

Suppose a continuous random variable has probability density function:

$$
f(x)=\frac{1}{\sigma\sqrt{2\pi}}
\exp\left(
-\frac{(x-\mu)^2}{2\sigma^2}
\right)
$$

1. Explain the role of the parameters:

$$
\mu,\quad \sigma
$$

2. Describe how changing:
   - $\mu$,
   - $\sigma$

affects the shape of the distribution.

3. Explain why:

$$
P(X=x)=0
$$

for any continuous random variable.

4. Explain why probabilities correspond to areas under the density curve.

5. Define the standardized random variable:

$$
Z=\frac{X-\mu}{\sigma}
$$

and explain its importance in statistical inference.
