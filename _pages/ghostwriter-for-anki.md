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
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/ghostwriter/01-copilot.png" class="img-fluid rounded z-depth-1" caption="AI Copilot — ghost-text suggestions while you type" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/ghostwriter/02-triage.png" class="img-fluid rounded z-depth-1" caption="Triage — review AI-generated cards before they hit your deck" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/ghostwriter/03-side-panel.png" class="img-fluid rounded z-depth-1" caption="Side panel — draft cards alongside what you're reading" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/ghostwriter/04-options.png" class="img-fluid rounded z-depth-1" caption="Options — choose your AI provider, keys stay local" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/ghostwriter/05-graph.png" class="img-fluid rounded z-depth-1" caption="Knowledge graph — explore your collection visually" %}</swiper-slide>
</swiper-container>

---

**Ghostwriter for Anki** is a Chrome extension that helps you quickly create Anki flashcards from the things you read online. It pairs a keyboard-driven card editor with an AI Copilot, a triage workflow for reviewing cards before they're sent, and one-click export to Anki via AnkiConnect.

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

- **AI Copilot** — ghost-text suggestions you accept with Tab
- **Smart generation** — highlight text on any page and generate cards from it
- **Triage queue** — review AI-generated cards (Accept / Reject / Next) before anything touches your deck
- **Outbox + undo** — accepted cards sit in an outbox; edit or undo the last batch
- **Markdown/MathJax** — write card content in markdown with live preview, including LaTeX math rendering
- **Bulk generation** — use [FlashcardGPT](https://chatgpt.com/g/g-690faa9681448191b2700ca01abdeca6-flashcardgpt) or [Gemini Gem](https://gemini.google.com/gem/1E1OquFI0cH_ohhvADJQ61qKYdjJ55Jcq) to generate in bulk, then import with `J`
- **Multiple AI providers** — bring your own key (Google Gemini, OpenAI, or UltimateAI). Keys stay local.
- **Knowledge graph** — explore your collection visually

## Demo

<div style="position:relative;padding-bottom:56.25%;height:0;overflow:hidden;margin-bottom:1.5rem;">
  <iframe src="https://www.youtube.com/embed/ucI45rKTztI"
          style="position:absolute;top:0;left:0;width:100%;height:100%;"
          frameborder="0" allowfullscreen></iframe>
</div>

## How it works

1. Open Ghostwriter with your chosen shortcut — as an overlay, side panel, or standalone tab.
2. Draft cards manually or generate from selected text on any page.
3. Review in **Triage** mode — accept, reject, or edit.
4. Send from your **Outbox** to Anki via AnkiConnect.

<details>
<summary><strong>Setup</strong></summary>
<div markdown="1">

1. [Install from the Chrome Web Store](https://chromewebstore.google.com/detail/ghostwriter-for-anki/aldemiobejkammdkfgpfnmeppnegfaoc).
2. Open the extension **Options** and choose an AI provider (or leave AI features off for manual-only use).
3. Paste your API key — it's stored locally in your browser, never sent anywhere except your chosen provider.
4. Choose a shortcut for opening the extension: go to `chrome://extensions/` → **Keyboard shortcuts** and set a key for "Open Ghostwriter for Anki Overlay".
5. Make sure Anki is open with AnkiConnect installed, then click "Refresh decks/types" inside Ghostwriter.

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
- You control the AI provider and API key.
- When you use AI features, only the text needed to generate suggestions is sent to your chosen provider.
- See the [full privacy policy](https://github.com/djt97/ghostwriter-for-anki/blob/main/PRIVACY_POLICY.md).

</div>
</details>

---

Feedback and issues welcome on [GitHub](https://github.com/djt97/ghostwriter-for-anki/issues).
