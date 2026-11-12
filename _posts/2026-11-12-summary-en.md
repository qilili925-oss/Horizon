---
layout: default
title: "Horizon Summary: 2026-11-12 (EN)"
date: 2026-11-12
lang: en
---

> From 52 items, 11 important content pieces were selected

---

**Technology News**
1. [Using Voltage Glitching to Unlock A100 in a Mining Card](#item-tech-news-1) ⭐️ 8.0/10
2. [AWS releases official aws-emulator, a Rust local AWS clone built by agent swarm](#item-tech-news-2) ⭐️ 8.0/10
3. [False smoke alarm nearly took Jane Street&\#x27;s NYC datacenter down](#item-tech-news-3) ⭐️ 7.0/10
4. [Python community mourns Tim Peters, author of the Zen of Python](#item-tech-news-4) ⭐️ 7.0/10
5. [Can a Linear Program Do Weight-Space Programming?](#item-tech-news-5) ⭐️ 7.0/10
6. [Google launches Gemini Decisions API with multimodal inputs and free output](#item-tech-news-6) ⭐️ 7.0/10
7. [Anthropic&\#x27;s IPO roadshow video details four-chip Claude strategy](#item-tech-news-7) ⭐️ 7.0/10
8. [ByteDance reportedly preps Muse-like AI agent, targets OpenAI parity by 2030](#item-tech-news-8) ⭐️ 7.0/10
9. [Report alleges 240,000 Nvidia H100/H200 chips diverted to China](#item-tech-news-9) ⭐️ 7.0/10

**Financial News**
1. [Goolsbee calls October inflation report &\#x27;borderline disturbing&\#x27; as Fed weighs more rate hikes](#item-finance-news-1) ⭐️ 8.0/10
2. [China&\#x27;s offshore trust tax transition ends with over 160 billion yuan declared](#item-finance-news-2) ⭐️ 8.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Using Voltage Glitching to Unlock A100 in a Mining Card](https://blog.kate.land/posts/using-voltage-glitching-to-unlock-the-a100/) ⭐️ 8.0/10

A technical blog post documents a hands-on voltage-glitching attempt to unlock A100-class capabilities in a mining card, focusing on defeating fuse-based locks that keep disabled hardware inactive. The write-up is an individual hardware-hacking account, not a vendor-supported modification or an independently verified result. Commenters identify the card as the 8GB model and debate whether the disabled features reflect market segmentation or chips that failed datacenter-grade fabrication.

hackernews · lae · Nov 11, 10:48 · [Discussion](https://news.ycombinator.com/item?id=50451903)

**「Background」** Nvidia’s CMP 170HX is a GA100-based mining card whose memory and SM counts are restricted by on-die fuses rather than only by software. The blog’s method is voltage fault injection: disturbing the chip’s power delivery so those fuse restrictions can be overridden at the hardware level. The post reports turning an 8GB CMP 170HX into what the author calls effectively an A100-80G by unlocking hidden memory and compute units.

**「Impact」** For CMP 170HX owners, the practical consequence is a one-way risk: the described method relies on blowing fuses and power-cycling the host, so a failed attempt can leave the card permanently unusable rather than merely locked. Anyone buying a card specifically to attempt the unlock now faces a worse bet, since reports cited alongside the listings describe 170HX prices rising from roughly $100 to over $1,000 following earlier unlock reports, and the extra HBM2e on the 10 GB variant has reportedly been reachable only through slow CPU-side copies rather than CUDA.

**「Community Discussion」** Commenters report mixed experiences: one has spent two weeks trying to unlock 80 GB on a CMP 170HX through software and considers the fuse-blowing route much riskier, while another questions whether the disabled hardware exists because of fabrication faults rather than deliberate segmentation. A separate commenter suggests an external PCIe riser with its own power supply, letting the host stay running while only the target card is power-cycled instead of putting the host into ACPI S3.

<details><summary>References</summary>
<ul>
<li><a href="https://news.lavx.hu/article/kate-uses-voltage-glitching-to-turn-a-cmp-170hx-mining-card-into-an-a100-class-gpu">Kate uses voltage glitching to turn a CMP 170HX mining card ...</a></li>
<li><a href="https://sitem.co/public/summary/7050/voltage-glitching-unlocks-nvidia-ga100-die-transforming-cmp-170hx-mining-cards-into-high-performance-a100-equivalents">Voltage Glitching Unlocks NVIDIA GA100 Die: Transforming CMP ...</a></li>
<li><a href="https://blog.kate.land/posts/using-voltage-glitching-to-unlock-the-a100/">Using voltage glitching to unleash the A100 in my mining card</a></li>
<li><a href="https://www.ebay.com/itm/276736911721">Used NVIDIA CMP 170HX 8GB Card GPU 164MH/s - eBay Cmp 170hx for sale | eBay Nvidia Cmp 170 Hx for sale - eBay Where to Buy a CMP 170HX | amoghmunikote/170th-Street | DeepWiki NVIDIA CMP 170HX 8/10 GB Prices Explode From $100 to Over ... NVIDIA CMP 170HX Prices Surge Past $1,000 After Tool Unlocks ...</a></li>

</ul>
</details>

**Tags**: `#voltage glitching`, `#GPU hardware hacking`, `#NVIDIA A100`, `#hardware security`, `#mining cards`

---

<a id="item-tech-news-2"></a>
### [AWS releases official aws-emulator, a Rust local AWS clone built by agent swarm](https://simonwillison.net/2026/Nov/11/aws-emulator/) ⭐️ 8.0/10

AWS has published aws-emulator, an official emulator that runs local clones of its services so tests can run without provisioning a paid API key. It is written in Rust and, per the project&\#x27;s account, was produced by a swarm of AI agents that landed 29,684 commits in the first three weeks; Swaminathan Sivasubramanian describes how it came about in a guest post on Werner Vogels&\#x27; blog. On macOS and Windows the emulator currently requires Docker, and Simon Willison writes that he would prefer a single downloadable binary usable in standard test suites on other platforms.

rss · Simon Willison · Nov 11, 21:18

**「Context」** Testing code against AWS services has generally required either provisioning real credentials in a paid account or depending on third-party emulators that track AWS APIs on their own schedule. The aws-emulator is AWS&\#x27;s own first-party alternative: a Rust implementation that, according to the source, lets tests run against local clones of its services without a provisioned API key.

**「Testing vs. security validation」** Teams can now exercise S3, Lambda, DynamoDB and other services locally without provisioning a paid API key, but AWS explicitly scopes the emulator to building and testing, not production workloads or security testing. Its documented gaps are concrete: it never denies a request signed with its own key, and it does not check KMS key policies or S3 bucket policies, so any IAM or permissions-boundary assumptions still need verification against real AWS. On macOS and Windows it also requires Docker, which complicates dropping it into a plain test suite.

**「Community discussion」** One commenter questioned whether the emulator is a maintained product rather than an internal exercise, saying Floci and Testcontainers already cover the need, while another quoted the project&\#x27;s security page, which warns against using the emulator to test IAM policies and permissions boundaries, resource-based policies such as bucket policies, KMS key policies, cross-account or cross-region access, or any other security control. Others argued that work on this scale across AWS&\#x27;s many services would not have been attempted without AI agents, regardless of the language chosen.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/aws/aws-emulator">GitHub - aws / aws - emulator : AWS Emulator is a local emulator of the...</a></li>
<li><a href="https://news.ycombinator.com/item?id=50456631">AWS emulator | Hacker News</a></li>

</ul>
</details>

**Tags**: `#aws`, `#cloud-emulation`, `#local-testing`, `#ai-agents`, `#rust`

---

<a id="item-tech-news-3"></a>
### [False smoke alarm nearly took Jane Street&\#x27;s NYC datacenter down](https://michael.bacarella.com/2026/11/10/false-smoke-alarm-jane-street-datacenter/) ⭐️ 7.0/10

A first-person postmortem recounts how a false smoke alarm at Jane Street&\#x27;s only New York City datacenter set off an incident that nearly took the facility offline. The account centers on emergency response and datacenter design around smoke alarms and power-off systems. It is an anecdotal operator narrative, not a vendor announcement or an independently measured failure.

hackernews · mbac32768 · Nov 11, 16:38 · [Discussion](https://news.ycombinator.com/item?id=50455394)

**「Background」** In a data hall, smoke detection is typically wired to shut down the CRAC units so they do not recirculate smoke, which leaves an enclosed, densely packed room heating up with no cooling. The account describes that chain directly: dust from contractors tripped an alarm, the cooling stopped, and the engineer raced to pull power cords before temperatures passed 150 °F and the sprinkler heads discharged, after which he wrote a small OCaml monitor that averages server onboard temperatures every minute and alerts on a fleet-wide rise.

**「Community discussion」** Commenters debate whether the facility should have had a physical emergency power-off button and a smoke-alarm interlink; one practitioner says the data halls they design deliberately do not shut down CRAC units on smoke detection, citing International Mechanical Code allowances for single-space air handlers over 2,000 cfm. Others share emergency-response anecdotes, including hauling diesel during Hurricane Sandy.

<details><summary>References</summary>
<ul>
<li><a href="https://michael.bacarella.com/2026/11/10/false-smoke-alarm-jane-street-datacenter/">How a false smoke alarm almost drowned Jane Street’s only NYC ...</a></li>
<li><a href="https://proomt.com/item/how-a-false-smoke-alarm-almost-drowned-jane-street-s-only-nyc-datacenter-37986aa2-b738-4757-9fd0-3cd51ca264bb">How a false smoke alarm almost drowned Jane Street&#x27;s only NYC ...</a></li>

</ul>
</details>

**Tags**: `#datacenter operations`, `#incident response`, `#infrastructure reliability`, `#fire suppression`

---

<a id="item-tech-news-4"></a>
### [Python community mourns Tim Peters, author of the Zen of Python](https://discuss.python.org/t/in-memoriam-tim-peters-1952-2026/110028) ⭐️ 7.0/10

The Python community is mourning Tim Peters, the long-time contributor whose death was announced in a Python Discourse memorial thread; the thread identifies him as 1952–2026. Commenters highlighted his authorship of the Zen of Python, which is displayed by Python&\#x27;s \`import this\`, and his involvement in projects including SpamBayes and the Python Cookbook. The linked notice itself is brief and does not provide technical details about his death.

hackernews · ayhanfuat · Nov 11, 07:03 · [Discussion](https://news.ycombinator.com/item?id=50450488)

**「Context」** Tim Peters was a Python core developer whose best-known contributions include the Zen of Python — the aphorisms printed by \`import this\` — and Timsort, the sorting algorithm he designed and implemented, which underlies Python&\#x27;s built-in sorting. Guido van Rossum announced the death on the Python discussion forum on November 11, 2026, noting that Peters had died earlier that year, on July 15.

**「Community Discussion」** Commenters recalled Peters as “Uncle Timmy” and described learning from his comp.lang.python posts and Python Cookbook contributions, while others credited him with helping turn the “A Plan for Spam” essay into the SpamBayes program, alongside Gary Robinson and Robert Woodhead. These are personal recollections and credit attributions from the discussion, not independently verified details in the linked notice.

<details><summary>References</summary>
<ul>
<li><a href="https://discuss.python.org/t/in-memoriam-tim-peters-1952-2026/110028">In Memoriam: Tim Peters 1952–2026 - Core Development ...</a></li>
<li><a href="https://grokipedia.com/page/Tim_Peters_%28software_engineer%29">Tim Peters (software engineer) — Grokipedia</a></li>

</ul>
</details>

**Tags**: `#Python`, `#open source`, `#software engineering`, `#community`, `#obituary`

---

<a id="item-tech-news-5"></a>
### [Can a Linear Program Do Weight-Space Programming?](https://nathan.rs/posts/weight-space-lp/) ⭐️ 7.0/10

A blog post on nathan.rs argues that linear programming can be used to find sparse, constraint-based edits to language-model weights by treating behavior changes as linear constraints over weight directions. The post is aimed at researchers and practitioners interested in direct weight editing, but the supplied material contains no independent validation or evidence of broad adoption. It is a personal technical analysis, not a shipped tool or peer-reviewed result.

hackernews · emschwartz · Nov 11, 12:30 · [Discussion](https://news.ycombinator.com/item?id=50452655)

**「Background」** Weight-space editing changes a model&\#x27;s behaviour by modifying a small subset of its parameters instead of fine-tuning on new data. The immediate backdrop is the &quot;Astra&quot; line of experiments in which an LLM edits Qwen weights without gradients: one Hugging Face write-up documents a behaviour edit confined to a single matrix — the last-layer MLP \`down\_proj\`, 89.1M weights, or 0.32% of the model — whose values shifted by 1.4%, while a separate critique argues that the framing of a model &quot;reading and writing weights&quot; is misleading. The LP argument reframes that kind of edit as a constrained optimisation problem rather than an ad-hoc prompted operation.

**「Impact」** If the reformulation holds, developers can derive sparse weight edits by stating constraints to an LP solver instead of hand-tuning search: the write-up reports its linear program matches the original edit on MATH-500, GSM8K and IFEval while changing 8× fewer weights and solving in about a minute. The demonstrated case is a single 0.8B-parameter Qwen3.5 model, so scaling to larger models and multi-variable reward constraints remains untested.

**「Community discussion」** Commenters treated the idea as a potentially useful tool for weight editing: jsw97 suggested LP solvers could guide edits by expressing behaviors to eliminate or preserve as constraints, while dansitu argued the approach should be applied during training through regularization. mirekrusin proposed using it for weight-space distillation, collecting paired examples, discovering behavioral directions, and solving for sparse edits to improve a target behavior while limiting unwanted changes.

<details><summary>References</summary>
<ul>
<li><a href="https://huggingface.co/jarrodwatts/Qwen3.8-27B-Astra-Stop">jarrodwatts/ Qwen 3.8-27B- Astra -Stop · Hugging Face</a></li>
<li><a href="https://honnibal.dev/blog/astra-read-write-misleading">The &#x27; Astra can read and write weights to improve Qwen &#x27; post is...</a></li>
<li><a href="https://nathan.rs/posts/weight-space-lp/">Can a Linear Program Do Weight-Space Programming? - nathan.rs</a></li>
<li><a href="https://proomt.com/item/can-a-linear-program-do-weight-space-programming-d1a13007-a589-44d0-b87e-067ea543171c">Can a Linear Program Do Weight-Space Programming? · proomt</a></li>

</ul>
</details>

**Tags**: `#machine-learning`, `#weight-editing`, `#linear-programming`, `#llm`, `#model-interpretability`

---

<a id="item-tech-news-6"></a>
### [Google launches Gemini Decisions API with multimodal inputs and free output](https://simonwillison.net/2026/Nov/11/gemini-decisions-api/) ⭐️ 7.0/10

Google has released the Gemini Decisions API, built on a model called Gemini Decision 1, entering a decision-model category already occupied by Jev and OpenAI&\#x27;s GPT-6 Luna decision model. Like Jev, it handles yes/no questions \(which Google calls &quot;Noul&quot;\), multiple-choice questions, and rubric scoring; unlike Jev&\#x27;s text-only and OpenAI&\#x27;s text-and-image support, Gemini accepts text, images, audio, video, and PDFs. It is priced at 10 cents per million input tokens with free output — matching GPT-6 Luna and above Jev&\#x27;s 4.2 cents per million. In Simon Willison&\#x27;s video test, Gemini returned graded probabilities \(about 0.923 for both &quot;robot&quot; and &quot;USA&quot;\) where Jev and OpenAI return 1.0 or 0.0.

rss · Simon Willison · Nov 11, 22:03

**「Background」** The category Google is entering consists of APIs built to answer closed-ended questions—yes/no, multiple-choice, or rubric scores—rather than generate free-form text. Jev and OpenAI&\#x27;s GPT-6 Luna decision model were already competing in that category, and Gemini Decision 1 adopts Jev&\#x27;s three question types and even its “Noul” label for yes/no prompts, according to the source.

**「Impact」** Developers gain a way to put closed-ended questions directly to video, audio, and PDF inputs, a capability neither Jev nor OpenAI&\#x27;s decision model offered in Willison&\#x27;s comparison. Teams comparing or switching providers should account for Gemini returning graded probabilities rather than the 1.0/0.0 values Jev and OpenAI produce, so fixed-threshold logic needs adjusting.

**Tags**: `#Gemini`, `#API`, `#decision models`, `#multimodal AI`, `#AI pricing`

---

<a id="item-tech-news-7"></a>
### [Anthropic&\#x27;s IPO roadshow video details four-chip Claude strategy](https://simonwillison.net/2026/Nov/11/anthropic-ipo-roadshow/) ⭐️ 7.0/10

Anthropic&\#x27;s IPO roadshow video disclosed that the company trains and serves Claude across four major chip families—AWS Trainium, Google TPUs, NVIDIA GPUs and AMD GPUs—according to co-founder Tom Brown, and Simon Willison published an extracted transcript because no official one was available. Brown said Anthropic began working with AMD GPUs this year and that a system called Mythos got Claude running on AMD in three days with almost no human intervention, writing nearly all of the kernels; he said new chip platforms previously took dozens of engineers months. He also described &quot;compute multipliers&quot; as stacking gains in total effective compute and said Anthropic believes Claude could eventually discover them autonomously as it approaches recursive self-improvement. These are claims from the roadshow presentation, not independently measured results.

rss · Simon Willison · Nov 11, 15:11

**「Background」** Anthropic had already signaled that it runs Claude across more than one accelerator family: a September postmortem of three recent issues described bugs that affected only its TPU deployments. That detail matters because each chip family needs its own tailored software and inference stack, making multi-chip support costly to build and maintain at scale.

**「Impact」** Because each chip family needs its own tailored software and inference stack, Anthropic&\#x27;s four-chip approach creates chip-specific operational risk alongside capacity flexibility; the post notes that Anthropic&\#x27;s September postmortem described bugs that affected only its TPU deployments. Customers assessing Claude should therefore watch for chip-specific incidents or performance differences rather than assuming a workload behaves identically across Trainium, TPUs, Nvidia and AMD.

**Tags**: `#Anthropic`, `#AI infrastructure`, `#AI chips`, `#IPO`

---

<a id="item-tech-news-8"></a>
### [ByteDance reportedly preps Muse-like AI agent, targets OpenAI parity by 2030](https://www.bloomberg.com/news/articles/2026-11-11/bytedance-prepares-muse-like-agent-in-push-to-close-ai-gap) ⭐️ 7.0/10

ByteDance is reportedly preparing a Muse-like AI assistant for release within weeks, according to Bloomberg-originated reporting, as part of an effort to defend its lead in AI video. Co-founder Zhang Yiming told an internal all-hands that reaching frontier parity with Anthropic and OpenAI would take until at least 2029 or 2030, and the company plans to invest up to $70 billion in its Seedance video AI platform. The report says ByteDance does not favor relying on model distillation, but it provides no technical details, model names, pricing, or independent verification.

telegram · zaihuapd · Nov 11, 12:31

**「What Meta&\#x27;s Muse is」** ByteDance&\#x27;s plan is framed around Meta&\#x27;s Muse, which Meta introduced in September 2026 as a &quot;personal AI agent&quot; that goes beyond answering questions to take on tasks and projects, and that remembers a user&\#x27;s context across conversations. Meta&\#x27;s version also browses the web and can make purchases, with the company saying it was the first AI agent covered by its purchase protections.

**「Impact」** For developers and enterprise buyers, the immediate consequence is uncertainty: the report gives no model, API, pricing, or availability details beyond a release expected within weeks, so integration and compatibility planning should wait for an official announcement.

<details><summary>References</summary>
<ul>
<li><a href="https://about.fb.com/news/2026/09/introducing-muse-personal-ai-agent/">Introducing Muse : The World’s First Personal AI Agent Built for...</a></li>
<li><a href="https://www.vktr.com/ai-platforms/meta-launches-muse-a-personal-ai-agent-that-browses-the-web-makes-purchases/">Meta Launches Muse , a Personal AI Agent That Browses the Web...</a></li>

</ul>
</details>

**Tags**: `#AI industry`, `#ByteDance`, `#AI agents`, `#frontier model competition`, `#video generation`

---

<a id="item-tech-news-9"></a>
### [Report alleges 240,000 Nvidia H100/H200 chips diverted to China](https://www.tomshardware.com/tech-industry/policy/alice-huang-reportedly-instrumental-in-securing-over-usd7-5-billion-of-nvidia-ai-gpu-imports-during-three-year-relationship-with-jensen-huang-helped-move-240-000-banned-chips-into-china-mostly-h100-and-h200) ⭐️ 7.0/10

An investigation by The Information, summarized in a secondary report, alleges that Alice Huang \(黄乐\) helped move roughly 240,000 banned Nvidia AI GPUs into China, mostly H100 and H200 parts, in transactions worth about $7.5 billion. The report ties the alleged shipments to her relationship with Nvidia CEO Jensen Huang and names companies including Shanghai Century Litong and Singapore&\#x27;s Megaspeed as involved intermediaries. The figures come from the investigation as relayed in the summary rather than from company disclosures, court findings, or independent measurement, and neither Nvidia nor the named companies are reported to have confirmed the allegations.

telegram · zaihuapd · Nov 11, 14:41

**「Background」** US export controls restrict sales of Nvidia&\#x27;s top data-center accelerators — including the H100, H200 and A100 — to China, so a large flow of those parts into the country implies diversion rather than authorized sales. Alice Huang, who is not related to Nvidia CEO Jensen Huang, previously held a senior position at Singapore-based Megaspeed International, one of the companies named in the reported network.

**「Impact」** The allegation points enforcement attention at intermediaries — resellers and Singapore-based cloud or channel companies — rather than only at end users, so firms handling Nvidia H100/H200 inventory face pressure to document where chips are ultimately deployed. Buyers and partners of the named companies would need to verify chain-of-custody records, since the report&\#x27;s figures are allegations that have not been confirmed by the companies or by regulators.

<details><summary>References</summary>
<ul>
<li><a href="https://invezz.com/news/2026/11/10/nvidia-stock-slides-6-as-chip-probe-puts-jensen-huang-under-pressure/">Nvidia stock slides 6% as chip probe puts Jensen Huang under pressure</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#AI chips`, `#export controls`, `#China`, `#semiconductor industry`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Goolsbee calls October inflation report &\#x27;borderline disturbing&\#x27; as Fed weighs more rate hikes](https://www.cnbc.com/2026/11/11/goolsbee-october-inflation-fed-rates-disturbing-distressing.html) ⭐️ 8.0/10

Chicago Fed President Austan Goolsbee called October’s inflation report “borderline disturbing” after consumer prices rose 0.4% from the prior month on a seasonally adjusted basis—the third straight month of outsized increases—as several Fed officials signaled another rate increase may be needed in December.

rss · CNBC Finance · Nov 11, 16:49

**「Background」** The Fed had raised its benchmark rate by a quarter-percentage point in September to a 3.75%-4% range and left it unchanged in October; it typically moves in quarter-point steps.

**「Impact」** Fed funds futures now unanimously expect a December rate increase, with 15% odds of a half-point move, according to CME’s FedWatch tool.

**Tags**: `#Federal Reserve`, `#inflation`, `#interest rates`, `#monetary policy`, `#CPI`

---

<a id="item-finance-news-2"></a>
### [China&\#x27;s offshore trust tax transition ends with over 160 billion yuan declared](https://www.news.cn/20261111/9bcce99c779b4a6197ff45bbbc3e4c50/c.html) ⭐️ 8.0/10

China&\#x27;s State Taxation Administration said on Nov. 11 that the 90-day transition period for taxing offshore trust income has ended, with more than 160 billion yuan in individual income tax declared and over 120 billion yuan paid in October, which it said drove a nearly 90% rise in national individual income tax revenue that month.

telegram · zaihuapd · Nov 11, 10:35

**「Background」** The 90-day window came from a July 24, 2026 joint notice by the finance ministry and tax administration: residents could declare offshore trust income earned before Jan. 1, 2026 as interest, dividend, or bonus income without late fees if they paid by Oct. 22.

**「Impact」** People with undeclared or underreported offshore trust income face back-tax demands, late-payment charges and possible audits, the administration said.

<details><summary>References</summary>
<ul>
<li><a href="https://t.me/zaihuapd/45068">在花 科技圈 – Telegram</a></li>
<li><a href="https://news.creaders.net/china/2026/10/20/3060337.html">截止前三 天 ，北京突然又打了6 个 补丁！ -中国瞭望-万维读者网（电脑版）</a></li>
<li><a href="https://www.giffordchen.com/blog/chinapersonalincometaxontrust2026">重磅消息：關於離 岸 信 託個 人 所 得 稅有關事項 - 信 託</a></li>

</ul>
</details>

**Tags**: `#离岸信托`, `#个人所得税`, `#税收征管`, `#财税政策`, `#中国`

---