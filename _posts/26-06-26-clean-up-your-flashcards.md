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

```
Front: What was agriculture's share of U.S. GDP in 1900 versus today?
Back: 1900: 15%, Today: <1%
```

```
Front: When is total boundedness equivalent to precompactness?
Back: In a complete metric space.
```

Or, my personal favourite:

```
Front: What does Hulten's Theorem say intuitively?
Back: If we want to look at shocks to output we can instead look at the effects on production.
```

The first card has me cold-recalling two statistics, and one of them isn’t even precise: “<1%”.

The second has a vague cue. “When” is far too broad—a better question would be “Total boundedness is equivalent to precompactness in […] metric spaces.” Or even, “In what kind of metric spaces is total boundedness equivalent to precompactness?” Or perhaps even: “Suppose *(M, d)* is totally bounded. What condition guarantees that *M* is precompact?” (I like this one!).

The final card is particularly insidious because on the surface it looks like a perfectly reasonable question and answer. Unfortunately, there is no one answer to “what X says intuitively”. The fix is to either divide this into several more specific cards, or if it was important for me to remember the back exactly as written, to convert the card to something like: “(Hulten’s Theorem) If we want to look at shocks to output, we can instead…”

## Finding your bad cards

Anyway, when you’re writing cards regularly, you’re bound to write the occasional dud, and you won’t realize it’s a dud until you start reviewing! Your review data is the best indicator of your cards that need rewriting.

But rewriting cards is such a pain! Anki’s interface for editing cards in bulk is terrible.<d-footnote>All due respect to the amazing people who maintain Anki and keep it open source — it’s just not built for bulk-editing cards.</d-footnote> Moreover, Anki doesn’t surface the metrics one would want for working out which cards are the “real” leeches. I say “real” because Anki has its own definition of what a leech is. By default, a leech is a card that you have forgotten the answer to 8 or more times. This is a decent metric, but it won’t surface cards as being bad until you’ve already wasted a considerable amount of time trying to remember them. It also misses some things.

For example, a card you’ve seen 10 times and failed 5 won’t show up as a leech (50% retention), while a card that you’ve seen 80 times and failed 8 (90% retention) will. The card with 50% is an obvious candidate for rewriting. I use a custom metric to score troubling cards. This metric combines four things: (1) how often you fail a card, (2) how far its ease has dropped, (3) how long you labour over it each time it appears, and (4) whether it’s a card you ought to have learned but keep forgetting. For those interested, I've included the exact metric at the end of this post.

## A skill to clean up your flashcards

Fortunately, while Claude Code / ChatGPT’s Codex are not particularly gifted at *writing* cards, they are great at analyzing cards, and they have a much nicer UI than Anki! They also offer the added convenience of being able to help you fill in the blanks on cards that you’re forgetting because you don’t have enough information (i.e. you need to write supporting cards for details you’re sketchy on).

<p style="text-align: center;">
  <img src="/assets/img/clean-up-your-flashcards.gif" alt="The Jordan Peterson 'clean up your room' meme, edited so 'room' is crossed out and 'flashcards' is scrawled above it." style="max-width: 480px; width: 100%; height: auto; border-radius: 8px;">
</p>

I’ve been using Claude Code to talk to my flashcards for a while. In an email to [Nate Meyvis](https://www.natemeyvis.com/) (the developer of [Zippyflash](https://zippyflash.com/user-guide)) back in April, I wrote:

> If you're not using Claude Code to talk to Anki via Ankiconnect, you're missing out. :)

I stand by it.

So I put together a skill to make it easier for YOU to talk to your flashcards with an LLM. The most important thing about the skill is that it keeps you in control of your cards: you decide what gets rewritten, what gets split up, what gets filled out, and what gets deleted. The LLM is under strict instructions not to do anything to your flashcards without explicit approval! Here’s how it works:

1. Install it by opening Claude Code (or Codex) and typing: *“Install this skill: https://github.com/djt97/anki-skill”*.
2. Open Anki and make sure you have [AnkiConnect](https://ankiweb.net/shared/info/2055492159) installed.
3. Open a new chat window and type `/anki` (in Claude Code) or `$anki` (in Codex).
4. The LLM will run a “health check” on your flashcards.
    a. As part of this, it will identify what conventions you use (I add “pink flags” to cards I see that I want to edit).
    b. It will also ask you about your preferences for fixing cards that you’re struggling to remember.
5. Then you work collaboratively to fix those pesky cards that have been causing you problems!

Below is a short video of me using the skill for the first time in Claude Code.

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.15); margin: 1rem 0;">
  <iframe src="https://www.youtube.com/embed/mwqNtWM56ZQ" title="Cleaning up your Anki deck with Claude Code" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0;"></iframe>
</div>

## The metric

For those interested, the formula for the trouble metric is:

$$
\text{trouble} = 0.35\,(\text{lapse rate}) + 0.25\,(\text{ease drop}) + 0.20\,(\text{relative time}) + 0.20\,(\text{mature failure})
$$

where:

- *lapse rate* = fails ÷ reviews;
- *ease drop* = how far the card’s ease has fallen below default;<d-footnote>“Ease” is only available if your scheduling algorithm is SM-2, which was the default algorithm in Anki before FSRS. If you’ve switched to FSRS (as most people now have), your cards don’t really have an ease factor, so the other three terms are all that matter.</d-footnote>
- *relative time* = your average time on it vs a typical card;
- *mature failure* = 1 if the card has a long interval yet you still fail it, else 0.

I hope someone finds this useful!

DJ
