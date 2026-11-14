---
layout: default
title: "Horizon Summary: 2026-11-14 (EN)"
date: 2026-11-14
lang: en
---

> From 40 items, 7 important content pieces were selected

---

**Technology News**
1. [TorchTitan trains ~1T-parameter MoE at 1,300 tokens/s per GPU on 384 GH200s](#item-tech-news-1) ⭐️ 8.0/10
2. [FAA ground stop halts US departures amid reported telecom outage](#item-tech-news-2) ⭐️ 7.0/10
3. [Microsoft Outlook, Teams, Copilot Hit by 12-Hour Global Outage](#item-tech-news-3) ⭐️ 7.0/10
4. [DeepSeek Opens Suite API for Search, Files, OCR and Speech](#item-tech-news-4) ⭐️ 7.0/10
5. [OpenAI launches ChatGPT Wallet for tokenized agent payments](#item-tech-news-5) ⭐️ 7.0/10

**Financial News**
1. [Lutnick faces Nvidia scrutiny as sons&\#x27; firm&\#x27;s reported stake falls](#item-finance-news-1) ⭐️ 7.0/10
2. [Chicago Fed&\#x27;s Goolsbee: central bank &\#x27;has definitely got work to do&\#x27; on inflation](#item-finance-news-2) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [TorchTitan trains ~1T-parameter MoE at 1,300 tokens/s per GPU on 384 GH200s](https://www.reddit.com/r/MachineLearning/comments/1xvce5h/scaling_to_1t_moe_on_torchtitan_p/) ⭐️ 8.0/10

A practitioner report describes training a ~1T-parameter mixture-of-experts model at about 1,300 tokens/s per GPU on 384 GH200 GPUs with TorchTitan, which the author says is 14x faster than their starting point. The setup used 384-way FSDP plus 4-way expert parallelism kept inside each node, and skipped pipeline parallelism to avoid long steps and slow debugging. Reported gains came from full activation checkpointing, offloading checkpoint activations to Grace, switching to Muon, FlexShard expert sharding, moving Newton-Schulz to the GPU, attention-cost load balancing, FP8 expert all-gather, a bf16 all-to-all with local fp32 summation, and fixing a CUDA allocator side-stream issue. These figures come from the author&\#x27;s account and linked blog posts, not an independent benchmark.

reddit · r/MachineLearning · /u/f14-bertolotti · Nov 13, 16:28

**「Background」** TorchTitan, the PyTorch distributed-training project the author worked with, already supports FSDP, which splits each parameter across ranks and gathers slices just before use, and expert parallelism, which assigns subsets of a mixture-of-experts model&\#x27;s experts to different GPUs and routes tokens to them. The report also explains why it avoided pipeline parallelism: hiding pipeline bubbles requires many microbatches, which lengthens steps and makes failures at scale slower to diagnose.

**「What practitioners can adopt now」** For teams running large MoE training on PyTorch/TorchTitan, the immediately usable pieces are the expert-wise FlexShard partitioning and the bf16 all-to-all gradient reduction, while the stream-placement fix that eliminated allocator retries still relies on FSDP2&\#x27;s private \`unshard\_async\_op\` flag until it becomes a public API — so reproducing the 13.5 GiB memory drop may mean pinning a specific TorchTitan build. PyTorch&\#x27;s own write-up confirms the same rise from 90 to ~1,300 tokens/s per GPU on 384 GH200s, but these numbers come from one 1T-parameter MoE configuration on JUPITER, so the communication-bound lessons apply most directly to clusters with comparable ~25 GB/s per-GPU inter-node bandwidth.

<details><summary>References</summary>
<ul>
<li><a href="https://pytorch.org/blog/training-a-1t-parameter-moe-on-eu-public-infrastructure-with-pytorch-and-torchtitan/">Training a 1T-Parameter MoE on EU public ... - PyTorch</a></li>
<li><a href="https://x.com/PyTorch/status/2120851611580785017">PyTorch on X: &quot;Thanks to PyTorch and TorchTitan, the Domyn ...</a></li>

</ul>
</details>

**Tags**: `#distributed-training`, `#mixture-of-experts`, `#PyTorch/TorchTitan`, `#GPU-optimization`, `#large-language-models`

---

<a id="item-tech-news-2"></a>
### [FAA ground stop halts US departures amid reported telecom outage](https://www.nbcnews.com/news/us-news/faa-orders-nationwide-ground-stop-departing-flights-reasons-safety-rcna609247) ⭐️ 7.0/10

The FAA issued a national ground stop on Nov. 13, 2026, halting departing flights across the United States, according to the submitted item. Official technical details were sparse: a Wall Street Journal report cited in the discussion said the disruption appeared to affect an L3Harris Technologies telecommunications network that carries radio frequencies used by air-traffic controllers to communicate with pilots, while it was unclear whether radar feeds were affected. A commenter citing The New York Times said the ground stop had been lifted, but the supplied material provides no confirmed cause or restoration details from the FAA.

hackernews · zulln · Nov 13, 21:05 · [Discussion](https://news.ycombinator.com/item?id=50489641)

**「Earlier Chicago halt」** The nationwide order followed an earlier FAA halt of traffic in Chicago due to air traffic control issues, according to ABC News. The FAA said the communication problems affected multiple Air Route Traffic Control Centers and that technicians were investigating.

**「Impact」** For airlines and passengers, the effect was immediate: a commenter tracking Los Angeles International Airport saw no departures from about 10:30 AM PST and later flights marked delayed or cancelled, while San Francisco International Airport&\#x27;s departures page was overloaded.

**「Community discussion」** Commenters emphasized how little official information was available, with one citing the WSJ report on L3Harris and another describing frozen or unusable airport departure boards. Others speculated—without supplied evidence—that the event was tied to a recently announced FAA AI/SMART rollout or to a Microsoft outage the previous day.

<details><summary>References</summary>
<ul>
<li><a href="https://www.faa.gov/newsroom/faa-statement-nationwide-ground-stop">FAA Statement on Nationwide Ground Stop | Federal Aviation ...</a></li>
<li><a href="https://www.abc.net.au/news/2026-11-14/follow-live-us-aviation-authority-grounds-all-flights/107385742">US aviation authority grounds all departing flights, citing...</a></li>

</ul>
</details>

**Tags**: `#FAA`, `#air traffic control`, `#critical infrastructure`, `#telecom outage`, `#aviation safety`

---

<a id="item-tech-news-3"></a>
### [Microsoft Outlook, Teams, Copilot Hit by 12-Hour Global Outage](https://www.reuters.com/technology/microsoft-365-outlook-down-thousands-us-users-downdetector-shows-2026-11-12/) ⭐️ 7.0/10

Microsoft Outlook, Teams, and Copilot remained down as of November 13 in an outage lasting more than 12 hours, disrupting enterprise and government communications worldwide. Microsoft attributed the failure to a server issue, said it found no evidence of malicious activity, and reported that it had widened remediation efforts and was seeing signs of stabilization. The source describes this as the second Microsoft 365 service disruption this year.

telegram · zaihuapd · Nov 13, 12:21

**「Background」** Microsoft 365 is Microsoft&\#x27;s cloud-delivered productivity suite, and Outlook, Teams, and Copilot depend on shared online infrastructure rather than software running only on each customer&\#x27;s machine. That architecture allows a server-side failure to affect many organizations at once; the report says this is the second Microsoft 365 disruption this year but does not identify the earlier one.

**「Operational Fallout」** Some government agencies in Australia, Japan, and the United States were affected, Euronext email traffic was disrupted, and financial institutions in Taiwan reportedly fell back to fax to confirm trades. For organizations that depend on Microsoft 365 for email and meetings, the outage forced temporary reliance on alternate channels while Microsoft&\#x27;s fix propagated.

**Tags**: `#Microsoft 365`, `#Outlook`, `#Teams`, `#service outage`, `#cloud reliability`

---

<a id="item-tech-news-4"></a>
### [DeepSeek Opens Suite API for Search, Files, OCR and Speech](https://mp.weixin.qq.com/s/78KBHc4-4N5b2vfL9SkutQ) ⭐️ 7.0/10

DeepSeek has opened what a Chinese tech aggregator describes as a full-suite application API: developers enable the relevant parameters in the existing API to get deep-thinking search, file input, link reading and speech inside conversations, with the server handling tool invocation and context stitching. The V4.1-Flash model is supported across three interfaces, and Search, Fetch, OCR, ASR and TTS can also be called individually. DeepSeek additionally open-sourced a front-end demo \(deepseek-ai/chat-demo\) that can import prior conversation history and lets users deploy the DeepSeek web experience locally via the API. The source is a brief aggregator post with no independent verification, and it gives no pricing, rate limits or latency details.

telegram · zaihuapd · Nov 13, 14:27

**「Background」** DeepSeek had already introduced V4.1-Flash, the model named in this API rollout, as the successor to V4-Pro: its notice said V4-Pro requests would route to V4.1-Flash at V4.1-Flash rates from 04:00 UTC on Sept 14, 2026, until V4.1-Pro launches.

**「Compatibility check for API builders」** Developers can add the chat, search, file, OCR, and speech capabilities by enabling parameters in existing DeepSeek API calls, leaving tool invocation and context assembly to the server. Teams using the Flash model should verify model identifiers: DeepSeek&\#x27;s API docs say the legacy deepseek-v4-flash and deepseek-v4-flash-vision-exp names remain accepted, but the underlying models are retired and requests are served by DeepSeek-V4.1-Flash-1017 at Flash pricing. The announcement does not list per-endpoint pricing or limits, so production users should confirm those before rollout.

<details><summary>References</summary>
<ul>
<li><a href="https://www.deepseek.com/en/news/deepseek-v4-1-flash/">DeepSeek | Introducing DeepSeek-V4.1-Flash: smarter, faster ...</a></li>
<li><a href="https://api-docs.deepseek.com/quick_start/pricing/?article_id=article_1779470751466_8">Models &amp; Pricing | DeepSeek API Docs</a></li>

</ul>
</details>

**Tags**: `#DeepSeek`, `#API`, `#multimodal AI`, `#open source`, `#AI developer tools`

---

<a id="item-tech-news-5"></a>
### [OpenAI launches ChatGPT Wallet for tokenized agent payments](https://openai.com/index/introducing-chatgpt-wallet/) ⭐️ 7.0/10

OpenAI launched ChatGPT Wallet with American Express, Mastercard, and Visa, letting AI agents make purchases without accessing users&\#x27; real card numbers. Each transaction requires the user to review the item and amount and confirm with Face ID or fingerprint, while the payment networks issue a token that replaces the real card number. The feature is available starting today in the US to ChatGPT Pro subscribers aged 18 and older using US-issued cards.

telegram · zaihuapd · Nov 13, 15:43

**「Background」** Payment tokenization, the prerequisite for this setup, replaces a real card number with a payment-network-issued token so an agent can complete a transaction without handling the underlying card credentials.

**「Impact」** For eligible US Pro subscribers, agent-initiated purchases cannot run fully unattended because every transaction needs an explicit item-and-amount check plus biometric approval. Users outside the US or without a US-issued card cannot use the feature at launch.

**Tags**: `#OpenAI`, `#agentic payments`, `#AI agents`, `#payment security`, `#tokenization`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Lutnick faces Nvidia scrutiny as sons&\#x27; firm&\#x27;s reported stake falls](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 7.0/10

CNBC reported that Cantor Fitzgerald, the Wall Street firm led by Commerce Secretary Howard Lutnick&\#x27;s sons, saw its reported Nvidia share count fall 49% between September 2025 and March 2026, amid scrutiny of Lutnick&\#x27;s handling of Nvidia-related China export controls. The report cited no evidence that the holdings changes were tied to intelligence warnings or that Lutnick shared nonpublic information, but an ethics expert said the relationship raises questions about appearances.

rss · CNBC Finance · Nov 13, 23:42

**「Background」** Howard Lutnick ran Cantor Fitzgerald, the Wall Street firm now led by his sons, before becoming U.S. commerce secretary in 2025; Commerce administers the export-control entity list at issue in the Nvidia case. Nvidia CEO Jensen Huang resigned Thursday after revelations of an extramarital affair with a suspected Chinese spy, adding to scrutiny of how Lutnick handled Nvidia-related export enforcement.

<details><summary>References</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Howard_Lutnick">Howard Lutnick - Wikipedia</a></li>
<li><a href="https://www.reuters.com/business/retail-consumer/nvidia-ceo-jensen-huang-step-down-big-blow-ai-boom-2026-11-12/">Nvidia CEO Jensen Huang resigns in blow to AI boom he helped ...</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#export controls`, `#conflict of interest`, `#Commerce Department`, `#Cantor Fitzgerald`

---

<a id="item-finance-news-2"></a>
### [Chicago Fed&\#x27;s Goolsbee: central bank &\#x27;has definitely got work to do&\#x27; on inflation](https://www.cnbc.com/2026/11/13/chicago-feds-goolsbee-says-central-bank-has-definitely-got-work-to-do-on-inflation.html) ⭐️ 7.0/10

Chicago Fed President Austan Goolsbee said the Federal Reserve &quot;has definitely got work to do to continue to reestablish its credibility&quot; on inflation, after the Labor Department reported October producer prices rose 6.5% from a year earlier — the highest annual gain since November 2022. Markets are fully pricing a quarter-point interest-rate increase at the Fed&\#x27;s Dec. 8-9 meeting, according to CME Group&\#x27;s FedWatch.

rss · CNBC Finance · Nov 13, 14:22

**「Background」** The Fed aims for 2% annual inflation, and Goolsbee said price growth has stayed above that level for almost six years without recent progress; he is not currently a voting member of the rate-setting committee but will be in 2027.

**「Impact」** If the Fed raises rates as markets expect, borrowing costs would edge higher for households and businesses with variable-rate or new loans, since the central bank&\#x27;s policy rate feeds through to consumer and commercial lending rates.

**Tags**: `#Federal Reserve`, `#monetary policy`, `#inflation`, `#producer prices`, `#interest rates`

---