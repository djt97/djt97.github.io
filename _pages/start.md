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
      essay, a tool, and a way to get in touch.
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

    <a class="start-route start-route-touch" href="#get-in-touch">
      <span class="start-route-icon"><i class="fa-solid fa-envelope-open-text"></i></span>
      <span class="start-route-label">Get in touch</span>
      <strong>Email, YouTube, and tools</strong>
      <p>Questions about research, talks, or the tools I've built.</p>
      <span class="start-route-action">Get in touch <i class="fa-solid fa-arrow-right"></i></span>
    </a>

  </section>

  <section id="get-in-touch" class="start-collab">
    <div>
      <p class="start-kicker">Contact</p>
      <h2>Get in touch.</h2>
      <p class="start-collab-copy">Email is the easiest way to reach me. I also post videos on YouTube and share tools I've built.</p>
    </div>

    {% include contact_links.liquid %}

  </section>

  <nav class="start-browse-strip" aria-label="Browse the full site">
    <a href="{{ '/projects/' | relative_url }}">research</a>
    <a href="{{ '/blog/' | relative_url }}">writing</a>
    <a href="{{ '/tools/' | relative_url }}">tools</a>
    <a href="{{ '/cv/' | relative_url }}">cv</a>
    <a href="{{ '/personal/' | relative_url }}">personal</a>
  </nav>
</div>
