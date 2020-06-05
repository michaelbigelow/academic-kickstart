---
# Course title, summary, and position.
linktitle: 
summary: These are scribe notes I have prepared from Professor Frederic Schuller's lectures on measure and integration.
weight: 1

# Page metadata.
title: Measure and Integration
date: "2020-05-27T00:00:00Z"
lastmod: "2020-05-27T00:00:00Z"
draft: false  # Is this a draft? true/false
toc: true  # Show table of contents? true/false
type: docs  # Do not modify.

# Add menu entry to sidebar.
# - name: Declare this menu item as a parent with ID `name`.
# - weight: Position of link in menu.
menu:
  docs:
    parent: Introduction
    weight: 5
    
weight: 5
---

The following notes are based on two excellent lectures by Dr. Frederic Schuller, augmented where appropriate for clarity.  Scroll to the bottom of this page to view the YouTube videos of the lectures.

I hope my notes help the material of the lectures linger for you as they have for me.  [Click here to jump in!](/notes/measure_integration/measure/general-measure-spaces/)

## Motivation - A Physicist's Perspective
*Below is Dr. Schuller's explanation of the motivation for the development of measure theory, from the perspective of the physicist.*

"We provide a short recap of basic notions of measure theory for two reasons:

1. Spectral theorem for self-adjoint operators requires--as we already saw from the axioms of quantum mechanics-- the (projection-valued) measures and unless we know what a measure is, and what a Borel measure is, we are lost there.

2. **The** most-commonly emerging $\infty$-dimensional separable Hilbert space in quantum mechanics is the space $L^2(\mathbb{R}^d)$ (often $d=3$).  Informally speaking (though it's not entirely correct), these are all square-integrable functions on $\mathbb{R}^d$.  

"Well not quite: first, you must take equivalence classes of all square-integrable functions because if two square-integrable functions are the same *almost everywhere* (what that means we will see), then they belong to the same equivalence class and they are the same element of this set of functions.  Secondly, if I say square integrable it is not square-integrable with respect to the Riemann integral, but with respect to the Lebesgue integral, and that makes all the difference!

"To this point you have probably seen a number of theorems telling you under what circumstances you can exchange integrals and limits, or integrals and sums and so on, and you know that if you use the Riemann integral you have rather strong conditions like uniform convergence and stuff like this.  The Lebesgue integral heals this: the Lebesgue integral is a very proper notion of an integral, which for Riemann-integrable functions agrees with them but no longer poses such strong conditions (from the point of view of Lebesgue theory virtually none) on the functions, in order to be able to exchange limits and integrals.  So that you no longer even need to say (as the physicists do), "for reasonably well-behaved functions;" instead you describe the functions without this rather uninsightful qualification of being "reasonably-behaved," so the Lebesgue integral is the physicist's integral.  

"...so there is no way in quantum mechanics to avoid the Lebesgue integral, everything else is child's play.  We are going to develop that integral, and what follows is the preparation for that."

## Lecture Videos

{{< youtube 6ad9V8gvyBQ >}}



{{< youtube ot253Lhx2_o >}}


