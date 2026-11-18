---
layout: default
title: "Horizon Summary: 2026-11-18 (EN)"
date: 2026-11-18
lang: en
---

> From 43 items, 12 important content pieces were selected

---

**Technology News**
1. [OpenAI releases GPT-6.2 Astra and Sol with lower Astra pricing](#item-tech-news-1) ⭐️ 9.0/10
2. [Java4Shell RCE in OpenJDK Base64 processing disclosed](#item-tech-news-2) ⭐️ 8.0/10
3. [Microsoft&\#x27;s ONNX Runtime GitHub Repository Goes Dark](#item-tech-news-3) ⭐️ 8.0/10
4. [Datasette Lite rewritten with service workers to run full Datasette in the browser](#item-tech-news-4) ⭐️ 8.0/10
5. [Phrack Issue 73 Released With Docker Escape and SSH1 History](#item-tech-news-5) ⭐️ 7.0/10
6. [Cloudflare Post Casts Quad9&\#x27;s France Exit as DNS Regulation Warning](#item-tech-news-6) ⭐️ 7.0/10
7. [SolidJS 2.0 Adds Server RPC, Live/Broadcast, and Diagnostics](#item-tech-news-7) ⭐️ 7.0/10
8. [Nvidia stops disclosing Singapore sales after $104B subsidiary revenue](#item-tech-news-8) ⭐️ 7.0/10
9. [Three external sandbox servers released for AI coding agents](#item-tech-news-9) ⭐️ 7.0/10
10. [China&\#x27;s Q/V-band wireless test hits 27 Gbps bidirectional, setting domestic record](#item-tech-news-10) ⭐️ 7.0/10

**Financial News**
1. [UK tribunal dismisses £1.97bn Sony PlayStation Store class action](#item-finance-news-1) ⭐️ 7.0/10
2. [China Reviews 17 Automakers’ 60-Day Supplier Payment Terms](#item-finance-news-2) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [OpenAI releases GPT-6.2 Astra and Sol with lower Astra pricing](https://openai.com/index/introducing-gpt-6-2-astra-sol/) ⭐️ 9.0/10

OpenAI introduced GPT-6.2 Astra, a frontier model for difficult projects, and GPT-6.2 Sol, an efficient model for everyday work; both are available through the API as gpt-6.2-astra and gpt-6.2-sol. Astra costs $8 per million input tokens and $40 per million output tokens, 80% of GPT-6 Astra&\#x27;s $10/$50, with cached input at $0.40 per million versus $1. Sol remains at $2/$10, matching GPT-6.1 Sol and GPT-6 Sol and half the price of GPT-5.6 Sol. Early reactions are mixed: Simon Willison reports Astra trailing Claude Fable 5.2 on several benchmarks, and some users criticize its communication style, while commenters also cite large cost reductions.

hackernews · jasondavies · Nov 17, 17:46 · [Discussion](https://news.ycombinator.com/item?id=50535230)

**「Earlier models and pricing」** OpenAI’s preceding lineup included GPT-6 Astra and GPT-6.1 Sol. The new release keeps a two-tier structure: Astra is positioned for harder projects and Sol for everyday work, with Astra’s API list price set at $8 per million input tokens and $40 per million output tokens, compared with $10/$50 for GPT-6 Astra.

**「Impact」** For developers running long agentic sessions, Astra&\#x27;s cached input price falls to $0.40 per million tokens from $1 for GPT-6 Astra, reducing a recurring cost that grows with context-heavy, multi-step work.

**「Community discussion」** Commenters were split: chriddyp reported similar accuracy on a data-analytics exam at about $4 for Astra versus $20 for the earlier V6 and $1.2 for Sol versus $2.6 for GPT-6.1 Sol, with fast responses but occasional early stops that missed the answer, while Topfi called OpenAI&\#x27;s office-work examples poor. thefourthchime&\#x27;s PacBench run put Astra at 92 in 6.6 minutes for $2.04, just behind Kimi K3.1 Pro&\#x27;s 93 at $0.68.

**Tags**: `#OpenAI`, `#LLM`, `#model release`, `#benchmark`, `#cost efficiency`

---

<a id="item-tech-news-2"></a>
### [Java4Shell RCE in OpenJDK Base64 processing disclosed](https://calif.io/java4shell/) ⭐️ 8.0/10

A technical disclosure describes CVE-2026-114938, a Java4Shell remote code execution flaw in OpenJDK&\#x27;s Base64 processing that carries a CVSS 4.0 score of 9.2 and is reported to have gone undetected for nearly four years. It affects Java 17 from 17.0.6 onward, plus Java 21, 25 and 27; standard Java 8 and 11 are generally unaffected, except Oracle Java 8 Performance Pack. The reported exposure is limited to x86-64 servers with AVX-512 VBMI—roughly Intel Ice Lake and newer Xeon and AMD Zen 4 and newer EPYC/Ryzen—while ARM64 is unaffected. The source does not state a fix version or whether public exploitation has occurred.

hackernews · werrett · Nov 17, 21:11 · [Discussion](https://news.ycombinator.com/item?id=50538240)

**「Background」** The reported flaw depends on a specific x86-64 vector instruction-set extension, AVX-512 VBMI, rather than on Java&\#x27;s platform-neutral code paths; that restricts the stated exposure to recent Intel and AMD server processors and excludes ARM64 hosts. The source says the defect remained latent for nearly four years across the affected JDK lines, which is why the scope centers on newer OpenJDK releases and not standard Java 8/11 deployments.

**「Impact」** For defenders, the practical scoping question is not just the Java version but also the JDK distribution and hardware: a community detection note says the condition applies to HotSpot-based OpenJDK, Oracle JDK and GraalVM, while OpenJ9 and GCJ do not generate the relevant stub. Organizations should inventory internet-facing services that decode Base64 and prioritize hosts running the listed Java lines on AVX-512 VBMI x86-64 CPUs.

**「Community discussion」** Commenters highlighted that the exploit&\#x27;s heap grooming is network-sensitive, with one quoting the write-up that low, stable round-trip times and jitter are preferred and that the attack was tested over public IP addresses. Another commenter shared Semgrep detection scripts aimed at five conditions and noted that only HotSpot generates the stub; a separate commenter said an AVX-512 Base64 decoding link and the -XX:UseAVX=2 workaround were unconfirmed suggestions from Twitter.

**Tags**: `#OpenJDK`, `#Java security`, `#remote code execution`, `#CVE`, `#exploit analysis`

---

<a id="item-tech-news-3"></a>
### [Microsoft&\#x27;s ONNX Runtime GitHub Repository Goes Dark](https://github.com/microsoft/onnxruntime) ⭐️ 8.0/10

The microsoft/onnxruntime GitHub repository, a widely used machine-learning runtime, has become inaccessible with no advance warning, according to developers reporting the outage. Users said evaluation pipelines began failing on the morning the repository disappeared, and the project&\#x27;s roughly 22,000-star presence is no longer available at its usual URL. The cause, permanence, and any connection to a security incident remain unconfirmed; Microsoft has not publicly explained the removal.

hackernews · nvader · Nov 17, 23:18 · [Discussion](https://news.ycombinator.com/item?id=50539610)

**「Background」** ONNX Runtime is Microsoft&\#x27;s cross-platform engine for running and training machine-learning models, and it is widely used to serve models in production, so its disappearance immediately broke downstream evaluation and deployment pipelines. Discussion of the takedown has also pointed to an earlier reported parser flaw, described as allowing a crafted ONNX model to make the runtime read arbitrary file paths or memory addresses without validation; commenters speculate that the removal may relate to that flaw or to a separate compromised Microsoft package, but no cause has been confirmed by Microsoft or GitHub.

**「Pipeline disruption」** One commenter reported that evaluation jobs began failing the same morning the microsoft/onnxruntime repository went dark, with no advance warning or official migration guidance in the thread. The suggested fallback, Intel&\#x27;s onnxruntime fork, includes OpenVINO-specific modifications, so teams should treat it as requiring compatibility testing rather than a drop-in replacement.

**「Community Discussion」** Commenters speculated that the removal could be related to a compromised package or a broader security cleanup, while another raised the possibility of newly discovered backdoor vectors in models. Developers also pointed to Intel&\#x27;s onnxruntime fork as a temporary alternative, though it includes Intel&\#x27;s OpenVINO modifications; one commenter separately claimed ONNX collects application telemetry that can only be avoided by building from source with telemetry disabled.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/microsoft/onnxruntime">GitHub - microsoft /onnxruntime: ONNX Runtime : cross-platform, high...</a></li>
<li><a href="https://news.ycombinator.com/item?id=50539610">Microsoft &#x27;s ONNX Runtime has disappeared from GitHub</a></li>

</ul>
</details>

**Tags**: `#ONNX Runtime`, `#Microsoft`, `#open source`, `#supply chain security`, `#GitHub`

---

<a id="item-tech-news-4"></a>
### [Datasette Lite rewritten with service workers to run full Datasette in the browser](https://simonwillison.net/2026/Nov/17/datasette-lite/) ⭐️ 8.0/10

Simon Willison released a complete rewrite of Datasette Lite that uses service workers and Pyodide to run the full Datasette Python application in the browser, rather than injecting server-rendered HTML into the page. A crafted URL to lite.datasette.io can load a SQLite database, JSON file, CSV file or SQL script; select a released Datasette version from PyPI or a specific GitHub commit, tag or branch; choose from over 100 SQLite versions; and install Datasette plugins from PyPI or wheel URLs, repeating the \`install\` parameter as needed. The original 2022 version simulated requests through a Pyodide web worker and wrote the resulting HTML into the top-level page with \`innerHTML\`, so features relying on JavaScript failed because script tags inserted that way do not execute; Willison says the rewritten version is now almost indistinguishable from the server-side application. Remote database and metadata URLs must be served with open CORS headers, which is why the example loads files from Gists.

rss · Simon Willison · Nov 17, 16:48

**「Background」** Datasette Lite launched in 2022 as a Pyodide/WebAssembly port that ran Datasette in a web worker, simulated requests through that stack, and injected the resulting HTML into the top-level page using \`innerHTML\`. Because script tags inserted via \`innerHTML\` do not execute, JavaScript-dependent features and additional plugins failed to work. The rewrite replaces that workaround with service workers, allowing the full Datasette Python application to handle browser requests more like the server-side version.

**「Impact」** Because the URL can pin a Datasette version, commit, SQLite version and plugin set, developers can link to a reproducible demo of a work-in-progress feature or a bug without standing up a web server. Willison reports already using it this way in Datasette&\#x27;s own issue tracker, posting \`?ref=1.0a42\` and \`?ref=1.0a43\` links to show a pagination bug and its fix.

**Tags**: `#Datasette`, `#Pyodide`, `#WebAssembly`, `#service workers`, `#SQLite`

---

<a id="item-tech-news-5"></a>
### [Phrack Issue 73 Released With Docker Escape and SSH1 History](https://phrack.org/issues/73/introduction_md) ⭐️ 7.0/10

Phrack issue 73 has been released, giving security researchers and hacker-culture readers a new set of articles. Commenters identify a Docker escape piece and a history of the 2000 SSH1 exploit among the contents. The release has also prompted a disclosure question: one reader asks whether the Docker escape was responsibly disclosed and assigned a CVE, or published without warning. The supplied item contains no issue text, so the full contents and disclosure status are not independently confirmed here.

hackernews · notmine1337 · Nov 17, 18:31 · [Discussion](https://news.ycombinator.com/item?id=50535992)

**「Background」** Phrack is a long-running, community-produced hacker publication that mixes original security research with historical writeups. Issue 73 includes a &quot;Phrack World History&quot; section that revisits the 2000 SSH1 CRC32 vulnerability, CVE-2001-0144, described in the issue as a pre-authentication, instant-root flaw affecting default SSH1 installs.

**「Impact」** Security teams reviewing the issue will need to check the Docker escape article against vendor advisories and CVE records, since the supplied comments do not establish whether that exploit was disclosed before publication.

**「Community Discussion」** Commenters raised whether the Docker escape was responsibly disclosed and assigned a CVE or dropped without warning, while one reader praised Phrack&\#x27;s unpolished style as enabling freer expression. Another pointed to the issue&\#x27;s history of the 2000 SSH1 exploit as a useful reflection on how fast security moves.

<details><summary>References</summary>
<ul>
<li><a href="https://phrack.org/issues/73/introduction_md">Introduction - phrack.org</a></li>
<li><a href="https://archives.phrack.org/dl/73/the-2000-ssh1-exploit-that-broke-the-internet.pdf">PHRACK-2026-DTP-main-content (1)</a></li>

</ul>
</details>

**Tags**: `#security research`, `#exploit development`, `#responsible disclosure`, `#Phrack`, `#hacker culture`

---

<a id="item-tech-news-6"></a>
### [Cloudflare Post Casts Quad9&\#x27;s France Exit as DNS Regulation Warning](https://blog.cloudflare.com/quad9-withdrawal-from-france/) ⭐️ 7.0/10

A Cloudflare blog post, discussed on Hacker News, frames Quad9&\#x27;s withdrawal from France over court-ordered DNS blocking as an early warning about internet regulation. The post is competitor commentary rather than a new Cloudflare policy; commenters note that Cloudflare states opposition but makes no concrete commitment to withdraw from countries where it loses similar appeals. Quad9 CTO John Todd said in the thread that support at IETF 127 was strong so far and that attendees felt &quot;general dread&quot; about DNS blocking cases, while noting that IETF participants sometimes object just to be contrarian.

hackernews · subset · Nov 17, 22:13 · [Discussion](https://news.ycombinator.com/item?id=50538994)

**「Earlier ruling and withdrawal」** Quad9, a Swiss non-profit operating a free public DNS resolver, announced in late October 2026 that it would withdraw from France after months of litigation. A French court had ordered it to block sports-streaming domains tied to alleged copyright infringement and imposed daily penalties for non-compliance; Quad9 argued that altering DNS answers as required was technically unfeasible and refused. The dispute follows earlier friction over geo-blocking, including a German case in which a rights holder used a VPN to circumvent a Quad9 block and Quad9 was subsequently fined for contempt.

**「Impact」** For French users and network operators, Quad9&\#x27;s withdrawal removes a public resolver option, making resolver selection and fallback configuration a continuity concern. Operators who depended on Quad9 should plan for an alternative resolver and update fallback settings.

**「Community Discussion」** Commenters broadly criticized the blocking mandates as overregulation and lamented what they see as the decline of earlier European internet freedoms, with one urging readers not to vote for politicians who support such rules. The sharpest challenge to the vendor came from driverdan, who asked Cloudflare to commit to withdrawing from affected countries if it loses its appeal rather than only stating opposition.

<details><summary>References</summary>
<ul>
<li><a href="https://blog.cloudflare.com/quad9-withdrawal-from-france/">Quad9’s withdrawal from France: A canary in the coal mine</a></li>
<li><a href="https://disputeindex.com/cases/quad9-france-bein-dns-blocking-withdrawal">Quad9 plans France withdrawal over beIN site-blocking orders</a></li>
<li><a href="https://reclaimthenet.org/quad9-leaving-france-over-dns-blocking-order">Quad9 to Leave France Over DNS Blocking Order - Reclaim The Net</a></li>

</ul>
</details>

**Tags**: `#DNS`, `#internet regulation`, `#privacy`, `#content blocking`, `#network infrastructure`

---

<a id="item-tech-news-7"></a>
### [SolidJS 2.0 Adds Server RPC, Live/Broadcast, and Diagnostics](https://www.solidjs.com/blog/solid-2-0-the-long-hold/) ⭐️ 7.0/10

SolidJS 2.0 has been published as a major release of the reactive JavaScript framework for frontend developers. The release discussion highlights server-side RPC and &quot;live&quot; and &quot;broadcast&quot; features, along with improved diagnostics, including material framed as &quot;Built to Be Written by Agents.&quot; The supplied material does not include exact availability, migration requirements, or independently measured performance results.

hackernews · pier25 · Nov 17, 18:56 · [Discussion](https://news.ycombinator.com/item?id=50536387)

**「Prior development」** SolidJS&\#x27;s path to 2.0 was set out in a GitHub roadmap discussion that described planned changes across a few key areas and drew community concern over changes to createEffect and whether existing code could be migrated feasibly. The 2.0 release was preceded by a release candidate that the project promoted on its own site.

**「Impact」** Developers evaluating Solid 2.0 get built-in server RPC plus live and broadcast primitives, which one commenter describes as more seamless than LiveView or htmx/Datastar; teams already using those stacks therefore have a concrete integration model to compare before switching. The improved diagnostics grouped under the release&\#x27;s agent-oriented messaging are also ordinary debugging aids, so they benefit hand-written Solid code as well.

**「Community Discussion」** One commenter argued that the diagnostics marketed for agent-assisted coding are also better for hand-written code, while another said Solid&\#x27;s server RPC and live/broadcast features feel more seamless than LiveView or htmx/datastar and address a gap Remix did not close. A separate commenter said they are waiting for Vue 3.6 Vapor and have moved code off Vue since 3.5, but did not connect that experience to measured Solid 2.0 performance.

<details><summary>References</summary>
<ul>
<li><a href="https://github.com/solidjs/solid/discussions/2425">The Road to 2 . 0 · solidjs solid · Discussion #2425 · GitHub</a></li>
<li><a href="https://www.solidjs.com/">SolidJS · Reactive Javascript Library</a></li>

</ul>
</details>

**Tags**: `#SolidJS`, `#JavaScript frameworks`, `#frontend development`, `#reactivity`, `#server RPC`

---

<a id="item-tech-news-8"></a>
### [Nvidia stops disclosing Singapore sales after $104B subsidiary revenue](https://www.ft.com/content/dbde7a30-548c-4f9d-a4be-7898a0c24dcf) ⭐️ 7.0/10

FT reports that Nvidia stopped disclosing Singapore sales after the external revenue of its Singapore subsidiary reached $104 billion, amid scrutiny of chip flows and export controls. The report does not establish that the figure represents local demand in Singapore or that the chips were ultimately shipped to China; it reflects sales booked through the subsidiary. The supplied material does not include an Nvidia explanation for the disclosure change.

hackernews · louiereederson · Nov 17, 17:12 · [Discussion](https://news.ycombinator.com/item?id=50534631)

**「Background」** US and Singapore authorities have been investigating Megaspeed, a Singapore-based Nvidia customer, over possible violations of chip export rules; the US Commerce and Justice departments have investigated since 2024, and Singapore police have also probed the company. Nvidia&\#x27;s board has separately created a committee to oversee exports and national security issues. The investigations have raised questions about Nvidia&\#x27;s ability to track its chip exports effectively and comply with US restrictions on advanced AI chip sales to China.

**「Impact」** Investors and export-control analysts lose a country-level disclosure they could previously use to track revenue booked through Singapore, leaving them to rely on broader regional reporting and subsidiary filings. Because the $104 billion is an accounting attribution rather than evidence of end use, the change also makes it harder to use Singapore bookings as a proxy for China-bound chip sales.

**「Community discussion」** Commenters dispute the implication that the $104 billion reflects Singapore demand: tamarind44 says it is the Singapore subsidiary&\#x27;s external revenue, including orders routed through that entity, while legitster argues the disclosure change is an accounting-attribution issue that says nothing about where chips end up. Those interpretations are commenter opinions, not independent confirmation of Nvidia&\#x27;s motives.

<details><summary>References</summary>
<ul>
<li><a href="https://www.theguardian.com/technology/2026/nov/17/nvidia-jensen-huang-statement">Jensen Huang says he would be ‘honored’ to return to Nvidia as CEO</a></li>
<li><a href="https://forums.hardwarezone.com.sg/threads/singapore-police-probe-nvidia-customer-megaspeed-over-alleged-china-export-violations.7162980/">Singapore police probe Nvidia customer Megaspeed over alleged...</a></li>

</ul>
</details>

**Tags**: `#Nvidia`, `#semiconductors`, `#export controls`, `#AI hardware`, `#corporate disclosure`

---

<a id="item-tech-news-9"></a>
### [Three external sandbox servers released for AI coding agents](https://simonwillison.net/2026/Nov/17/external-sandboxes-for-coding-agents/) ⭐️ 7.0/10

Simon Willison and Prime Radiant have released three sandbox server implementations for the external sandbox pattern, in which an AI coding agent runs outside a dedicated sandbox while the code it executes runs inside one. The implementations are external-sandbox-v86, a Node.js server running Alpine Linux in WebAssembly via v86; external-sandbox-container, a Python server running Alpine Linux in an Apple Containers instance; and external-sandbox-quicksand, a Python server using Microsoft&\#x27;s Quicksand library, which bundles QEMU and Alpine Linux in a Python package. All three expose the same localhost API, which can be configured in Pi, Claude Code, or Codex for code execution. They also include an optional HTTP/HTTPS allow-list proxy and a credential replacement mechanism intended to let agent code make authenticated API calls without receiving the secret.

rss · Simon Willison · Nov 17, 22:52

**「Background」** Sandboxing runs untrusted code in an isolated environment so mistakes or malicious instructions cannot freely affect the host machine. In this external sandbox pattern, that boundary is placed around the code the agent executes rather than around the agent itself: the agent stays outside and sends execution requests to a sandbox server over a localhost API. The stated motivation is making it safer to try local models despite the risk of prompt injection.

**「Impact」** Developers testing local models can point Pi, Claude Code, or Codex at a sandbox&\#x27;s localhost API, keeping the agent outside the execution environment; the allow-list proxy restricts which hosts its code can reach, and credential replacement avoids handing the agent a secret. Adoption requires configuring the agent to call that API.

**Tags**: `#AI coding agents`, `#sandboxing`, `#prompt injection`, `#security`, `#local models`

---

<a id="item-tech-news-10"></a>
### [China&\#x27;s Q/V-band wireless test hits 27 Gbps bidirectional, setting domestic record](https://www.news.cn/tech/20261117/d6323540dccf4e2a976c48a762795956/c.html) ⭐️ 7.0/10

Researchers from the Aerospace Information Research Institute of the Chinese Academy of Sciences and partner institutions reported a bidirectional Q/V-band wireless communication experiment at the Lijiang China Remote Sensing Satellite Ground Station, reaching 27 Gbps using dual carriers and polarization multiplexing. A single channel achieved 6.75 Gbps bidirectional under 512QAM, and the team tested modulation from 64QAM through 512QAM; the report describes the result as China&\#x27;s highest data rate in this band, with key indicators called domestically leading and internationally advanced. The team aims to exceed 50 Gbps, but the demonstration is an experimental, single-site validation reported by Xinhua, not an independently confirmed world record or a commercially deployed service.

telegram · zaihuapd · Nov 17, 08:45

**「Why Q/V band matters」** The Q/V band is a millimeter-wave range that satellite and future 6G planners treat as a key candidate because it offers roughly 10 GHz of available bandwidth, far more than conventional lower-frequency links, for ultra-high-speed satellite communications. The trade-off is heavy atmospheric attenuation and rain fade at those frequencies, which is why work in this band centers on link-budget and modulation techniques rather than routine commercial service today.

<details><summary>References</summary>
<ul>
<li><a href="https://www.asiaict.com/finance/22484.html">China&#x27;s 6G Communications Breakthrough: Q/V-Band Experiment ...</a></li>
<li><a href="https://www.rfwireless-world.com/terminology/q-v-band-satellite-communication">Q/V-Band SATCOM: Advantages &amp; Disadvantages - RF Wireless World</a></li>

</ul>
</details>

**Tags**: `#Q/V频段`, `#6G`, `#卫星互联网`, `#512QAM`, `#无线通信`

---

## Financial News

<a id="item-finance-news-1"></a>
### [UK tribunal dismisses £1.97bn Sony PlayStation Store class action](https://www.reuters.com/world/sony-defeats-2-billion-uk-claim-over-playstation-store-pricing-2026-11-17/) ⭐️ 7.0/10

The UK Competition Appeal Tribunal dismissed a class action seeking about £1.97 billion from Sony over alleged abuse of dominance in PlayStation Store digital content pricing, ruling that competition between consoles constrained how Sony priced. The case had been brought on behalf of about 12.2 million UK consumers.

telegram · zaihuapd · Nov 17, 16:02

**「Background」** The case was first filed in August 2022 and cleared to proceed in November 2023 as an opt-out collective claim—a UK procedure that lets one representative sue for a defined group without each member signing up—covering about 12.2 million UK PlayStation users, and was then valued at up to £5 billion.

<details><summary>References</summary>
<ul>
<li><a href="https://www.brickcourt.co.uk/news/detail/competition-appeal-tribunal-dismisses-2-billion-playstation-class-action-against-sony">Competition Appeal Tribunal dismisses £2 billion PlayStation ...</a></li>

</ul>
</details>

**Tags**: `#Sony`, `#PlayStation Store`, `#UK Competition Appeal Tribunal`, `#class action`, `#competition law`

---

<a id="item-finance-news-2"></a>
### [China Reviews 17 Automakers’ 60-Day Supplier Payment Terms](http://www.caam.org.cn/chn/5/cate_68/con_5237404.html) ⭐️ 7.0/10

China’s Ministry of Industry and Information Technology has asked the China Association of Automobile Manufacturers to assess whether 17 major automakers pay suppliers within 60 days, CAAM said in a Nov. 16 notice. The review also checks that cash and bank-acceptance payments to non-small and medium-sized suppliers are at least 80%, and calls for company submissions, a task-force review, expert evaluation and public release.

telegram · zaihuapd · Nov 18, 01:15

**「Background」** China&\#x27;s 60-day payment ceiling comes from the national regulation on payments to small and medium-sized enterprises that took effect on 1 June 2025, which major automakers pledged to follow; CAAM later clarified the clock starts when delivered parts pass the carmaker&\#x27;s inspection and runs at most 60 calendar days \(tool-2-3, tool-2-2\). An earlier CAAM review of the same 17 companies found most had brought payment terms within 60 days, averaging about 54 days, roughly 10 days shorter than a year earlier \(tool-1-1\).

<details><summary>References</summary>
<ul>
<li><a href="https://news.qq.com/rain/a/20260212A06GZY00">中 汽 协 ：绝大多数重点 车 企 已把 账 期 压缩至 60 ...</a></li>
<li><a href="https://www.bjnews.com.cn/detail/1757900884168181.html">中 汽 协明确 车 企 “ 60 天 账 期 ” 支 付 时间自验收合格之日起算 — 新京报</a></li>
<li><a href="https://c.m.163.com/news/a/K22VDN0R05129QAF.html">车 企 集体 承 诺“ 60 天 账 期 ” 业 内： 承 兑 汇 票 等潜规则不变 账 期 仍然长</a></li>

</ul>
</details>

**Tags**: `#China auto industry`, `#supply-chain finance`, `#payment terms`, `#regulatory oversight`, `#MIIT/CAAM`

---