---
title: Sets of Measure Zero
linktitle: 5. Sets of Measure Zero
toc: true
type: docs
date: "2020-05-27T00:00:00Z"
draft: false
menu:
  measure_integration:
    parent: Measure
    weight: 60

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 60
---
*This section of notes summarizes material from 1:34:04 to the end of Dr. Frederic Schuller's lecture on measure theory, viewable on [YouTube](https://youtu.be/6ad9V8gvyBQ?t=5644).*

"Almost everywhere" is a term applied in various circumstances, but it always has to do with sets of measure zero.

## Sets of Measure Zero
**Definition.** Let $(M, \mathfrak{F}, \mu)$ be a measure space.  Then $A \in \mathfrak{F}$ is called a *set of measure zero* (null set) if $\mu(A)=0$.  

**Remark** There may be other null sets than $\emptyset$.  What is special about them?  From the set theoretic perspective, nothing.  From the measurable space perspective, something, because at least they are measurable.  From the measure space perspective, they are invisible.

## Almost Everywhere
Many statements we are going to prove hold "almost everywhere."  

**Terminology.**  A condition, e.g. equality or convergence or..., is said to hold "almost everywhere" (a.e.) if it holds for all $m \in M \setminus A$ for some $A$ with $\mu(A)=0$.  

## Examples
**Definition.** Let $f: m \to N$ and $g: M \to N$ be maps from a measure space $(M, \mathfrak{F}, \mu)$ and any naked set $N$.  Then $f =_{a.e.} g$ if and only if there exists some $A \in \mathfrak{F}$ with $\mu(A)=0$ such that for all $m \in M \setminus A \\; f(m)=g(m)$.

**Definition.** Now consider a sequence of maps $f_n : M \to N$ and a map $f: M \to N$.  Let $(M, \mathfrak{F}, \mu)$ be a measure space and $(N, \mathscr{O)})$ be a topological space.  Then $f_n \to_{a.e.} f$ if and only if there exists some $A \in \mathfrak{F}$ with $\mu(A)=0$ such that for all $m \in M \setminus A$ we have $f_n(m) \to f(m)$.


