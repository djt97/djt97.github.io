---
layout: distill
title: Cleaning up your Anki deck with Claude Code
date: 2026-06-29 09:00:00+1100
description: A skill that finds your worst Anki cards and helps you fix them.
giscus_comments: true
tags: [tools, anki, AI, spaced-repetition, memory, flashcards]
categories: [tools]
toc:
  - name: My terrible cards
  - name: Finding your bad cards
  - name: A skill to clean up your flashcards
  - name: The metric
related_posts: false
published: true
---

<script>
MathJax = {
  tex: {
    inlineMath: [['$', '$']],
    displayMath: [['$$', '$$'], ['\\[', '\\]']]
  }
};
</script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

This month I officially crossed two years on my Anki streak. 🎉

Not to brag, but (to brag) that makes me 77th out of about 20,000 people who use the Anki leaderboard. You know, if you care about that sort of thing (which I obviously don’t).<d-footnote>Methinks the lady doth protest too much.</d-footnote>

{% include figure.liquid path="assets/img/anki-leaderboard.png" class="img-fluid rounded z-depth-1" alt="My Anki leaderboard row: rank 77 (A+), a 2-year (751-day) streak, ~102 reviews per day, 88% retention." %}

So it’s safe to say Anki is a part of my life now. We’ll stay together until we die. Um, until I die. Or maybe superintelligence takes over and puts all the open-source software behind a paywall I can’t afford (that’s my version of an AI-dystopian nightmare).

## My terrible cards

Unfortunately over the years I have created many terrible cards. Like, really terrible. Here’s a sample:

> Front: What was agriculture's share of U.S. GDP in 1900 versus today?
>
> Back: 1900: 15%, Today: <1%

> Front: When is total boundedness equivalent to precompactness?
>
> Back: In a complete metric space.

Or, my personal favourite:

> Front: What does Hulten's Theorem say intuitively?
>
> Back: If we want to look at shocks to output we can instead look at the effects on production.

The first card has me cold-recalling two statistics, and one of them isn’t even precise: “<1%”.

The second has a vague cue. “When” is far too broad—a better question would be “Total boundedness is equivalent to precompactness in […] metric spaces.” Or even, “In what kind of metric spaces is total boundedness equivalent to precompactness?” Or perhaps even: “Suppose *(M, d)* is totally bounded. What condition guarantees that *M* is precompact?” (I like this one!).

The final card is particularly insidious because on the surface it looks like a perfectly reasonable question and answer. Unfortunately, there is no one answer to “what X says intuitively”. The fix is to either divide this into several more specific cards, or if it was important for me to remember the back exactly as written, to convert the card to something like: “(Hulten’s Theorem) If we want to look at shocks to output, we can instead…”

## Finding your bad cards

Anyway, when you’re writing cards regularly, you’re bound to write the occasional dud, and you won’t realize it’s a dud until you start reviewing! Your review data is the best indicator of your cards that need rewriting.

But rewriting cards is such a pain! Anki’s interface for editing cards in bulk is terrible.<d-footnote>All due respect to the amazing people who maintain Anki and keep it open source — it’s just not built for bulk-editing cards.</d-footnote>

Most people are familiar with the “leech” tag that Anki adds to cards you’ve failed 8 or more times. But Anki actually computes far more useful metrics than that. For example, if you open the card browser, right click on a column and enable the “retrievability” column, you can sort cards by how likely you are to recall them. When FSRS chooses how long to wait before it surfaces a card again, it combines retrievability with a difficulty and stability metric for the card.

I use the interval to rank cards by a simple cost: how often a card fails you, divided by how long Anki plans to wait before surfacing it again. The worst cards are not just the ones you keep getting wrong, they’re the ones you keep seeing over and over again. For those interested, I've included the exact metric at the end of this post.

## A skill to clean up your flashcards

