---
layout: default
title: "Horizon Summary: 2026-11-09 (EN)"
date: 2026-11-09
lang: en
---

> From 24 items, 3 important content pieces were selected

---

**Technology News**
1. [KetchUp: open-source Rust/WebGPU SketchUp alternative](#item-tech-news-1) ⭐️ 7.0/10
2. [Outlook.com Reportedly Rejects Mail From Domains Without DMARC](#item-tech-news-2) ⭐️ 7.0/10
3. [Goldman Sachs reportedly pulls Claude Code from bankers and traders](#item-tech-news-3) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [KetchUp: open-source Rust/WebGPU SketchUp alternative](https://ketchup3d.github.io/app/) ⭐️ 7.0/10

KetchUp is an open-source, browser-based 3D modeling application built with Rust and WebGPU and presented as a SketchUp alternative. The project page at ketchup3d.github.io/app is accessible, but the supplied material does not specify a version, license, supported file formats, or export capabilities. Its Hacker News submission drew positive attention for running a responsive Rust UI in the browser, including text rendering.

hackernews · dcoulmbe · Nov 8, 22:35 · [Discussion](https://news.ycombinator.com/item?id=50418176)

**「Context」** SketchUp&\#x27;s current free version already runs in a web browser under Trimble, so browser-based modeling is an established category rather than something KetchUp introduces. KetchUp&\#x27;s distinction is that it is an open-source implementation built with Rust and WebGPU, which is the technical premise users are being asked to evaluate.

**「Impact」** For SketchUp users and 3D-printing hobbyists, the immediate option is a SketchUp-style modeler that runs in the browser without a desktop install; the available material does not establish SketchUp file compatibility or standard 3D-printing export workflows, so it should be assessed as a separate tool rather than a drop-in replacement.

**「Community Discussion」** Commenters welcomed a SketchUp-style alternative, with one long-time SketchUp user lamenting the original&\#x27;s shrinking free offering and another 3D-printing hobbyist saying SketchUp 8 was easier to learn than FreeCAD. Feedback also flagged a concrete UX issue—rectangle creation prompts for an object name—and one commenter praised the Rust/WebGPU UI&\#x27;s responsiveness while asking for feature showcases.

<details><summary>References</summary>
<ul>
<li><a href="https://sketchup.trimble.com/en/plans-and-pricing/sketchup-free">Free 3 D Modeling Software | 3 D Design Online | SketchUp ... | Trimble</a></li>

</ul>
</details>

**Tags**: `#Rust`, `#WebGPU`, `#open-source 3D modeling`, `#SketchUp alternative`, `#browser graphics`

---

<a id="item-tech-news-2"></a>
### [Outlook.com Reportedly Rejects Mail From Domains Without DMARC](https://mailroute.net/blog/outlook-rejecting-email-without-dmarc) ⭐️ 7.0/10

Outlook.com is reportedly rejecting email from domains that do not publish a DMARC record, affecting domain owners and mail senders whose messages are routed to Microsoft&\#x27;s consumer mailbox service. The report does not include a Microsoft statement, enforcement date, rejection code, or scope, so it is not confirmed whether all such domains or only some traffic are affected. It also characterizes the enforcement as quiet, a point commenters dispute.

hackernews · xmddmx · Nov 8, 19:20 · [Discussion](https://news.ycombinator.com/item?id=50416158)

**「What DMARC does」** DMARC is a DNS TXT record that tells receiving mail services how to handle messages that fail SPF or DKIM alignment, giving domain owners a way to prevent spoofing. Reports say Outlook.com and Hotmail began rejecting mail from domains with no DMARC record on Nov. 5, 2026; the remedy is to publish a record, provided SPF or DKIM aligns with the From domain.

**「Impact」** For domain owners, publishing a DMARC record may become a prerequisite for delivery to Outlook.com, so senders should check their DNS policy and DMARC reporting before assuming a blocklist issue. The report does not establish whether a monitor-only policy is sufficient or whether enforcement applies uniformly.

**「Community Discussion」** Commenters broadly supported requiring DMARC, but disputed whether the change is &\#x27;quiet&\#x27;: one said Outlook.com returns 5xx permanent delivery failures, while another reported years of silent drops even with SPF, DKIM, and DMARC configured. A separate complaint focused on non-public blocklists that a VPS operator said left an entire provider blocked with no clear way to get unblocked.

<details><summary>References</summary>
<ul>
<li><a href="https://mailroute.net/blog/outlook-rejecting-email-without-dmarc">Outlook.com Is Quietly Rejecting Email From Domains Without DMARC</a></li>
<li><a href="https://tosend.com/articles/outlook-rejects-email-without-dmarc/">Outlook.com now rejects email from domains without DMARC</a></li>
<li><a href="https://news.lavx.hu/article/outlook-com-rejects-some-email-from-domains-without-dmarc-records">Outlook.com Rejects Some Email From Domains Without DMARC ...</a></li>

</ul>
</details>

**Tags**: `#DMARC`, `#email deliverability`, `#Microsoft Outlook`, `#email infrastructure`, `#spam filtering`

---

<a id="item-tech-news-3"></a>
### [Goldman Sachs reportedly pulls Claude Code from bankers and traders](https://www.thestateofai.com/news/goldman-sachs-claude-code-traders-bankers) ⭐️ 7.0/10

Goldman Sachs is reportedly pulling Claude Code from its bankers and traders. The item provides no company statement or details on timing, scope, or whether other employees retain access. Discussion of the move centers on security isolation, compliance constraints, and consumption-based billing for enterprise AI coding agents.

hackernews · TheWiggles · Nov 8, 18:16 · [Discussion](https://news.ycombinator.com/item?id=50415628)

**「Earlier Claude restriction」** Goldman Sachs had already restricted Claude access before this broader pullback: the same report says the bank barred its Hong Kong bankers from Claude in April. That earlier step was a narrower, region-specific limit, so the reported withdrawal from most traders and bankers represents an expansion of the restriction.

**「Impact」** Any replacement rollout for bankers and traders would face the constraint cited in the discussion: coding agents running on primary workstations with access to client, trade, and email data need isolation or narrower entitlements.

**「Community Discussion」** Commenters offered competing explanations: one argued that semi-unattended coding agents on finance workstations create an unacceptable security exposure because those machines also hold client, trade, and email data, while another reported that their organization had clawed back Claude access over chronic billing overages and that Gemini was gaining ground with flat, consistent billing. A separate commenter emphasized compliance and auditability, arguing that LLM-assisted proofs of concept reach production faster without equivalent controls.

<details><summary>References</summary>
<ul>
<li><a href="https://www.thestateofai.com/news/goldman-sachs-claude-code-traders-bankers">Goldman Sachs Is Pulling Claude Code From Its Bankers and...</a></li>

</ul>
</details>

**Tags**: `#AI coding agents`, `#enterprise security`, `#financial services`, `#AI governance`, `#Claude Code`

---