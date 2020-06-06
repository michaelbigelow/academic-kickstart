---
title: Measurable Maps
linktitle: Measurable Maps
toc: true
type: docs
date: "2020-05-27T00:00:00Z"
draft: false
menu:
  docs:
    parent: measure
    weight: 40

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 40
---
*This section of notes summarizes material from 1:10:42 to 1:24:36 of Dr. Frederic Schuller's lecture on measure theory, viewable on [YouTube](https://youtu.be/6ad9V8gvyBQ?t=4242).*

## Motivation
The standard philosophy is to study spaces of a certain structure by studying maps between them which preserve the structure: 

$$(M, \mathfrak{F}_M) \to (N, \mathfrak{F}_N)$$

(where the map takes elements from the underlying set to the underlying set, but then you may employ the extra structure to impose a condition on the map).  In topology we have continuous maps that preserve the topology by pullback, so you do here by measurable maps.

## Measurable Maps
**Definition.** A map $f: M \to N$ is called *measurable* with respect to $\mathfrak{F}_M, \mathfrak{F}_N$ if for all $A \in \mathfrak{F}_N$ we have $f^{-1}(A) \in \mathfrak{F}_M$ (where $f^{-1}$ denotes the preimage of $f$).

Note that this is the definition of continuous maps, but with "topology" replaced by "$\sigma$-algebra" and "continuous" replaced by "measurable."  One immediately sees that this is compatible with choosing a Borel $\sigma$-algebra that is made from open sets; then one may see that continuous maps are measurable (though they are not the only measurable maps).  With one extra condition, the measurable maps are in fact the ones we can integrate.

## Testing for Measurability
**Lemma.** To show that a function $f$ is measurable, it suffices to check whether for all sets $A \in \mathfrak{A}$ we have $f^{-1}(A) \in \mathfrak{F}_M$ where $\mathfrak{F}_N = \sigma(\mathfrak{A})$.

As an example, if $\mathfrak{F}_N$ is the Borel $\sigma$-algebra, then the generating set $\mathfrak{A}$ is the collection of open sets.  Hence in particular, continuous maps are measurable.

**Corollary.** 
1. Any continuous map is measurable with respect to the Borel $\sigma$-algebras.  
2. Any monotonous map $f: \mathbb{R} \to \mathbb{R}$ is measurable with respect to the Borel $\sigma$-algebra.  

**Proof.** (of (2)) $f^{-1}(a, b) = (c, d)$ where $(a, b)$ and $(c, d)$ are intervals.  

**Theorem.** The composition $f \circ g : A \to C$ of two measurable maps $f: B \to C$ and $g: A \to B$ is again measurable.  

The proof is left as an exercise.  