Fortunately, while Claude Code / ChatGPT’s Codex are not particularly gifted at *writing* cards (see the “[memory machines](https://memory-machines.com/report)” report by [Ozzie Kirkby](https://kirkbyo.com/) and [Andy Matuschak](https://andymatuschak.org/)),<d-footnote>The skill uses the framework outlined in this report to "score" cards. Even good LLMs do not categorize the cards perfectly, but the framework is useful.</d-footnote> they are great at analyzing cards, and they have a much nicer UI than Anki!

<p style="text-align: center;">
  <img src="/assets/img/clean-up-your-flashcards.gif" alt="The Jordan Peterson 'clean up your room' meme, edited so 'room' is crossed out and 'flashcards' is scrawled above it." style="max-width: 480px; width: 100%; height: auto; border-radius: 8px;">
</p>

I’ve been using Claude Code to talk to my flashcards for a while. In an email to [Nate Meyvis](https://www.natemeyvis.com/) (the developer of [Zippyflash](https://zippyflash.com/user-guide)) back in April, I wrote:

> If you're not using Claude Code to talk to Anki via Ankiconnect, you're missing out. :)

I stand by it.

I’m not the first person to point an LLM at Anki---there are a few skills out there already, and even a full [Anki MCP server](https://www.ankimcp.com/). But almost all of them are built around *generating* cards, which is the one thing [LLMs are reliably bad at](https://memory-machines.com/). I wanted a skill for *fixing* the cards that you (or your review data) already know are bad.

So I put together a skill<d-footnote>Although this post was written entirely by me, the skill itself wasn't---it was written by Claude Opus 4.8 + ChatGPT Pro with my prompting. I've tested it and am confident that it can be used for its intended purpose, but as with any AI-written tool you should expect the occasional mistake.</d-footnote> to make it easier for YOU to talk to your flashcards with an LLM. The most important thing about the skill is that it keeps you in control of your cards: you decide what gets rewritten, what gets split up, what gets filled out, and what gets deleted. The LLM is under strict instructions not to do anything to your flashcards without explicit approval! Here’s how it works:

1. Install it by opening Claude Code (or Codex) and typing: *“Install this skill: https://github.com/djt97/anki-skill”*.
2. Open Anki and make sure you have [AnkiConnect](https://ankiweb.net/shared/info/2055492159) installed.
3. Open a new chat window and type `/anki` (in Claude Code) or `$anki` (in Codex).
4. The LLM will run a “health check” on your flashcards.
   <ol type="a">
     <li>As part of this, it will identify what conventions you use (I add “pink flags” to cards I see that I want to edit).</li>
     <li>It will also ask you about your preferences for fixing cards that you’re struggling to remember.</li>
   </ol>
5. Then you work collaboratively to fix those pesky cards that have been causing you problems!

Below is a short video of me using the skill for the first time in Claude Code.

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.15); margin: 1rem 0;">
  <iframe src="https://www.youtube.com/embed/mwqNtWM56ZQ" title="Cleaning up your Anki deck with Claude Code" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0;"></iframe>
</div>

## The metric

For those interested, the cost of a card is:<d-footnote>I was concerned that lapse rate and 1/interval would be collinear because “the cards you fail” are going to be exactly “the cards you see most often”. It turns out they capture different things: across my own collection their correlation is only about 0.1, because a card’s interval is driven mostly by how long it's been in your collection for, whereas its lapse rate is how often you’ve failed it over its whole history.</d-footnote>

$$\text{cost} = \frac{\text{lapse rate}}{\text{interval}}\qquad\text{where lapse rate}=\frac{\text{lapses}}{\text{reviews}}$$

I had initially played with more sophisticated metrics combining different statistics that Anki records, until I realized that the interval given by the FSRS algorithm already bakes in how hard it thinks a card is for you (and this is optimized for your own review data).<d-footnote>Anki’s FSRS scheduler estimates each card’s difficulty, stability, and retrievability, and you can sort by them in the card Browser (though I maintain that editing them in Anki is a pain). AnkiConnect unfortunately doesn’t expose those numbers, so the skill uses what it can get: lapses, reviews, and the interval set by FSRS.</d-footnote> Of course, if you manually flag the cards you think are troubling (as I do), the exact details of the metric are less relevant to you. Moreover, there may even be cards you tend to get right, but feel you don’t understand. The FSRS parameters are not going to pick up on those cards, even though you want to edit them, hence why I manually flag.

I hope someone finds this useful!

DJ
