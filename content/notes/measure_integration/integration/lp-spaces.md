---
title: The Function Spaces $L^p(\Omega, \mathfrak{F}, \mu)$ 
linktitle: The Function Spaces $L^p(\Omega, \mathfrak{F}, \mu)$
toc: true
type: docs
date: "2020-05-27T00:00:00Z"
draft: false
menu:
  docs:
    parent: integration
    weight: 100

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 100
---
*This section of notes summarizes material from 1:13:46 to the end of Dr. Frederic Schuller's lecture on integration of measurable functions, viewable on [YouTube](https://youtu.be/ot253Lhx2_o?t=4426).*

## Introduction
**Fact.** Quantum mechanics of a particle in 3 space dimensions rests on the Hilbert space $L^2(\mathbb{R}^3, \mathfrak{B}_{\mathbb{R}^3}, \lambda^3)$.

While for quantum mechanics we will need the theory for the special case $p=2$ only, it is worthwhile to develop it for any real $1 \leq p \leq \infty$.  

## $\mathscr{L}^p$ Spaces
**Definition.** For $f$ measurable, we define the set $$\mathscr{L}^p := \left\\{f: \Omega \to \mathbb{C} \\; \bigg\vert \\; \int \left| f \right|^p d\mu < \infty \right\\}.$$

We equip $\mathscr{L}^p$ with pointwise $+$ and $\cdot$.  For an explanation of this, see [Dr. Schuller's exposition.](https://youtu.be/ot253Lhx2_o?t=4726) Doing so makes $(\mathscr{L}^p(\Omega, \mathfrak{F}, \mu), +, \cdot)$ into a $\mathbb{C}$-vector space.  

We would like to make progress toward Hilbert and Banach spaces; to this end, let us give this vector space a norm to make it a normed space. We may then check that the space is complete with respect to the norm, which would make it a Banach space.  It turns out that  these $L^p$ spaces are all Banach spaces with respect to a norm.  There is a small complication that is often suppressed in quantum mechanics courses, but which becomes important in other areas, such as solid state physics.  

## Semi-norms
**Theorem.** The map $\left\|\cdot \right\|_{p}^{\text{(semi)}}: \mathscr{L}^p \to \mathbb{R}$ defined as $\left\|\cdot \right\|_{p}^{\text{(semi)}} := \left( \int \left| f \right|^p d\mu \right)^{\frac{1}{p}}$ for $p \in \mathbb{R}$ with $1 \leq p \leq \infty$ is a seminorm, satisfying:

1. (positive homogeneity) $\forall \alpha \in \mathbb{C}$ we have $\left\| \alpha f \right\|_{p}^{\text{(semi)}} = \left| \alpha \right| \cdot \left\|f \right\|_{p}^{\text{(semi)}}$
2. (Minkowski identity) $\left\|f + g \right\|_{p}^{\text{(semi)}} \leq \left\| f \right\|_{p}^{\text{(semi)}} + \left\| g \right\|_{p}^{\text{(semi)}}$
3. $\left\|f \right\|_{p}^{\text{(semi)}} \geq 0$.

Note that the requirement of a norm is that whenever the norm of the function is zero, the function itself is equal to zero; here we have only that whenever the seminorm is zero, the function is equal to zero *almost everywhere*. This causes means that $(\mathscr{L}^p, +, \cdot, \left\|\cdot \right\|_{p}^{\text{(semi)}})$ is not even a normed space, and hence we are not going to work with the spaces $\mathscr{L}^p$.

## $L^p$ Spaces
To remove the troublesome f which are zero almost everywhere while refusing to be zero everywhere, define the following equivalence relation: call $f, g \in \mathscr{L}^p$ equivalent:
$$f \sim g : \iff f =_{a.e.} g$$

**Proof.** To show that this is an equivalence relation, we must check that it satisfies:
1. (Symmetry) $f \sim g \iff g \sim f$
2. (Reflexivity) $f \sim f$
3. (Transitivity) $f \sim g$ and  $g \sim h \implies f \sim h$.

Clearly these hold, with (3) due to the fact that the union of two sets of measure zero is itself measure zero.  

**Definition.** For any equivalence relation $\sim$ on a set $\Omega$ one has the so-called *quotient space,* 
$$\Omega / \sim \\; := \\{[\omega]_{\sim} \\; \vert \\; \omega \in \Omega \\}$$
where 
$$[\omega] := \\{\bar{\omega} \\; \vert \\; \bar{\omega} \sim \omega \\} .$$

**Definition.** For our $f \sim g : \iff f =_{a.e.} g$ we have 
$$L^p := \mathscr{L}^p/ \sim \\; = \\{[f]_{\sim} \\; \vert \\; f \in \mathscr{L}^p \\}$$

It remains to check that we can declare an addition and scalar multiplication, and inherit a norm on the space $L^p$, and that these are well-defined.  Such checks are beyond the current scope of these notes.

## Banach Spaces
**Theorem.** $|| \cdot ||_p :L^p \to \mathbb{R}$ where $|| \cdot ||_p := \left\| [\cdot] \right\|_{p}^{\text{(semi)}}$ is a norm on $L^p$.  That is, $(L^p(\Omega, \mathfrak{F}, \mu), +, \cdot, ||\cdot||_p)$ is a normed space.

**Theorem.** $(L^p(\Omega, \mathfrak{F}, \mu), +, \cdot, ||\cdot||_p)$ is a *Banach space*.

**Fact.** (Hölder inequality) Provided $1 \leq p, q < \infty$ and $\frac{1}{p} + \frac{1}{q} = 1$, then
$$\bigg\vert \int \bar{f} \cdot g \\; d\mu \bigg\vert \leq \left(\int\vert f \vert^p \\; d\mu \right) ^{\frac{1}{p}} + \left(\int\vert g \vert^q \\; d\mu \right) ^{\frac{1}{q}}. $$

**Observation.** Letting $\langle[f], [g]\rangle := \int \bar{f} \cdot g \\; d\mu$ (which we must check for well-definition), $\langle\cdot, \cdot\rangle: L^p \times L^p \to \mathbb{C}$, we have defined a *sesquilinear inner product.*

So under what conditions does this become a Cauchy inequality? As it turns out, only in the case $p=2$ do we have the Cauchy inequality:
$$\langle[f], [g]\rangle \leq ||[f]||_2 + ||[g]||_2.$$

**Corollary.** $(L^p(\Omega, \mathfrak{F}, \mu), +, \cdot, \langle\cdot|\cdot\rangle)$ is a Hilbert space.

This is the space of (so-called) square-integrable complex functions, or in quantum mechanics, the wave functions.
