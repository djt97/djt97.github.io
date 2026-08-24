---
layout: page
title: Gloss
permalink: /gloss/
nav: false
published: true
images:
  slider: true
---

<swiper-container keyboard="true" navigation="true" pagination="true" pagination-clickable="true" pagination-dynamic-bullets="true" rewind="true">
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/gloss/hero.png" class="img-fluid rounded z-depth-1" caption="Annotate as you read — highlight a passage, attach a note" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/gloss/reader.png" class="img-fluid rounded z-depth-1" caption="Reader — inline and display LaTeX, with an outline rail" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/gloss/export.png" class="img-fluid rounded z-depth-1" caption="Export — a structured packet, framed for your LLM" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/gloss/library.png" class="img-fluid rounded z-depth-1" caption="Library — your documents, stored locally" %}</swiper-slide>
</swiper-container>

---

**Gloss** is a desktop reader for annotating documents — lecture materials, research papers, LLM outputs, etc. — and exporting your highlights and notes as a single structured packet you can hand to an LLM.

When you want ChatGPT / Claude to revise or explain _several specific parts_ of the output, the UI only allows you to directly reply to one selected piece of text at a time. More generally, if you're using Claude Code / Codex or similar, you have to type out all your questions / requests in the chat box, rather than being able to annotate the model's output directly.

Gloss is built to fix this: open a markdown, LaTeX, or PDF file, highlight the passages you care about, attach a note (or dictate one by voice), and export everything---your highlights, their surrounding context, and your questions---as one block of markdown text. Paste it into Claude Code, Codex, or your favourite LLM, and the model will respond to each item in order. If you use Claude Code / Codex, you can easily get it to update the relevant document in-place to address your annotations.

<div class="d-flex flex-wrap gap-2 my-3">
  <a href="https://github.com/djt97/Gloss/releases" class="btn btn-primary btn-sm z-depth-0">
    <i class="fa-brands fa-apple"></i> Download for Mac
  </a>
  <a href="https://github.com/djt97/Gloss/releases" class="btn btn-outline-primary btn-sm z-depth-0">
    <i class="fa-brands fa-android"></i> Download APK
  </a>
  <a href="https://github.com/djt97/Gloss" class="btn btn-outline-primary btn-sm z-depth-0">
    <i class="fa-brands fa-github"></i> GitHub
  </a>
</div>

Everything after this point is AI-generated.

## Features

- **Annotate as you read** — select any passage and type or dictate a note. Highlights stick to the text, even across inline math.
- **Built for real papers** — renders inline and display LaTeX; imports markdown, `.tex` (via pandoc), and PDFs (via Mathpix).
- **Export a structured packet** — your annotations plus surrounding context, framed for the model. Use the default instruction or write your own, and choose how much context to include.
- **Dictation-friendly** — your keystrokes go straight into the note, so any dictation tool (Wispr Flow, macOS Dictation) lets you speak an annotation instead of typing it.
- **Local-first and private** — no accounts, no telemetry, no network calls except a PDF conversion you trigger yourself.
- **Android companion** — read and annotate markdown on the go.

<!--
## Demo
Drop the demo video in here once it's recorded (same pattern as the ghostwriter page):
<div style="position:relative;padding-bottom:56.25%;height:0;overflow:hidden;margin-bottom:1.5rem;">
  <iframe src="https://www.youtube.com/embed/VIDEO_ID"
          style="position:absolute;top:0;left:0;width:100%;height:100%;"
          frameborder="0" allowfullscreen></iframe>
</div>
-->

## How it works

1. **Import** a markdown, LaTeX, or PDF file — or paste text.
2. **Annotate** the parts you want to ask about.
3. **Export** the packet and paste it into your LLM.

<details>
<summary><strong>Install</strong></summary>
<div markdown="1">

- **macOS** — download the `.dmg` from [Releases](https://github.com/djt97/Gloss/releases), drag `Gloss.app` to Applications, and open it. The build is unsigned, so on first launch use **right-click → Open**. Apple-silicon Macs only.
- **Android** — a markdown-only companion, distributed as a debug APK for now. Install with `adb install -r Gloss-android-debug.apk`.
- Or [build from source](https://github.com/djt97/Gloss#building-from-source) (JDK 17 + Gradle).

</div>
</details>

<details>
<summary><strong>Optional helper tools (desktop)</strong></summary>
<div markdown="1">

Markdown and plain text work with no setup. To import other formats:

- `.tex` — install [pandoc](https://pandoc.org) (`brew install pandoc`), runs locally.
- `.pdf` — install the Mathpix `mpx` CLI, or paste a Mathpix API key in Preferences. PDF OCR uploads the file to Mathpix; nothing else leaves your machine.

</div>
</details>

<details>
<summary><strong>Privacy</strong></summary>
<div markdown="1">

- Everything stays local by default — documents and annotations live in a local database.
- No analytics, no telemetry, no background network calls.
- The only network call is PDF conversion via Mathpix, and only when you actively import a PDF on desktop.
- See the [full privacy note](https://github.com/djt97/Gloss/blob/master/PRIVACY.md).

</div>
</details>

---

Open source under the MIT license. Feedback and issues welcome on [GitHub](https://github.com/djt97/Gloss/issues).
