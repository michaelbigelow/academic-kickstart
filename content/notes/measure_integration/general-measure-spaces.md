---
title: Measure Theory
linktitle: I. General Measure Spaces
toc: true
type: docs
date: "2020-05-27T00:00:00Z"
draft: false
menu:
  measure_integration:
    parent: Measure
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

## I. General Measure Space
The first definition we provide is that of a $\sigma$-algebra, which bears resemblance to a topology, but is different.

Definition. Let $M$ be a non-empty set.  Then a collection of subsets $\mathfrak{F} \subseteq P(M)$ is called a $\sigma \text{-algebra for} M$ if

(i) $M \in \mathfrak{F}$

(ii) $A \in \mathfrak{F} \implies M \setminus A \in \mathfrak{F}$

(iii) $A_1, A_2, \ldots \in \mathfrak{F}$ and $A_i \cap A_j = \emptyset$ for $i \neq j \implies \bigcup_{n \geq 1} A_n \in \mathfrak{F}$



