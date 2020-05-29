---
title: General Measure Spaces
linktitle: 1. General Measure Spaces
toc: true
type: docs
date: "2020-05-27T00:00:00Z"
draft: false
menu:
  measure_integration:
    parent: Measure
    weight: 10

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 10
---
*This section of notes summarizes material from 5:18 to 36:33 of Dr. Frederic Schuller's lecture on measure theory, viewable on [YouTube](https://youtu.be/6ad9V8gvyBQ?t=318).*

## Sigma-Algebras
The first definition we provide is that of a $\sigma$-algebra, which bears resemblance to a topology, but is different.

**Definition.** Let $\Omega$ be a non-empty set.

Then a collection of subsets $\mathfrak{F} \subseteq \mathscr{P}(\Omega)$ is called a $\sigma$ *-algebra for* $\Omega$ if

1. $\Omega \in \mathfrak{F}$

2. $A \in \mathfrak{F} \implies \Omega \setminus A \in \mathfrak{F}$

3. $A_1, A_2, \ldots \in \mathfrak{F} \implies \bigcup_{n \geq 1} A_n \in \mathfrak{F}$

We will see what one can do with a $\sigma$-algebra, and why one needs one, but first, some terminology:

## Measurable Sets
**Terminology.** $A \in \mathfrak{F}$ is called a *measurable set* in $\Omega$. Naively one might think that if we take a subset of $\Omega$, why wouldn't we be able to assign a volume to every subset?  It turns out we cannot do this: only the sets in the $\sigma$-algebra can be assigned a meaningful volume.  The $\sigma$-algebra might as well be termed "the set of measurable subsets."


**Terminology.** The pair $(\Omega, \mathfrak{F})$ is called a *measurable space* (so we already have a double-working of the word "measurable": you may have a measurable set -- itself an element of $\mathfrak{F}$-- and then the pair $(\Omega, \mathfrak{F})$ is called a measurable space).  This stands distinct from a *measure space*, which is a measurable space, together with a *measure*, which is a map that assigns to each measurable set a number interpreted as the "volume" of that set.

**Remark.** Clearly, taking $\mathfrak{F}=\mathscr{P}(\Omega)$ is a $\sigma$-algebra.  In general, however, it does not provide a useful $\sigma$-algebra (similar to how the discrete topology is not a useful topology) if M is non-countable. (examine Banach-Tarski)

## Measures
**Definition.** A measure $\mu : \mathfrak{F} \to \bar{\mathbb{R}}_0^+$ (where $\bar{\mathbb{R}} = \mathbb{R} \cup \\{ -\infty, + \infty \\}$) on a measurable space $(M, \mathfrak{F})$ is a map satisfying:

1. $\mu(\emptyset) = 0$

2. For pairwise disjoint $A_1, A_2, \ldots \in \mathfrak{F};$  $\forall i \neq j, A_i \cap A_j = \emptyset$ we have $\mu(\bigcup_{n\geq1}A_n)=\sum_{n \geq 1} \mu(A_n)$.

Property (2) is often called $\sigma$-additivity.  

So the whole raison d'être for a measurable space is that on it I can assign to each measurable set an actual number; one could call it the "volume" of the set. In probability theory for instance, one may assign to a set of outcomes the probability of that set.  In $\mathbb{R}^d$ we will have a canonical measure called the *Lebesgue measure* but we start in this abstraction to be sufficiently prepared for all the applications of measure theory.

**Terminology.** The triple $(\Omega, \mathfrak{F}, \mu)$ is called a *measure space.*

## Properties of a Measure
1. Monotony: $A_1 \subseteq A_2 \implies \mu(A_1) \leq \mu(A_2)$ for $A_1, A_2 \in \mathfrak{F}$

2. Sub-additivity: $\{A_1, A_2, \ldots \} \subseteq \mathfrak{F} \implies \mu \left(\bigcup_{n \geq 1} A_n \right) \leq \sum_{n \geq 1} \mu(A_n)$

3. Continuity from below: Suppose we have an increasing exhaustive sequence of measurable sets: $A_1 \subseteq A_2 \subseteq \ldots; \bigcup_{n \geq 1} A_n = A$.  Then we have $lim_{n \to \infty}\mu(A_n) = \mu(A)$.

4. Continuity from above: Suppose we have an decreasing enveloping sequence of measurable sets: $A_1 \supseteq A_2 \supseteq \ldots; \bigcap_{n \geq 1} A_n = A$ (note that $\bigcap_{n \geq 1} A_n \in \mathfrak{F}$ due to deMorgan's rule), and $\mu(A_n) < \infty$ for some $n$.  Then we have $lim_{n \to \infty}\mu(A_n) = \mu(A)$.  

Proof of (3) and (4) are left as an exercise.

**Definition.**  A measure $\mu$ is called *finite* if $\exists \\{A_1, A_2, ...\\} \subseteq \mathfrak{F}$ with $\bigcup_{n \geq 1}A_n = \Omega$ such that $\mu(A_n) < \infty \\; \forall n \in \mathbb{N}$.

## Summary
"So we start with a set ($\Omega$), and we make a selection of sets of subsets which we call measurable, and in order for our theorems to work they must satisfy certain conditions.  

"The basic idea is that not every subset can be called a meaningful set for our purposes.  Once we have chosen sets that are meaningful in this way, together constituting a $\sigma$-algebra, we can define a function $\mu$ that takes each of the sets of the $\sigma$-algebra and assigns it a number.  For a while people thought that to each subset you could assign a measure, and that led to great trouble. The breakthrough was to realize that this is not possible, not for the purpose you have in mind." --Dr. Frederic Schuller

