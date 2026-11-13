---
layout: default
title: "Horizon Summary: 2026-11-13 (EN)"
date: 2026-11-13
lang: en
---

> From 44 items, 13 important content pieces were selected

---

**Technology News**
1. [Rust 1.100 stabilizes never type, custom allocators, and Cargo cooldowns](#item-tech-news-1) ⭐️ 9.0/10
2. [Nvidia CEO Jensen Huang reported to step down; Kress interim CEO](#item-tech-news-2) ⭐️ 8.0/10
3. [22-year-old PostgreSQL type-confusion primitive turned into RCE](#item-tech-news-3) ⭐️ 8.0/10
4. [Google releases Gemini 4 Hydrogen, claiming 2.5x speed over 3.8 Flash](#item-tech-news-4) ⭐️ 8.0/10
5. [Open-source project claims 16B LLMs on sub-1GB devices](#item-tech-news-5) ⭐️ 8.0/10
6. [Anthropic IPO thread weighs valuation, compute commitments, local models](#item-tech-news-6) ⭐️ 8.0/10
7. [UMAP 0.6 adds faster initialization and opt-in optimizers](#item-tech-news-7) ⭐️ 8.0/10
8. [US Commerce finalizing rule to block Chinese AI firms&\#x27; remote chip access](#item-tech-news-8) ⭐️ 8.0/10
9. [Chips and Cheese interviews AMD&\#x27;s Mike Clark on Zen 6](#item-tech-news-9) ⭐️ 7.0/10
10. [Microsoft 365 email outage runs eight hours as status page falters](#item-tech-news-10) ⭐️ 7.0/10
11. [Independent TRIBE v2 audit reports no retinotopy or tonotopy, but MT+ motion](#item-tech-news-11) ⭐️ 7.0/10

**Financial News**
1. [Nvidia&\#x27;s Jensen Huang resigns amid spy-allegation scrutiny](#item-finance-news-1) ⭐️ 7.0/10
2. [China Approves Eli Lilly’s Oral Weight-Loss Drug, Its First Oral GLP-1](#item-finance-news-2) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Rust 1.100 stabilizes never type, custom allocators, and Cargo cooldowns](https://blog.rust-lang.org/2026/11/12/Rust-1.100.0/) ⭐️ 9.0/10

Rust 1.100 has been released, stabilizing the never type and custom allocators. Cargo adds a minimum publish age setting for dependency cooldowns: when configured, the resolver ignores versions published more recently than the threshold unless they are already in Cargo.lock \(RFC 3923\). The release also makes cargo install use the lockfile shipped in the .crate tarball by default, so --locked becomes a no-op, and Cargo now reports unused dependencies by default.

hackernews · mbStavola · Nov 12, 18:39 · [Discussion](https://news.ycombinator.com/item?id=50472038)

**「Background」** In Rust&\#x27;s release process, a feature becomes stable only after a period as an unstable, feature-gated item on nightly, which is the path the never type and the Allocator trait took before this release; Rust 1.100 was branched from master on 25 September 2026 and published on 12 November 2026. Cargo&\#x27;s resolver had previously been willing to pick the newest version matching a requirement as soon as it was published, so the new minimum publish age setting adds a delay that did not exist before.

**「Impact」** Projects that enable a minimum publish age will not resolve crate versions published inside the configured window unless Cargo.lock already pins them, so dependency updates can be delayed by design. Projects that deny warnings may need to remove or allow dependencies newly surfaced by Cargo&\#x27;s default unused-dependency warning.

**「Community discussion」** Commenters welcomed the release, with one highlighting the never type, custom allocators, and Cargo&\#x27;s minimum publish age, and another pointing to stabilized APIs omitted from the post such as bool::toggle and Box::map. A separate commenter asked whether compile times improved and complained about repeatedly cleaning large temp directories; no answer or measured result was supplied.

<details><summary>References</summary>
<ul>
<li><a href="https://blog.rust-lang.org/2026/11/12/Rust-1.100.0/">Announcing Rust 1.100.0 | Rust Blog</a></li>
<li><a href="https://releases.rs/docs/1.100.0/">1.100.0 | Rust Changelogs - releases.rs</a></li>

</ul>
</details>

**Tags**: `#Rust`, `#programming languages`, `#Cargo`, `#dependency management`, `#open source`

---

<a id="item-tech-news-2"></a>
### [Nvidia CEO Jensen Huang reported to step down; Kress interim CEO](https://apnews.com/article/nvidia-megaspeed-china-singapore-huang-5403f152a601cf82ce939f1d24fffa0f) ⭐️ 8.0/10

A Hacker News link post reports that Nvidia CEO Jensen Huang, who led the company for 33 years, has stepped down, citing an Nvidia newsroom “CEO transition” announcement and Reuters and NYT live coverage. The post says Colette Kress has been named interim CEO while Nvidia searches for a permanent successor; it also relays SemiAnalysis claims that the board was investigating Huang’s conduct and that export-control and GPU-smuggling concerns contributed. The supplied item is largely headline and link stubs, so the board’s stated rationale, the terms of the departure, and any confirmed product or policy changes remain unverified.

hackernews · lldb · Nov 12, 13:52 · [Discussion](https://news.ycombinator.com/item?id=50467087)

**「Background」** Huang founded Nvidia and had led it for 33 years, running an unusually flat organization with roughly 60 direct reports and no deep public bench of successors. The board&\#x27;s review of his conduct followed reports of extramarital relationships with two women, one identified by U.S. intelligence as a Chinese spy.

**「Impact」** Nvidia’s customers and CUDA developers face leadership uncertainty over GPU roadmaps and export-compliance decisions, because the source describes a CEO who centralized major decisions and left a shallow successor bench; no product or shipment change is confirmed in the supplied material.

**「Community discussion」** Commenters disputed why the departure happened now: some focused on the reputational risk of alleged affairs for a CEO central to the AI economy, while others argued the real driver was alleged evasion of U.S. export controls. Those are opinions from the thread; the supplied material does not establish either explanation.

<details><summary>References</summary>
<ul>
<li><a href="https://www.nytimes.com/live/2026/11/12/business/nvidia-jensen-huang-resigns">Jensen Huang Resigns as Nvidia CEO After Affairs : Live Updates</a></li>
<li><a href="https://www.theguardian.com/technology/2026/nov/12/nvidia-ceo-jensen-huang-resigns">Jensen Huang resigns as Nvidia CEO after alleged affairs</a></li>
<li><a href="https://www.cnn.com/2026/11/11/business/live-news/nvidia-jensen-huang-investigation-fallout">Jensen Huang resigns as Nvidia CEO | CNN Business</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#CEO transition`, `#AI industry`, `#semiconductor industry`, `#corporate governance`

---

<a id="item-tech-news-3"></a>
### [22-year-old PostgreSQL type-confusion primitive turned into RCE](https://mehmetince.net/part-3-6-how-i-ended-up-turning-a-22-year-old-postgresql-type-confusion-primitive-into-rce-cve-2026-6460/) ⭐️ 8.0/10

A security researcher published a detailed write-up showing how a 22-year-old PostgreSQL type-confusion primitive was developed into a code-execution exploit, tracked as CVE-2026-6460. The post walks through PostgreSQL internals to explain how the primitive was chained into code execution. The supplied material does not include affected version ranges, patch status, or independent reproduction of the exploit.

hackernews · ozirus · Nov 12, 18:22 · [Discussion](https://news.ycombinator.com/item?id=50471761)

**「Background」** The flaw sits in PostgreSQL&\#x27;s handling of type changes: CVE-2026-6460 describes a type confusion that occurs after ALTER ... SET DATA TYPE and can let an object creator execute arbitrary code as the operating-system user running the database. The fix landed in a November 2026 PostgreSQL security release that bundled 52 CVEs, six of which the researcher links to this work; CVE-2026-6460 is the umbrella fix and introduced composite attribute versioning.

**「Who is actually exposed」** The exposure is any authenticated role permitted to create or alter database objects: PostgreSQL&\#x27;s advisory and Red Hat&\#x27;s analysis both describe the trigger as DDL such as ALTER TABLE ... ALTER COLUMN ... SET DATA TYPE, which lets the object creator run code as the operating-system user that owns the database process. Operators should therefore treat DDL privileges as the containment boundary and apply the vendor fix, rather than assuming the flaw is reachable only by unauthenticated remote attackers.

**「Community discussion」** Several commenters, including logophobia and jmuguy, argued that &quot;RCE&quot; overstates the issue because the exploits require an authenticated database account and are better described as privilege escalation, mattering most for multi-tenant databases. Others, including amluto and sailfast, praised the write-up for its detailed exposition of PostgreSQL internals, with amluto describing the Datum pointer-versus-inline-value design as unusually risky.

<details><summary>References</summary>
<ul>
<li><a href="https://www.postgresql.org/support/security/CVE-2026-6460/">PostgreSQL : CVE - 2026 - 6460 : PostgreSQL type confusion after...</a></li>
<li><a href="https://www.phoronix.com/news/PostgreSQL-52-CVEs">PostgreSQL Sees New Releases For 52 Security Vulnerabilities ...</a></li>
<li><a href="https://mehmetince.net/part-3-6-how-i-ended-up-turning-a-22-year-old-postgresql-type-confusion-primitive-into-rce-cve-2026-6460/">Part 3/6 | How I Ended Up Turning a 22-Year-Old PostgreSQL ...</a></li>
<li><a href="https://www.postgresql.org/support/security/CVE-2026-6460/">PostgreSQL: CVE-2026-6460: PostgreSQL type confusion after ...</a></li>
<li><a href="https://access.redhat.com/security/cve/cve-2026-6460">CVE-2026-6460 - Red Hat Customer Portal</a></li>

</ul>
</details>

**Tags**: `#PostgreSQL`, `#security vulnerability`, `#type confusion`, `#RCE`, `#database internals`

---

<a id="item-tech-news-4"></a>
### [Google releases Gemini 4 Hydrogen, claiming 2.5x speed over 3.8 Flash](https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-hydrogen/) ⭐️ 8.0/10

Google has released Gemini 4 Hydrogen, a model positioned for fast everyday coding and agent workflows and made available to developers, enterprises, and consumer users. Google prices it at $1.50 per million input tokens and $7.50 per million output tokens. The company says it is 2.5x faster than Gemini 3.8 Flash, raises its Terminal-Bench 4.1 score from 18.2% to 57%, and beats Argon on the Artificial Analysis index in its default tier. These are vendor-provided comparisons; the supplied material does not include independent benchmark results or detailed availability limits.

hackernews · dvaplima · Nov 12, 18:01 · [Discussion](https://news.ycombinator.com/item?id=50471431)

**「Background」** Gemini 3.8 Flash is the earlier model that Google uses as the baseline for Gemini 4 Hydrogen&\#x27;s claimed 2.5x speed increase and its Terminal-Bench 4.1 score change. Those comparisons make the new release understandable as an update to an existing Gemini model line, not a standalone first-generation product.

**「Impact」** Developers choosing a Gemini 3.8 Flash replacement can try Hydrogen immediately, but should re-run their own coding and agent evaluations: the supplied evidence is limited to Google&\#x27;s aggregate speed, Terminal-Bench, and index comparisons, not per-workload latency or regression results.

**「Community discussion」** A commenter criticized the element-based naming, saying a user who encounters “4 Hydrogen” cannot infer how it compares with 3.8 Flash. Another argued that Hydrogen looks like an entry-level replacement for 3.5 Flash Lite but is priced at the same rate as undiscounted 3.8 Flash, questioning whether Google is abandoning its fast-and-cheap tier.

**Tags**: `#Google Gemini`, `#LLM releases`, `#generative AI`, `#AI pricing`, `#model selection`

---

<a id="item-tech-news-5"></a>
### [Open-source project claims 16B LLMs on sub-1GB devices](https://github.com/hyperionaidev/smolmaxxing/) ⭐️ 8.0/10

An open-source project is releasing kernels and modified model variants that its author says run 16B-parameter LLMs on an iPad Air 1st gen and a Xiaomi TV box, each with less than 1GB of usable memory. The author reports decent speeds on that hardware, publishes the kernels and results for reproduction, and hosts modified models on Hugging Face. The supplied comments give no benchmark figures, and the claims have not been independently reproduced.

hackernews · mrashad74 · Nov 12, 15:23 · [Discussion](https://news.ycombinator.com/item?id=50468888)

**「Background」** Running an LLM normally requires holding model weights and runtime state in memory, so models with billions of parameters are far larger than the roughly 1 GB of usable RAM in devices such as first-generation iPads and TV boxes. The smolmaxxing project targets exactly those TV boxes, old phones, single-board computers and routers, aiming to find the largest model each device can run and then push further with custom kernels, tighter memory use and weight streaming.

**「Impact」** Developers can try the released kernels and modified Hugging Face models on similarly constrained hardware, but should treat the 16B-on-sub-1GB claim as unverified until speed, memory use, and output quality are measured independently.

**「Community discussion」** Commenters disagreed about novelty: Farmadupe2 argued that modern coding agents can already one-shot much of this porting work, leaving access to old hardware as the main obstacle, while cjdell and nico welcomed the push to optimize old or small hardware and reported that small models are improving at tool calling and local tasks.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/hyperionaidev/smolmaxxing">GitHub - hyperionaidev/smolmaxxing: maxxing the ability to ...</a></li>

</ul>
</details>

**Tags**: `#LLM inference`, `#edge AI`, `#model optimization`, `#open source`, `#old hardware`

---

<a id="item-tech-news-6"></a>
### [Anthropic IPO thread weighs valuation, compute commitments, local models](https://ipo.anthropic.com/us/) ⭐️ 8.0/10

An item pointing to ipo.anthropic.com/us/ prompted Hacker News discussion of an Anthropic IPO, with one commenter citing a $70–$78 price range, an $85.3B gross deal including a $26B private placement, and an implied market value of about $968B at the $74 midpoint. The same commenter listed Q3 2026 revenue of $17.0B, roughly $81B run-rate revenue as of October 2026, $900.9B of compute commitments through 2045, and the ticker ANT on Nasdaq; those figures come from the discussion and were not independently verified in the supplied material. The thread debated whether the IPO reflects durable frontier-model dominance or a need to raise before cheaper and local models erode pricing power.

hackernews · josephljohnston · Nov 12, 11:46 · [Discussion](https://news.ycombinator.com/item?id=50465829)

**「Background」** Anthropic&\#x27;s offering follows an amended pre-IPO S-1 filing, reported around November 2–3, 2026, which disclosed third-quarter revenue of nearly $17 billion and roughly $900 billion in computing commitments alongside the deal&\#x27;s price range. Coverage of that filing noted sequential revenue growth slowing to 47% from 144% and compute costs rising to 58% of revenue, with investors trimming their target valuation ahead of the listing. Those disclosures are the documents Hacker News commenters are reading figures such as the price range and implied market cap from.

**「Impact」** If the cited terms hold, Anthropic would enter public markets with $900.9B in compute commitments through 2045, making those obligations a central factor for public investors assessing the durability of its revenue.

**「Community discussion」** Commenters split on the IPO&\#x27;s timing and moat: maerF0x0 argued that if Anthropic&\#x27;s models were capable of recursive self-improvement, VCs would have preferred to wait for clearer dominance rather than accept dilution now, while brainless and maupin contended that LLM workloads are easy to switch and that improving local models will compress demand for frontier APIs. irthomasthomas raised a separate valuation concern, suggesting the Series H could be underwater if the IPO prices at the low end of the cited range.

<details><summary>References</summary>
<ul>
<li><a href="https://www.techtimes.com/articles/329931/20261103/anthropic-ipo-filing-shows-revenue-growth-slowing-investors-cut-target-valuation.htm">Anthropic IPO Filing Shows Revenue Growth Slowing as ...</a></li>
<li><a href="https://www.forbes.com/sites/zacharyfolk/2026/11/02/anthropic-hit-17-billion-in-third-quarter-revenue-ahead-of-ipo-but-ai-spending-commitments-hit-900-billion/">Anthropic Hit $17 Billion In Third Quarter Revenue Ahead Of ...</a></li>

</ul>
</details>

**Tags**: `#Anthropic`, `#IPO`, `#AI industry`, `#LLM business models`, `#Hacker News`

---

<a id="item-tech-news-7"></a>
### [UMAP 0.6 adds faster initialization and opt-in optimizers](https://www.reddit.com/r/MachineLearning/comments/1xudaah/umap_06_new_initialization_new_optimizers_and/) ⭐️ 8.0/10

UMAP 0.6 is available via \`pip install -U umap-learn\` and conda-forge; the author reports ~4x faster nearest-neighbor search, a new recursive initialization, and new optimizers that make a seeded run reproducible while using every core. On 3 million arXiv papers, the author says UMAP 0.6 finishes in under 5 minutes, whereas a seeded 0.5 run took 52 minutes single-threaded—12x longer. The release also claims better quality at million scale, with finer cluster structure resolved in fewer epochs and better neighborhood accuracy than 0.5. The new initialization and optimizers are opt-in through \`compatibility\_layout=False\` because they change the output, and the author plans to make them defaults in future versions.

reddit · r/MachineLearning · /u/lmcinnes · Nov 12, 13:51

**「Background」** UMAP is a nonlinear dimensionality-reduction library that embeds high-dimensional data by initializing a low-dimensional layout and then refining it with an attraction-repulsion optimizer. Earlier releases used spectral initialization or PCA for that starting layout; the source describes those starts as “messy blurs” and says a seeded UMAP 0.5 run was single-threaded.

**「Impact」** Because opting in changes embeddings, users should revalidate downstream clustering, visualization, or model inputs before replacing 0.5 in production; the new path is not yet the default.

**Tags**: `#UMAP`, `#dimensionality reduction`, `#open source`, `#performance optimization`, `#nearest neighbor search`

---

<a id="item-tech-news-8"></a>
### [US Commerce finalizing rule to block Chinese AI firms&\#x27; remote chip access](https://www.theinformation.com/articles/commerce-department-finalizing-long-awaited-ai-remote-access-rule) ⭐️ 8.0/10

The U.S. Commerce Department is reportedly finalizing a rule that would block Chinese AI companies from remotely using advanced AI chips through overseas data centers, with publication possible as soon as this month. According to The Information, the controls would extend existing semiconductor export restrictions to seven countries, including Malaysia, Singapore and Thailand, to close remote-access and chip-smuggling gaps. The rule is still being coordinated with other government agencies and is not final. Nvidia reportedly lobbied against closing the remote-access gap, arguing that U.S. AI infrastructure needs to prevail globally.

telegram · zaihuapd · Nov 12, 03:42

**「Background」** Existing U.S. semiconductor export controls restrict sales of advanced AI chips to China, so attention has shifted to the workaround of renting compute in third countries; reporting has described Chinese AI firms reaching restricted chips through data centers in Singapore and Malaysia. Regional enforcement has been tightening in parallel: Malaysia introduced export controls on advanced U.S.-origin AI chips in June 2026, and its customs service has intercepted smuggled AI hardware shipments at Kuala Lumpur airport, including one valued at $12.1 million.

**「Who bears the compliance burden」** Chinese AI developers that rent GPU capacity in Malaysia, Singapore and Thailand would need to relocate those workloads or lose access once the rule is finalized, while data-center and cloud operators in those countries would become the enforcement chokepoint for remote access rather than only for hardware shipments. Export-control lawyers cited in earlier reporting say the cloud-access gap is difficult to police in practice \(tool-3-2\), so how much changes will depend on compliance duties that the draft text has not yet made public.

<details><summary>References</summary>
<ul>
<li><a href="https://aipolicydaily.org/archive/daily/2026-11-10/">Commerce chip probe went to DOJ | WH seeks... — AI Policy Daily</a></li>
<li><a href="https://factlen.com/news/malaysian-customs-seize-12-1-million-in-smuggled-ai-chips-at-kuala-lumpur-airpor-38681-96d95b54">Malaysian Customs Seize $12.1 Million in Smuggled AI Chips at</a></li>
<li><a href="https://www.cnbc.com/2026/08/19/china-ai-nvidia-chips-us-export-controls.html">China AI firms tap Nvidia power overseas as U.S ... - CNBC</a></li>
<li><a href="https://www.techtimes.com/articles/325957/20260829/commerce-drafts-ai-chip-rule-loophole-it-created-rescinding-biden-know-your-customer.htm">Commerce Drafts AI Chip Rule for Loophole It Created by ...</a></li>
<li><a href="https://www.nbcnews.com/tech/tech-news/nvidia-chips-loophole-export-ruleschinese-companies-access-megaspeed-rcna608601">How Chinese companies access Nvidia chips through a loophole ...</a></li>

</ul>
</details>

**Tags**: `#export controls`, `#AI chips`, `#US-China tech`, `#data centers`, `#semiconductor policy`

---

<a id="item-tech-news-9"></a>
### [Chips and Cheese interviews AMD&\#x27;s Mike Clark on Zen 6](https://chipsandcheese.com/p/talking-zen-6-with-mike-clark-at) ⭐️ 7.0/10

Chips and Cheese published an in-depth interview with AMD&\#x27;s Mike Clark covering the Zen 6 CPU architecture, dated 12 November 2026. The piece is a technical conversation with an AMD designer rather than a product announcement, and the source material available here does not include the architectural specifics, performance figures, core counts, or launch timing discussed in it. No claim about Zen 6 specifications or availability can be attributed from what is currently supplied. Readers should treat the article itself as the record of what Clark said.

hackernews · dverlaeckt80 · Nov 12, 14:12 · [Discussion](https://news.ycombinator.com/item?id=50467460)

**「Background」** Mike Clark is an AMD Zen chief architect, and Chips and Cheese previously interviewed him for a Zen 5 discussion; the video description for that earlier interview includes his correction that Zen 5 can issue two 128-bit or 256-bit stores but only one 512-bit store per cycle. That earlier exchange shows the outlet&\#x27;s access to cycle-level microarchitectural detail, which the new Zen 6 conversation builds on.

**「What Zen 6&\#x27;s dual variants mean for tuning」** AMD builds Zen 6 and Zen 6 c from the same ISA with the same IPC characteristics, differing in physical design style and how many cores fit in a complex, so teams tuning for EPYC &quot;Venice&quot; should not need a separate code path for the denser variant. Phoronix&\#x27;s testing found SMT remains worthwhile on both the 256-core EPYC 9996 and the 96-core high-frequency EPYC 9686F, making an enabled-SMT default the practical choice, while the reported MEXT behavior of roughly 95% performance at 50% DRAM capacity should be treated as a preliminary vendor claim rather than a measured guarantee.

**「Community Discussion」** One commenter described the article as interesting and noted that it is very rare to see CPU designers go into this level of depth. That is a reader&\#x27;s reaction to the interview&\#x27;s format, not an assessment of any Zen 6 detail.

<details><summary>References</summary>
<ul>
<li><a href="https://www.youtube.com/watch?v=8PubQh7WpBo">[36] 5min with AMD Zen Chief Architect , Mike Clark - YouTube</a></li>
<li><a href="https://www.youtube.com/watch?v=YoZ0hP9mkU4">Chips and Cheese Interviews Mike Clark | Interview #1 - YouTube</a></li>
<li><a href="https://www.tomshardware.com/pc-components/cpus/amd-zen-6-epyc-venice-deep-dive-and-benchmarking-dual-epyc-9996-with-1-024-threads-delivers-up-to-93-percent-performance-gain-gen-on-gen-9686f-outclasses-nvidias-vera">AMD Zen 6 EPYC ‘Venice’ deep dive and... | Tom&#x27;s Hardware</a></li>
<li><a href="https://www.phoronix.com/review/amd-epyc-zen6-smt">AMD Zen 6 SMT Proves Very Advantageous Even For 256... - Phoronix</a></li>
<li><a href="https://www.techpowerup.com/review/amd-zen-6-technical-deep-dive/5.html">AMD Zen 6 Technical Deep Dive - Cache Hierarchy... | TechPowerUp</a></li>

</ul>
</details>

**Tags**: `#CPU architecture`, `#AMD Zen 6`, `#semiconductor hardware`, `#technical interview`

---

<a id="item-tech-news-10"></a>
### [Microsoft 365 email outage runs eight hours as status page falters](https://status.cloud.microsoft/) ⭐️ 7.0/10

Microsoft 365 email was unavailable for many organizations during an outage that administrators reported stretching past eight hours, while Teams chat and meetings kept working. In a 9:02 PM UTC update, Microsoft said it had validated an alternative health check method on a subset of affected infrastructure, which allowed servers in that subset to return to service, and that it was applying the change more broadly while preparing an automated recovery process to detect and restart unresponsive servers. The submission is a status-page link plus news and Downdetector links, so the cause and full scope have not been published; one commenter noted the status page itself was loading poorly and that updates were arriving through Microsoft&\#x27;s RSS feed. Reported evidence points to a Microsoft 365-specific fault, with one admin saying their Azure infrastructure appeared unaffected.

hackernews · dkpk · Nov 12, 18:20 · [Discussion](https://news.ycombinator.com/item?id=50471731)

**「Background」** Microsoft 365 is Microsoft’s cloud suite for email, chat, meetings, and other productivity workloads, and Microsoft normally communicates incidents through its status page. In this event, users reported that the status page itself was not working well and that they relied on its RSS feed for periodic updates, while Teams chat and meetings continued to work even as email was unavailable.

**「Impact」** Organizations that depend on Exchange Online mailboxes had to route urgent communication through Teams or other channels while email stayed down, and administrators checking for progress could not rely on the status page alone — subscribing to Microsoft&\#x27;s RSS feed was one workaround reported in the thread.

**「Community discussion」** One commenter attributed the outage to reliability neglect across Microsoft products, citing GitHub, Xbox, Azure, Entra and Intune as evidence — an opinion rather than a verified cause. Administrators described firsthand effects: one said email for more than 15,000 employees was still down at hour eight and called it worse than the usual US-East-1 issues, while another said their organization had not seen a worse 365 outage since adopting M365 in 2019.

**Tags**: `#Microsoft 365`, `#cloud outage`, `#service reliability`, `#enterprise email`, `#incident response`

---

<a id="item-tech-news-11"></a>
### [Independent TRIBE v2 audit reports no retinotopy or tonotopy, but MT+ motion](https://www.reddit.com/r/MachineLearning/comments/1xuillf/does_metas_brainresponse_model_tribe_v2_actually/) ⭐️ 7.0/10

A self-funded Reddit audit reports that Meta&\#x27;s TRIBE v2, which predicts fMRI responses from video, audio, and text, does not recover classic retinotopic or tonotopic maps: the author reports d=0.05 \(n.s.\) for retinotopy and ρ=-0.07 \(n.s.\) for tonotopy even with loudness controlled. The same tests found sharp motion selectivity in MT+ \(d=4.31, 52× enrichment over chance\). The author says eccentricity became significant and “correct” only under three stimulus-geometry controls, suggesting an image-statistics confound rather than a true positional code; the results come from a single solo, non-peer-reviewed project and have not been independently verified.

reddit · r/MachineLearning · /u/Own\_Tank1283 · Nov 12, 17:16

**「Background」** TRIBE v2 is Meta&\#x27;s multimodal foundation model that predicts high-resolution human fMRI activity from video, audio, or language, according to a report on its release \[tool-2-1\]. The audit targets a design detail in the model&\#x27;s methods: video features are spatially averaged before prediction, an operation that would discard the position information that retinotopic and tonotopic maps are built on.

**「Impact」** Researchers evaluating TRIBE v2 should not treat its MT+ motion selectivity as evidence that it preserves topographic position information; tests of retinotopy, tonotopy, or eccentricity need stimulus-geometry controls to rule out image-statistics confounds.

<details><summary>References</summary>
<ul>
<li><a href="https://www.builderhustle.com/p/meta-tribe-v2-iphone-fold-ai-gym-hacker-youtube-partner">Meta TRIBE v 2 , iPhone Fold Rumors, AI Gym Hacker &amp; YouTube...</a></li>

</ul>
</details>

**Tags**: `#fMRI`, `#model evaluation`, `#retinotopy`, `#TRIBE v2`, `#confounds`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Nvidia&\#x27;s Jensen Huang resigns amid spy-allegation scrutiny](https://www.cnbc.com/2026/11/13/jensen-huang-nvidia-us-china-relations.html) ⭐️ 7.0/10

Nvidia&\#x27;s Jensen Huang resigned Thursday and agreed to testify before Congress by Nov. 26 amid scrutiny of an alleged affair with a woman reports say U.S. intelligence believes was recruited by China&\#x27;s Ministry of State Security; Beijing calls the spy allegation an unfounded smear. Analysts predict Congress could tighten semiconductor export controls before year-end, though no policy change has been confirmed.

rss · CNBC Finance · Nov 13, 02:56

**「Background」** Washington began restricting Nvidia&\#x27;s advanced chip sales to China in 2022, the Trump administration eased many Biden-era limits in 2025, and Huang had argued U.S. technology needed to be used in China to remain globally relevant.

**「Impact」** If Congress tightens export rules, Nvidia and other U.S. chipmakers could lose more Chinese sales, and Beijing could retaliate by restricting rare-earth or chipmaking-material supplies, analysts warn.

**Tags**: `#U.S.-China relations`, `#Nvidia`, `#export controls`, `#semiconductors`, `#geopolitical risk`

---

<a id="item-finance-news-2"></a>
### [China Approves Eli Lilly’s Oral Weight-Loss Drug, Its First Oral GLP-1](https://www.reuters.com/business/healthcare-pharmaceuticals/china-approves-eli-lillys-weight-loss-pill-orforglipron-2026-11-12/) ⭐️ 7.0/10

China’s drug regulator approved Eli Lilly’s once-daily oral GLP-1 weight-loss drug, orforglipron calcium tablets \(brand name Muoyouda\), on November 12 as a Class 1 new drug for adults who are obese or overweight with at least one weight-related comorbidity. It is the country’s first approved oral GLP-1 for weight loss; Lilly has not disclosed pricing or launch timing, and a Type 2 diabetes indication is still under review.

telegram · zaihuapd · Nov 12, 10:09

**「Background」** GLP-1 drugs mimic a gut hormone that curbs appetite, but the earlier versions are peptides that break down in the digestive tract, so they are given by injection. Orforglipron is a non-peptide molecule designed to be swallowed, which is why its approval makes it China&\#x27;s first oral option in this class.

**「Market impact」** The approval gives Chinese patients a once-daily oral alternative to weekly injections and clears Eli Lilly to compete in a GLP-1 obesity market that China Daily says is bracing for a shake-up after semaglutide’s March patent expiry opened the door to domestic generics competing for tens of billions of yuan.

<details><summary>References</summary>
<ul>
<li><a href="https://pmc.ncbi.nlm.nih.gov/articles/PMC12898445/">Orforglipron: A Comprehensive Review of an Oral Small ...</a></li>
<li><a href="https://global.chinadaily.com.cn/a/202604/02/WS69ce1a08a310d6866eb416e6.html">Price war looms in China&#x27;s booming weight-loss drug market</a></li>

</ul>
</details>

**Tags**: `#pharma`, `#regulatory approval`, `#GLP-1`, `#China`, `#Eli Lilly`

---