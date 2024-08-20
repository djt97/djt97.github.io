---
layout: page
title: Learning with Feedback Loops
description: What happens when LLMs learn from their own output?
img: assets/img/learning.png
importance: 1
category: "research (in progress)"
related_publications: false # true for references.
images:
  compare: true
  slider: true
---

### Abstract
I develop a model of learning in which information is subject to *feedback loops*. In my leading example, a "Large Language Model" (LLM) draws signals from a *database*, and updates its belief about a state of the world. The LLM chooses whether to make a recommendation to agents on how they should act, and these actions feed back into the next-period database. Because actions based on the LLM's recommendation are totally uninformative to the LLM, the quality of information deteriorates over time. LLM recommendations generate "synthetic data" which can improve short-term outcomes for agents (*agent learning*) but this always comes at the expense of data-pollution, which lowers the quality of recommendations (*LLM  learning*). An LLM which values the future quality of agents' decisions may prefer to slow down the frequency with which it makes recommendations. I discuss policies that lead to better outcomes ex-ante and consider the implications of my model for the future of generative AI.

The paper is currently undergoing revisions but you can find slides for an earlier draft of the paper [here]({% link assets/pdf/learning_feedback_old_slides.pdf %}).

{% comment %}
, and a summary of the model below. {% cite CTZ2024 %}.

<swiper-container keyboard="true" navigation="true" pagination="true" pagination-clickable="true" pagination-dynamic-bullets="true" rewind="true">
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/family_photos/Chels-Family-Session19.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/family_photos/Chels-Family-Session03.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/family_photos/Chels-Family-Session55.jpg" class="img-fluid rounded z-depth-1" %}</swiper-slide>
</swiper-container>

{% endcomment %}