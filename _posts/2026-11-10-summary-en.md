---
layout: default
title: "Horizon Summary: 2026-11-10 (EN)"
date: 2026-11-10
lang: en
---

> From 46 items, 9 important content pieces were selected

---

**Technology News**
1. [Google expands TPU lineup with 8tx and 8i Max chips](#item-tech-news-1) ⭐️ 8.0/10
2. [E-means claims to outperform k-means in one-tenth the epochs](#item-tech-news-2) ⭐️ 7.0/10
3. [Report claims consumer Google Gemini sends Drive and Gmail data to human reviewers](#item-tech-news-3) ⭐️ 7.0/10
4. [watched.earth maps a week of satellite passes and retrieves their imagery](#item-tech-news-4) ⭐️ 7.0/10
5. [LingBot-Touch tactile encoder predicts latents, reports gains over reconstruction](#item-tech-news-5) ⭐️ 7.0/10
6. [Storm-outage-risk model claims 2.4× PR-AUC over NWS/SPC on 2025 holdout](#item-tech-news-6) ⭐️ 7.0/10
7. [OPPO, vivo, Xiaomi, Honor launch joint ADV verification for Android sideloading in China](#item-tech-news-7) ⭐️ 7.0/10
8. [EU draft Digital Fairness Act targets addictive design and virtual currency](#item-tech-news-8) ⭐️ 7.0/10

**Financial News**
1. [China NEV passenger vehicle exports jump 138.8% in first three quarters](#item-finance-news-1) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Google expands TPU lineup with 8tx and 8i Max chips](https://www.bloomberg.com/news/articles/2026-11-09/google-escalates-nvidia-rivalry-with-new-versions-of-its-tpu-systems) ⭐️ 8.0/10

Google announced two new Tensor Processing Units: TPU 8tx, intended for government agencies and tightly regulated industries handling classified data and designed to work alongside AMD chips, and TPU 8i Max, which is designed to place two TPU chips in one package for ultra-long-context AI workloads that need more compute and memory. Google is adding these chips within a single year instead of following its earlier roughly two-year cadence, and it named Apple, Meta, Oracle and Anthropic as customers as it promotes TPUs as an alternative to Nvidia GPUs. The supplied summary provided no performance benchmarks, power figures, pricing or availability dates, so the chips&\#x27; actual competitiveness is not established.

telegram · zaihuapd · Nov 9, 13:36

**「Background」** TPUs are Google’s custom AI accelerators, positioned as an alternative to Nvidia GPUs. Google had previously introduced one new TPU processor roughly every two years; the current launch breaks that cadence by expanding the lineup within a single year with specialized chips.

**「Impact」** Organizations considering TPU 8tx for secure workloads may need to plan for a mixed Google–AMD accelerator environment, while those weighing TPU 8i Max for long-context models cannot yet compare its memory and compute gains with Nvidia parts without published benchmarks or pricing.

**「Community discussion」** Commenters focused on the missing economic comparisons, asking for watt/token and dollar/token figures against Nvidia equivalents and why Google does not sell the chips directly. One user said Colab still offers only the v6e-1 TPU, which they called too small for serious work, while another recommended Google&\#x27;s TPUSync post as relevant to open-source implementations.

**Tags**: `#TPU`, `#Google`, `#AI hardware`, `#Nvidia`, `#semiconductors`

---

<a id="item-tech-news-2"></a>
### [E-means claims to outperform k-means in one-tenth the epochs](https://e-means.github.io/) ⭐️ 7.0/10

E-means has published a clustering method that it claims outperforms k-means while requiring one-tenth the epochs, pitched as an alternative for large-scale clustering work such as vector indexing. That performance claim remains a project assertion rather than an independently verified result in the supplied material. Early Hacker News experiments are mixed and preliminary, so the method is best treated as promising but unproven.

hackernews · porridgeraisin · Nov 9, 18:45 · [Discussion](https://news.ycombinator.com/item?id=50429734)

**「Background」** Conventional k-means is usually implemented with Lloyd&\#x27;s algorithm, which alternates assigning each point to its nearest centroid and recomputing each centroid as the cluster mean. FAIR&\#x27;s Faiss default runs 25 such epochs, a costly loop at billions of vectors and tens of millions of clusters. E-means instead uses mini-batch updates with exponential moving averages; Meta FAIR researchers report that it reaches a lower loss than 25-epoch Lloyd k-means within 1.2 to 3 epochs.

**「Workload-specific gains」** The practical payoff appears workload-dependent rather than universal. A commenter who adapted the method to an IVF index reports a 146x GPU speedup, and another reports that full bulk rebuilds of an existing index \(as in a shard split\) ran 2.5x faster, while noting that overall insertion time barely moved because incremental clustering is a small share of CPU time. A third commenter tried adapting it for spherical mesh relaxation and found it clearly worse, so teams should benchmark against Lloyd&\#x27;s algorithm on their own access pattern before swapping it in.

**「Community discussion」** Commenters reported practical results: one claimed a 146x GPU speedup after adapting the method to an IVF index, another saw 2.5x faster bulk reindexing during shard splits but little change in overall insertion time, and a third found it did not improve spherical mesh relaxation. A separate commenter suggested the update may be understood as expectation maximization with a friction term, noting that it keeps centroids within the convex hull.

<details><summary>References</summary>
<ul>
<li><a href="https://openreview.net/pdf?id=pt14gnV3dl">E-MEANS OUTPERFORMING K MEANS IN ONE TENTH THE EPOCHS</a></li>
<li><a href="https://agihunt.info/en/papers/2611.09501">Meta FAIR&#x27;s e-means beats 25-epoch k-means loss… · AGI Hunt</a></li>
<li><a href="https://daily.dev/posts/e-means-10x-faster-k-means-at-equal-loss-wjgmcpump">E-means: 10x faster k-means at equal loss - daily.dev</a></li>

</ul>
</details>

**Tags**: `#clustering`, `#machine-learning`, `#k-means`, `#algorithms`, `#performance`

---

<a id="item-tech-news-3"></a>
### [Report claims consumer Google Gemini sends Drive and Gmail data to human reviewers](https://github.com/thisisme6598/gemini_files/) ⭐️ 7.0/10

A Hacker News discussion examines claims that consumer Google Gemini with Connected Apps can route personal Drive files and emails to human annotators when a user authorizes apps such as Gmail. Commenters distinguish that setup from Workspace Gemini and Workspace Intelligence, which they say still claim not to be subject to human review. The supplied material contains no primary report or official Google confirmation, so the exact data flows and conditions remain unverified.

hackernews · gf74918 · Nov 9, 18:24 · [Discussion](https://news.ycombinator.com/item?id=50429426)

**「Background」** The distinction at issue is between the standalone consumer Gemini app and Gemini in Google Workspace: Google&\#x27;s Workspace terms say Workspace data is not used for training and is not subject to human review, while the consumer app trains on interactions by default and human reviewers may read a subset of chats. Consumer Gemini&\#x27;s Connected Apps feature can retrieve content from services such as Gmail and Drive once a user authorizes access; separately, Gemini Apps Activity can retain interactions for up to three years and make them available for human review and training when enabled.

**「Impact」** If the claim holds, consumer users who connect Gmail or Drive to Gemini face potential human review of personal content, while the distinction drawn by commenters implies organizations should keep sensitive work in Workspace accounts rather than consumer Gemini. Users can review Connected Apps permissions to limit which data Gemini can retrieve.

**「Community discussion」** Commenters distinguish consumer Gemini with Connected Apps from Workspace and enterprise Gemini, which they say still claims no human review. One user reports Gemini responses that seemed uncannily tuned to an email, while others argue such review is routine across annotation-dependent tools and reflects broader privacy erosion.

<details><summary>References</summary>
<ul>
<li><a href="https://www.qadar.ai/ai-tools/gemini">Is Gemini safe for work ? Privacy &amp; AI governance | Qadar AI</a></li>
<li><a href="https://proton.me/blog/turn-off-gemini-on-android">Google AI is watching: How to turn off Gemini on Android | Proton</a></li>

</ul>
</details>

**Tags**: `#AI privacy`, `#Google Gemini`, `#data governance`, `#human review`, `#Hacker News`

---

<a id="item-tech-news-4"></a>
### [watched.earth maps a week of satellite passes and retrieves their imagery](https://www.watched.earth/) ⭐️ 7.0/10

watched.earth is an open-source browser tool that finds every satellite pass over a chosen location in the past seven days using SGP4 against the CelesTrak catalog, then retrieves Sentinel-2, Landsat, and NASA images from those passes. The author says the pass search runs client-side in about half a second and was checked against brute force at the poles, the antimeridian, and tiny swaths with zero missed passes; these correctness and performance claims are author-reported, not independently verified. The tool renders roughly 17,000 orbital objects on the GPU, labels a location as &quot;watched&quot; only when a real image exists, and does not store the user&\#x27;s location.

hackernews · a585gupt · Nov 9, 17:51 · [Discussion](https://news.ycombinator.com/item?id=50428907)

**「Background」** Orbital pass search relies on SGP4, a standard propagation model that converts public two-line element sets into predicted satellite positions; CelesTrak has distributed such data and SGP4 tooling for decades. The project applies that model to the CelesTrak catalog in the browser, then matches the resulting passes to Sentinel-2, Landsat, and NASA imagery.

**「Impact」** Geospatial practitioners and trip planners can identify and inspect imagery from a specific overpass without searching each archive separately, but should account for the author-reported 5–10-minute Sentinel-2 timestamp discrepancy when timing matters.

**「Community discussion」** Several commenters praised the execution and data integration; one geospatial worker said the notable feature is seeing the exact image taken by a satellite, and another reported using it for backpacking planning because it is easier to access than Copernicus. These are user opinions from the Show HN thread, not independent evaluations.

<details><summary>References</summary>
<ul>
<li><a href="https://celestrak.org/software/tutorials/sgp4.php">CelesTrak: SGP4 Software Tutorial</a></li>
<li><a href="https://celestrak.org/software/tskelso-sw.php">CelesTrak: Satellite Tracking Software by T.S. Kelso</a></li>

</ul>
</details>

**Tags**: `#satellite-tracking`, `#geospatial`, `#orbital-mechanics`, `#webgl`, `#open-source`

---

<a id="item-tech-news-5"></a>
### [LingBot-Touch tactile encoder predicts latents, reports gains over reconstruction](https://www.reddit.com/r/MachineLearning/comments/1xs05uo/latent_prediction_beats_reconstruction_for/) ⭐️ 7.0/10

According to a Reddit post, Robbyant released LingBot-Touch, a JEPA-style self-supervised tactile encoder that predicts latent representations of masked contact rather than reconstructing raw sensor signals; inference code and checkpoints are public. In reported same-size comparisons on the same data, tactile-to-video top-5 recall at 1K hours was 32.1% for JEPA versus 5.6% for MAE and 4.4% for VAE, and at 4K hours JEPA reached 49.3% while MAE stayed below 9% and VAE fell to 3.1%. The encoder combines magnetic, piezoresistive, and visuotactile inputs in one Transformer via canonical fingertip coordinates and 5D RoPE, and warms masking from 40% to 80% over 300 steps to avoid hiding contacting taxels and causing gradient explosions. On 26 real robot tasks with four policies, frozen encoder features scored highest in 89 of 104 policy-task combinations, and on a magnetic hand unseen in pretraining LingBot-VLA improved from 57.21 to 75.04.

reddit · r/MachineLearning · /u/Zealousideal-War7154 · Nov 9, 18:52

**「Background」** JEPA-style pretraining predicts latent representations of masked input instead of reconstructing raw signals, a design intended to keep the learning signal focused on contact rather than the sparse, near-zero background in tactile clips. LingBot-Touch comes from Robbyant, whose LingBot family already includes LingBot-VLA, described on the project&\#x27;s GitHub page as a vision-language-action model pretrained on 20,000 hours of real-world data across nine dual-arm robot configurations.

**「Impact」** For robotics teams building tactile pretraining pipelines, the posted results argue for evaluating contact-specific retrieval or policy transfer rather than reconstruction loss alone, because sparse near-zero background can make reconstruction look better without encoding contact. The public checkpoints also provide a direct baseline for testing whether latent-prediction features transfer to a new tactile sensor; the reported unseen-hand gain is one evaluation, not broad validation.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/Robbyant/lingbot-vla">GitHub - Robbyant / lingbot - vla : A Pragmatic VLA Foundation Model</a></li>
<li><a href="https://technology.robbyant.com/">Technology - Robbyant</a></li>

</ul>
</details>

**Tags**: `#tactile representation learning`, `#self-supervised learning`, `#JEPA`, `#dexterous manipulation`, `#robotics`

---

<a id="item-tech-news-6"></a>
### [Storm-outage-risk model claims 2.4× PR-AUC over NWS/SPC on 2025 holdout](https://www.reddit.com/r/MachineLearning/comments/1xs4hq8/forecasting_new_power_outages_per_county_hourly_2/) ⭐️ 7.0/10

A Reddit user reports an XGBoost model that forecasts new county-level power outages hourly, two hours ahead, across 216 counties in Missouri and Illinois using HRRR storm forecasts, county facts, current outages, and neighboring-county data. The target is the probability that at least 5% of a county&\#x27;s customers will newly lose power during the six hours starting two hours from now; the model was trained on 2020–2024 and tested on 2025 with HRRR forecasts as issued \(the mean of the last five runs\), not observed weather. On the 2025 holdout, the self-reported PR-AUC was 0.094 versus 0.039 for a baseline rate table built from NWS warnings and the SPC Day 1 outlook—about 2.4×, with a bootstrap 95% range of 2.0–3.3×—and at equal alert volume it caught 30% of new outages versus 17%, with precision of 15% versus 11% against a 0.5% base rate. An early transfer test on Iowa, Indiana, and Michigan reported 31% versus 19% capture, and the forecasts have been live since November 1 with every forecast saved for a blind test; the work is not peer-reviewed.

reddit · r/MachineLearning · /u/CarRepresentative843 · Nov 9, 21:34

**「Background」** The model is driven by HRRR forecasts, which extend to 48 hours for the 00, 06, 12 and 18 Z cycles and to 18 hours otherwise \[tool-2-1\]. The evaluation uses those forecasts as issued—averaging the last five runs—rather than observed weather, so the two-hour-ahead test reflects information available before an outage begins. Its comparison baseline is a rate table keyed to existing NWS warnings and SPC Day 1 outlooks and fitted on the same county-hour rows.

**「Impact」** For utility and emergency-management triage, the reported operating point matters more than the headline PR-AUC: at the same alert volume, the model flags 30% of new outage events instead of 17%, but 15% precision means most alerts would still be false positives given the 0.5% base rate. That makes it a prioritization aid rather than a stand-alone trigger until the saved live forecasts are evaluated in the blind test.

<details><summary>References</summary>
<ul>
<li><a href="https://www.weathernerds.org/models/hrrr.html">Weathernerds HRRR</a></li>

</ul>
</details>

**Tags**: `#machine learning`, `#power outages`, `#weather forecasting`, `#XGBoost`, `#grid resilience`

---

<a id="item-tech-news-7"></a>
### [OPPO, vivo, Xiaomi, Honor launch joint ADV verification for Android sideloading in China](https://mp.weixin.qq.com/s/ZiKBASSLzvsZ6WR2AUmFeg) ⭐️ 7.0/10

OPPO, vivo, Xiaomi, and Honor have launched an Android sideloading developer identity verification \(ADV\) mechanism in mainland China, with each company recognizing the others&\#x27; verification results. Apps already registered and listed on the four vendors&\#x27; open platforms are submitted for verification automatically and do not need a separate application. When an unverified app is installed via sideloading, the system displays an “unverified” warning and requires the user to confirm manually before installation continues.

telegram · zaihuapd · Nov 9, 11:44

**「Google&\#x27;s ADV program as the precursor」** ADV \(Android Developer Verification\) is the mechanism Google introduced to tie a verified developer identity to Android apps, warning users when an app comes from an unverified developer. An August 19, 2026 report on the incoming side-loading rules described a September 30 deadline for Google&\#x27;s ADV program, and noted that open-source store F-Droid had publicly criticized Google&\#x27;s implementation in a July 1, 2026 blog post. The four Chinese OEMs&\#x27; joint rollout applies the same identity-verification concept within mainland China, adding mutual recognition of each vendor&\#x27;s verification results.

**「What developers must do」** Apps already registered and listed on any of the four vendors&\#x27; open platforms are submitted for ADV verification automatically, so developers who ship only through those stores face no extra step. Anyone distributing a build that is not registered there — an internal test build, a third-party market listing, or a directly shared APK — will trigger the &quot;unverified&quot; prompt, and users must manually confirm before installation proceeds; those developers should complete verification before pushing sideload builds to avoid the added friction.

<details><summary>References</summary>
<ul>
<li><a href="https://post.smzdm.com/p/a825vxmq/">安 卓 侧 载 新规进入倒计时：9月30...</a></li>

</ul>
</details>

**Tags**: `#Android`, `#app security`, `#sideloading`, `#developer verification`, `#China mobile ecosystem`

---

<a id="item-tech-news-8"></a>
### [EU draft Digital Fairness Act targets addictive design and virtual currency](https://www.mlex.com/mlex/articles/2546584/digital-businesses-face-addictive-design-controls-under-draft-eu-consumer-law) ⭐️ 7.0/10

A leaked draft of the EU Digital Fairness Act would require digital companies to let users switch off autoplay and continuous-use rewards, and to provide cancellation buttons, renewal reminders and human support for online subscriptions, plus explicit consent before a free trial becomes paid. It would also ban paid in-game draws, pay-to-win mechanics and profiling advertising aimed at minors, and require game virtual currencies to show their real-world value. The European Commission is due to present the bill on 11 November alongside a reform of the consumer-protection cooperation framework; violations would carry fines of up to 6% of global turnover, and both proposals need approval from the European Parliament and EU governments.

telegram · zaihuapd · Nov 9, 16:42

**「Background」** The Digital Fairness Act is a planned EU law that would update consumer-protection rules for online services, targeting dark patterns, addictive design and subscription practices. Euronews&\#x27;s reporting on the same leaked draft says it would blacklist ten manipulative designs outright, including false low-stock claims, pre-ticked add-ons and nagging pop-ups.

**「Impact」** Game publishers and subscription providers would face compliance work across monetization and account flows if the bill passes, particularly around minors&\#x27; paid in-game draws, pay-to-win mechanics, profiling ads and real-world value labels for virtual currency. The draft&\#x27;s 6% global-turnover penalty cap raises the cost of non-compliance, though no final obligations exist until the European Parliament and EU governments approve the proposal.

<details><summary>References</summary>
<ul>
<li><a href="https://www.euronews.com/2026/11/09/eu-to-blacklist-ten-manipulative-online-design-traps-leaked-draft-shows">EU to blacklist ten manipulative online design &#x27;traps&#x27;, leaked draft s...</a></li>
<li><a href="https://vgtimes.com/articles/172316-eu-gaming-law-plans.html">EU Gaming Law Plans and You: Kid Mode, In-Game Currency , Loot...</a></li>

</ul>
</details>

**Tags**: `#EU regulation`, `#dark patterns`, `#subscription traps`, `#virtual currency`, `#consumer tech`

---

## Financial News

<a id="item-finance-news-1"></a>
### [China NEV passenger vehicle exports jump 138.8% in first three quarters](https://finance.sina.com.cn/tech/roll/2026-10-26/doc-iniwpfnc2438186.shtml) ⭐️ 7.0/10

In the first three quarters of 2026, China’s new-energy passenger vehicle exports reached 3.887 million units, up 138.8% from a year earlier, while domestic retail sales fell 12.8% to 7.758 million units.

telegram · zaihuapd · Nov 10, 02:56

**「Background」** New-energy vehicle \(NEV\) purchase subsidies and purchase-tax breaks are being scaled back, a change the article links to weaker domestic demand, while the year-earlier sales comparison was also unusually high.

**「Impact」** Export growth has become an important support for Chinese automakers’ sales as domestic retail demand weakens.

<details><summary>References</summary>
<ul>
<li><a href="https://post.smzdm.com/p/axkwk30d/">2026 ...</a></li>

</ul>
</details>

**Tags**: `#China auto industry`, `#NEV exports`, `#domestic vehicle demand`, `#purchase subsidies`, `#retail sales`

---