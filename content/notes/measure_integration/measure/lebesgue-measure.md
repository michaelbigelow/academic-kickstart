---
title: Lebesgue Measure
linktitle: Lebesgue Measure
toc: true
type: docs
date: "2020-05-27T00:00:00Z"
draft: false
menu:
  docs:
    parent: measure
    weight: 30

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 30
---
*This section of notes summarizes material from 58:16 to 1:10:42 of Dr. Frederic Schuller's lecture on measure theory, viewable on [YouTube](https://youtu.be/6ad9V8gvyBQ?t=3496).*

## Motivation
We have seen how to generate a measurable space from a topological space.  How do we construct a measure?  The answer greatly depends upon the space under consideration.  The Lebesgue measure is a special construction of a measure defined on a very specific kind of sets, namely $\Omega = \mathbb{R}^d$. 

## Construction
**Definition.** Consider $\Omega = \mathbb{R}^d$ and its Borel $\sigma$-algebra $\mathfrak{B}\_{\mathbb{R}^d}$ as defined in the previous section.
Then the **unique** map $\lambda := \mu_{Lebesgue, \mathbb{R}^d} : \mathfrak{B}\_{\mathbb{R}^d} \to \bar{\mathbb{R}}^+_0$ is defined by 

$$\begin{aligned}
\lambda \left([a_1, b_1) \times [a_2, b_2) \times \ldots \times [a_d, b_d) \right) \\\\
= (b_1-a_1) \cdot \ldots \cdot (b_d - a_d), \\; a_i < b_i.
\end{aligned}$$ 

is called the *Lebesgue measure on $\mathbb{R}^d$*.  The proof of its existence and uniqueness is not a minor result and is treated elsewhere.

**Remark.** Consider $(\mathbb{R}^d, + , \cdot, | \cdot |)$.  This can be readily recovered from $(\mathbb{R}^d, \mathfrak{B}_{\mathbb{R}^d}, \lambda)$.  

From now on, we will operate under the assumption that $\mathbb{R}^d$ always be equipped, if the need arises, with the Borel $\sigma$-algebra $\mathfrak{B}_{\mathbb{R}^d}$, and the Lebesgue measure.

**Remark.** Obviously, $\lambda$ is a finite measure.

**Remark.** An alternative unique characterization of $\lambda$ is that it is the measure that is invariant under translation: 

$$\lambda(A + v) = \lambda(A) \\; \forall A \in \mathfrak{B}_{\mathbb{R}^d}, \\; \forall v \in \mathbb{R}^d$$

and which sends $\lambda \left( [0,1]^d \right)$ to $+1$.  The proof of this shall be [left as an exercise](/notes/measure_integration/exercises/measure-theory-exercises/#5-invariance-of-lebesgue-measure/).
