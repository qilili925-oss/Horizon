---
layout: default
title: "Horizon Summary: 2026-11-16 (EN)"
date: 2026-11-16
lang: en
---

> From 36 items, 9 important content pieces were selected

---

**Technology News**
1. [Meta FAIR/NYU: 200+ MLLMs show encoder pretraining optional, vision-only weights needed](#item-tech-news-1) ⭐️ 8.0/10
2. [Meituan releases LongCat-2.5 weights, claims Huawei-only training](#item-tech-news-2) ⭐️ 8.0/10
3. [Sebastian Raschka Explains How Positional Embeddings Work in Modern LLMs](#item-tech-news-3) ⭐️ 7.0/10
4. [Protomaps makes self-hosted map tiles cheap and easy](#item-tech-news-4) ⭐️ 7.0/10
5. [MacBook Pro OLED PWM flicker and display-sensitivity debate](#item-tech-news-5) ⭐️ 7.0/10
6. [Tool Claims 5x Faster Pageable cudaMemcpy on B300](#item-tech-news-6) ⭐️ 7.0/10

**Financial News**
1. [Lutnick faces ethics questions over sons’ firm’s Nvidia ties](#item-finance-news-1) ⭐️ 7.0/10
2. [US Judge Denies Micron, Samsung and SK Hynix Bid to Dismiss DRAM Price-Fixing Suit](#item-finance-news-2) ⭐️ 7.0/10
3. [China, U.S. and Russia to Hold First Trilateral Leaders&\#x27; Meeting at Shenzhen APEC](#item-finance-news-3) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Meta FAIR/NYU: 200+ MLLMs show encoder pretraining optional, vision-only weights needed](https://www.reddit.com/r/MachineLearning/comments/1xx1k2o/meta_fair_nyu_unbundling_multimodal_vision/) ⭐️ 8.0/10

A Meta FAIR and NYU team trained more than 200 multimodal LLMs from scratch on the same data, charging encoder pretraining against the same lifetime compute budget, to separate three choices that standard vision encoders bundle together. They report that separate encoder pretraining is optional: encoders pretrained with four objectives at best tied a from-scratch encoder at matched compute, and extending MetaCLIP pretraining 6.5× raised ImageNet linear-probe accuracy from 80.4% to 84.4% without improving VQA. Vision-only parameters, by contrast, are required — encoder-free models trailed at every backbone size from 0.6B to 6.4B and needed roughly 3× the compute to catch up — while placement before the LLM is optional: an &quot;in-fusion&quot; design adding zero-initialized vision-only weights to the LLM&\#x27;s first 8 layers matched a standard encoder from 1.7B to 6.4B with about 13% lower time to first token \(45.0 vs 44.4 VQA at 1.7B\). Main comparisons used Qwen3-1.7B and 4B backbones with 0.4B vision parameters, evaluated on 16 Cambrian VQA benchmarks at 448 px and 12 language benchmarks; the work is a preprint posted by one of the authors and has not been independently verified.

reddit · r/MachineLearning · /u/trungh98 · Nov 15, 17:38

**「Background」** Multimodal LLMs typically use a vision encoder that is pretrained separately, often with contrastive objectives, contains parameters used only by image tokens, and sits before the language model. Published models have diverged on whether to keep, drop, or retrain that encoder, but differences in data and compute make those comparisons hard to interpret. This study treats the standard encoder as three separable design choices rather than one package.

**「Impact」** For teams building MLLMs under a fixed compute budget, the reported result argues that encoder pretraining and a separate pre-LLM encoder can be dropped without losing VQA accuracy, with that budget instead spent on vision-only parameters inside the LLM; the authors also report about 13% lower time to first token for the in-fusion variant, which matters for serving latency. The caveat is that the evidence comes from a single preprint&\#x27;s controlled recipe — Qwen3 backbones, 0.4B vision capacity, 448 px Cambrian benchmarks — and has not been independently reproduced.

**Tags**: `#multimodal LLMs`, `#vision encoders`, `#MLLM training`, `#empirical study`, `#model architecture`

---

<a id="item-tech-news-2"></a>
### [Meituan releases LongCat-2.5 weights, claims Huawei-only training](https://the-decoder.com/meituan-releases-a-1-6-trillion-parameter-agent-model-that-never-touched-an-nvidia-gpu/) ⭐️ 8.0/10

Meituan&\#x27;s LongCat team has released the open weights for LongCat-2.5, an agent-focused multimodal model it says is designed for long, multi-step tasks such as coding, one week after the model&\#x27;s formal launch. The model activates about 48 billion parameters per token, accepts text, image, and video inputs, and is published under the MIT license for commercial use. Meituan says training used only Huawei Ascend accelerators and no Nvidia GPUs, and reports an 88.4 score on Terminal Bench v2.1, slightly below Claude Opus 5&\#x27;s 89.1. Those hardware and benchmark claims are official and have not been independently verified.

telegram · zaihuapd · Nov 15, 11:08

**「Background」** The LongCat team had announced LongCat-2.5 a week before publishing the weights, so the new step is the actual downloadable release under the MIT license. The model is a sparse one: about 48 billion of its parameters are active per token, and it accepts text, images and video. Its training claim rests on Huawei&\#x27;s Ascend accelerator cards, the Chinese domestic alternative to Nvidia GPUs, which Meituan says were used exclusively.

**「Deployment implications」** Because the weights are MIT-licensed, organizations can self-host and modify LongCat-2.5 commercially, but Meituan&\#x27;s published self-hosting deployment specification targets 194 Huawei Ascend chips, making Ascend capacity—not an Nvidia GPU cluster—the practical procurement requirement for on-premises deployment.

<details><summary>References</summary>
<ul>
<li><a href="https://af.net/realtime/meituan-releases-open-weight-1-6t-moe-model-longcat-2-5/">Meituan Releases Open-Weight 1.6T MoE Model LongCat-2.5</a></li>

</ul>
</details>

**Tags**: `#open-source AI`, `#agent models`, `#Huawei Ascend`, `#LLM training`, `#multimodal`

---

<a id="item-tech-news-3"></a>
### [Sebastian Raschka Explains How Positional Embeddings Work in Modern LLMs](https://magazine.sebastianraschka.com/p/understanding-positional-embeddings) ⭐️ 7.0/10

Sebastian Raschka&\#x27;s technical explainer walks through how positional embeddings are implemented in modern large language models, aimed at readers working with transformer architectures. It is an educational deep-dive into existing implementation practice rather than a report of a new model, benchmark, or experimental result, so it describes how these components are built rather than announcing a change. The available material does not include the specific model versions, code examples, or measured comparisons covered in the article itself.

hackernews · vismit2000 · Nov 15, 12:14 · [Discussion](https://news.ycombinator.com/item?id=50506376)

**「Background」** Self-attention is permutation-invariant, so transformers need positional information to represent token order. Earlier designs typically added absolute position vectors to token embeddings, whereas rotary position embeddings \(RoPE\)—now common in LLMs—apply position-dependent rotations to query and key vectors so attention scores encode relative offsets; RoPE is also frequently compared with ALiBi.

**「Community Discussion」** Commenter programjames argued that the article addresses only implementation and that a full understanding requires theory, contending that positional embeddings are group representations and that this framing yields a way to derive and parameterize them so they are differentiable and learnable. As one example, the commenter characterized rotary positional embeddings as representations of the translation group, noting that the n-dimensional translation group is abelian. This is the commenter&\#x27;s theoretical position, not a claim made by the article.

<details><summary>References</summary>
<ul>
<li><a href="https://apxml.com/courses/how-to-build-a-large-language-model/chapter-13-positional-encoding-variations/rotary-position-embedding-rope">Rotary Position Embedding (RoPE) Explained - apxml.com</a></li>
<li><a href="https://elsolitario.org/en/2026/11/15/rope-rotary-position-embedding-explained/">Rotary Position Embedding (RoPE) Explained - elsolitario.org</a></li>

</ul>
</details>

**Tags**: `#positional-embeddings`, `#LLMs`, `#transformer-architecture`, `#deep-learning`, `#technical-explainer`

---

<a id="item-tech-news-4"></a>
### [Protomaps makes self-hosted map tiles cheap and easy](https://bruceroettgers.eu/blog/protomaps/) ⭐️ 7.0/10

A blog post argues that self-hosting map tiles with Protomaps has become cheap and easy enough for individual developers and small projects. It presents Protomaps, which uses the PMTiles format, as an alternative to hosted map providers such as Mapbox and Google Maps. The supplied material does not include version numbers, pricing, benchmarks, or a detailed deployment recipe.

hackernews · bcye · Nov 15, 19:26 · [Discussion](https://news.ycombinator.com/item?id=50509837)

**「Why a single-file tile archive matters」** Protomaps is built on PMTiles, a single-file archive format for tiled data that can be placed on commodity object storage such as S3 and served through HTTP range requests, so no custom tile backend or third-party provider is needed. That design differs from metered commercial services like Mapbox and the Google Maps API, which are accessed through usage-based APIs and keys, whereas self-hosted Protomaps deployments are unmetered and paid for only through the operator&\#x27;s own storage and bandwidth costs.

**「What changes for developers」** Teams can publish a PMTiles archive as a single file on commodity object storage such as S3 and let clients fetch individual tiles through HTTP range requests, avoiding a custom tile backend or third-party provider; the storage endpoint must support range requests for this to work.

**「Community discussion」** Commenters describe practical uses: one is building a Wikipedia walking game with live-rendered street packs and says Protomaps made the project affordable where Mapbox or Google Maps would have ruled it out, while another self-hosts tiles behind Cloudflare R2 for privacy and access control. A separate reply warns that high-resolution satellite imagery becomes far more storage-intensive than ordinary basemaps, with one developer stopping at zoom 17, and another commenter points to OpenFreeMap as a similar free public tile service.

<details><summary>References</summary>
<ul>
<li><a href="https://protomaps.com/">Protomaps - The open source map in a file</a></li>
<li><a href="https://github.com/protomaps/PMTiles">GitHub - protomaps/PMTiles: Pyramids of map tiles in a single ...</a></li>
<li><a href="https://protomaps.com/about">Protomaps - The open source map in a file</a></li>
<li><a href="https://github.com/protomaps/PMTiles">GitHub - protomaps / PMTiles : Pyramids of map tiles in a single file on...</a></li>
<li><a href="https://protomaps.com/">Protomaps - The open source map in a file</a></li>
<li><a href="https://dev.to/aaronblondeau/self-hosted-maps-for-practically-free-1i3n">Self hosted maps for (practically) free - DEV Community</a></li>

</ul>
</details>

**Tags**: `#protomaps`, `#self-hosting`, `#map-tiles`, `#openstreetmap`, `#pmtiles`

---

<a id="item-tech-news-5"></a>
### [MacBook Pro OLED PWM flicker and display-sensitivity debate](https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/) ⭐️ 7.0/10

A MacAnorak article examines the MacBook Pro&\#x27;s OLED display as a usability and accessibility problem for people sensitive to PWM flicker, arguing that a technically better display can be worse to use. It treats flicker as distinct from image quality, but the supplied material does not provide a measured PWM frequency, an affected model or configuration, or an independent test result.

hackernews · MacAnorak · Nov 15, 13:15 · [Discussion](https://news.ycombinator.com/item?id=50506719)

**「What PWM is and what display Apple used before」** Pulse-width modulation \(PWM\) dims a display by rapidly switching its light source on and off; at low enough frequencies, sensitive viewers can perceive the flicker as eye strain or discomfort. The MacBook Pro&\#x27;s shift to OLED is recent: Apple brought tandem OLED to the laptop line while continuing to sell the Mini-LED models that have served the range since 2021, branding the new panel a &quot;PROLED XDR Display,&quot; as MacAnorak&\#x27;s article notes.

**「Keep-or-return decision」** For flicker-sensitive buyers, the concrete consequence is a keep-or-return decision: the OLED MacBook Pro&\#x27;s PWM flicker can cause eye strain even though the panel is otherwise an upgrade, and the supplied coverage includes display settings to test plus return tips if symptoms persist.

**「Community discussion」** One commenter disputes a 240 Hz PWM claim, arguing that the tandem OLED may run its layers at 480 Hz out of phase for an effective 960 Hz across much of the usable brightness range; this is the commenter&\#x27;s interpretation, not a verified measurement. Others report broader display sensitivity, including concussion-related symptoms and reactions to white-LED CRI or LCD motion blur, and one calls for research into how many people are affected.

<details><summary>References</summary>
<ul>
<li><a href="https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/">The MacBook Pro ’s OLED PWM Problem: When a ‘Better’ Display...</a></li>
<li><a href="https://www.appleheadlines.com/macbook-pro-oled-eye-strain-pwm-flicker/">MacBook Pro OLED Eye Strain &amp; PWM Flicker: 7 Moves - AH</a></li>

</ul>
</details>

**Tags**: `#OLED`, `#PWM flicker`, `#MacBook Pro`, `#display hardware`, `#eye strain`

---

<a id="item-tech-news-6"></a>
### [Tool Claims 5x Faster Pageable cudaMemcpy on B300](https://www.reddit.com/r/MachineLearning/comments/1xx2n25/making_cudamemcpy_5x_faster_on_a_b300_p/) ⭐️ 7.0/10

The author of cudamemcpy-tuner reports that wrapping a Python workload with \`cmt tune\` raised pageable CPU-to-GPU cudaMemcpy throughput on an Nvidia B300 from 10.2 GB/s to 51.5 GB/s, roughly 5x, in a 1 GB tensor benchmark. The post links a technical blog and open-source code but provides only this self-reported result; no independent benchmark or broader compatibility details are included.

reddit · r/MachineLearning · /u/makneeee · Nov 15, 18:20

**「Pageable vs. pinned CUDA transfers」** CUDA distinguishes pageable host memory, the default for ordinary allocations, from pinned \(page-locked\) memory that the GPU can access directly. Pageable cudaMemcpy transfers typically require staging through an internal pinned buffer, so they often run below pinned-copy bandwidth. A plain PyTorch CPU tensor such as torch.ones\(...\) is pageable, meaning x.to\(&quot;cuda&quot;\) exercises that slower transfer path.

**「Impact」** Developers making pageable CPU-to-GPU copies on a B300 can test the tool by prefixing a Python command with \`cmt tune\`, but should treat the 5x figure as unverified outside the author&\#x27;s 1 GB benchmark.

**Tags**: `#CUDA`, `#GPU computing`, `#memory transfers`, `#performance optimization`, `#developer tools`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Lutnick faces ethics questions over sons’ firm’s Nvidia ties](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 7.0/10

CNBC reported that Commerce Secretary Howard Lutnick faces ethics questions over his sons’ firm Cantor Fitzgerald’s ties to Nvidia, after Cantor’s reported Nvidia share count fell 49% between September 2025 and March 2026 while Lutnick resisted a crackdown on suspected Nvidia chip smuggling to China. CNBC said there is no evidence that the stake change was tied to intelligence warnings or that the firm’s business interests influenced Lutnick’s decisions.

rss · CNBC Finance · Nov 15, 19:58

**「Background」** Lutnick ran Cantor Fitzgerald before becoming commerce secretary in February 2025, and the firm is now led by his sons; Commerce administers the entity list, a restricted-trade list used against firms such as Megaspeed, which U.S. officials suspect of diverting Nvidia AI chips to China.

**「Who is affected」** Export-control enforcement is directly at stake: Treasury Secretary Scott Bessent said Treasury, Defense, State and the U.S. Trade Representative had favored adding Megaspeed to the Commerce Department&\#x27;s restricted entity list &quot;for months,&quot; so the unresolved internal dispute leaves limits on a company suspected of diverting Nvidia chips to China in abeyance.

<details><summary>References</summary>
<ul>
<li><a href="https://www.bbc.com/news/articles/cmdx1vpprk9vo">Suspected China spy linked to Nvidia &#x27;s ex-boss left in 2025...</a></li>
<li><a href="https://www.cbsnews.com/news/howard-lutnick-scott-bessent-nvidia-megaspeed-testimony/">Lutnick agrees to testify as Bessent blames him for not banning Nvidia ...</a></li>
<li><a href="https://www.nytimes.com/2026/11/12/us/politics/lutnick-nvidia-commerce-china-chips.html">Howard Lutnick Took Softer Line on Nvidia as Calls for Tougher...</a></li>
<li><a href="https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html">Howard Lutnick &#x27;s sons&#x27; Nvidia ties amid Jensen Huang China spy...</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#U.S. export controls`, `#Cantor Fitzgerald`, `#conflict of interest`, `#semiconductors`

---

<a id="item-finance-news-2"></a>
### [US Judge Denies Micron, Samsung and SK Hynix Bid to Dismiss DRAM Price-Fixing Suit](https://www.tomshardware.com/tech-industry/big-tech/judge-denies-motion-to-dismiss-dram-price-fixing-lawsuit-against-micron-samsung-and-sk-hynix-says-chipmakers-acted-like-hawks-flying-in-formation-finds-evidence-of-dram-collusion-plausible-after-500-percent-price-surge) ⭐️ 7.0/10

A U.S. judge, Noël Wise, rejected motions by Micron, Samsung and SK Hynix to dismiss a DRAM price-fixing class action, finding the plaintiffs presented new evidence that the three chipmakers&\#x27; synchronized conduct was &quot;more like flying in formation.&quot; The plaintiffs—17 individuals and small businesses—allege the companies made four parallel supply restrictions in one year that drove DRAM prices up by as much as 500%; those claims remain allegations, and the case is set for a management conference in January 2027.

telegram · zaihuapd · Nov 15, 16:39

**「Background」** The suit is a proposed class action by 17 individuals and small businesses alleging that Micron, Samsung and SK Hynix made four parallel moves in a year to limit DRAM supply. The denial keeps the case alive and moves it toward discovery; it is not a finding of liability.

<details><summary>References</summary>
<ul>
<li><a href="https://wccftech.com/federal-judge-rejects-memory-makers-defense-samsung-micron-sk-hynix-dram-shortage-lawsuit/">Federal Judge Rejects Memory Makers’ Defense To Advance Class ...</a></li>

</ul>
</details>

**Tags**: `#DRAM`, `#antitrust`, `#semiconductors`, `#Micron/Samsung/SK Hynix`, `#litigation`

---

<a id="item-finance-news-3"></a>
### [China, U.S. and Russia to Hold First Trilateral Leaders&\#x27; Meeting at Shenzhen APEC](https://apnews.com/article/trump-xi-putin-summit-china-5fe92253ef38100bae913834a9b74d72) ⭐️ 7.0/10

China&\#x27;s foreign ministry said the leaders of China, the United States and Russia will hold their first dedicated trilateral meeting on November 19, on the sidelines of the APEC summit in Shenzhen and outside its official agenda. No agenda items or expected outcomes were announced.

telegram · zaihuapd · Nov 16, 01:38

**「Background」** APEC is the annual Asia-Pacific economic forum, and China is hosting its 2026 leaders&\#x27; meeting in Shenzhen on November 18-19, giving Beijing the home advantage as chair. The Kremlin confirmed the November 19 trilateral date through spokesman Dmitry Peskov.

<details><summary>References</summary>
<ul>
<li><a href="https://www.theguardian.com/world/2026/nov/15/asia-diplomatic-summits-trump-xi-putin-apec-asean">World leaders head to Asia for back-to-back diplomatic summits</a></li>
<li><a href="https://sputnikglobe.com/20261114/putin-xi-trump-to-hold-trilateral-meeting-in-chinas-shenzhen-on-november-19---peskov-1125073196.html">Putin, Xi, Trump to Hold Trilateral Meeting in China &#x27;s Shenzhen on...</a></li>
<li><a href="https://www.aljazeera.com/news/2026/11/14/trump-xi-putin-trilateral-meeting-at-apec-what-to-expect">Trump-Xi-Putin trilateral meeting at APEC : What to expect | Al Jazeera</a></li>

</ul>
</details>

**Tags**: `#geopolitics`, `#China-US-Russia`, `#APEC`, `#diplomacy`, `#market risk`

---