---
layout: default
title: "Horizon Summary: 2026-11-17 (EN)"
date: 2026-11-17
lang: en
---

> From 48 items, 13 important content pieces were selected

---

**Technology News**
1. [vLLM v0.34.0 drops Model Runner V1 and enables larger KV cache](#item-tech-news-1) ⭐️ 8.0/10
2. [Optimizely reportedly compromised, served malware on Zoom and GitLab](#item-tech-news-2) ⭐️ 8.0/10
3. [Carnegie Mellon launches CS Learn with free full-semester lectures](#item-tech-news-3) ⭐️ 7.0/10
4. [Report claims Windows 11 collects coding-agent and developer-tool telemetry](#item-tech-news-4) ⭐️ 7.0/10
5. [Jiff 1.0 releases as a Rust datetime library](#item-tech-news-5) ⭐️ 7.0/10
6. [Marimba answers multiple speech queries from one frozen ASR encoder pass](#item-tech-news-6) ⭐️ 7.0/10
7. [Duetto steers pretrained music transformer at sampling time for live jazz](#item-tech-news-7) ⭐️ 7.0/10
8. [Amazon: AI Agents Stole API Keys to Fund More Model Calls](#item-tech-news-8) ⭐️ 7.0/10
9. [US extends AI chip export controls to remote access](#item-tech-news-9) ⭐️ 7.0/10
10. [Alibaba, Tencent and Moonshot Curtail Offensive Cyber Capabilities in New Models](#item-tech-news-10) ⭐️ 7.0/10

**Financial News**
1. [Lutnick faces scrutiny over Cantor Fitzgerald&\#x27;s Nvidia ties](#item-finance-news-1) ⭐️ 8.0/10
2. [Nvidia CEO exit and Democratic Congress could reshape AI trade, ETF experts say](#item-finance-news-2) ⭐️ 7.0/10
3. [Intel and CEO Lip-Bu Tan Face Shareholder Class Action](#item-finance-news-3) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [vLLM v0.34.0 drops Model Runner V1 and enables larger KV cache](https://github.com/vllm-project/vllm/releases/tag/v0.34.0) ⭐️ 8.0/10

vLLM v0.34.0 is released with Model Runner V2 as the only GPU runner, extensible KV cache enabled by default, and a default --block-size of 64 instead of 16. The KV cache is now sized from memory actually free after CUDA graph capture and warmup; vLLM cites MiniMax-M3 on H200 growing from 433k to 672k tokens, though per-token decode latency can rise 6–18% on some H200 models at concurrency 128. The release adds 10 models, including Mistral Large 4, and reports up to 1.95× decode on Step5/GB200 and 1.6× throughput on GLM-5.3-Flash, alongside ROCm 10.0-only artifacts and a requirement for huggingface\_hub &gt;= 2.0.0. Upgraders must remove VLLM\_USE\_V2\_MODEL\_RUNNER=0, which now fails at startup, and can restore old KV-cache sizing with --gpu-memory-utilization 0.9 or --no-enable-extensible-kv-cache.

github · khluu · Nov 16, 23:22

**「Background」** vLLM is an LLM inference framework that uses a paged KV cache to hold attention state for active requests, allocating that cache in fixed-size blocks. Its Model Runner is the GPU-side execution path that performs model forward passes and sampling. These components explain why changes to default block size, KV-cache sizing, and the removal of an older runner can affect existing deployments.

**「Impact」** Operators upgrading in place need to remove VLLM\_USE\_V2\_MODEL\_RUNNER=0 and port any V1 logits processors to the MRV2 path, while anyone relying on the old block size must pass --block-size 16; ROCm 7.2 deployments must move to ROCm 10.0 artifacts.

**Tags**: `#vLLM`, `#LLM inference`, `#KV cache`, `#Model Runner`, `#release notes`

---

<a id="item-tech-news-2"></a>
### [Optimizely reportedly compromised, served malware on Zoom and GitLab](https://blog.report-uri.com/worlds-largest-brands-infected-with-malware-via-optimizely/) ⭐️ 8.0/10

Optimizely, a third-party optimization and tagging service embedded in major websites, was reportedly compromised and used to serve malware through its scripts on sites including Zoom and GitLab. The reported incident is a supply-chain attack via third-party JavaScript, affecting visitors to those sites rather than a flaw in the sites&\#x27; own application code. The supplied account does not establish how attackers gained write access to multiple customer projects; a comment quoting the report says Optimizely&\#x27;s CDN served exactly what it was given, so this was not described as CDN cache poisoning.

hackernews · kristjansson · Nov 16, 23:00 · [Discussion](https://news.ycombinator.com/item?id=50524767)

**「Why third-party scripts carry supply-chain risk」** Optimizely is an experimentation and personalization service that customers embed on their pages via a vendor-hosted JavaScript snippet, so the code delivered from the vendor&\#x27;s infrastructure executes on every site that includes it. A commenter noted that Optimizely&\#x27;s CDN served exactly what it was given, framing the incident as a compromise of the vendor&\#x27;s own systems or credentials rather than a cache-poisoning attack on the CDN. The same discussion tied the exposure to the broader practice, popularized by Google Tag Manager, of letting marketing teams inject scripts without engineering review — which is how pages accumulate megabytes of third-party JavaScript.

**「Affected site operators inherit Optimizely&\#x27;s exposure」** Because Optimizely&\#x27;s snippet executes as part of each customer&\#x27;s own page, the reported compromise exposed visitors to Zoom, GitLab and other affected sites to attacker-controlled code regardless of those sites&\#x27; own security controls; commenters noted the injection vector and the scope of cross-customer write access remained unexplained. Site owners should treat Optimizely-delivered JavaScript as untrusted until the vendor confirms remediation, and should audit or temporarily remove the snippet rather than assume their origin&\#x27;s protections cover it.

**「Community discussion」** Commenters treated the incident as a symptom of marketing-controlled third-party tags: one said Google Tag Manager&\#x27;s model led to heavy JavaScript on news pages and hoped teams would re-evaluate it, while another called for release controls and accountability from both Optimizely and large sites. Others questioned why high-profile sites would expose sensitive functions on the same origin and recommended NoScript to limit script exposure.

**Tags**: `#supply-chain-security`, `#web-security`, `#third-party-scripts`, `#optimizely`, `#malware-distribution`

---

<a id="item-tech-news-3"></a>
### [Carnegie Mellon launches CS Learn with free full-semester lectures](https://www.cs.cmu.edu/learn/) ⭐️ 7.0/10

Carnegie Mellon&\#x27;s Griffin School of Computer Science launched CS Learn, a site that publishes full-semester lecture videos from current CMU computer science courses for free on YouTube. One course is premiering each day this week, with more courses promised for January. The topics mentioned by the organizer and commenters include ML Systems and 15-259 Probability and Computing, though at least one of those courses was described as coming soon.

hackernews · pcompeau · Nov 16, 20:43 · [Discussion](https://news.ycombinator.com/item?id=50522980)

**「Background」** CMU’s Griffin School of Computer Science already maintains a general YouTube channel with 257 videos; CS Learn is a separate channel built around complete course playlists. It also enters a field long represented by MIT OpenCourseWare, which describes itself as offering free online open educational resources from more than 2,500 MIT courses.

**「What learners get now, and what&\#x27;s missing」** Self-learners can watch full-semester lectures from current CMU courses immediately at no cost, but the launch as described provides video lectures rather than enrolled credit, certification, or graded feedback. A commenter noted that courseware is described as coming next, so learners who need projects, notes, and a way to check their work will have to supply that themselves until it ships.

**「Community discussion」** Commenters welcomed specific courses, including Tianqi Chen&\#x27;s ML Systems and 15-259 Probability and Computing, and organizer Phillip Compeau said student-built tools automate much of production. One commenter argued that lectures alone can fall flat without projects, slides, and feedback, while another said learning fundamentals properly makes AI a power tool rather than a replacement.

<details><summary>References</summary>
<ul>
<li><a href="https://www.youtube.com/channel/UCqvooOJo8792T83va7LMMSA">CS Learn at Carnegie Mellon - YouTube</a></li>
<li><a href="https://www.youtube.com/CMUComputerScience">CMU Kenneth C. Griffin School of Computer Science - YouTube</a></li>
<li><a href="https://ocw.mit.edu/stories/mostafa-fawzy/">Mostafa Fawzy | MIT OpenCourseWare | Free Online Course Materials</a></li>

</ul>
</details>

**Tags**: `#computer science education`, `#CMU`, `#free courses`, `#machine learning systems`, `#online learning`

---

<a id="item-tech-news-4"></a>
### [Report claims Windows 11 collects coding-agent and developer-tool telemetry](https://xusheng.dev/posts/windows-coding-agent-telemetry/) ⭐️ 7.0/10

A report at xusheng.dev claims Windows 11 collects telemetry on which coding agents and developer tools users run. No source text was supplied with the item, so the exact fields collected, where they are sent, and the default setting are not independently established here. The claim prompted Hacker News discussion about developer privacy, platform trust, and alternatives to Windows.

hackernews · cwaffles · Nov 16, 22:58 · [Discussion](https://news.ycombinator.com/item?id=50524736)

**「Background」** The report is based on reverse engineering Windows 11&\#x27;s MissionControlAggregator, which places coding-agent and developer-tool usage bits into a diagnostic ETW report. Those bits are queued for upload when optional diagnostic data is enabled, and the U.S. configuration tested had that optional diagnostic data enabled.

**「Who is affected」** Developers running Windows 11 with diagnostic data left at the default &quot;optimal&quot; level may have developer-tool and coding-agent usage included in uploaded telemetry, according to the report. The reported opt-out is Settings → Privacy &amp; security → Diagnostics &amp; feedback, making that setting the concrete action point for developers who consider their tool choices sensitive.

**「Community discussion」** Commenters were divided: some described moving to Linux as increasingly practical, including for gaming, while others argued that GPU drivers and browsers already collect similar usage data. One commenter said Windows needs non-invasive telemetry to prioritize agent sandboxing because its MXC sandbox launched only in October and Claude Code does not yet support it, and another pointed readers to Settings → Privacy &amp; security → Diagnostics &amp; feedback to disable diagnostics.

<details><summary>References</summary>
<ul>
<li><a href="https://xusheng.dev/posts/windows-coding-agent-telemetry/">Windows 11 Is Collecting Data on Which Coding Agents and ...</a></li>
<li><a href="https://windowsforum.com/news/windows-11-optional-telemetry-can-report-coding-agent-usage-research-finds.452631/">Windows 11 Optional Telemetry Can Report Coding Agent Usage ...</a></li>
<li><a href="https://news.lavx.hu/article/windows-11-collects-data-on-coding-agents-and-developer-tools-you-use">Windows 11 Collects Data on Coding Agents and Developer Tools ...</a></li>

</ul>
</details>

**Tags**: `#Windows 11`, `#telemetry`, `#privacy`, `#developer tools`, `#AI coding agents`

---

<a id="item-tech-news-5"></a>
### [Jiff 1.0 releases as a Rust datetime library](https://burntsushi.net/jiff/) ⭐️ 7.0/10

Jiff 1.0, a datetime library for Rust from maintainer burntsushi, has reached its 1.0 release. The release gives Rust developers a new stable-version option alongside chrono, the longstanding crate discussed in the Hacker News thread. The supplied material does not detail Jiff&\#x27;s API, feature set, or compatibility guarantees beyond the 1.0 designation.

hackernews · burntsushi · Nov 16, 16:53 · [Discussion](https://news.ycombinator.com/item?id=50519744)

**「Background」** Jiff was developed through a pre-1.0 series before this release. Its GitHub release notes had said the next breaking-change release was planned as Jiff 1.0 in roughly six months, with the maintainer intending to commit to it indefinitely once 1.0 shipped.

**「Impact」** For Rust developers evaluating datetime crates, Jiff 1.0 is now a candidate with a 1.0 version, but the supplied discussion does not show migration commitments or ecosystem-wide adoption; commenters describe wider uptake as a hope.

**「Community discussion」** In the Hacker News thread, a former chrono maintainer said that crate&\#x27;s API stability made improvements difficult and expressed gratitude for Jiff, while other commenters praised Jiff for stating that it is not always the right tool and one asked about support for additional timescales such as UT1 in long-span orbital simulations. Those are individual opinions and open questions, not evidence of consensus.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/BurntSushi/jiff/releases">Releases · BurntSushi / jiff · GitHub</a></li>

</ul>
</details>

**Tags**: `#Rust`, `#datetime`, `#open source`, `#libraries`, `#API design`

---

<a id="item-tech-news-6"></a>
### [Marimba answers multiple speech queries from one frozen ASR encoder pass](https://www.reddit.com/r/MachineLearning/comments/1xxsqro/marimba_a_system_one_model_for_speech_r/) ⭐️ 7.0/10

Marimba, a preprint \(arXiv 2611.18330\) released with Apache-2.0 weights on Hugging Face and a pip package \(marimba-audio\), answers typed yes/no, multiple-choice, or score questions about an 8-second audio window and returns a calibrated probability from a single frozen Qwen3-ASR-0.6B encoder pass. Term spotting is zero-shot, scored from the decoder&\#x27;s greedy and four beam hypotheses and then Platt-calibrated; language ID uses the ASR model&\#x27;s own scores, while turn-end, speaker-change, and speaker-count predictions come from small readouts on frozen layers 18 and 12. On the same 1,000 public questions the authors report matching or beating Qwen3-Omni \(30B-A3B\) on 6 of 9 tests, 100% language ID on 300 FLEURS clips, and speaker-change AUROC of 0.966–0.980 on AMI and VoxConverse, but it loses to Smart Turn v3.2 on turn-end detection \(0.930 vs 0.982 AUROC on Smart Turn&\#x27;s own test set, and a 0.716 vs 0.712 tie on ICSI\) and every head is at chance on CochlScene scene classification. These are self-reported preprint results: the turn-end readout was trained on Smart Turn data, making that row in-distribution, and no independent validation is presented.

reddit · r/MachineLearning · /u/solanotodesch · Nov 16, 15:47

**「Background」** Marimba builds on the Qwen3-ASR-0.6B speech-recognition model: instead of training a separate model for each speech-analysis task, it reuses one frozen encoder pass and adds lightweight readouts or calibration for typed questions. The Reddit post is a follow-up to an earlier announcement and now points to the arXiv paper, Apache-2.0 weights, code, and a demo.

**「Impact」** Because every query reuses one encoder pass per window, adding an analysis costs only a small readout or calibration step rather than another full ASR run, which suits always-on speech pipelines that need several labels per window. The chance-level CochlScene result marks the practical boundary: the released checkpoints cover the query types described \(terms, language, turn end, speaker change and count\) and should not be assumed to transfer to new audio-classification tasks.

**Tags**: `#speech recognition`, `#efficient inference`, `#model calibration`, `#audio benchmarks`, `#machine learning`

---

<a id="item-tech-news-7"></a>
### [Duetto steers pretrained music transformer at sampling time for live jazz](https://www.reddit.com/r/MachineLearning/comments/1xxkyh3/steering_a_pretrained_music_transformer_at/) ⭐️ 7.0/10

Duetto, a project by Riccardo Cataldi, is a real-time jazz partner for a MIDI keyboard that runs a pretrained Anticipatory Music Transformer without fine-tuning and controls it at sampling time. Before each note, a rule layer masks disallowed events—such as a waiting hand, an out-of-register pitch, or an off-beat bass note—and biases likely ones such as chord tones, downbeat guide tones, and quoted phrases. The author reports roughly 12 ms per note for the medium model and 18 ms per note for the large model on an RTX 3080 Ti, with the large model at about 90 ms per note on a Jetson Orin Nano. The project includes a demo of “Autumn Leaves” at 160 bpm and code free for noncommercial use; the author says it can drift from the player, its responses are hard to predict, and the balance between model and rules is fragile.

reddit · r/MachineLearning · /u/GGAllin43 · Nov 16, 09:19

**「The model underneath Duetto」** Duetto steers the Anticipatory Music Transformer, published by John Thickstun, David Hall, Chris Donahue and Percy Liang in June 2023 as arXiv:2306.08620. That paper introduced &quot;anticipation,&quot; a method for building a controllable generative model of a temporal point process by conditioning on events rather than modeling only past context, which is the pretrained checkpoint the project reuses unchanged.

**「Deployment and licensing considerations」** Developers can reproduce the sampling-time steering approach on modest hardware: the author reports roughly 12–18 ms per note on a 3080 Ti and about 90 ms per note for the large model on a Jetson Orin Nano, which is enough for live play but leaves little latency headroom on edge devices. Teams considering a product should note the code is released free only for noncommercial use, so commercial deployment would require separate licensing or a reimplementation.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/abs/2306.08620">[2306.08620] Anticipatory Music Transformer</a></li>
<li><a href="https://www.emergentmind.com/papers/2306.08620">Anticipatory Music Transformer</a></li>

</ul>
</details>

**Tags**: `#music generation`, `#inference-time control`, `#transformers`, `#real-time systems`, `#open source`

---

<a id="item-tech-news-8"></a>
### [Amazon: AI Agents Stole API Keys to Fund More Model Calls](https://cybernews.com/security/amazon-autonomous-cybercrime-artex-framework/) ⭐️ 7.0/10

Amazon says it disrupted an AI-agent-driven campaign that stole API keys from publicly exposed AI applications, including LiteLLM and Dify, and reused them to pay for additional large-model calls. According to the company, attackers drove the agents with the open-source penetration-testing framework Artex, validated the stolen keys and pooled them; the campaign began on October 3 and was blocked by Amazon&\#x27;s MadPot honeypot network on November 5. Amazon attributed the activity to a China-related threat group with medium confidence, said not all listed targets were compromised, and notified AWS customers that may have been affected.

telegram · zaihuapd · Nov 16, 13:00

**「Background」** Amazon’s MadPot is an existing network of decoy sensors that gathers threat intelligence from attacker traffic and can disrupt activity using AWS network controls. In this campaign, the agents were reportedly run through ARTEX, an open-source AI penetration-testing framework, and hunted internet-exposed AI applications such as LiteLLM and Dify for stored provider API keys that authorize billable model calls.

**「What exposed AI deployments should do」** For teams running LiteLLM, Dify, One API, or similar AI gateways on the public internet, the concrete risk is that a harvested master key can be reused for model calls billed to the victim, turning the theft into direct compute costs. Amazon says it notified potentially affected AWS customers but that not every listed target was compromised, so operators should check public exposure, rotate provider keys, and set spending limits rather than assume the Nov. 5 disruption resolved the exposure.

<details><summary>References</summary>
<ul>
<li><a href="https://qz.com/amazon-ai-agents-steal-provider-keys-artex-111626">Amazon captured records of AI agents trying to steal AI keys</a></li>
<li><a href="https://thehackernews.com/2026/11/amazon-uncovers-ai-agent-campaign.html">Amazon Uncovers AI Agent Campaign Targeting LiteLLM, Dify, and...</a></li>
<li><a href="https://www.aboutamazon.com/news/aws/amazon-madpot-stops-cybersecurity-crime">How Amazon helps stop cybersecurity threats across the internet</a></li>
<li><a href="https://thehackernews.com/2026/11/amazon-uncovers-ai-agent-campaign.html">Amazon Uncovers AI Agent Campaign Targeting LiteLLM, Dify ...</a></li>

</ul>
</details>

**Tags**: `#AI security`, `#API key theft`, `#autonomous agents`, `#AWS`, `#cybercrime`

---

<a id="item-tech-news-9"></a>
### [US extends AI chip export controls to remote access](https://www.reuters.com/legal/litigation/us-issues-rule-protect-advanced-ai-chips-being-accessed-remotely-2026-11-16/) ⭐️ 7.0/10

On Nov 16, the US Commerce Department issued an interim final rule extending export controls on advanced AI chips and servers to remote access, aiming to prevent third-country data centers from circumventing existing restrictions. According to the source, the Treasury Department and National Security Council led drafting of the rule, which could further tighten China&\#x27;s access to advanced chips. The Verge reported that the measure also requires licenses to re-export AI chips to Indonesia, Malaysia, Singapore, Thailand, and Brazil. The source did not provide the rule text, detailed scope, or effective date.

telegram · zaihuapd · Nov 16, 14:44

**「Background」** Previously, U.S. export controls covered the physical shipment of advanced AI chips and servers, allowing chips hosted in third-country data centers to serve restricted users without a license. The Commerce Department&\#x27;s Bureau of Industry and Security \(BIS\) issued this interim final rule explicitly to address &quot;remote access to advanced super intelligence \(SI\) chips and servers,&quot; closing a channel that earlier controls left open, as Reason noted that chip export controls had &quot;largely failed to stop transshipments&quot; through third countries.

**「Compliance impact」** Suppliers and data-center operators exporting, reexporting, or transferring advanced semiconductors to or within Indonesia, Malaysia, Singapore, Thailand, or Brazil now need a license, reviewed case by case with weight given to each country’s export-control enforcement. The rule excludes commercial recommender systems, so organizations should confirm whether their workload falls within that exception before moving hardware.

<details><summary>References</summary>
<ul>
<li><a href="https://reason.com/2026/11/16/trumps-new-chip-export-rule-targets-china-but-exempts-tiktoks-parent-company/">Trump’s new chip export rule exempts TikTok’s parent company</a></li>
<li><a href="https://wccftech.com/the-u-s-shuts-chinas-access-to-advanced-chips-via-singapore-brazil-indonesia-malaysia-and-thailand-as-scott-bessent-gives-nvidia-10-days-to-show-it-did-not-goose-its-revenues/">The U.S. Shuts China&#x27;s Access To Advanced Chips Via Singapore...</a></li>
<li><a href="https://www.nixonpeabody.com/insights/alerts/2026/11/16/bis-targets-remote-access-to-advanced-chips-through-overseas-data-centers">BIS targets remote access to advanced chips through overseas ...</a></li>
<li><a href="https://kpmg.com/us/en/taxnewsflash/news/2026/11/commerce-advanced-semiconductor-export-controls.html">U.S. Commerce restricts remote access to advanced ...</a></li>
<li><a href="https://www.datacenterdynamics.com/en/news/us-dept-of-commerce-issues-rule-to-restrict-remote-access-to-advanced-ai-chips/">US Dep’t of Commerce issues rule to restrict remote access to ...</a></li>

</ul>
</details>

**Tags**: `#AI芯片`, `#出口管制`, `#美国政策`, `#半导体`, `#数据中心`

---

<a id="item-tech-news-10"></a>
### [Alibaba, Tencent and Moonshot Curtail Offensive Cyber Capabilities in New Models](https://www.bloomberg.com/news/articles/2026-11-16/china-s-top-ai-firms-limit-cyber-capabilities-in-latest-models) ⭐️ 7.0/10

Alibaba, Tencent and Moonshot reportedly weakened the offensive cyber capabilities of their new-generation models while improving defensive performance, according to Bloomberg. Alibaba&\#x27;s latest flagship Qwen was not released as open weights, so users cannot download and customize the full version. Tencent cut cyber functions in its Hy4 model before releasing it this month. The changes are tied to a draft export-control rule published by the Ministry of Commerce last month that would ban exports of AI tools capable of attacking critical infrastructure and government networks; the reported curbs and the draft rule&\#x27;s eventual scope are not independently confirmed.

telegram · zaihuapd · Nov 17, 02:20

**「The export-control draft behind the changes」** China&\#x27;s Ministry of Commerce and Ministry of Science and Technology published a draft update to the national catalog of export-banned and export-restricted technologies on October 16, 2026, covering 40 technologies — 23 of them in AI, including large models, agents and compute clusters — with public comment open through November 15 \(tool-2-1, tool-2-3\). The MOFCOM notice states that technologies already in the public domain through open-sourcing or published papers fall outside the managed scope, while law-firm analysis of the draft advised companies deploying China-developed models or agents abroad to assess whether the use could trigger the controls \(tool-2-1, tool-2-2\).

**「Impact」** Developers who relied on downloadable Qwen weights must switch to Alibaba&\#x27;s hosted API for the flagship, since Qwen4-Max ships without open weights, ruling out local fine-tuning and offline deployment of the top-tier model. Security teams that used earlier Qwen or Tencent releases for red-teaming should also re-validate results, because Tencent reportedly stripped cyber capabilities from Hy4 before its release this month.

<details><summary>References</summary>
<ul>
<li><a href="https://www.mofcom.gov.cn/zwgk/zcfb/art/2026/art_0a31a3c9ac404f7a9b0e917ce3412997.html">商务部 科技部公告2026年第48号 就修订《中国禁止出口限制出口技术目...</a></li>
<li><a href="https://sanctionsnews.bakermckenzie.com/china-proposes-expanded-export-controls-on-ai-biopharma-and-solar-energy-technologies/">China Proposes Expanded Export Controls on AI, Biopharma and ...</a></li>
<li><a href="https://apnews.com/article/china-export-restrictions-ai-chips-solar-us-5ac381c0c6d6628bbea2e0da7d855a5b">China moves to curb tech exports including for AI and solar ...</a></li>
<li><a href="https://thenextweb.com/news/alibaba-launches-qwen4-max-flagship-ai-model-without-open-weights">Alibaba launches Qwen4-Max flagship AI model without open weights</a></li>

</ul>
</details>

**Tags**: `#AI policy`, `#China AI`, `#cybersecurity`, `#open weights`, `#model releases`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Lutnick faces scrutiny over Cantor Fitzgerald&\#x27;s Nvidia ties](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 8.0/10

Commerce Secretary Howard Lutnick is facing questions over his former firm Cantor Fitzgerald&\#x27;s Nvidia ties after Axios reported he resisted a U.S. crackdown on suspected chip smuggling to China and had received a classified warning about Nvidia CEO Jensen Huang&\#x27;s ties to a suspected Chinese spy; Huang resigned Thursday. Cantor&\#x27;s securities filings show its reported Nvidia stake fell 49% over the six months to March 2026, to 1.78 million shares worth $310 million, according to CNBC&\#x27;s analysis.

rss · CNBC Finance · Nov 16, 12:14

**「Background」** Howard Lutnick left Cantor Fitzgerald to become commerce secretary in February 2025. Nvidia CEO Jensen Huang resigned on Nov. 12 after reports of extramarital affairs, including with a woman suspected of working for Chinese intelligence, according to PC Gamer.

<details><summary>References</summary>
<ul>
<li><a href="https://www.pcgamer.com/software/ai/trump-supports-jensen-huangs-return-as-nvidia-ceo-but-it-doesnt-sound-like-the-board-is-interested/">Trump supports Jensen Huang &#x27;s return as Nvidia CEO... | PC Gamer</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#Howard Lutnick`, `#Cantor Fitzgerald`, `#U.S.-China export controls`, `#conflict of interest`

---

<a id="item-finance-news-2"></a>
### [Nvidia CEO exit and Democratic Congress could reshape AI trade, ETF experts say](https://www.cnbc.com/2026/11/14/nvidia-ai-trade-data-centers-congress.html) ⭐️ 7.0/10

Nvidia CEO Jensen Huang resigned and Democrats won control of Congress—developments that exchange-traded fund experts said in a Monday interview before the resignation could redirect the AI stock trade toward Big Tech and rival chipmakers. Yorkville Ives cut its Nvidia price target to $225 from $300 but kept a buy rating, and Nvidia shares closed the week at $162.85.

rss · CNBC Finance · Nov 16, 12:13

**「Background」** Nvidia&\#x27;s interim CEO and CFO, Colette Kress, will face investors when the company reports third-quarter earnings next Tuesday, its first results since Huang&\#x27;s departure.

**「Impact」** If Congress slows data-center construction, Yorkville Ives estimates 10% of planned data centers may not be built on the low end and 15%-20% on the high end, which could affect cloud operators and chip suppliers even as demand is said to outstrip supply four to one.

**Tags**: `#Nvidia`, `#AI trade`, `#ETFs`, `#semiconductors`, `#US policy`

---

<a id="item-finance-news-3"></a>
### [Intel and CEO Lip-Bu Tan Face Shareholder Class Action](https://www.investing.com/news/stock-market-news/intel-sued-by-shareholders-following-29-stock-plunge-5028171) ⭐️ 7.0/10

Intel and CEO Lip-Bu Tan were sued by shareholders in a class action alleging the company concealed weak PC demand and inventory buildup before its Oct. 29 fourth-quarter revenue and profit forecast fell short of expectations, sending the stock down 28.6% the next day and erasing about $140 billion in market value. The suit, led by a Michigan pension fund and filed Friday in federal court in San Jose, seeks damages on behalf of investors who bought Intel shares between July 23 and Oct. 29, 2026, and also names CFO Zinsner as a defendant.

telegram · zaihuapd · Nov 16, 11:10

**「Background」** The class action—a lawsuit brought on behalf of affected investors—follows Intel’s Oct. 29 fourth-quarter forecast, after which management said it did not expect the PC market to recover in 2027 and projected unit volumes to decline again, with memory shortages limiting sales of other system components.

<details><summary>References</summary>
<ul>
<li><a href="https://www.fool.com/earnings/takeaways/2026/10/30/intel-3-key-takeaways-for-long-term-investors/">Intel : 3 Key Takeaways for Long-Term Investors | The Motley Fool</a></li>

</ul>
</details>

**Tags**: `#Intel`, `#shareholder class action`, `#earnings guidance`, `#stock plunge`, `#semiconductors`

---