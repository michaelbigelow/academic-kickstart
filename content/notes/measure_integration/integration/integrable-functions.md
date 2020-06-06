---
title: Integrable Functions
linktitle: Integrable Functions
toc: true
type: docs
date: "2020-05-27T00:00:00Z"
draft: false
menu:
  docs:
    parent: integration
    weight: 90

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 90
---
*This section of notes summarizes material from 49:04 to 1:13:46 of Dr. Frederic Schuller's lecture on integration of measurable functions, viewable on [YouTube](https://youtu.be/ot253Lhx2_o?t=2944).*

## Introduction
In order for a *general* (not necessarily non-negative) function $f: \Omega \to \bar{\mathbb{R}}$ to be integrable (having $\int f \\; d\mu$ defined) one needs, beyond $f$ being measurable, one very small extra technical condition.  If this extra condtion is satisfied, $f$ is called *integrable*.

## Integrability
More precisely,
**Definition.** A function $f: \Omega \to \bar{\mathbb{R}}$ is called *integrable* if:
1. $f$ is measurable; that is, $(\Omega, \mathfrak{F}, \mu)$ is a measure space and $(\bar{\mathbb{R}}, \bar{\sigma})$ a measurable space.
2. $\int \left| {f} \right|  d\mu < \infty$.

**Remark.** Condition (2) is equivalent to $\int f^+ \\; d\mu < \infty$ and $\int f^- \\; d\mu < \infty$ where both $f^+ := \max(f, 0)$ and $f^- := \max(-f, 0)$ pointwise and $f = f^+ - f^-$.

To define the integral of a general function, we must reduce it to the integrals over non-negative functions.  

## Integrals
**Definition.** The *integral* $\int f \\; d\mu$ of an integrable function $f$ is defined as: 
$$\int f \\; d\mu := \int f^+ \\; d\mu - \int f^- \\; d\mu$$

**Remark.** In quantum mechanics, we need to deal with functions $f: \Omega \to \mathbb{C}$.  Their integration theory follows immediately by treating the real and imaginary parts of $f$, $\Re(f)$ and $\Im(f)$ separately:
$$\int f \\; d\mu := \int \Re(f) \\; d\mu + i \int \Im(f) \\; d\mu.$$

## Properties
Consider integrable functions $f, g : \Omega \to \mathbb{R}$.  Then we have:
1. $f \leq_{a.e.} g \implies \int f \\; d\mu \leq \int g \\; d\mu$
2. $\int (f + \alpha g) d\mu = \int f \\; d\mu + \alpha \int g \\; d\mu \\; \\; \forall \alpha \in \mathbb{R}$ (linearity of the integral).

## Dominated Convergence Theorem
**Theorem.** Let:
1. $f_1, f_2, \ldots$ be a sequence of measurable functions
2. $f_n \to_{a.e.} f$ pointwise for some function f
3. $g$ be a non-negative measurable function with $\int g \\; d\mu < \infty$ 

such that for all $n \in \mathbb{N}, \left|f_n \right| \leq_{a.e.} g$.  Then we have:
1. $f$ and $f_1, f_2, \ldots$ are integrable.
2. $\lim_{n \to \infty} \int \left| f_n - f \right| \\; d\mu = 0$
3. $\lim_{n \to \infty} \int f_n \\; d\mu = \int f \\; d\mu$.

This theorem will prove quite useful.

**Theorem.** (Markov property) For all $z \in \mathbb{R}^+_0, \int f \\; d\mu \geq z \cdot (\mu \circ f^{-1})([z, \infty))$.
