---
layout: distill
title: Talk to Your Flashcards with Claude Code
date: 2026-03-01 09:00:00+1100
description: An Anki skill for Claude Code that lets you search, triage, and rewrite your cards from the terminal.
giscus_comments: true
tags: [tools, anki, ai, spaced-repetition]
categories: [tools]
toc:
  - name: Introduction
  - name: What the Skill Does
  - name: Getting Started
  - name: The Triage Workflow
  - name: Get the Skill
related_posts: false
published: false
---

## Introduction

If you've read my [earlier post](/blog/2025/memorize-first-understand-later/) on memory practice, you know I take flashcards seriously. I use Anki daily, and over the past year my collection has grown to several thousand cards. That's mostly a good thing — but it also means maintenance becomes a real task. Suspended cards pile up. Leeches accumulate. Poorly-worded questions linger until you finally get annoyed enough to fix them.

I've been using [Claude Code](https://docs.anthropic.com/en/docs/claude-code) — Anthropic's CLI for Claude — as my primary coding tool for a few months now. One of its lesser-known features is **skills**: reusable instruction files that teach Claude how to do specific things. I wrote a skill that connects Claude to my local Anki collection via the [AnkiConnect](https://ankiweb.net/shared/info/2055492159) add-on, and it has become one of the most useful things in my workflow.

<!-- TODO: embed demo video here -->

---

## What the Skill Does

With the skill loaded, you can talk to your Anki collection in natural language:

| Task          | What you type                                                  |
| ------------- | -------------------------------------------------------------- |
| **Search**    | `/anki find all cards tagged "leech"`                          |
| **Review**    | `/anki show me my 10 most-lapsed cards`                        |
| **Rewrite**   | `/anki that question is vague — rewrite it`                    |
| **Triage**    | `/anki walk me through my suspended cards`                     |
| **Bulk edit** | `/anki add the tag "reviewed" to all cards in my Biology deck` |
| **Stats**     | `/anki give me a breakdown of my collection`                   |
| **Delete**    | `/anki delete the duplicates we just found`                    |

Under the hood, the skill teaches Claude how to call the AnkiConnect API, what response shapes to expect, and how to handle the gotchas that trip everyone up (the card ID vs. note ID distinction being the main offender). It also includes flashcard writing principles — so when Claude rewrites a card, it follows good SRS practice: atomic questions, no yes/no answers, no vague "explain..." prompts, and proper use of the Context field for disambiguation.

---

## Getting Started

### 1. Install AnkiConnect

In Anki: **Tools > Add-ons > Get Add-ons...** &rarr; enter code `2055492159` &rarr; restart Anki.

### 2. Install Claude Code

Follow the [official instructions](https://docs.anthropic.com/en/docs/claude-code) if you haven't already.

### 3. Add the skill

Save the skill file (provided below) to:

```
~/.claude/skills/anki/SKILL.md
```

### 4. Use it

With Anki running, open Claude Code and type:

```
/anki show me my suspended cards
```

Claude connects to your local Anki instance and starts working with your cards.

---

## The Triage Workflow

The most valuable thing I use the skill for is triaging problematic cards. Here's what a typical session looks like.

I ask Claude to triage my suspended cards:

```
> /anki triage my suspended cards
```

Claude surveys the collection, groups the cards by deck and note type, and presents them in batches. For each card it shows the question, answer, tags, and lapse count, then recommends one of:

- **Unsuspend** — card is fine, return to rotation
- **Rewrite + unsuspend** — poorly worded; Claude improves it, then returns it
- **Delete** — redundant, trivial, or unfixable
- **Keep suspended** — not ready to decide

I review Claude's suggestions, approve or override, and it executes the changes. A session that used to take me an hour of manual editing in the Anki browser is done in ten minutes. The rewrite quality is genuinely good — Claude follows the flashcard principles baked into the skill, so the cards that come back are tighter and more precise than what I wrote the first time around.

---

## Get the Skill

Copy the skill file below and save it to `~/.claude/skills/anki/SKILL.md`. Claude Code will pick it up automatically the next time you start a session.

<details>
<summary><strong>Click to expand the full skill file</strong></summary>

<div markdown="1">

```markdown
---
name: anki
description: Talk to your Anki flashcards with Claude Code. Search, review, edit, rewrite, and triage cards via AnkiConnect. Use when the user asks anything about their Anki collection — searching cards, editing content, managing suspension, tagging, deleting, or getting stats.
user_invocable: true
---

# Anki Skill for Claude Code

> **Talk to your flashcards.** Search, review, rewrite, and triage your Anki cards using natural language — all from the terminal.

This is a [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skill that connects to [Anki](https://apps.ankiweb.net/) via the [AnkiConnect](https://ankiweb.net/shared/info/2055492159) add-on. Drop it into your skills folder and you can ask Claude to work with your flashcards directly.

## Setup

### 1. Install AnkiConnect

In Anki: **Tools > Add-ons > Get Add-ons...** > enter code `2055492159` > restart Anki.

### 2. Install this skill

Save this file to:

    ~/.claude/skills/anki/SKILL.md

### 3. Use it

With Anki running, ask Claude Code anything about your cards:

    /anki show me my suspended cards
    /anki how many cards do I have in each deck?
    /anki find cards about mitochondria and show me the worst ones
    /anki rewrite this card to use better cloze deletions
    /anki triage my leech cards

---

## What You Can Do

| Task          | Example prompt                                                 |
| ------------- | -------------------------------------------------------------- |
| **Search**    | `/anki find all cards tagged "leech"`                          |
| **Review**    | `/anki show me my 10 most-lapsed cards`                        |
| **Rewrite**   | `/anki that question is vague — rewrite it`                    |
| **Triage**    | `/anki walk me through my suspended cards`                     |
| **Bulk edit** | `/anki add the tag "reviewed" to all cards in my Biology deck` |
| **Stats**     | `/anki give me a breakdown of my collection`                   |
| **Delete**    | `/anki delete the duplicates we just found`                    |
| **Unsuspend** | `/anki unsuspend the cards we just rewrote`                    |

---

## How It Works

Everything below is what Claude sees when the skill loads. It tells Claude how to call the AnkiConnect API, what response shapes to expect, and how to handle common gotchas.

---

## Prerequisites

- Anki must be running with AnkiConnect installed (add-on code: `2055492159`).
- Verify connectivity before any operation:

  curl -s localhost:8765 -X POST -d '{"action":"version","version":6}'

If this fails, tell the user: "Anki doesn't seem to be running, or AnkiConnect isn't installed. Please open Anki and try again."

## Core API Pattern

All AnkiConnect calls follow the same shape. Always use this Python helper:

    import json, urllib.request

    def anki(action, **params):
        req = json.dumps({'action': action, 'version': 6, 'params': params}).encode()
        resp = json.loads(urllib.request.urlopen(
            urllib.request.Request('http://localhost:8765', req)
        ).read())
        if resp['error']:
            raise Exception(resp['error'])
        return resp['result']

Define this at the top of every Python script that talks to Anki.

---

## Flashcard Writing Principles

**You MUST follow these rules when creating or rewriting cards.** These are non-negotiable.

### Core Principles

1. **Atomicity** — One card = one fact. If the back contains two facts, split into two cards. Don't add unnecessary detail to the back.
2. **Univocality** — Every front must admit exactly one correct answer. If a tired learner at 11pm could plausibly give two correct-but-different answers, **rewrite the front** to narrow the answer space (add scope, units, timeframe, or context) — without giving away the answer.
3. **Multiple angles without redundancy** — Present information from different angles (forward/reverse, rule/example, definition/application), but never duplicate the same card. Purposeful variants are good; copies are not.

### Card Writing Rules

1. **Always use Basic type** (Front/Back). No cloze deletions.
2. **No yes/no answers.** Rephrase to ask for the fact directly.
3. **Lists must be split.** If the answer is a list of items, make a separate card for each item. Never write "Name 3 things..." as a single card.
4. **Acronyms get their own card.** If an answer uses an acronym, create a separate card asking what it stands for.
5. **Avoid vague prompts.** Never use "What is X?", "Explain...", "Discuss...", or "Describe...". Prefer **What/Which/When/Where/Define** with enough constraint to pin down a unique answer.
6. **Avoid "advantages/benefits/reasons"** unless constrained to one canonical answer (e.g., "primary mechanism", "statutory threshold").
7. **Back phrasing test:** If the back has more than ~15 words, ask: can this be split into two cards? If not, is there a shorter phrasing?
8. **Use the Context field** for brief disambiguation cues (e.g., "WWII" or "measure theory") — without giving away the answer.

### Examples

**Bad:** "What is an advantage of cloud computing?"
**Better:** "Which pricing model shifts CapEx to OpEx?" → "Pay-as-you-go."

**Bad:** "Explain how L2 regularization reduces overfitting."
**Better:** "What is the mechanism by which L2 reduces overfitting?" → "It shrinks the weights, which lowers variance."

**Bad:** "Threshold for severe anemia?"
**Better:** "What is the severe anemia threshold (g/dL) for adult non-pregnant females?" → "<8 g/dL."

---

## Discovering the User's Collection

Before working with cards, explore what the user has. Run this on first use or when asked for stats:

    # Decks
    print('Decks:', anki('deckNames'))

    # Note types (models)
    print('Note types:', anki('modelNames'))

    # Fields for each note type
    for model in anki('modelNames'):
        fields = anki('modelFieldNames', modelName=model)
        print(f'  {model}: {fields}')

    # Card counts by state
    for q in ['is:suspended', 'is:new', 'is:due', 'is:learn', 'is:review']:
        print(f'  {q}: {len(anki("findCards", query=q))}')

    print(f'  Total: {len(anki("findCards", query="*"))}')

This tells you the deck structure, what fields exist on each note type, and the overall health of the collection. Use this information to tailor your responses — don't assume field names.

---

## Operations Reference

### 1. Search for Cards

Use `findCards` with Anki's search syntax:

    # By state
    anki('findCards', query='is:suspended')
    anki('findCards', query='is:new')
    anki('findCards', query='is:due')

    # By tag
    anki('findCards', query='tag:leech')
    anki('findCards', query='-tag:marked')        # NOT tagged

    # By deck (quote names with spaces)
    anki('findCards', query='deck:"My Deck"')

    # By note type
    anki('findCards', query='"note:Basic (and reversed card)"')

    # Full-text search
    anki('findCards', query='"mitochondria"')

    # By review history
    anki('findCards', query='added:7')             # added in last 7 days
    anki('findCards', query='rated:3')             # reviewed in last 3 days
    anki('findCards', query='prop:lapses>=5')      # 5+ lapses (leeches)
    anki('findCards', query='prop:ivl<7')          # interval under 7 days

    # Combine freely
    anki('findCards', query='is:suspended tag:leech deck:"Biology"')

### 2. Read Card Content

**Critical:** `cardsInfo` returns card-level data where the `note` field is an **integer** (the note ID), not a nested object. To get tags, you must make a separate `notesInfo` call.

    card_ids = anki('findCards', query='is:suspended')
    cards = anki('cardsInfo', cards=card_ids)

    # Display fields
    import re
    def strip_html(s):
        return re.sub(r'<[^>]+>', '', s).strip()

    for c in cards:
        print(f"Card {c['cardId']} | {c['modelName']} | {c['deckName']}")
        for fname, fdata in c['fields'].items():
            val = strip_html(fdata['value'])
            if val:
                print(f"  {fname}: {val[:200]}")

    # Get tags (separate call!)
    note_ids = list(set(c['note'] for c in cards))
    notes = anki('notesInfo', notes=note_ids)
    tags_by_note = {n['noteId']: n['tags'] for n in notes}

    for c in cards:
        print(f"  Tags: {tags_by_note[c['note']]}")

### 3. Edit / Rewrite Fields

Use `updateNoteFields` with the **note ID** (not card ID):

    # Get note ID from a card
    cards = anki('cardsInfo', cards=[card_id])
    note_id = cards[0]['note']

    # Update only the fields you want to change
    anki('updateNoteFields', note={
        'id': note_id,
        'fields': {
            'Front': 'What is the powerhouse of the cell?',
            'Back': 'The mitochondrion'
        }
    })

Omitted fields are left unchanged.

### 4. Add / Remove Tags

    # Add tags (space-separated string)
    anki('addTags', notes=[note_id_1, note_id_2], tags='reviewed rewritten')

    # Remove tags
    anki('removeTags', notes=[note_id], tags='leech')

### 5. Suspend / Unsuspend

These take **card IDs**:

    anki('suspend', cards=[card_id])
    anki('unsuspend', cards=[card_id_1, card_id_2])

### 6. Delete Notes

**Permanently deletes the note and ALL its cards.** Always show the user what will be deleted and confirm before proceeding.

    anki('deleteNotes', notes=[note_id])

### 7. Move Cards Between Decks

    anki('changeDeck', cards=[card_id], deck='New Deck Name')

### 8. Create New Notes

    anki('addNote', note={
        'deckName': 'My Deck',
        'modelName': 'Basic',
        'fields': {
            'Front': 'Question',
            'Back': 'Answer'
        },
        'tags': ['my-tag']
    })

### 9. Multi-action Batch Operations

AnkiConnect supports `multi` for executing several actions atomically:

    anki('multi', actions=[
        {'action': 'unsuspend', 'params': {'cards': [id1, id2]}},
        {'action': 'addTags', 'params': {'notes': [nid1, nid2], 'tags': 'reviewed'}},
    ])

---

## Card ID vs Note ID — When to Use Which

This is the most common source of errors. A **note** is the content (fields + tags). A **card** is a specific review item generated from a note. One note can produce multiple cards (e.g., a "Basic (and reversed card)" note creates both a forward and reverse card).

| Operation                | Takes                |
| ------------------------ | -------------------- |
| `findCards`              | returns **card IDs** |
| `cardsInfo`              | **card IDs**         |
| `suspend` / `unsuspend`  | **card IDs**         |
| `changeDeck`             | **card IDs**         |
| `updateNoteFields`       | **note ID**          |
| `deleteNotes`            | **note IDs**         |
| `addTags` / `removeTags` | **note IDs**         |
| `notesInfo`              | **note IDs**         |

To go from card to note: `note_id = anki('cardsInfo', cards=[card_id])[0]['note']`

---

## Triage Workflow

When the user asks to triage cards (suspended, leeches, etc.), follow this structure:

### Step 1 — Survey

Find and categorize the target cards. Present a summary:

    from collections import Counter

    cards = anki('findCards', query='is:suspended')
    info = anki('cardsInfo', cards=cards)

    by_deck = Counter(c['deckName'] for c in info)
    by_model = Counter(c['modelName'] for c in info)

    print(f"Found {len(cards)} suspended cards")
    print(f"By deck: {dict(by_deck)}")
    print(f"By type: {dict(by_model)}")

### Step 2 — Review in batches

Show 5-10 cards at a time. For each card, display:

- Question / front side (HTML-stripped)
- Answer / back side
- Tags
- Deck and note type
- Lapse count if relevant (`c['lapses']` from cardsInfo)

### Step 3 — Recommend actions

For each card, suggest one of:

- **Unsuspend** — card is fine, return to rotation
- **Rewrite + unsuspend** — poorly worded; improve it, then return to rotation
- **Delete** — redundant, trivial, or unfixable
- **Keep suspended** — not ready to decide yet

### Step 4 — Execute

Apply the user's decisions. Confirm before any deletions.

---

## Tips

- **HTML in fields:** Card content often contains HTML (`<br>`, `<b>`, `<img>`). Strip it for display, but preserve it when editing unless the user asks to reformat.
- **Cloze numbering:** `{{c1::...}}` and `{{c2::...}}` create separate cards from the same note. Don't accidentally merge or renumber them.
- **Sync reminder:** After making changes, suggest the user sync (`Cmd+Shift+Y` on Mac, or Tools > Sync) if they use AnkiWeb.
- **Large collections:** For collections with thousands of cards, always use targeted queries rather than fetching everything. Use `head_limit` style pagination in your Python (e.g., `cards[:50]`).
- **Leech detection:** Cards with `tag:leech` or `prop:lapses>=8` are struggling. These are the highest-value triage targets — a rewrite can save a card from deletion.
```

</div>

</details>

---

Happy triaging,

DJ
