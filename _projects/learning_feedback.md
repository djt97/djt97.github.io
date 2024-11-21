---
layout: page
title: Learning with Feedback Loops
description: Many learning processes have the feature that realizations of the data affect the data generating process itself.
img: assets/img/learning.png
importance: 1
category: "research (in progress)"
related_publications: false # true for references.
images:
  compare: true
  slider: true
---

### Abstract
Many learning processes have the feature that realizations of the data affect the data generating process itself. I present a class of sequential learning games in which learning is subject to feedback: a platform observes the actions of a sequence of agents who, in turn, observe actions from the platform. The resulting stochastic belief process is time-inhomogeneous because agents expect that the platform learns over time, and incentives for the platform exhibit the classic exploration-exploitation trade-off present in models of learning with experimentation. I provide a characterization of limiting equilibrium behavior when the platform is a benevolent social planner. Despite the complexity of the model, I show that in equilibrium, asymptotic learning turns on whether private beliefs are bounded or unbounded, as in the classic literature on social learning. I then show that a sophisticated platform is essential: even if private signals are unbounded, asymptotic learning can be derailed by a non-Bayesian social planner.

The paper is currently undergoing revisions.

{% comment %}
, and a summary of the model below. {% cite CTZ2024 %}.

<swiper-container keyboard="true" navigation="true" pagination="true" pagination-clickable="true" pagination-dynamic-bullets="true" rewind="true">
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/family_photos/Chels-Family-Session19.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/family_photos/Chels-Family-Session03.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/family_photos/Chels-Family-Session55.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
</swiper-container>

{% endcomment %}