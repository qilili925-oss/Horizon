---
layout: default
title: "Horizon Summary: 2026-11-15 (EN)"
date: 2026-11-15
lang: en
---

> From 39 items, 10 important content pieces were selected

---

**Technology News**
1. [Lovable-built apps exposed passport data and 200K private messages](#item-tech-news-1) ⭐️ 8.0/10
2. [Project Zero reportedly sets 90-day disclosure, with 60- and 30-day targets](#item-tech-news-2) ⭐️ 7.0/10
3. [Show HN: DeepSeek V3 reimplemented in about 200 lines of JAX](#item-tech-news-3) ⭐️ 7.0/10
4. [EFF says tech companies are trying to redefine privacy again](#item-tech-news-4) ⭐️ 7.0/10
5. [PyPI project pages get clearer security and provenance signals](#item-tech-news-5) ⭐️ 7.0/10
6. [OpenAI disbands independent robotics team, citing general models](#item-tech-news-6) ⭐️ 7.0/10
7. [Cloudflare open-sources Kitesurf, a stateless AI-agent browser](#item-tech-news-7) ⭐️ 7.0/10
8. [Tesla Cybercab terms require $299 monthly autonomy subscription to operate](#item-tech-news-8) ⭐️ 7.0/10
9. [FAA ground stop blamed on router failure during copper-to-fiber upgrade](#item-tech-news-9) ⭐️ 7.0/10

**Financial News**
1. [🤖 Anthropic IPO 拒绝中国内地及香港投资者下单](#item-finance-news-1) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Lovable-built apps exposed passport data and 200K private messages](https://www.crissyfield.de/research/lovable-en/) ⭐️ 8.0/10

A Crissy Field security review reported that apps built with Lovable exposed passport details and more than 200,000 private messages because Row-Level Security was insufficient. Lovable&\#x27;s head of security said insufficient RLS was the root cause and that Lovable automatically scans every app before publishing and offers a free deeper SAST scan, with users able to apply fixes or enable auto-fix; those remediation capabilities are the vendor&\#x27;s account, not an independent audit. The supplied material does not quantify how many apps or users were affected.

hackernews · armcat · Nov 14, 17:43 · [Discussion](https://news.ycombinator.com/item?id=50499017)

**「Background」** Row-Level Security is a PostgreSQL feature, which Supabase exposes, that decides which rows a database query is allowed to return; when tables are created without policies, requests carrying the app&\#x27;s public API key can read records the app never intended to show. Because Lovable generates apps on top of Supabase and sets up the database for its users, the platform&\#x27;s defaults determine whether a newly published app is restricted out of the box.

**「What to check」** Developers shipping Lovable apps backed by Supabase should verify Row-Level Security on every exposed table and test access as unauthenticated and non-owner users before publishing; Lovable&\#x27;s pre-publish scanning and auto-fix are vendor-described safeguards, not evidence that already-published apps have been remediated.

**「Responsibility debate」** Commenters debated responsibility: one pointed to Supabase&\#x27;s permissive RLS defaults and said a fix reported for October 30 might not cover existing projects, while another argued AI-generated apps mainly make such breaches easier to find and more numerous. A separate commenter framed the incidents as canaries showing that platforms need deny-by-default databases and automated authorization tests.

**Tags**: `#AI app builders`, `#application security`, `#Row-Level Security`, `#Supabase`, `#data exposure`

---

<a id="item-tech-news-2"></a>
### [Project Zero reportedly sets 90-day disclosure, with 60- and 30-day targets](https://projectzero.google/2026/11/disclosure-policy.html) ⭐️ 7.0/10

Google Project Zero is reportedly adopting a 90-day vulnerability disclosure window, under which bugs are made public 90 days after vendors are notified. A commenter quoting the policy says Project Zero will shorten that to 60 days on February 2, 2027, and to 30 days on January 3, 2028. The details come from that comment and have not been independently confirmed in the item. The change would affect the vendors and open-source projects to which Project Zero reports vulnerabilities.

hackernews · hacb · Nov 14, 11:13 · [Discussion](https://news.ycombinator.com/item?id=50496051)

**「Earlier policy context」** Since 2021, Project Zero has followed a &quot;90 + 30&quot; disclosure policy, giving vendors up to 90 days to remediate a vulnerability plus an extra 30 days of &quot;soak time&quot; for patch rollout before technical details became public. The new &quot;Full X&quot; schedule removes that soak period — the 90-day clock now runs from the initial report — with planned reductions to 60 days on February 2, 2027 and 30 days on January 3, 2028, a compression one analysis attributes to AI-accelerated exploit development.

**「Impact」** Vendors and open-source maintainers would need to triage, fix, and release patches within the shorter windows—an operational burden that grows sharply at 30 days, especially for projects with slower release cycles.

**「Community discussion」** Commenters disagreed over whether the deadlines would force fixes: one argued for immediate disclosure because nothing else compels vendors to act, while another said Ubuntu would need “a LOT more time” than 30 days.

<details><summary>References</summary>
<ul>
<li><a href="https://projectzero.google/2026/11/disclosure-policy.html">Policy and Disclosure: 2026 Edition - Project Zero</a></li>
<li><a href="https://www.verisq.ai/intelligence/policy-and-disclosure-2026-edition-72908">Google Project Zero Shifts to Full 90 Disclosure, Plans Full ...</a></li>

</ul>
</details>

**Tags**: `#vulnerability disclosure`, `#Project Zero`, `#security policy`, `#open source`, `#Google`

---

<a id="item-tech-news-3"></a>
### [Show HN: DeepSeek V3 reimplemented in about 200 lines of JAX](https://github.com/Vaibhaav-Tiwari/deepseek-v3-jax) ⭐️ 7.0/10

A Show HN project by VaibhaavTiwari reimplements DeepSeek V3 in roughly 200 lines of pure JAX, aimed at studying the model and experimenting locally. It is a third-party educational implementation, and the roughly 200-line scope points to a compact codebase rather than a production inference stack. One commenter reported running it end-to-end on an AMD RX 7600 XT 16GB under ROCm, with the setup needing HSA\_OVERRIDE\_GFX\_VERSION=11.0.0 for that GPU.

hackernews · VaibhaavTiwari · Nov 14, 15:04 · [Discussion](https://news.ycombinator.com/item?id=50497589)

**「Background」** DeepSeek-V3 is a Mixture-of-Experts language model with 671B total parameters, of which 37B are activated for each token, according to its technical report and model card \(tool-2-1, tool-2-2, tool-2-3\). That sparse, expert-routing architecture is the prerequisite for assessing what a roughly 200-line pure-JAX reimplementation covers; the available material does not specify whether the code reproduces the full model or an educational subset.

**「Practical impact」** Developers experimenting on AMD GPUs have a concrete path: a commenter reports this implementation ran end-to-end on an RX 7600 XT 16GB with ROCm and JAX after setting HSA\_OVERRIDE\_GFX\_VERSION=11.0.0, though the second required environment variable is truncated in the comment. Others should expect extra setup, because JAX&\#x27;s ROCm wheels do not automatically install ROCm packages and ROCm does not support every AMD GPU.

**「Community discussion」** Commenters largely treated the post as a learning resource: one asked for a roadmap aimed at developers comfortable with Java and Python, and another said they planned to recreate it for study. The thread contained praise for the first-principles approach but no substantive technical disagreement.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/deepseek-ai/DeepSeek-V3-Base">deepseek -ai/ DeepSeek - V 3 -Base · Hugging Face</a></li>
<li><a href="https://arxiv.org/abs/2412.19437">[2412.19437] DeepSeek - V 3 Technical Report</a></li>
<li><a href="https://paperlens.io/idea/deepseek-moe/">Advanced Mixture of Experts : The DeepSeek - V 3 Architecture</a></li>
<li><a href="https://github.com/ROCm/TheRock/blob/main/RELEASES.md">TheRock/RELEASES.md at main · ROCm /TheRock · GitHub</a></li>
<li><a href="https://docs.ollama.com/gpu">Hardware support - Ollama</a></li>

</ul>
</details>

**Tags**: `#JAX`, `#DeepSeek V3`, `#LLM implementation`, `#ROCm`, `#open source`

---

<a id="item-tech-news-4"></a>
### [EFF says tech companies are trying to redefine privacy again](https://www.eff.org/deeplinks/2026/11/tech-companies-are-trying-shift-entire-concept-privacy-again) ⭐️ 7.0/10

An EFF analysis argues that technology companies are again trying to shift the meaning of privacy, but the supplied item does not identify specific companies, proposals, or policy text. The piece is advocacy and commentary rather than a report of a shipped product or a concrete policy change.

hackernews · gslin · Nov 14, 12:45 · [Discussion](https://news.ycombinator.com/item?id=50496602)

**「Background」** AI meeting notetakers have become common in professional settings, automatically joining calls to capture audio and produce transcripts and summaries. Privacy advocates have warned that these tools can create voiceprints without consent and that some vendors resell notetaker data or use confidential meeting transcripts to train their AI models.

**「Impact」** For workers, the concrete concern raised is that AI notetakers can record routine one-on-one meetings and that opting out may be impractical without risking employment.

**「Community discussion」** Commenters debated whether such recording can be refused, with one asking whether teams can normalize turning off AI notetakers when transcription is unnecessary. Another argued that live transcription can be transformative for deaf and hard-of-hearing users and that local-only models could avoid retention, though retention remains a configuration change away.

<details><summary>References</summary>
<ul>
<li><a href="https://techxplore.com/news/2026-07-ai-notetakers-easy-recaps-professionals.html">AI notetakers promise easy meeting recaps, but some professionals...</a></li>

</ul>
</details>

**Tags**: `#privacy`, `#AI notetakers`, `#surveillance`, `#tech policy`, `#workplace recording`

---

<a id="item-tech-news-5"></a>
### [PyPI project pages get clearer security and provenance signals](https://blog.pypi.org/posts/2026-11-06-ui-updates-complete/) ⭐️ 7.0/10

PyPI&\#x27;s redesigned project pages are now live, making security and provenance signals more prominent for people browsing Python packages. The change is a UI and metadata update: commenters point to per-file provenance indicators, with datasette showing provenance and dlt not. The supplied material does not describe new signing requirements, compatibility changes, or a staged rollout.

hackernews · rbanffy · Nov 14, 15:40 · [Discussion](https://news.ycombinator.com/item?id=50497892)

**「Background」** PyPI&\#x27;s provenance display builds on trusted publishing, the OIDC-based flow that lets a CI provider publish a package without a long-lived API token, with attestations recording how a file was built. The distinction matters: provenance can show that a release came from an expected workflow, but it does not establish that the project itself is free of malicious code.

**「Impact」** Users can now use provenance status as a per-file signal when choosing a release, but because it covers the publishing path rather than project intent, they still need separate checks for malicious packages.

**「Community discussion」** Commenters broadly welcomed more visible provenance and keyless signing, but one questioned whether the trust model effectively centralizes trust in large cloud CI providers; another asked PyPI to support reusable workflows for trusted publishing. A further comment stressed that provenance detects compromised releases from previously benign projects, not malicious projects from the outset.

**Tags**: `#PyPI`, `#software supply chain security`, `#provenance`, `#Python packaging`, `#open source infrastructure`

---

<a id="item-tech-news-6"></a>
### [OpenAI disbands independent robotics team, citing general models](https://fortune.com/2026/11/13/openai-disbands-robotics-team-as-its-general-models-start-running-robots/) ⭐️ 7.0/10

OpenAI has disbanded its independent robotics team and reassigned its researchers to broader research groups, according to a Fortune report summarized in the item. The company said robotics remains part of its long-term vision but that general frontier models such as GPT-6 Astra can now directly control robots, reducing the need for a dedicated robotics team. The report also notes that OpenAI disbanded an earlier robotics team in 2020, rebuilt it in 2024 with a Figure partnership that ended in February 2025, and is still developing a humanoid robot, with its CEO targeting a first public demonstration in 2027. Claims about GPT-6 Astra&\#x27;s robot-control capabilities and the 2027 demonstration were not independently substantiated in the supplied material.

telegram · zaihuapd · Nov 14, 04:00

**「Background」** OpenAI’s robotics effort has cycled through prior reorganizations: it disbanded an earlier robotics team in 2020, rebuilt one in 2024, and its partnership with Figure AI ended in February 2025. The current change moves robotics staff into broader research teams under Mark Chen and Greg Brockman, making the work part of general model development rather than a standalone robotics unit.

<details><summary>References</summary>
<ul>
<li><a href="https://theroboticsmedia.com/article/openai-disbands-robotics-team-gpt-6-astra">OpenAI Disbands Robotics Team, Bets on GPT-6 Astra Instead</a></li>
<li><a href="https://madrobot.blog/2026/11/13/openai-disbands-robotics-team-gpt-6-astra/">OpenAI reorganises its robotics team as GPT-6 Astra runs robots</a></li>

</ul>
</details>

**Tags**: `#OpenAI`, `#robotics`, `#foundation models`, `#AI strategy`, `#humanoid robots`

---

<a id="item-tech-news-7"></a>
### [Cloudflare open-sources Kitesurf, a stateless AI-agent browser](https://www.phoronix.com/news/Cloudflare-Kitesurf-Open-Source) ⭐️ 7.0/10

Cloudflare has open-sourced Kitesurf under Apache 2.0, describing it as a stateless browser for AI agents built on Cloudflare Workers. It parses HTML, processes CSS, and executes JavaScript without a browser container, and the code is available on GitHub. Cloudflare claims it uses less CPU and memory than Chromium and can scale on demand across the Workers network; the source provides no independent benchmark or detailed compatibility information.

telegram · zaihuapd · Nov 14, 09:33

**「Background」** Kitesurf runs without Chromium underneath: Cloudflare&\#x27;s documentation says it runs entirely on Workers, while a third-party technical overview describes it as running in V8 isolates with most of its code written in Rust and compiled to WebAssembly. The GitHub repository labels the project experimental and notes that running it on Cloudflare requires Dynamic Workers, which are part of the Workers Paid plan; local development uses \`wrangler dev\`.

**「Impact」** Developers building browser-using AI agents gain an Apache-2.0 alternative to maintaining Chromium containers on Workers, but the short announcement leaves JavaScript and CSS compatibility and the claimed resource savings unverified, so it should be tested against required sites before production use.

<details><summary>References</summary>
<ul>
<li><a href="https://developers.cloudflare.com/changelog/post/2026-11-12-kitesurf-open-source/">Kitesurf is now open source · Changelog | Cloudflare Docs</a></li>
<li><a href="https://www.eesel.ai/blog/cloudflare-kitesurf">Cloudflare Kitesurf : the agent browser that trades speed... | eesel AI</a></li>
<li><a href="https://github.com/cloudflare/kitesurf">GitHub - cloudflare / kitesurf : Kitesurf is an experimental browser ...</a></li>

</ul>
</details>

**Tags**: `#Cloudflare`, `#AI agents`, `#browser automation`, `#open source`, `#serverless`

---

<a id="item-tech-news-8"></a>
### [Tesla Cybercab terms require $299 monthly autonomy subscription to operate](https://www.tesla.com/configurator/api/v4/terms?category=autonomy_subs&amp;amp;locale=en_US&amp;amp;model=cc&amp;amp;saleType=Sale) ⭐️ 7.0/10

Tesla&\#x27;s Cybercab terms state the vehicle costs $29,990 and requires a $299 monthly autonomous-driving subscription; without it, the car cannot operate. Tesla can change the price with one month&\#x27;s notice, and missed payments or unauthorized use can lead to suspension or cancellation, with three accumulated warnings disabling autonomous driving for one week. The terms also restrict operation to designated areas and bar unauthorized connection to ride-hailing, delivery, or rental platforms. Electrek notes that the Cybercab and the Model Y used for Robotaxi share AI4 hardware and autonomous-driving software, while owner-facing FSD still requires human supervision.

telegram · zaihuapd · Nov 15, 01:10

**「Background」** Tesla positions Cybercab as a purpose-built robotaxi, and Electrek notes that it shares AI4 hardware and autonomous-driving software with the Model Y vehicles used for robotaxi service. That differs from the FSD package sold to ordinary car owners, which still requires human supervision.

**「Impact」** For prospective owners and fleet operators, the $29,990 vehicle price does not cover an operational Cybercab: the $299 monthly fee is mandatory, and the geofencing and platform restrictions limit where and how the car can be used commercially.

**Tags**: `#Tesla`, `#Cybercab`, `#autonomous driving`, `#subscription pricing`, `#robotaxi`

---

<a id="item-tech-news-9"></a>
### [FAA ground stop blamed on router failure during copper-to-fiber upgrade](https://www.theverge.com/transportation/1033898/faa-ground-stop-sean-duffy-faa-copper-wire) ⭐️ 7.0/10

A nationwide FAA ground stop that halted thousands of flights was triggered by a router failure during routine copper-to-fiber maintenance at a remote facility, according to U.S. Transportation Secretary Sean Duffy. Duffy said on Nov. 14 that the root cause is not yet established and could be a hardware failure, a configuration error, or a mistake by contractor L3Harris. The router sent more than 1,000 connection requests every 4 to 5 seconds to other routers, interfering with radar signals and aircraft communications, he said. Duffy called for Congress to provide additional funding for air-traffic-control modernization.

telegram · zaihuapd · Nov 15, 02:10

**「Background」** NPR reported that the FAA ground stop had ended but that passengers were still stuck at airports. The maintenance work was carried out by L3Harris, a long-time FAA contractor, according to NPR.

**「Ongoing rollout risk」** L3Harris&\#x27;s copper-to-fiber replacement program covers all FAA facilities, from major air route traffic control centers to remote radar sites and weather stations, so the remaining cutover work carries the same change-control risk that surfaced here. The FAA has kept funding that work, obligating an additional $21.5 million in July 2026 and bringing cumulative obligations toward $2.1 billion. Transportation Secretary Sean Duffy said the investigation is examining L3Harris&\#x27;s work on the individual router, which means the contractor&\#x27;s configuration and testing practices at other sites are now the focal point.

<details><summary>References</summary>
<ul>
<li><a href="https://www.npr.org/2026/11/14/nx-s1-6040952/faa-ground-stop-airplane-travel">FAA ground stop ends but passengers stuck at airport : NPR</a></li>
<li><a href="https://www.l3harris.com/all-capabilities/faa-telecommunications-infrastructure-fti">FAA Telecommunications Infrastructure (FTI) - L3Harris</a></li>
<li><a href="https://www.federalmediagroup.com/news/faa-adds-21-5m-to-l3harris-telecom-infrastructure-order-cumulative-obligations-approach-2-1-billion">FAA Adds $21.5M to L3Harris Telecom Infrastructure Order ...</a></li>
<li><a href="https://www.usatoday.com/story/news/nation/2026/11/14/faa-ground-stop-probe-l3harris/92780406007/">Air traffic probe looks at work of FAA contractor and a ...</a></li>

</ul>
</details>

**Tags**: `#network outage`, `#router failure`, `#infrastructure reliability`, `#FAA`, `#aviation systems`

---

## Financial News

<a id="item-finance-news-1"></a>
### [🤖 Anthropic IPO 拒绝中国内地及香港投资者下单](https://m.economictimes.com/markets/us-stocks/news/anthropic-ipo-share-orders-from-china-are-said-to-be-rebuffed/articleshow/135809948.cms) ⭐️ 7.0/10

Anthropic&\#x27;s reported IPO is said to bar mainland Chinese and Hong Kong investors under ITAR-related restrictions, with pricing set for Nov. 18 at a $1.4 trillion valuation and a raise of up to $90.4 billion.

telegram · zaihuapd · Nov 14, 10:18

**Tags**: `#Anthropic IPO`, `#China/Hong Kong investors`, `#ITAR export controls`, `#AI financing`, `#IPO valuation`

---