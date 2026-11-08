---
layout: default
title: "Horizon Summary: 2026-11-08 (EN)"
date: 2026-11-08
lang: en
---

> From 39 items, 11 important content pieces were selected

---

**Technology News**
1. [Asahi Linux progress report 7.3: same-day Fedora Remix, licensing warning](#item-tech-news-1) ⭐️ 8.0/10
2. [SemiAnalysis Tours 800MW Galaxy AI Datacenter Campus in Inner Mongolia](#item-tech-news-2) ⭐️ 8.0/10
3. [GitHub&\#x27;s Rubicon Git storage targets 7,200 pushes per second](#item-tech-news-3) ⭐️ 8.0/10
4. [Report: Microsoft Research&\#x27;s AI Frontiers Group Ends as John Langford Exits](#item-tech-news-4) ⭐️ 7.0/10
5. [Coldframe honeypot mimics Danfoss and Dixell controllers](#item-tech-news-5) ⭐️ 7.0/10
6. [Need for Speed Underground 2 Goes Online in the Browser](#item-tech-news-6) ⭐️ 7.0/10
7. [Claude Code &\#x27;Don&\#x27;t Ask Again&\#x27; tied to 1,122 exposed GitHub files](#item-tech-news-7) ⭐️ 7.0/10
8. [MaxxBench tests whether DeepSWE scores survive changed task specs](#item-tech-news-8) ⭐️ 7.0/10
9. [Post claims Macs since 2022 run undocumented relationship-graph daemons](#item-tech-news-9) ⭐️ 7.0/10

**Financial News**
1. [Berkshire Hathaway more than doubles Q3 buybacks to $9.6 billion as earnings decline](#item-finance-news-1) ⭐️ 7.0/10
2. [SoftBank and ABB Weigh China Carve-Out to Salvage $5.4 Billion Robotics Deal](#item-finance-news-2) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Asahi Linux progress report 7.3: same-day Fedora Remix, licensing warning](https://asahilinux.org/2026/11/progress-report-7-3/) ⭐️ 8.0/10

Asahi Linux&\#x27;s progress report for version 7.3 says Fedora Asahi Remix shipped on the same day as Fedora Linux 45&\#x27;s 3 November release, the first time the remix has matched an upstream Fedora release. The report also warns that multiple attempts were made to exploit Asahi&\#x27;s permissive licensing to hijack its work with a direct view to replacing the project and aggressively monetising Linux on Apple Silicon.

hackernews · ackyshake · Nov 7, 05:20 · [Discussion](https://news.ycombinator.com/item?id=50401867)

**「Background」** Asahi Linux is an open-source project that develops Linux support for Apple Silicon Macs, and Fedora Asahi Remix is its Fedora-based distribution built on that work. The project has used permissive licensing, and the 7.3 progress report says the team became aware of attempts to exploit that licensing to replace the project and monetize Linux on Apple Silicon.

**「Impact」** Fedora Asahi Remix users can get Fedora Linux 45 changes without the usual remix delay. Developers reusing Asahi code should review the licensing warning and how permissive terms apply to downstream reuse.

**「Community discussion」** Commenters cited missing USB-C display support as a practical blocker for MacBook Air use, while a longtime financial backer welcomed the same-day Fedora delivery. Another commenter promoted Gravity Linux, claiming Vulkan 1.4, M4/M5 support and suspend-to-RAM progress that they said no Asahi version supports.

<details><summary>References</summary>
<ul>
<li><a href="https://asahilinux.org/2026/11/progress-report-7-3/">Progress Report: Linux 7.3 - Asahi Linux</a></li>

</ul>
</details>

**Tags**: `#Asahi Linux`, `#Apple Silicon`, `#Linux kernel`, `#Fedora`, `#open source`

---

<a id="item-tech-news-2"></a>
### [SemiAnalysis Tours 800MW Galaxy AI Datacenter Campus in Inner Mongolia](https://newsletter.semianalysis.com/p/we-visited-chinas-stargate-in-inner) ⭐️ 8.0/10

SemiAnalysis published an on-site report from Ulanqab in Inner Mongolia&\#x27;s Chahar High-tech Zone, where it toured &quot;Galaxy,&quot; a datacenter campus planned for up to 800MW of IT capacity and roughly the size of Stargate&\#x27;s Abilene core campus. The first 120MW phase was delivered within a year at a fifth of US costs, and all four phases are built-to-suit for two unnamed internet giants; the rest of the site was still under construction during the September visit. The campus is owned by Envision Group, a renewable-systems integrator with more than 100GW of wind turbines installed worldwide, which also builds the wind farms and dedicated power line serving the site, runs a blade factory across the road, and designed the low-voltage power modules, 800V system, load-smoothing battery storage, and prefabricated substation. A local report cited by SemiAnalysis counted nearly 30,000 construction workers across 22 datacenter projects in the zone, and the report contrasts this acceleration with rising anti-datacenter sentiment in the US. The cost and timeline figures are the outlet&\#x27;s own reporting rather than independently audited numbers.

rss · Semianalysis · Nov 7, 19:01

**「Context」** Stargate Abilene, a gigawatt-scale campus on the Texas plains built for OpenAI, has become the reference symbol of the US AI buildout. Inner Mongolia, which SemiAnalysis calls China&\#x27;s fastest-growing AI datacenter region and the country&\#x27;s &quot;West Texas,&quot; is accelerating its buildout without the anti-datacenter backlash Texas faces. The report follows SemiAnalysis&\#x27;s earlier primer on the China datacenter market.

**「Why It Matters」** The Galaxy case shows the cost gap resting on scope rather than just cheap labor: Envision supplies its own generation, power distribution, batteries, and substation hardware, so developers comparing US builds against Chinese ones are effectively comparing a vertically integrated utility-and-equipment vendor with a chain of separate suppliers. That makes the quoted one-fifth-of-US-cost figure a benchmark tied to a specific ownership model, and one that competing developers cannot match simply by hiring more construction labor.

**Tags**: `#AI infrastructure`, `#data centers`, `#China AI`, `#datacenter economics`, `#vertical integration`

---

<a id="item-tech-news-3"></a>
### [GitHub&\#x27;s Rubicon Git storage targets 7,200 pushes per second](https://github.blog/engineering/architecture-optimization/inside-githubs-new-git-storage-architecture/) ⭐️ 8.0/10

GitHub has introduced a new Git storage architecture, codenamed Rubicon, designed for the case where large numbers of AI agents operate concurrently on a single repository. In internal testing, the system supported 5,000 agents collaborating at once and handled 7,200 pushes per second while keeping read latency low. The design stores Git objects in Azure Blob Storage, manages reference state through Ref-CAS, and uses virtual replicas to handle reads and writes while background nodes compact data packs. Rubicon is currently in a limited private preview, with GitHub planning to widen rollout gradually. The throughput and latency figures are vendor-reported internal test results from a short secondhand summary of the announcement, not independently measured numbers, and no general availability date was given.

telegram · zaihuapd · Nov 7, 14:12

**「Background」** Git repositories pair an object database—commits, trees, and blobs, typically stored in packfiles—with mutable references such as branches. Keeping object storage and reference updates consistent under many concurrent writers to the same repository is the problem GitHub’s Rubicon design addresses by moving Git objects to Azure Blob Storage and coordinating refs through Ref-CAS, according to GitHub’s report.

**「Impact」** Because Rubicon is confined to a limited private preview, developers and organizations cannot yet opt in or plan a migration, and existing repositories continue to run on the current storage backend. The architecture&\#x27;s stated focus on many agents hitting one repository signals that high-concurrency automated workloads, rather than human push volume, are the capacity case GitHub is engineering for.

<details><summary>References</summary>
<ul>
<li><a href="https://github.blog/engineering/architecture-optimization/inside-githubs-new-git-storage-architecture/">Inside GitHub’s new Git storage architecture - The GitHub Blog</a></li>
<li><a href="https://stack-archive.com/blog/github-rubicon-git-storage-architecture-agents-2026/">GitHub Rubicon: Git Storage Built for 5,000 Concurrent Agents</a></li>

</ul>
</details>

**Tags**: `#GitHub`, `#Git 存储`, `#系统架构`, `#AI 智能体`, `#Azure Blob Storage`

---

<a id="item-tech-news-4"></a>
### [Report: Microsoft Research&\#x27;s AI Frontiers Group Ends as John Langford Exits](https://hunch.net/?p=13764006) ⭐️ 7.0/10

A Hacker News thread discusses a linked report that Microsoft Research&\#x27;s AI Frontiers group has been declared closed and that researcher John Langford has exited Microsoft. The submitted item consists mainly of links — an archive copy and a businessexaminer.ca article — rather than the article text itself, so the closure&\#x27;s scope, timing, and Microsoft&\#x27;s stated rationale are not available in the supplied material. Commenters also clarified that &quot;AI Frontiers&quot; is a specific MSR group focused on fundamental advances in AI, not the field as a whole.

hackernews · srean · Nov 7, 18:02 · [Discussion](https://news.ycombinator.com/item?id=50406563)

**「Background」** AI Frontiers was the Microsoft Research group whose closure John Langford announced; Langford was a partner researcher manager at Microsoft Research New York. In his November 6, 2026 post on the Machine Learning \(Theory\) blog, he described the group&\#x27;s approach as organizing coherent research efforts in a &quot;messy middle&quot; between top-down and bottom-up direction, and that post is the basis for reports that he has left Microsoft.

**「Community discussion」** Several commenters argue the reported closure fits an industry-wide pattern in which companies prioritize transformer-based scaling and discourage exploratory research into alternative methods; one cited Meta&\#x27;s treatment of a former research lead as an example, and another said the shift is &quot;culture-destroying&quot; at Microsoft. Others pushed back on treating the two as substitutes, arguing that research and scale both matter and that starving either is a risk, though these remain opinions rather than established facts about the group&\#x27;s work.

<details><summary>References</summary>
<ul>
<li><a href="https://businessexaminer.ca/victoria-articles/item/microsoft-researcher-john-langford-exits-as-ai-frontiers-group-is-declared/">Microsoft Researcher John Langford Exits as AI Frontiers Group ...</a></li>
<li><a href="https://hunch.net/?p=13764006">The End of AI Frontiers – Machine Learning (Theory)</a></li>

</ul>
</details>

**Tags**: `#Microsoft Research`, `#AI research strategy`, `#transformer scaling`, `#industry restructuring`, `#Hacker News`

---

<a id="item-tech-news-5"></a>
### [Coldframe honeypot mimics Danfoss and Dixell controllers](https://github.com/hedgerow-dev/coldframe) ⭐️ 7.0/10

Coldframe is a new open-source Python honeypot, contained in one file and using only the standard library, that impersonates Danfoss AK-SM 800A and Dixell XWEB supermarket refrigeration controllers. Its author says the Danfoss and Dixell personas are recognized by Shodan as real devices rather than honeypots, matching header order, the Dixell page length of exactly 8,202 bytes, certificate fields, and TLS versions from Shodan records; it also recognizes CVE-2025-41450, three other Danfoss CVEs, and XWEB exploits. Default logins open a fake store dashboard with defrost buttons so operators can see second-stage activity, and the author reports that two instances live for one day have so far seen only generic scanners and Shodan&\#x27;s refrigerator.census.shodan.io crawler.

hackernews · hedgerow-dev · Nov 7, 17:27 · [Discussion](https://news.ycombinator.com/item?id=50406292)

**「Background」** Coldframe&\#x27;s target personas are tied to known security problems in real refrigeration equipment: Danfoss&\#x27;s advisory identifies CVE-2025-41450 as an improper-authentication vulnerability in its AK-SM8xxA series that enables an authentication bypass and is remediated by patch 4.2. Claroty&\#x27;s Team82 separately examined the AK-SM 800A embedded web management interface and found multiple vulnerabilities, which helps explain why a honeypot would emulate those specific interfaces and recognize exploit attempts against them.

**「Impact」** For OT/IoT security researchers, the default-login path into a fake store dashboard lets an operator observe post-authentication actions, including attempts to manipulate defrost settings, rather than stopping at initial exploit detection; nothing behind the dashboard is connected to real equipment.

**「Community discussion」** Commenters questioned the evidence base: supriyo-biswas warned that Shodan-derived device fingerprints are unreliable because many exposed devices are themselves honeypots or already compromised, and recommended probing a physical unit; xrd asked whether a large-scale hack was ever definitively established, noting earlier speculation that a simultaneous software update could explain the pattern.

<details><summary>References</summary>
<ul>
<li><a href="https://claroty.com/team82/research/freeze-the-controller-defrost-the-food-uncovering-vulnerabilities-in-danfoss-refrigeration-controllers">Freeze the Controller, Defrost the Food: Uncovering ...</a></li>
<li><a href="https://nvd.nist.gov/vuln/detail/cve-2025-41450">NVD-CVE-2025-41450</a></li>
<li><a href="https://www.danfoss.com/en/service-and-support/coordinated-vulnerability-disclosure/danfoss-security-advisories/dsa-2025-03-01/">DSA-2025-03-01 | Danfoss</a></li>

</ul>
</details>

**Tags**: `#honeypots`, `#industrial-control-systems`, `#IoT-security`, `#open-source`, `#Python`

---

<a id="item-tech-news-6"></a>
### [Need for Speed Underground 2 Goes Online in the Browser](https://nfsu2.xyz/) ⭐️ 7.0/10

A browser-playable, online-enabled version of Need for Speed Underground 2 is available at nfsu2.xyz, built through reverse engineering and WebGPU. Players report that it runs on phones and supports multiplayer races with friends, though it requires WebGPU and Linux users may need to enable unsafe WebGPU features in Chromium. The site is not an official release, and its legal status is uncertain.

hackernews · fluxusars · Nov 7, 09:36 · [Discussion](https://news.ycombinator.com/item?id=50403052)

**「Background」** Need for Speed Underground 2 is an older racing title that commenters describe as abandonware no longer available for purchase and difficult to run from retail copies on modern PCs. The browser port depends on WebGPU, the web graphics API that users report must be enabled—on Linux Chromium, via unsafe WebGPU flags—before the game will run.

**「Compatibility requirement」** Because the port renders the game&\#x27;s Direct3D 9 output through WebGPU, players need a WebGPU-capable Chrome or Firefox rather than an installer or EA account. One commenter reports that Linux Chromium users must additionally enable unsafe WebGPU features before the game will run.

**「Community Discussion」** Commenters praise the technical feat and the nostalgia of playing the game on phones and with friends, but they disagree on its legitimacy: one calls soliciting donations for copyrighted content “highly dubious,” while another hopes the project is left alone because the game is no longer commercially available.

<details><summary>References</summary>
<ul>
<li><a href="https://underground2revived.com/">Underground 2 Revived: Play NFSU 2 in Browser</a></li>
<li><a href="https://portedgames.com/need-for-speed-underground-2-browser/">NFS Underground 2 Browser Game: Play NFSU 2 Online at nfsu 2 . xyz</a></li>

</ul>
</details>

**Tags**: `#browser gaming`, `#WebGPU`, `#reverse engineering`, `#abandonware`, `#online multiplayer`

---

<a id="item-tech-news-7"></a>
### [Claude Code &\#x27;Don&\#x27;t Ask Again&\#x27; tied to 1,122 exposed GitHub files](https://apiiro.com/blog/coding-agents-leaking-secrets-github-dont-ask-again) ⭐️ 7.0/10

Security researchers at Apiiro report that credentials appeared in 1,122 public GitHub files after users committed Claude Code local settings containing commands approved through “Don&\#x27;t Ask Again.” The Claude Code team&\#x27;s Boris Cherny said .claude/settings.local.json is meant to stay local and is automatically gitignored when Claude creates it, so the reported files were manually created and checked into source control. He added that Claude Code has historically not done secret scrubbing but that the team is looking into preventing this.

hackernews · shmulc · Nov 7, 20:45 · [Discussion](https://news.ycombinator.com/item?id=50407882)

**「How the approval file works」** Claude Code pauses for approval before running shell commands, and choosing &quot;Don&\#x27;t ask again&quot; persists that exact command string into \`.claude/settings.local.json\` so identical invocations run later without a prompt. If the approved command carried an inline API key, password, or token, the secret is stored verbatim in that file — which the Claude Code team says is auto-gitignored when Claude creates it, but not when a user creates and commits it manually. Apiiro&\#x27;s scan targeted public repositories where such settings files had been checked in, then searched those files for embedded credentials.

**「Impact」** For teams using Claude Code, committing .claude/settings.local.json can publish the exact command lines they approved, so repositories need auditing and any exposed credentials need rotation.

**「Community discussion」** Commenters disputed the framing: Aurornis argued that pressing “Don&\#x27;t Ask Again” alone does not expose passwords, and that exposure requires committing local settings containing manually approved commands with secrets. Others described isolating agents in ephemeral VMs with restricted API access, while binarymax said keeping credentials in 1Password and exposing them only through the op CLI limits what Claude can see.

<details><summary>References</summary>
<ul>
<li><a href="https://thehackernews.com/2026/11/claude-codes-dont-ask-again-file.html">Claude Code&#x27;s “Don&#x27;t Ask Again” File Exposes Passwords and ...</a></li>

</ul>
</details>

**Tags**: `#security`, `#secrets-management`, `#ai-coding-agents`, `#claude-code`, `#github`

---

<a id="item-tech-news-8"></a>
### [MaxxBench tests whether DeepSWE scores survive changed task specs](https://maxxbench.unlap.ai/research/why-maxxbench/) ⭐️ 7.0/10

MaxxBench has published a meta-evaluation of the DeepSWE coding benchmark that varies task specifications and checks whether high scores generalize. The analysis asks whether a strong DeepSWE result reflects broad coding capability or depends on how individual tasks are phrased and constrained.

hackernews · antiuniverse · Nov 7, 17:19 · [Discussion](https://news.ycombinator.com/item?id=50406222)

**「Background」** DeepSWE is a coding-agent benchmark that evaluates models on 113 original, long-horizon software-engineering tasks across 91 repositories and five languages, using isolated task environments and program-based verifiers. Because such benchmarks reduce agent performance to a headline score, MaxxBench tests whether that score remains meaningful when the task specification is varied.

**「Impact」** For teams using DeepSWE to compare coding models, the analysis supports treating a single headline score as fragile and checking whether rankings hold when task specifications are varied.

**「Community discussion」** Commenters broadly welcomed the parameter-perturbation approach, with one calling task-spec variation a good default and another observing that smaller “flash” models collapsed most in the article’s graph. Others questioned benchmark quality—citing bugs in DeepSWE and arguing that sloppy RL environments, rather than direct benchmark training, may drive overfitting—and one drew a practical warning against using “max mode.”

<details><summary>References</summary>
<ul>
<li><a href="https://benchlm.ai/benchmarks/deepswe">DeepSWE Leaderboard &amp; Scores — September 2026 | BenchLM.ai</a></li>
<li><a href="https://arxiv.org/html/2607.07946">DeepSWE : Measuring Frontier Coding Agents on Original...</a></li>

</ul>
</details>

**Tags**: `#LLM benchmarks`, `#evaluation methodology`, `#DeepSWE`, `#AI research`, `#benchmark robustness`

---

<a id="item-tech-news-9"></a>
### [Post claims Macs since 2022 run undocumented relationship-graph daemons](https://8rank.ai/game/apple-intelligence-personal-knowledge-graph) ⭐️ 7.0/10

A reverse-engineering investigation published on 8rank.ai claims that every Mac since 2022 ships a pair of undocumented daemons that build a personal knowledge graph of the user and their contacts, including how people are related, how they communicate, where the user goes, and what they do. The post describes the system as undocumented by Apple; the item provides no Apple confirmation or independent verification. The author answered questions in the Hacker News thread and linked follow-up research.

hackernews · infwhispers · Nov 7, 09:46 · [Discussion](https://news.ycombinator.com/item?id=50403097)

**「What a local knowledge graph is」** A personal knowledge graph is a structured, on-device index that links people, contact records and communication events so that local features can resolve references — for instance, working out which &quot;James&quot; a message is meant for, or who someone&\#x27;s boss is. The write-up scopes the affected systems to macOS 13 and later on both Intel and Apple silicon, which underlies its &quot;every Mac since 2022&quot; framing. Commenters noted that Apple already does comparable local indexing elsewhere, such as the names and faces Photos associates with people, and the author points readers to follow-up research on the same site.

**「Impact」** If the claim holds, Mac users face a consent gap: because the daemons are described as undocumented, users cannot learn from Apple&\#x27;s public settings what relationship or location data macOS derives about them and their contacts.

**「Community discussion」** Commenters split between treating the graph as useful local context for disambiguating Siri requests such as “Text James” and objecting that undocumented relationship modeling breaks the social expectation that casual conversations are not remembered. The author joined the thread to answer questions and point to follow-up research.

<details><summary>References</summary>
<ul>
<li><a href="https://8rank.ai/game/apple-intelligence-personal-knowledge-graph">Anatomy of Apple &#x27;s Personal Knowledge Graph — Eighth Rank</a></li>

</ul>
</details>

**Tags**: `#apple`, `#macos`, `#privacy`, `#reverse-engineering`, `#personal-knowledge-graph`

---

## Financial News

<a id="item-finance-news-1"></a>
### [Berkshire Hathaway more than doubles Q3 buybacks to $9.6 billion as earnings decline](https://www.cnbc.com/2026/11/07/berkshire-hathaway-q3-2026-earnings-buybacks.html) ⭐️ 7.0/10

Berkshire Hathaway repurchased $9.6 billion of its own stock in the third quarter of 2026, more than double the $4.5 billion bought back in the second quarter, while operating earnings from its wholly-owned businesses fell 5.8% year on year to $12.705 billion. Insurance underwriting profit dropped 43% to $1.352 billion, offset by growth in the railroad, energy and manufacturing units, and overall earnings including the stock portfolio fell 28% to $22.112 billion.

rss · CNBC Finance · Nov 7, 15:23

**「Background」** Berkshire&\#x27;s operating profit excludes gains and losses from its stock portfolio, so the 5.8% decline in its wholly-owned businesses differed from the 28% drop in overall earnings.

**「Impact」** The larger buyback means remaining Berkshire shareholders hold a bigger proportional claim on the company&\#x27;s future earnings, even as the insurance unit — the source of the profit decline — weighs on results.

**Tags**: `#Berkshire Hathaway`, `#share buybacks`, `#Q3 earnings`, `#insurance underwriting`, `#cash reserves`

---

<a id="item-finance-news-2"></a>
### [SoftBank and ABB Weigh China Carve-Out to Salvage $5.4 Billion Robotics Deal](https://www.bloomberg.com/news/articles/2026-11-07/softbank-abb-weigh-china-carve-out-to-salvage-robotics-deal) ⭐️ 7.0/10

SoftBank and ABB are considering separating the China portion of ABB&\#x27;s robotics business into a standalone entity with different equity rights, in an effort to rescue a $5.4 billion acquisition that China&\#x27;s foreign investment security review office blocked on Thursday, Bloomberg reported. People familiar with the matter said the plan may fail and that ABB is also weighing other options, including finding another buyer for the business, which is valued at $2 billion to $3 billion; both companies declined to comment.

telegram · zaihuapd · Nov 7, 11:24

**「Background」** The acquisition was halted this week by China&\#x27;s foreign investment security review; the Financial Times reports the block came from the National Development and Reform Commission, the state planner also tasked with safeguarding supply chains.

**「Who is affected」** If the carve-out fails, ABB could instead seek another buyer for the robotics unit at an estimated $2bn–$3bn — well below the blocked $5.4bn price — leaving the ownership of the business and its China operations unresolved.

<details><summary>References</summary>
<ul>
<li><a href="https://www.ft.com/content/f10c3e24-45e4-47ff-bde2-24a8de90aec4?syn-25a6b1a6=1">China blocks SoftBank’s $5.4bn takeover of ABB’s robotics ...</a></li>
<li><a href="https://supplychaindigital.com/news/china-blocks-softbanks-us-5-37bn-bid-for-abb-robotics">China blocks SoftBank’s US$5.37bn bid for ABB Robotics</a></li>
<li><a href="https://www.reuters.com/business/media-telecom/china-blocks-softbanks-54-billion-takeover-abbs-robotics-division-ft-reports-2026-11-05/">China blocks SoftBank’s $5.4 billion takeover of ABB’s ...</a></li>

</ul>
</details>

**Tags**: `#SoftBank`, `#ABB`, `#robotics`, `#China FDI screening`, `#cross-border M&amp;A`

---