---
layout: page
title: Ghostwriter for Anki
permalink: /ghostwriter-for-anki/
nav: false
published: true
images:
  slider: true
---

<swiper-container keyboard="true" navigation="true" pagination="true" pagination-clickable="true" pagination-dynamic-bullets="true" rewind="true">
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/ghostwriter/01-highlight-to-card.png" class="img-fluid rounded z-depth-1" caption="Highlight → card — the source travels with everything you write" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/ghostwriter/02-copilot-autocomplete.png" class="img-fluid rounded z-depth-1" caption="Copilot autocomplete — ghost-text suggestions while you type; Tab to accept" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/ghostwriter/03-copilot-model-visible.png" class="img-fluid rounded z-depth-1" caption="Transparent routing — the badge always shows which model wrote the suggestion" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/ghostwriter/04-side-panel.png" class="img-fluid rounded z-depth-1" caption="Side panel — draft cards alongside what you're reading" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/ghostwriter/05-your-ai-your-keys.png" class="img-fluid rounded z-depth-1" caption="100 included model requests — or bring your own provider" %}</swiper-slide>
</swiper-container>

---

**Ghostwriter for Anki** is a Chrome extension that helps you write Anki flashcards from the things you read online. The extension is built around a keyboard-driven workflow and an AI copilot that autocompletes the card _you're_ writing. It doesn't generate cards for you (because LLMs are bad at this!), it just helps you write cards faster.

Version 2 strips out some of the bloated features from v1 and focuses on making the app as good as it can be for the purpose that it was built: highlight → write → send to Anki, with automatic tagging, context, and source links on every card. I've included 100 free model requests per browser (I'm not trying to make money from this, hence no paid plan — after the free requests you can bring your own API key or run a local model).

<div class="d-flex flex-wrap gap-2 my-3">
  <a href="https://chromewebstore.google.com/detail/ghostwriter-for-anki/aldemiobejkammdkfgpfnmeppnegfaoc" class="btn btn-primary btn-sm z-depth-0">
    <i class="fa-brands fa-chrome"></i> Install from Chrome Web Store
  </a>
  <a href="https://github.com/djt97/ghostwriter-for-anki" class="btn btn-outline-primary btn-sm z-depth-0">
    <i class="fa-brands fa-github"></i> GitHub
  </a>
  <a href="https://github.com/djt97/ghostwriter-for-anki/blob/main/docs/SHORTCUTS.md" class="btn btn-outline-primary btn-sm z-depth-0">
    <i class="fa-solid fa-keyboard"></i> Keyboard shortcuts
  </a>
</div>

## Features

- **Copilot autocomplete** — "ghost-text" suggestions you can accept with the Tab key. You begin the card and the AI helps you write it faster. The copilot has built-in safeguards to prevent suggestions that aren't grounded in the source material.
- **Source-grounded cards** — highlight text on any website and the exact highlight, URL, and context (from page metadata) get sent to Anki with the card, so future-you knows where it came from.
- **Auto-tagging** — cards are tagged automatically based on the highlighted material and page metadata (yay!).
- **100 included model requests** — no account needed, no paid plans. After that, you can bring your own key (Gemini, OpenAI, OpenRouter, Claude, UltimateAI), run a local model (Ollama / LM Studio), or use Chrome's free on-device AI.
- **Markdown/MathJax** — write cards using markdown format and preview them on the spot, including LaTeX math rendering. Special care taken to ensure math cards get sent to Anki in the right format!

## Demo

<div style="position:relative;padding-bottom:56.25%;height:0;overflow:hidden;margin-bottom:1.5rem;">
  <iframe src="https://www.youtube.com/embed/nlLI6qsPC80"
          style="position:absolute;top:0;left:0;width:100%;height:100%;"
          frameborder="0" allowfullscreen></iframe>
</div>

## How it works

1. Highlight a passage of text.
2. Open Ghostwriter with your chosen shortcut as an overlay, side panel, or standalone tab. I use the overlay -- default shortcut is ⌥⇧F, I rebind to ⌘⇧F.
3. Start typing the card, use ⌘⇧X to autocomplete with the Copilot.
4. Tab to accept. Any other key to reject.
5. Add to Anki with ⌘⇧A (make sure Anki is open!)

Everything after this point is AI-generated.

<details>
<summary><strong>Setup</strong></summary>
<div markdown="1">

1. [Install from the Chrome Web Store](https://chromewebstore.google.com/detail/ghostwriter-for-anki/aldemiobejkammdkfgpfnmeppnegfaoc).
2. That's it for AI: 100 model requests are included per browser. To keep going after that, open **Options** and add your own API key (stored locally, sent only to your chosen provider), point it at a local model, or enable Chrome's on-device AI. Manual-only use needs no AI at all.
3. Choose a shortcut for opening the extension: go to `chrome://extensions/` → **Keyboard shortcuts** and set a key for "Open Ghostwriter for Anki Overlay".
4. Make sure Anki is open with AnkiConnect installed, then click "Refresh decks/types" inside Ghostwriter.

</div>
</details>

<details>
<summary><strong>Requirements</strong></summary>
<div markdown="1">

- Desktop **Anki** installed and running
- **AnkiConnect** add-on (ID `2055492159`): [install from AnkiWeb](https://ankiweb.net/shared/info/2055492159)

</div>
</details>

<details>
<summary><strong>Privacy</strong></summary>
<div markdown="1">

- No account required.
- You control the model: your own key, a local model, Chrome's on-device AI, or the included hosted allowance — a visible badge always shows which one wrote a suggestion.
- When you use AI features, only the text needed for the suggestion is sent to the model you chose. The included hosted tier stores usage counters, never raw IP addresses.
- See the [full privacy policy](https://github.com/djt97/ghostwriter-for-anki/blob/main/PRIVACY_POLICY.md).

</div>
</details>

---

Feedback and issues welcome on [GitHub](https://github.com/djt97/ghostwriter-for-anki/issues).
