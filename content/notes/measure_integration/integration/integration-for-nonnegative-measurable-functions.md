---
title: Integration for Non-negative Measurable Functions
linktitle: Non-negative Measurable Functions
toc: true
type: docs
date: "2020-05-27T00:00:00Z"
draft: false
menu:
  docs:
    parent: integration
    weight: 80

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 80
---
*This section of notes summarizes material from 10:53 to 49:04 of Dr. Frederic Schuller's lecture on integration of measurable functions, viewable on [YouTube](https://youtu.be/ot253Lhx2_o?t=653).*

## Introduction
One might think that we immediately begin integrating simple functions, but in fact we start much more generally by defining integration for non-negative measurable functions.  Ultimately there is a small extra condition beyond measurability that is needed for integrability; however, at this point we make still another restriction, and that is that the functions in question be non-negative.  In the next section we shall extend this to any measurable function satisfying the extra condition to which we allude above.

## Non-negative Measurable Functions
**Definition.** By a non-negative measurable function, we mean $f: \Omega \to \bar{\mathbb{R}}$ such that 
1. $f(\omega) \geq 0$ for all $\omega \in \Omega$  
2. $f$ is measurable.

Once again, "measurable" implies the selection of a $\sigma$-algebra on both $\Omega$ and $\bar{\mathbb{R}}$.  For $\Omega$ let the $\sigma$-algebra be $\mathfrak{F}$; for $\bar{\mathbb{R}}$ we may not take the Borel $\sigma$-algebra $\mathfrak{B}_{\mathbb{R}}$ because the target is no longer $\mathbb{R}$, but $\bar{\mathbb{R}}$ -- the extended real numbers (this choice permits us to leave the domain untouched, which will serve us here better).  We instead equip $\bar{\mathbb{R}}$ with a $\sigma$-algebra 

$$\bar{\sigma} = \\{A \subseteq \bar{\mathbb{R}} \\;|\\; A \cap \mathbb{R} \in \mathfrak{B}_{\mathbb{R}} \\}.$$

With these conditions, all measurable functions are integrable.  Later, when we drop the non-negativity condition, that is the point at which a small condition beyond measurability enters.  

## Integral
In order to define the integral of a non-negative measurable function, we need to have a measure $\mu$ on the domain.  

**Definition.** Let $(\Omega, \mathfrak{F}, \mu)$ be a measure space [($\bar{\mathbb{R}}, \bar{\sigma})$ a measurable space].  Then the integral $\int f \\; d\mu $ of a non-negative measurable function $f: \Omega \to \bar{\mathbb{R}}$ is the number $(\in \bar{\mathbb{R}})$

$$\int_{\Omega} f \\; d\mu := \sup \left\\{ \sum_{z \in s(\Omega)} z \cdot (\mu \circ s^{-1})(z) \\; \vert \\; 0 \leq s \leq f \right\\}$$

for all simple functions $s$. 

**Definition.** Let $A \in \mathfrak{F}$; i.e., a measurable subset $A \subseteq \Omega$, then we define 

$$\int_A f \\; d\mu := \int f \cdot \mathbf{1}_A d\mu$$

where $(f \cdot \mathbf{1}_A)(\omega):=f(\omega)\cdot \mathbf{1}_A(\omega)$.

**Notation.** It is often *very* convenient to write the function values, i.e. $\int f(x) \\; \mu(dx)$, instead of $\int f \\; d\mu$, the function itself.

**Application.** Often in the spectral theorem and elsewhere, we wish to write $\int sq_{\mathbb{R}} \\; d\mu$ where $sq_\mathbb{R}: \mathbb{R} \to \mathbb{R}$ is defined as the function that takes $x \mapsto x^2$.  But it would be so much more convenient to write 

$$\int x^2 \\; \mu(dx) \\; \\; \left(= \int sq_{\mathbb{R}}(x) \\; \mu(dx) \right).$$

Of course, $x^2$ is not a function: it is the function values; this is merely notation.

## Properties of Non-negative Measurable Functions
1. Markov inequality: for $z \in \mathbb{R}^+_0$, $\int f \\; d\mu \geq z \cdot (\mu \circ f^{-1}(z))$
2. $f \leq_{a.e.} g \implies \int f \\; d\mu \leq \int g \\; d\mu$
3. $f =_{a.e.} g \implies \int f \\; d\mu = \int g \\; d\mu$
4. $\int f \\; d\mu = 0 \implies f =_{a.e.} 0$
5. $\int f \\; d\mu < \infty \implies f <_{a.e.} \infty$

## Monotone Convergence Theorem
The pivotal theorem of Lebesgue integration theory is the Theorem on Monotone Convergence.

**Theorem.** Let $ 0 \leq f_1 \leq f_2 \leq \ldots$ be a sequence of measurable functions $ f_n: \Omega \to \bar{\mathbb{R}}$.  Provided $f:= \sup_{n\geq 1} f_n$ pointwise, then 
$$\lim_{n \to \infty} \int f_n \\; d\mu = \int f \\; d\mu.$$
The idea is that you can exchange the limit and the integration.  This is unheard-of in Riemann integration: it is simply not true. This theorem is thus a consequence of having defined the Lebesgue integral.  

## Additional Results
Before we continue, let us collect two results:

**Theorem.** Let $ f, g \leq 0$ be measurable.  Let $\alpha \in \mathbb{R}^+_0$.  Then 
$$\int (f+\alpha g) \\; d\mu = \int f \\; d\mu + \alpha \int g \\; d\mu.$$

**Theorem.** For any sequence $f_n: \Omega \to \bar{\mathbb{R}}^+_0$ (measurable) we have 
$$\int \left( \sum_{n=1}^{\infty} f_n \right) d\mu = \sum_{n=1}^{\infty} \int f_n \\; d\mu .$$

This is simply not true with the Riemann integral.  You can imagine how useful this result will be on an infinite-dimensional Hilbert space.  Any non-negative measurable function can be given a value in $\bar{\mathbb{R}}^+_0$ with this definition of integral; all that remains is to get rid of the non-negativity condition we have imposed.
