---
layout: page
title: Learning with Feedback Loops
description: Many learning processes have the feature that realizations of the data affect the data generating process itself.
img: assets/img/learning-with-feedback.png
importance: 1
category: "research (in progress)"
related_publications: false # true for references.
images:
  compare: true
  slider: true
---

### Abstract
Many learning processes have the feature that realizations of the data affect the data generating process itself. I investigate the impact of this phenomena—which I term "feedback loops"—on learning processes mediated by recommendation systems. In particular, I characterize the learning outcomes when the platform is naïve in the sense that it fails to account for feedback in the data. Naïve platforms induce failures of asymptotic learning among agents, even when agents possess arbitrarily precise information. This results in persistent errors in recommendations, which can influence the actions of a large number of agents in equilibrium. Conversely, platforms which correctly account for feedback guarantee asymptotic learning and correct herding. My findings emphasize the critical need for recommendation systems to account for feedback in the data.

The paper is currently undergoing revisions but you can find slides on the paper [here](/assets/pdf/LWFL_DJ_Dec24.pdf).

{% comment %}
, and a summary of the model below. {% cite CTZ2024 %}.

<swiper-container keyboard="true" navigation="true" pagination="true" pagination-clickable="true" pagination-dynamic-bullets="true" rewind="true">
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/family_photos/Chels-Family-Session19.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/family_photos/Chels-Family-Session03.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/family_photos/Chels-Family-Session55.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
</swiper-container>

{% endcomment %}