---
layout: page
title: start here
permalink: /start/
description: a few places to begin
nav: true
nav_order: 1
body_class: start-layout
---

<div class="start-page">
  <section class="start-intro">
    <p class="start-lede">
      I'm an economist at the <a href="https://www.cognitiveeconomics.com/" rel="noopener">Manos Institute for Cognitive Economics</a>, working on how people reason and how groups coordinate. Here's a paper, an
      essay, a tool, and a way to stay in touch.
    </p>
  </section>

  <section class="start-route-grid" aria-label="Recommended starting points">
    <a class="start-route start-route-paper" href="{% link _projects/bad_networks.md %}">
      <span class="start-route-icon"><i class="fa-solid fa-file-lines"></i></span>
      <span class="start-route-label">Read a paper</span>
      <strong>Bad Networks</strong>
      <p>Why useful-but-harmful networks are easy to establish and hard to escape.</p>
      <span class="start-route-action">Open research <i class="fa-solid fa-arrow-right"></i></span>
    </a>

    <a class="start-route start-route-essay" href="{% link _posts/25-12-18-proof-checkers.md %}">
      <span class="start-route-icon"><i class="fa-solid fa-pen-nib"></i></span>
      <span class="start-route-label">Read an essay</span>
      <strong>AI is turning us into proof-checkers, not proof-writers</strong>
      <p>In a world where AI writes proofs, the real skill is asking the right questions.</p>
      <span class="start-route-action">Read essay <i class="fa-solid fa-arrow-right"></i></span>
    </a>

    <a class="start-route start-route-tool" href="{% link _pages/ghostwriter-for-anki.md %}">
      <span class="start-route-icon"><i class="fa-solid fa-screwdriver-wrench"></i></span>
      <span class="start-route-label">Try a tool</span>
      <strong>Ghostwriter for Anki</strong>
      <p>A Chrome extension for making flashcards from what you read.</p>
      <span class="start-route-action">Try it <i class="fa-solid fa-arrow-right"></i></span>
    </a>

    <a class="start-route start-route-touch" href="{% if site.newsletter.enabled %}#start-newsletter{% else %}{{ '/blog/' | relative_url }}{% endif %}">
      <span class="start-route-icon"><i class="fa-solid fa-envelope-open-text"></i></span>
      <span class="start-route-label">Stay in touch</span>
      <strong>Essays every few weeks</strong>
      <p>On economics, AI, and tools&nbsp;for&nbsp;thought.</p>
      <span class="start-route-action">Subscribe <i class="fa-solid fa-arrow-right"></i></span>
    </a>

  </section>

  <section class="start-collab">
    <div>
      <p class="start-kicker">Open Questions</p>
      <h2>Subscribe to Open Questions.</h2>
      <p class="start-collab-copy">Essays on economics, AI, and tools&nbsp;for&nbsp;thought — every few weeks.</p>
    </div>

    {% if site.newsletter.enabled %}
      <div id="start-newsletter" class="start-newsletter">
        {% include scripts/newsletter.liquid left=true %}
      </div>
    {% else %}
      <a class="start-rss-link" href="{{ '/feed.xml' | relative_url }}">Follow by RSS</a>
    {% endif %}

  </section>

  <nav class="start-browse-strip" aria-label="Browse the full site">
    <a href="{{ '/projects/' | relative_url }}">research</a>
    <a href="{{ '/blog/' | relative_url }}">blog</a>
    <a href="{{ '/tools/' | relative_url }}">tools</a>
    <a href="{{ '/cv/' | relative_url }}">cv</a>
    <a href="{{ '/personal/' | relative_url }}">personal</a>
  </nav>
</div>
