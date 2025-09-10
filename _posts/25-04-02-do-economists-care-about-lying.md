---
layout: distill
title: Do Economists Care About Lying?
date: 2025-04-02 09:00:00+1100
description: When do processes matter more than outcomes?
giscus_comments: true
tags: [economics, ethics, lying, algorithms, communication games]
categories: [economics]
toc:
    - name: Introduction
    - name: Models
    - name: Why the models are the same, and different
    - name: Where does this leave us?
    - name: Why we should care.
    - name: Conclusion
related_posts: false
published: true
---

## Introduction

*(Note: This is a bit of an esoteric post based on an idea that came up when working on research about communication games— see [Targeted Persuasion](/projects/targeted_persuasion).)*

My goal here is to show you two economic models of communication which are the same from a consequentialist perspective, but different from the perspective of our (or at least *my*) moral intuitions. I will then make the case that this is not just some abstract distinction, but that it has real, practical, ethical and legal consequences. I did not think it would be difficult to convince people that these two models are importantly different, until I started talking about this with economic theorists. I hope I will not have to convince *you* that they are different, but let's see.

This all started when I saw two models of communication that an economic theorist told me were "the same". I've written this post in such a way that it should be readable for anyone, including those who have no familiarity with communication games or even with economics. So let's jump into the two models, and a specific communication strategy under which these are considered "the same".

## The Models

I am selling a product which has some unknown quality denoted by $q$. The quality can either be good ($q=G$) or bad ($q=B$). If the product is good quality you would prefer to buy it. If it is bad quality you would prefer not to. Hence you will only buy the product if you believe that it is good quality with sufficiently high probability.

**Model 1.** I learn the true quality of the product. Then, knowing the quality, I send you one of two messages $m$: I either say
1. "the quality is good" ($m=g$), or
2. "the quality is bad" ($m=b$).

If the quality is good ($q=G$), then I will always send you $m=g$. If the quality is bad ($B$), I toss a fair coin and only send you $m=b$ if it lands tails. Otherwise, if it lands heads I send you $m=g$. You then decide whether to purchase the product.

The basic idea here is that if I learn the product is good quality, I'll always tell you the truth. But if I learn it's bad quality, I'll only tell you the truth half the time. So if (for example) you observe the message $m=b$, you know for sure that the product must be bad quality (for, if it were good quality, I would have sent you $m=g$). Economic theorists will recognize this as the kind of strategy which is typical in models of [Bayesian Persuasion](https://web.stanford.edu/~gentzkow/research/BayesianPersuasion.pdf).

**Model 2.** An autonomous machine learns the true quality of the product. If the product is good quality, the machine will always send me $m=g$. If the product is bad quality, the machine will toss a fair coin and send me $m=b$ if it lands tails, otherwise it will send me $m=g$. Once I have received the message, I *pass the message directly on to you* and then you decide whether to purchase the product.


## Why the models are the same, and different

The reason these two models are considered "the same", is that the rational beliefs about the product conditional on observing the message $m=b$ or $m=g$ are identical in both. In particular, if you observe $m=b$, then you infer that with certainty the product is of bad quality. If you observe $m=g$, then you infer that with some probability (let's say $\tau$) the product is of good quality, and with probability $1-\tau$ it is of bad quality but the coin toss landed heads. As long as $\tau$ is large enough, you will buy the product whenever you observe $m=g$.

Since beliefs determine actions, and actions determine payoffs, the two models lead to identical *outcomes*. It is in this sense— the consequential sense— that they are the same. But I hope you can see why I find this unsettling— there seems to me something fundamentally different between the two models: In Model 1, I have the ability to *lie*, in Model 2 I do not. In Model 1, I am informed; in Model 2, I am a messenger. We do hold people (morally, legally) responsible for lying to us, but we all know that you don't shoot the messenger.

## Where does this leave us?

Thankfully there are economists taking these ideas seriously. [Joel Sobel](https://scholar.google.com/citations?user=vFx4c3EAAAAJ&hl=en) (who many economic theorists would know from the seminal paper by [Crawford & Sobel, 1982](https://econweb.ucsd.edu/~vcrawfor/CrawfordSobel82EMT.pdf) which developed the  "cheap-talk" communication model) wrote a paper titled "[Lying and Deception in Games](https://par.nsf.gov/servlets/purl/10143200)" in which he offers one formalization of what it means to lie in a communication game. Unfortunately his model does not encapsulate the difference between Model 1 and Model 2— since his "Sender" (the equivalent of my "seller") always knows the state. In fact, Sobel points exactly this out on page 941 of the paper under the heading "Imperfect Knowledge of the State". He says that if the seller has imperfect knowledge of the "state" (the quality $q$), then it would be natural to define lying in terms of what the seller communicates about the message(s) they *observe*, rather than having to communicate the true quality (since they may not know what the actual quality is). And indeed, if we extend the definition of lying in this natural way then the seller in Model 1 has the ability to lie, while the seller in Model 2 does not, in agreement with our intuition.

## Why we should care

The distinction between Model 1 and Model 2 becomes important in a world that is increasingly mediated by algorithms. When you receive a product recommendation, a news article, or a tailored advertisement, you're often receiving the output of a system that has been designed to maximize some objective function—for example, the profit of the system's owner.

If the algorithm "learns" to lie in a way that is optimal for the seller, who bears the responsibility? For example, a medical diagnosis algorithm might occasionally provide false negatives to reduce health care costs. Is this meaningfully different from a doctor who occasionally lies about test results for the same reason? In both cases, the outcome is identical— some sick patients go untreated. But the mechanisms— and our intuitions about moral responsibility— differ dramatically.

Or what about an algorithmic credit score system that systematically discriminates against certain populations to maximize bank's profit? The algorithm creates a shield of plausible deniability. This is the difference between Model 1 and Model 2.

An uncomfortable possibility is that as we delegate more decision-making to algorithms, we may be inadvertently creating systems that implement Model 1-type strategies (strategic lying) while maintaining the moral and legal protections of Model 2 (mere message passing). "You can't shoot the messenger" becomes a useful shield when the messenger is a complex algorithm whose inner workings remain inscrutable—even to its creators. As such, we need to think carefully about the incentives for firms in designing these systems, and whether we can create a framework that holds them accountable for the outcomes of their algorithms.

## Conclusion

The seemingly abstract distinction between our two models ultimately reveals something about how we assign moral responsibility in communication. When outcomes are identical but mechanisms differ, our intuitions suggest that *process* matters—not just results. It matters not just for moral reasons, but for legal ones too.

How then, should economists think about the differences in mechanism which are outcome-equivalent? Perhaps more importantly, how do we develop ethical and legal frameworks that properly account for these distinctions? This is, in some sense, *not* a new discussion in economics. We abstract from processes and focus on outcomes. But processes are important, and good research highlights exactly when or why they are important, and allows us to design policy accordingly. 

Great work is being done specifically on the topic of developing a framework for AI liability, see for example [this paper](https://doi.org/10.1016/j.clsr.2023.105794), [this paper](https://www.jstor.org/stable/26810851), or [this medical review](https://pmc.ncbi.nlm.nih.gov/articles/PMC10711067/). But as far as I can tell, very little has been done on the economics of lying in the context of algorithms. I think this would be a really interesting area to explore.

DJ