---
title: Simple Functions
linktitle: Simple Functions
toc: true
type: docs
date: "2020-05-27T00:00:00Z"
draft: false
menu:
  docs:
    parent: integration
    weight: 70

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 70
---
*This section of notes summarizes material from 0:00 to 10:53 of Dr. Frederic Schuller's lecture on integration of measurable functions, viewable on [YouTube](https://youtu.be/ot253Lhx2_o).*

## Introduction
The key definition of the next sections is that of the *Lebesgue integral*.  Previously we have developed the Lebesgue measure on $\mathbb{R}^d$.  Now the Lebesgue integral is not necessarily to be performed with the Lebesgue measure, though it can be.  The key application from the point of view of the physicist will be to define the $L^p$-spaces, which are the spaces of functions whose p-th power of their absolute value is integrable.  There are certain other conditions that must be entertained to make these into proper *Banach spaces*, or in the case $p=2$, a *Hilbert space*, approximately the space of square-integrable functions, seen everywhere in quantum mechanics.

## Simple Functions
As a technical tool, we introduce the following:

**Defintion.**  A measurable function $s: \Omega \to \mathbb{R}^+_0$ is called a *simple function* if $s(\Omega) = \\{s_1, \ldots, s_N \\}$ for some $N \in \mathbb{N}$.  

Implicit in the word "measurable" is the fact that we have chosen $\sigma$-algebras $\mathfrak{F}$ on $\Omega$, and $\sigma(\mathscr{O} |_{\mathbb{R}^+_0})= \mathfrak{B}_{\mathbb{R}}$ on $\mathbb{R}^+_0$.

In the domain, the function takes only finitely many different values, so this truly is a simple function.

**Implication.** $s^{-1}(\\{s_i\\}) \in \mathfrak{F}$, as of course $s_i \in \mathfrak{B}_{\mathbb{R}}$.

**Implication.** $s = \sum_{z \in s(\Omega)} z \cdot \mathbf{1}_{s^{-1}(\\{s_i\\})}$ where for any $A \subseteq \Omega$ we define $\mathbf{1}_A : \Omega \to \mathbb{R}$ as 
$$\mathbf{1}_{A}(\omega):= 
\begin{cases}
1 & \omega \in A \\\\
0 & \omega \notin A .
  \end{cases}$$

Note that the above sum is not a series: it is finite.


