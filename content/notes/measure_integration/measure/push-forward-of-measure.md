---
title: Push-Forward of a Measure
linktitle: Push-Forward of a Measure
toc: true
type: docs
date: "2020-05-27T00:00:00Z"
draft: false
menu:
  docs:
    parent: measure
    weight: 50

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 50
---
*This section of notes summarizes material from 1:24:36 to 1:34:04 of Dr. Frederic Schuller's lecture on measure theory, viewable on [YouTube](https://youtu.be/6ad9V8gvyBQ?t=5078).*

## Motivation
Say one has a space equipped with a structure, and another space with not quite as much structure, you may be able to "inherit" the structure from the one space to the other space.  Below is one way to inherit a measure by "carrying" the measure on the domain to the target. It is quite a natural way to inherit a measure, though by far not the only one.

## Push-Forward of a Measure
**Definition.** Let $(M, \mathfrak{F}, \mu)$ be a measure space and $(N, \mathfrak{G})$ be a measurable space.  Further, let $f: M \to N$ be a measurable map.  Then the so-called *push-forward* $f^*\mu: \mathfrak{G} \to \bar{\mathbb{R}}^+_0$ is a measure on $(N, \mathfrak{G})$ and is defined by $(f^*\mu)(A) := \mu(f^{-1}(A))$ for a set $A \in N$.

**Proof.** (left as an exercise)



