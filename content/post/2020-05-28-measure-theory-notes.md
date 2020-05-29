---
title: Measure Theory Notes
author: Michael Bigelow
date: '2020-05-28'
slug: measure-theory-notes
categories:
  - Probability
tags:
  - mathematics
  - measure theory
  - probability
  - proofs
subtitle: ''
summary: 'Scribe notes on measure and integration.'
authors: [admin]
lastmod: '2020-05-28T21:24:32-06:00'
featured: yes
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

[Click here to go to the notes.](/notes/measure_integration/general-measure-spaces/)

## About the Notes
In preparation for a graduate course in probability theory, I have been preparing [scribe notes](/notes/measure_integration/general-measure-spaces/) on measure theory and integration.  The arc of the notes follows a pair of excellent measure theory lectures from a quantum theory lecture series by [Dr. Frederic Schuller](https://www.perimeterinstitute.ca/people/frederic-schuller). 

Throughout I use notation more like that employed by Dr. Davar Khoshnevisan, whose lecture notes on probability have proved useful to me.  I will be adding in some of the proofs omitted from Dr. Schuller's lectures, as I have encountered several of them as excercises while working through the preliminary chapters of Dr. Khoshnevisan's notes.  

These notes are intended to accompany a student who, like me, has enjoyed Dr. Schuller's very clear treatment of measure and integration on YouTube, but perhaps wishes to have the content accessible in written form for faster review or reference while working on other mathematics.

## Motivation - Physicist's Perspective
*As Schuller's [lecture](https://www.youtube.com/watch?v=6ad9V8gvyBQ) on YouTube provides the basis for the majority of the following scribe notes, I have transcribed (with a couple edits for better readability on the page) his perspective of the motivation below.*

"We provide a short recap of basic notions of measure theory for two reasons:

(1) Spectral theorem for self-adjoint operators requires--as we already saw from the axioms of quantum mechanics-- the (projection-valued) measures and unless we know what a measure is, and what a Borel measure is, we are lost there.

(2) **The** most-commonly emerging $\infty$-dimensional separable Hilbert space in quantum mechanics is the space $L^2(\mathbb{R}^d)$ (often $d=3$).  Informally speaking (though it's not entirely correct), these are all square-integrable functions on $\mathbb{R}^d$.  

"Well not quite: first, you must take equivalence classes of all square-integrable functions because if two square-integrable functions are the same *almost everywhere* (what that means we will see), then they belong to the same equivalence class and they are the same element of this set of functions.  Secondly, if I say square integrable it is not square-integrable with respect to the Riemann integral, but with respect to the Lebesgue integral, and that makes all the difference!

"To this point you have probably seen a number of theorems telling you under what circumstances you can exchange integrals and limits, or integrals and sums and so on, and you know that if you use the Riemann integral you have rather strong conditions like uniform convergence and stuff like this.  The Lebesgue integral heals this: the Lebesgue integral is a very proper notion of an integral, which for Riemann-integrable functions agrees with them but no longer poses such strong conditions (from the point of view of Lebesgue theory virtually none) on the functions, in order to be able to exchange limits and integrals.  So that you no longer even need to say (as the physicists do), "for reasonably well-behaved functions;" instead you describe the functions without this rather uninsightful qualification of being "reasonably-behaved," so the Lebesgue integral is the physicist's integral.  

"So there is no way in quantum mechanics to avoid the Lebesgue integral, everything else is child's play.  So we are going to develop that integral and what follows is the preparation for that."
