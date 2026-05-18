---
layout: page
title: personal
permalink: /personal/
description: music, coffee, and family
nav: true
nav_order: 7
published: true
body_class: personal-layout
images:
  slider: true
---

<div class="personal-page">
  <section class="personal-hero">
    <div>
      <p class="personal-kicker">Outside academia</p>
      <h2>Music, coffee, and family.</h2>
    </div>
    <p>
      This is the small, non-CV corner of the site: a few things I care about outside research, plus some family photos that make the place feel
      less like an academic filing cabinet.
    </p>
  </section>

  <section class="personal-music">
    <div>
      <p class="personal-kicker">Music</p>
      <h2>A few of my favourite artists.</h2>
    </div>
    <div class="personal-chips">
      <a class="personal-chip" href="https://open.spotify.com/artist/0QWrMNukfcVOmgEU0FEDyD" target="_blank" rel="noopener">Jacob Collier</a>
      <a class="personal-chip" href="https://open.spotify.com/artist/0G7KI9I5BApiXc5Sqpyil9" target="_blank" rel="noopener">Melt</a>
      <a class="personal-chip" href="https://open.spotify.com/artist/1GmsPCcpKgF9OhlNXjOsbS" target="_blank" rel="noopener">Lizzy McAlpine</a>
      <a class="personal-chip" href="https://open.spotify.com/artist/3nYyLjhw4mYzYfJePsCJYJ" target="_blank" rel="noopener">Couch</a>
      <a class="personal-chip" href="https://open.spotify.com/artist/7ENzCHnmJUr20nUjoZ0zZ1" target="_blank" rel="noopener">Snarky Puppy</a>
      <a class="personal-chip" href="https://open.spotify.com/artist/3mIj9lX2MWuHmhNCA7LSCW" target="_blank" rel="noopener">The 1975</a>
      <a class="personal-chip" href="https://open.spotify.com/artist/0nnYdIpahs41QiZ9MWp5Wx" target="_blank" rel="noopener">Holly Humberstone</a>
      <a class="personal-chip" href="https://open.spotify.com/artist/6VuMaDnrHyPL1p4EHjYLi7" target="_blank" rel="noopener">Charlie Puth</a>
    </div>
  </section>

  <section class="personal-coffee">
    <div>
      <p class="personal-kicker">Coffee</p>
      <h2>Currently brewing.</h2>
      <p>
        <a href="https://limebluecoffee.com/collections/fresh-coffee/products/500g-4kg-brazil-sao-paulo-single-origin-1" target="_blank" rel="noopener">Brazil São Paulo Single Origin</a> from Lime Blue Coffee.
      </p>
    </div>
  </section>

  <section class="personal-bloom">
    <div>
      <p class="personal-kicker">Bloom Paediatric Studio</p>
      <h2>A clinic my wife and I run in Sydney.</h2>
      <p>
        Bloom is a paediatric occupational therapy clinic for children and families. Supported Children Bloom.
      </p>
    </div>
    <a class="personal-link" href="https://www.bloom-ps.com.au/" target="_blank" rel="noopener">
      Visit Bloom <i class="fa-solid fa-arrow-right"></i>
    </a>
  </section>

  <section class="personal-gallery">
    <div class="personal-gallery-head">
      <p class="personal-kicker">Family photos</p>
      <h2>A few photos of my family.</h2>
    </div>

    <swiper-container
      class="personal-carousel"
      keyboard="true"
      navigation="true"
      pagination="true"
      pagination-clickable="true"
      pagination-dynamic-bullets="true"
      rewind="true"
    >
      <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/family_photos/DSCN0452.JPG" class="personal-carousel-img" alt="DJ Thornton family photo" %}</swiper-slide>
      <swiper-slide>{% include figure.liquid loading="lazy" path="assets/img/family_photos/DSCN0466.JPG" class="personal-carousel-img" alt="DJ Thornton family photo" %}</swiper-slide>
      <swiper-slide>{% include figure.liquid loading="lazy" path="assets/img/family_photos/DSCN0510.JPG" class="personal-carousel-img" alt="DJ Thornton family photo" %}</swiper-slide>
      <swiper-slide>{% include figure.liquid loading="lazy" path="assets/img/family_photos/DSCN0522.JPG" class="personal-carousel-img" alt="DJ Thornton family photo" %}</swiper-slide>
      <swiper-slide>{% include figure.liquid loading="lazy" path="assets/img/family_photos/DSCN0571.JPG" class="personal-carousel-img" alt="DJ Thornton family photo" %}</swiper-slide>
    </swiper-container>

  </section>
</div>
