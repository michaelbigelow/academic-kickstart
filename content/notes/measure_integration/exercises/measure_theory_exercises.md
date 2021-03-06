---
title: 'Measure Theory'
author: "Michael Bigelow"
date: '2020-06-03'
output: pdf_document
draft: no
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
lastmod: '2020-06-03T16:20:05-06:00'
categories: [Probability]
projects: []
slug: measure-theory-exercises
subtitle: ''
summary: 'Key proofs from measure theory, in preparation for a course in rigorous probability theory.'
type: docs
toc: true
tags:
- measure theory
- probability
- proofs
- mathematics
authors: [admin]
menu:
  docs:
    parent: exercises
    weight: 200
weight: 200
---

# Introduction
Below are my solutions to measure theory exercises from Professor Davar Khoshnevisan's [lecture notes](http://www.math.utah.edu/~davar/lecture-notes.html) on probability theory.  Nearly all of the exercises illustrate or prove key results that were left omitted from my [measure theory scribe notes](/notes/measure_integration), which are themselves based on Professor Frederic Schuller's illuminating lectures on [measure](https://www.youtube.com/watch?v=6ad9V8gvyBQ) and [integration](https://www.youtube.com/watch?v=ot253Lhx2_o), given during a series on quantum theory.

## 1. Generated $\sigma$-algebra
Prove the following lemma:

**Lemma.** If $I$ is any set (denumerable or not) and if $\mathfrak{F}\_i$ is a $\sigma$-algebra of subsets of $\Omega$ for each $i \in I$, then $\cap\_{i \in I} \mathfrak{F}\_i$ is also such a $\sigma$-algebra.  Consequently, given any algebra $\mathfrak{A}$, there exists a smallest $\sigma$-algebra containing $\mathfrak{A}$.

**Proof.**

[Recall](/notes/measure_integration/measure/general-measure-spaces/#sigma-algebras) that a collection $\mathfrak{F}$ of subsets of $\Omega$ is a $\sigma$-algebra if:

1. $\Omega \in \mathfrak{F}$
2. $A \in \mathfrak{F} \implies A^c \in \mathfrak{F}$ and
3. $A_1, A_2, ... \in \mathfrak{F} \implies \cup_{n=1}^{\infty}A_n \in \mathfrak{F}$.

Hence, from the definition of intersection, $\cap_{i \in I}\mathfrak{F}_i$ is a $\sigma$-algebra because:

1. $\Omega \in \mathfrak{F}\_i$ for all $i\in I$ implies $\Omega \in \cap\_{i \in I}\mathfrak{F}\_i$.
2. $A \in \cap\_{i \in I}\mathfrak{F}\_i$ implies $A \in \mathfrak{F}\_i$ for all $i\in I$, which implies $A^c \in \mathfrak{F}\_i$ for all $i\in I$, which implies $A^c \in \cap\_{i \in I}\mathfrak{F}\_i$.
3. $A_1, A_2, ... \in  \cap_{i \in I}\mathfrak{F}_i$ implies $A_1, A_2, ... \in \mathfrak{F}_i$ for all $i\in I$, which implies $\cup_{n=1}^{\infty}A_n \in \mathfrak{F}_i$ for all $i\in I$, which implies $\cup_{n=1}^{\infty}A_n \in \cap_{i \in I}\mathfrak{F}_i$ $\square$

[*(back to generated $\sigma$-algebras)*](/notes/measure_integration/measure/borel-sigma-algebras/#generators)

## 2. Continuity of Measures
Prove the following lemma:

**Lemma.** If $(\Omega, \mathfrak{F}, \mu)$ is a measure space, then:

1. (Continuity from below) If $A_1 \subseteq A_2 \subseteq \ldots$ are all measurable, then $\lim_{n \to \infty} \mu(A_n) = \mu(\bigcup_{m=1}^\infty A_m)$.
2. (Continuity from above) If $A_1 \supseteq A_2 \supseteq \ldots$ are all measurable, and if $\mu(A_n)<+\infty$ for some $n$, then $\lim_{n \to \infty} \mu(A_n) = \mu(\bigcap_{m=1}^\infty A_m)$.

**Proof.**

To show (i), let $A_m = A_n \setminus A_{n-1}$ so that the $A_m$ are disjoint (and we have $A_n = \bigcup_{m=1}^n A_m$).  By the countable additivity of measures we have
$$\mu\left(\bigcup_{m=1}^\infty A_m\right) = \sum_{m=1}^\infty \mu(A_m)$$
$$= \lim_{n \to \infty} \sum_{m=1}^n \mu(A_m)$$
but from the above construction of the disjoint sets $A_m$ and finite additivity of measures we know that $\mu(A_n) = \sum_{m=1}^n \mu(A_m)$ so we have
$$= \lim_{n \to \infty}\mu(A_n).$$

On the other hand to show (ii), WLOG let $\mu(A_1)<+\infty$. Let $A = \bigcap_{m=1}^\infty A_m$ and $A_k = A_n \setminus A_{n+1}$ so that the $A_k$ are disjoint, and also any $A_k$ and $A$ are disjoint because 
$$x \in A \implies x \in A_n \forall n \implies x \notin A_k(:= A_n \setminus A_{n+1}).$$  

Then we have 
$$A_1 = A \cup \bigcup_{k=1}^\infty A_k.$$

By countable additivity we have 

$$\mu(A_1) = \mu(A) + \sum_{k=1}^\infty \mu(A_k)$$
$$= \mu(A) + \lim_{n \to\infty}\sum_{k=1}^n \mu(A_k)$$
but from the construction of $A_k$ and finite additivity of measures we know that $\mu(A_k) = \mu(A_n) - \mu(A_{n+1})$ so after cancellation of terms in the sum, we have
$$= \mu(A) + \lim_{n \to\infty} \left(\mu(A_1) - \mu(A_{n+1}) \right).$$
Hence, 
$$\mu(A_1) = \mu(A) + \mu(A_1) - \lim_{n \to \infty} \mu(A_n)$$
or equivalently, 
$$\lim_{n \to \infty} \mu(A_n) = \mu(A) = \mu\left(\bigcap_{m=1}^\infty A_m\right)$$
which is the desired result. $\square$

[*(back to properties of a measure)*](/notes/measure_integration/measure/general-measure-spaces/#properties-of-a-measure)

## 3. Discrete Probability Measure
Prove the following lemma:

**Lemma.** Suppose $\Omega=\{\omega_1, \ldots , \omega_n \}$ is a finite set.  Then we can find $p_1, \ldots, p_n \in [0,1]$ such that:

1. $p_1 + \ldots + p_n = 1$ and
2. for all $A \subseteq \Omega$, $P(A) = \sum_{i:w_i \in A} p_i$.

Conversely, any sequence $p_1, \ldots, p_n \in [0,1]$ that has the property (a) above defines a probability measure $P$ on the power set of $\Omega$ via the assignment $P(\{\omega_i\}):=p_i(i=1, \ldots, n).$

**Proof.**

We will always be able to find at least one such set $\{p_i:i= 1, \ldots,n\}$ satisfying (a), for example by defining ${p_i} =\frac{1}{n}$ for $i=1,\ldots,n$ so we have $\sum_{i=1}^n \frac{1}{n}=1$. Then $P(\emptyset) = 0, P(\Omega)=1$ and we have $P(A)=\sum_{i:\omega \in A}p_i$ for any set $A \subseteq \Omega$. $\square$

## 4. Intersection of Monotone Classes
Prove the following lemma:

**Lemma.** An arbitrary intersection of monotone classes is a monotone class.  In particular, there exists a smallest monotone class containing $\mathfrak{A}$.

**Proof.**

Recall that a class $\mathscr{M}$ of subsets of $\Omega$ is called a *monotone class* if it is closed under countable increasing unions and countable decreasing intersections:

1. $A_1, A_2, \ldots \in \mathscr{M}$ and $A_n \nearrow A \implies A \in \mathscr{M}$
2. $B_1, B_2, \ldots \in \mathscr{M}$ and $B_m \searrow B \implies B \in \mathscr{M}$

Let $\mathscr{M}\_i$ be monotone classes for all $i \in I$ for some possibly uncountable index set $I$.  Consider the set $\mathscr{M} = \bigcap_{i \in I} \mathscr{M}\_i$.  Suppose $A_n, B_m \in \mathscr{M}$ for all $n, m \in \mathbb{N}$.  

First we will show that $\mathscr{M}$ satisfies (1); i.e., that $A = \bigcup_n A_n \in \mathscr{M}$.  By the construction of $\mathscr{M}$ and the definition of intersection, we know that $A_n \in \mathscr{M_i}$ for all $i \in I, n \in \mathbb{N}$.  Since each $\mathscr{M}_i$ is a monotone class and is therefore closed under countable increasing unions, we have $A_n \nearrow A \implies A \in \mathscr{M}_i$ for all $i \in I$. Hence by the definition of intersection, $A \in \mathscr{M}$.  

Next we will show by a similar argument that $\mathscr{M}$ satisfies (2); i.e., that $B = \bigcap_m B_m \in \mathscr{M}$. By the definition of intersection, we know that $B_m \in \mathscr{M_i}$ for all $i \in I, m \in \mathbb{N}$.  Since each $\mathscr{M}_i$ is closed under countable decreasing intersections, $B_m \searrow B \implies B \in \mathscr{M}_i$ for all $i \in I$. Hence by the definition of intersection, $B \in \mathscr{M}$.  

We conclude that $\mathscr{M}$ is a monotone class. $\square$

## 5. Invariance of Lebesgue Measure
Prove that Lebesgue measure is translation invariant; i.e., the measure of $x+A$ is the same as the measure of $A$ provided $x+A$ and $A$ are $\mathfrak{B}_{\mathbb{R}}$-measurable.  Here, $x+A := \{x+y \; \vert \; y \in A\}$.  

Furthermore, if $m_{\alpha}$ denotes the Lebesgue measure on $([0,\alpha], \mathfrak{B}([0, \alpha]))$ for a given $\alpha > 0$, prove that for all measurable $A \subseteq [0, \alpha], \alpha^{-1}A$ is in $\mathfrak{B}([0,1])$ and $m_{\alpha}(A) = \alpha m_1 (\alpha^{-1}A)$.  In other words, prove that Lebesgue measure is scale-invariant.

**Proof.**
*(coming soon)*

[*(back to Lebesgue measure)*](/notes/measure_integration/measure/lebesgue-measure/#construction/)

## 6. Push-Forward Measure is a Measure
Suppose $(\Omega, \mathfrak{F}, \mu)$ is a measure space.  Let $\Omega'$ be as set, and let $\mathfrak{F}'$ denote a $\sigma$-algebra of subsets of $\Omega'$.  If $f: \Omega \to \Omega'$ is measurable, show that $f_*\mu := \mu \circ f^{-1}$ is a measure on $(\Omega', \mathfrak{F}')$, where 
$$\mu \circ f^{-1}(A) := \mu(\{\omega \in \Omega \; \vert \; f(\omega) \in A \})$$

**Proof.**

[Recall](/notes/measure_integration/measure/general-measure-spaces/#measures) that a *measure* $\mu : \mathfrak{F} \to \bar{\mathbb{R}}_0^+$ (where $\bar{\mathbb{R}} = \mathbb{R} \cup \{ -\infty, + \infty \}$) on a measurable space $(M, \mathfrak{F})$ is a map satisfying:

1. $\mu(\emptyset) = 0$

2. For pairwise disjoint $A_1, A_2, \ldots \in \mathfrak{F};$  $\forall i \neq j, A_i \cap A_j = \emptyset$ we have $\mu(\bigcup_{n\geq1}A_n)=\sum_{n \geq 1} \mu(A_n)$.

[Recall further](/notes/measure_integration/measure/measurable-maps/#measurable-maps) that a map $f: \Omega \to \Omega'$ is called *measurable* with respect to $\mathfrak{F}, \mathfrak{F}'$ if for all $A \in \mathfrak{F}'$ we have $f^{-1}(A) \in \mathfrak{F}$ (where $f^{-1}$ denotes the preimage of $f$).

First, to show that $\mu \circ f^{-1}(A)$ satisfies (1), let $A= \emptyset$.  Then by the measurability of $f$, clearly $f^{-1}(A) \in \mathfrak{F}$ and since $\mu$ is a measure on $\mathfrak{F}$, it satisfies $\mu(\emptyset) = 0$, and hence 
$$\mu \circ f^{-1}(A) = \mu(f^{-1}(A)) = \mu(\emptyset) = 0.$$

Now, to show that $\mu \circ f^{-1}(A)$ satisfies (2) ($\sigma$-additivity), we note that for a countable family of disjoint sets $A_1, A_2, \ldots \in \mathfrak{F}'$, we have (by the definition of measurable $f$) that $f^{-1}(A_1), f^{-1}(A_2), \ldots \in \mathfrak{F}$, and since $\mu$ is a measure on $\mathfrak{F}$, we have 
$$\begin{aligned}\mu \circ f^{-1}(\bigcup_{k \in \mathbb{N}} A_k) &= \mu(f^{-1}(\bigcup_{k \in \mathbb{N}} A_k)) \\\\
&= \mu(\bigcup_{k \in \mathbb{N}}f^{-1}( A_k)) \end{aligned}$$
and hence by the $\sigma$-additivity of $\mu$,
$$= \sum_{k \in \mathbb{N}} \mu(f^{-1}( A_k))$$
$$= \sum_{k \in \mathbb{N}} \mu \circ f^{-1}(A_k)$$
which is the desired result.  Hence we have proved that $\mu \circ f^{-1}(A)$ is a measure on $(\Omega', \mathfrak{F}')$. $\square$

[*(back to push-forward of a measure)*](/notes/measure_integration/measure/push-forward-of-measure/#motivation)

## 7. An Unmeasurable Set

*(coming soon)*

