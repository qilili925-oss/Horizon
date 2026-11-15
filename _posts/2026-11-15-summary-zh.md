---
layout: default
title: "Horizon Summary: 2026-11-15 (ZH)"
date: 2026-11-15
lang: zh
---

> 从 39 条内容中筛选出 10 条重要资讯。

---

**科技新闻**
1. [Lovable 应用因 RLS 不足泄露护照与逾 20 万条私信](#item-tech-news-1) ⭐️ 8.0/10
2. [Project Zero 将漏洞披露期设为 90 天并计划缩短至 30 天](#item-tech-news-2) ⭐️ 7.0/10
3. [约 200 行纯 JAX 实现 DeepSeek V3](#item-tech-news-3) ⭐️ 7.0/10
4. [EFF 批评科技公司再次试图重新定义隐私概念](#item-tech-news-4) ⭐️ 7.0/10
5. [PyPI 新版项目页上线，突出安全与来源信号](#item-tech-news-5) ⭐️ 7.0/10
6. [OpenAI 解散独立机器人团队，改由通用模型驱动](#item-tech-news-6) ⭐️ 7.0/10
7. [Cloudflare 开源无状态 AI 代理浏览器 Kitesurf](#item-tech-news-7) ⭐️ 7.0/10
8. [特斯拉 Cybercab：月租 299 美元才能运行](#item-tech-news-8) ⭐️ 7.0/10
9. [FAA 全国停飞起因：铜线换光纤升级引发路由故障](#item-tech-news-9) ⭐️ 7.0/10

**财经新闻**
1. [🤖 Anthropic IPO 拒绝中国内地及香港投资者下单](#item-finance-news-1) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Lovable 应用因 RLS 不足泄露护照与逾 20 万条私信](https://www.crissyfield.de/research/lovable-en/) ⭐️ 8.0/10

一篇安全研究文章称，部分由 Lovable 构建的应用因为 Supabase 的行级安全（RLS）配置不足，暴露了护照信息和超过 20 万条私人消息；研究者只需检查浏览器的网络请求就能访问这些数据。Lovable 安全负责人回应称，这些应用的根因正是 RLS 配置不足；Lovable 会在每次发布前自动扫描应用，并提供免费的深度 SAST 扫描，发现问题后可以协助修复或启用后台自动修复。上述扫描和修复能力来自 Lovable 的说明；现有材料没有交代涉事应用是否经过这些检查，也没有给出受影响应用和用户的具体数量。

hackernews · armcat · 11月14日 17:43 · [社区讨论](https://news.ycombinator.com/item?id=50499017)

**「背景」** Supabase 的访问控制依赖 Row-Level Security（行级安全，RLS）：数据表若未启用 RLS，任何持有项目公开 anon key 的浏览器请求都可能直接读取整表记录。Crissy Field 的扫描覆盖 159,041 个 Lovable 项目，其中 24,664 个应用在未登录状态下就会返回数据库记录，涉及护照信息、支付资料和 20 多万条聊天消息；研究者强调根因是缺失的数据库访问规则，而非 Lovable 平台本身遭入侵。

**「影响」** 对使用 Lovable 等 AI 应用生成器的开发者来说，直接后果是要自行核查 Supabase 表的 RLS 是否启用、是否按用户隔离；由于研究者仅靠浏览器网络请求就能读取数据，任何客户端可访问的接口都不应返回未授权记录。

**「社区讨论」** 评论区的争论集中在责任归属：有评论者认为，Supabase 多年前为降低上手门槛而设定的默认权限同样有责任，并提到相关修复据称在 10 月 30 日完成，但有报告称已有项目可能仍沿用旧默认值；也有评论者主张，平台应采用默认拒绝的数据库权限、最小权限 API 和自动化鉴权测试。另有评论认为，数据泄露早在 AI 出现之前就已存在，但 AI 生成应用数量多、攻击门槛低，普通用户难以判断风险。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://cybernews.com/security/lovable-ai-apps-expose-personal-information/">Lovable AI apps exposed sensitive data in open databases ...</a></li>
<li><a href="https://dailysecurityreview.com/cyber-security/24664-lovable-built-apps-leak-passports-and-chat-messages/">24,664 Lovable-Built Apps Leak Passports and Chat Messages</a></li>
<li><a href="https://www.techzine.eu/news/security/145550/thousands-of-lovable-apps-are-leaking-personal-data/">Thousands of Lovable apps are leaking personal data</a></li>

</ul>
</details>

**标签**: `#AI app builders`, `#application security`, `#Row-Level Security`, `#Supabase`, `#data exposure`

---

<a id="item-tech-news-2"></a>
### [Project Zero 将漏洞披露期设为 90 天并计划缩短至 30 天](https://projectzero.google/2026/11/disclosure-policy.html) ⭐️ 7.0/10

根据帖子标题及评论中引述的公告，Google Project Zero 将漏洞披露窗口设为向厂商报告后 90 天，称为“Full 90”；公告还计划在 2027 年 2 月 2 日缩短到 60 天，并在 2028 年 1 月 3 日进一步缩短到 30 天。当前生效的是 90 天规则，60 天和 30 天是未来安排、尚未生效。

hackernews · hacb · 11月14日 11:13 · [社区讨论](https://news.ycombinator.com/item?id=50496051)

**「背景」** Project Zero 自 2021 年起采用“90+30”漏洞披露政策：给厂商最多 90 天修复，再留 30 天用于补丁部署。新的“Full 90”政策改为在报告后 90 天公开，并计划于 2027 年 2 月 2 日转为 60 天、2028 年 1 月 3 日转为 30 天。

**「对维护者的影响」** 对厂商和开源维护者来说，修复、验证和发布协调都需要压缩到 90 天披露窗口内，而未来窗口缩短会进一步收紧排期；60 天和 30 天的具体执行细则尚未在现有材料中说明。

**「评论讨论」** 评论者对缩短窗口的可行性有分歧：一人认为 Ubuntu 等下游发行版需要远多于 30 天的时间，另一人则主张应立即披露，否则厂商不会被迫修复。还有评论提出，发现漏洞的公司也应向厂商或开源项目提供其用于发现漏洞的产品访问权限；这些均为评论者观点。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://projectzero.google/2026/11/disclosure-policy.html">Policy and Disclosure: 2026 Edition - Project Zero</a></li>
<li><a href="https://projectzero.google/vulnerability-disclosure-faq.html">Vulnerability Disclosure FAQ - Project Zero</a></li>
<li><a href="https://www.verisq.ai/intelligence/policy-and-disclosure-2026-edition-72908">Google Project Zero Shifts to Full 90 Disclosure, Plans Full ...</a></li>

</ul>
</details>

**标签**: `#vulnerability disclosure`, `#Project Zero`, `#security policy`, `#open source`, `#Google`

---

<a id="item-tech-news-3"></a>
### [约 200 行纯 JAX 实现 DeepSeek V3](https://github.com/Vaibhaav-Tiwari/deepseek-v3-jax) ⭐️ 7.0/10

开发者 VaibhaavTiwari 在 Hacker News 的 Show HN 发布了 deepseek-v3-jax：一个用约 200 行纯 JAX 代码实现 DeepSeek V3 的开源项目，面向希望从零理解模型并进行本地实验的开发者。该项目以代码精简为卖点，更适合作为教学性实现来评估，并非经过验证的生产级推理方案；现有材料没有说明它是否覆盖完整模型权重、训练或推理流程，也没有给出性能指标。

hackernews · VaibhaavTiwari · 11月14日 15:04 · [社区讨论](https://news.ycombinator.com/item?id=50497589)

**「背景」** DeepSeek V3 的原始技术报告与模型卡将其描述为一个混合专家（MoE）语言模型：总参数约 671B，但每个 token 只激活 37B 参数。这一架构规模也解释了为何用约 200 行 JAX 复现 V3 更适合作为理解模型内部计算的精简教学实现，而不是完整模型的等价替代。

**「对本地 AMD GPU 用户的实际意义」** 对使用 ROCm 未完整支持的消费级 AMD 显卡的开发者来说，这条路径给出了可复现的起点：有评论者报告，该项目是其 RX 7600 XT 16GB 上首个端到端跑通的本地方案，并需设置 HSA\_OVERRIDE\_GFX\_VERSION=11.0.0 等环境变量来绕开 JAX 插件对该卡架构的限制。鉴于实现仅约 200 行，它更适合作为理解推理流程和本地验证的教学起点，而非直接用于生产规模的 DeepSeek V3 部署。

**「社区讨论」** 多位评论者肯定从第一性原理重建模型的学习价值，armcat 和 itsthecourier 表示受启发想复现或重拾 JAX。joebarbere 报告称，该项目在其 Fedora + ROCm、RX 7600 XT 16GB 环境中首次端到端跑通，并提到需要设置 HSA\_OVERRIDE\_GFX\_VERSION=11.0.0 等环境变量；这属于单个用户的运行经验，尚非独立基准测试。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://huggingface.co/deepseek-ai/DeepSeek-V3-Base">deepseek -ai/ DeepSeek - V 3 -Base · Hugging Face</a></li>
<li><a href="https://arxiv.org/abs/2412.19437">[2412.19437] DeepSeek - V 3 Technical Report</a></li>
<li><a href="https://paperlens.io/idea/deepseek-moe/">Advanced Mixture of Experts : The DeepSeek - V 3 Architecture</a></li>

</ul>
</details>

**标签**: `#JAX`, `#DeepSeek V3`, `#LLM implementation`, `#ROCm`, `#open source`

---

<a id="item-tech-news-4"></a>
### [EFF 批评科技公司再次试图重新定义隐私概念](https://www.eff.org/deeplinks/2026/11/tech-companies-are-trying-shift-entire-concept-privacy-again) ⭐️ 7.0/10

电子前哨基金会（EFF）于 2026 年 11 月 14 日在其 Deeplinks 博客发布分析文章，主张科技公司正在再一次试图改写“隐私”这一概念本身的含义。需要区分的是：这是倡导性评论，而非产品发布、诉讼或已生效的政策变更；在现有材料中，文章没有点名具体公司、具体立法条款或给出可核验的数据，因此上述主张应视为 EFF 的立场陈述，而不是已被证实的事实变动。

hackernews · gslin · 11月14日 12:45 · [社区讨论](https://news.ycombinator.com/item?id=50496602)

**「背景：AI 会议记录器与隐私担忧」** AI 会议记录器（AI notetaker）会自动加入线上会议或通话，录制音频、转写内容并生成摘要，还能从中提取待办事项。此前已有报道指出，隐私倡导者担心这类工具会在未经与会者同意的情况下生成声纹，部分厂商还会转售记录器产生的数据，或用机密的会议记录和转录内容训练自家模型。

**「社区讨论」** 有评论者（toddmorey）描述自己的处境：如今几乎每场职业会议，包括经理与同事之间的一对一谈话，都会被可见或不可见的 AI 参会者录音并上传，而自己虽然不认同这种做法，却很难在不影响就业的情况下选择退出；他还询问是否有人把“本次会议不需要转录，请先关闭 AI 记录工具”变成惯例。另一位评论者（abecedarius）则从残障使用角度提出不同看法，认为做得好的实时转录眼镜对失聪和重度听障者可能具有变革意义，且完全可以用本地模型实现不保存、不导出，但他也承认这类系统距离“保留数据”只差一个条件判断，并质疑全面禁用是否会连带波及开源的辅助设备。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://techxplore.com/news/2026-07-ai-notetakers-easy-recaps-professionals.html">AI notetakers promise easy meeting recaps, but some professionals...</a></li>

</ul>
</details>

**标签**: `#privacy`, `#AI notetakers`, `#surveillance`, `#tech policy`, `#workplace recording`

---

<a id="item-tech-news-5"></a>
### [PyPI 新版项目页上线，突出安全与来源信号](https://blog.pypi.org/posts/2026-11-06-ui-updates-complete/) ⭐️ 7.0/10

PyPI 宣布其项目页改版已完成并上线，页面会更清晰地展示安全与来源证明（provenance）信号。对浏览和安装 Python 包的开发者和维护者来说，这些信号现在直接出现在项目页面上，便于在采用包之前查看其来源信息。

hackernews · rbanffy · 11月14日 15:40 · [社区讨论](https://news.ycombinator.com/item?id=50497892)

**「背景」** PyPI 早已支持可信发布（Trusted Publishing）与来源证明（provenance attestations）等机制，但相关信号此前并未在项目页面上集中呈现。评论中提到的 datasette 就属于已附带来源证明的项目，而 dlt 则没有，说明这类信息在实际项目中存在有无之别。此次改版属于界面与元数据呈现层面的调整，把既有的安全与来源信息更醒目地暴露给浏览者，而非新增签名或验证能力。

**「影响」** 对依赖 PyPI 的团队，项目页上的 provenance 标记可用于区分提供来源证明的包与未提供的包，从而在安装前多一个核查点；有评论者提醒，这类信号并不能判断项目本身是否恶意，主要针对原本正常、后被接管的项目。

**「社区讨论」** 多位评论者欢迎 provenance 更显眼，并希望受信任发布支持可复用工作流、Sigstore 式无密钥短时签名更普及；也有人担心信任链过度依赖大型云厂商和 OIDC，带来锁定问题。另有评论强调，provenance 只能帮助识别被接管的老项目，无法检测一开始就恶意的项目。

**标签**: `#PyPI`, `#software supply chain security`, `#provenance`, `#Python packaging`, `#open source infrastructure`

---

<a id="item-tech-news-6"></a>
### [OpenAI 解散独立机器人团队，改由通用模型驱动](https://fortune.com/2026/11/13/openai-disbands-robotics-team-as-its-general-models-start-running-robots/) ⭐️ 7.0/10

据该条目转述的 Fortune 报道，OpenAI 已解散独立机器人团队，并将研究员重新分配到更通用的研究团队。OpenAI 表示机器人仍是其长期愿景的核心，并称调整原因是 GPT-6 Astra 等通用前沿模型已能直接操控机器人执行任务，因此不再需要专门的机器人团队；这些说法尚未在条目中获得独立验证。条目还称 OpenAI 仍在自研人形机器人，CEO 的目标是 2027 年首次公开展示；此前其机器人团队于 2020 年解散、2024 年重建，与 Figure 的合作已于 2025 年 2 月终止。

telegram · zaihuapd · 11月14日 04:00

**「背景」** OpenAI 的机器人研究此前已多次调整：早期机器人团队于 2020 年解散，2024 年重建并与 Figure AI 合作，但该合作在 2025 年 2 月终止。公司随后仍推进自研人形机器人，并把 2027 年首次公开展示设为目标；此次将机器人研究人员转入通用团队，延续了从独立机器人项目转向通用模型能力的路线。

**「影响」** 对内部研究员而言，直接后果是转入更通用的研究团队，机器人能力将更多依赖 GPT-6 Astra 等通用模型的进展，而非独立机器人团队的专门路线。OpenAI 未在条目中说明这是否会改变人形机器人项目的资源投入、外部合作或 2027 年公开展示目标。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://theroboticsmedia.com/article/openai-disbands-robotics-team-gpt-6-astra">OpenAI Disbands Robotics Team, Bets on GPT-6 Astra Instead</a></li>
<li><a href="https://madrobot.blog/2026/11/13/openai-disbands-robotics-team-gpt-6-astra/">OpenAI reorganises its robotics team as GPT-6 Astra runs robots</a></li>

</ul>
</details>

**标签**: `#OpenAI`, `#robotics`, `#foundation models`, `#AI strategy`, `#humanoid robots`

---

<a id="item-tech-news-7"></a>
### [Cloudflare 开源无状态 AI 代理浏览器 Kitesurf](https://www.phoronix.com/news/Cloudflare-Kitesurf-Open-Source) ⭐️ 7.0/10

Cloudflare 以 Apache 2.0 协议开源了面向 AI 代理的无状态浏览器 Kitesurf，代码已发布在 GitHub。它基于 Cloudflare Workers 构建，无需浏览器容器即可解析 HTML、处理 CSS 并执行 JavaScript。Cloudflare 声称，相比 Chromium，它占用更少 CPU 和内存，并能在全球 Workers 网络上按需扩展；目前尚无独立性能评测。

telegram · zaihuapd · 11月14日 09:33

**「背景」** Kitesurf 是 Cloudflare 专门为 AI 代理构建的浏览器，它不依赖 Chromium，而是运行在 Workers 的 V8 isolate 中，主体用 Rust 编写并编译为 WebAssembly。按照 Cloudflare 文档和 GitHub 仓库的说明，Kitesurf 依赖 Dynamic Workers 为每个页面创建相互隔离的 worker，而这项能力属于 Workers 付费计划；本地开发则通过 wrangler dev 运行。

**「影响」** 使用 Workers 的开发者可以让 AI 代理在边缘解析和执行页面脚本，而无需维护 Chromium 容器；但由于缺少独立评测，依赖复杂浏览器 API 的站点仍需自行验证兼容性和执行结果。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.eesel.ai/blog/cloudflare-kitesurf">Cloudflare Kitesurf : the agent browser that trades speed... | eesel AI</a></li>
<li><a href="https://github.com/cloudflare/kitesurf">GitHub - cloudflare / kitesurf : Kitesurf is an experimental browser ...</a></li>

</ul>
</details>

**标签**: `#Cloudflare`, `#AI agents`, `#browser automation`, `#open source`, `#serverless`

---

<a id="item-tech-news-8"></a>
### [特斯拉 Cybercab：月租 299 美元才能运行](https://www.tesla.com/configurator/api/v4/terms?category=autonomy_subs&amp;amp;locale=en_US&amp;amp;model=cc&amp;amp;saleType=Sale) ⭐️ 7.0/10

根据特斯拉公布的 Cybercab 订阅条款，车辆售价为 29,990 美元，车主还须每月支付 299 美元自动驾驶订阅费，否则车辆无法运行；特斯拉可提前一个月通知调价。条款还规定，欠费或违规使用可导致订阅暂停或取消，累计三次警告将停用自动驾驶一周；车辆仅在指定区域运行，未经授权不得接入网约车、配送或租赁平台。Electrek 指出，Cybercab 与用于 Robotaxi 的 Model Y 采用相同的 AI4 硬件和自动驾驶软件，但面向普通车主的 FSD 仍需人类监督。

telegram · zaihuapd · 11月15日 01:10

**「背景」** 特斯拉现有的 Robotaxi 服务以 Model Y 为载体，Cybercab 与这些车辆使用相同的 AI4 硬件和自动驾驶软件；而面向普通车主的 FSD 仍要求人类监督。这一差异是理解 Cybercab 将无监督自动驾驶作为独立月费项、并与车辆能否运行绑定的前提。

**「影响」** 对个人买家而言，车辆能否使用取决于持续订阅，指定区域和平台接入限制会直接影响跨区出行或营运用途；在把 Cybercab 接入网约车、配送或租赁服务前，需先确认获得授权，否则可能被暂停或取消订阅。

**标签**: `#Tesla`, `#Cybercab`, `#autonomous driving`, `#subscription pricing`, `#robotaxi`

---

<a id="item-tech-news-9"></a>
### [FAA 全国停飞起因：铜线换光纤升级引发路由故障](https://www.theverge.com/transportation/1033898/faa-ground-stop-sean-duffy-faa-copper-wire) ⭐️ 7.0/10

美国交通部长 Sean Duffy 11 月 14 日表示，周五 FAA 下令的全国停飞源于一处偏远设施在例行维护中把老旧铜线换成光纤；新装路由器随后出现问题，导致数千航班停飞。他说根因尚不明确，可能是硬件故障、配置错误或承包商 L3Harris 失误；该路由器每 4 到 5 秒向其他路由器发出逾千次连接请求，干扰雷达信号与飞机通信。Duffy 还呼吁国会追加空管现代化资金。

telegram · zaihuapd · 11月15日 02:10

**「背景」** 据 NPR 和 CNBC 报道，L3Harris 是 FAA 的长期承包商，负责一套较旧的通信系统；此次全国停飞发生在这套系统于偏远 FAA 站点进行铜线转光纤的例行维护之后。这有助于解释为何一处远端设施的升级故障会波及雷达信号与飞机通信，而不是只影响局部机场。

**「后续影响」** 这次停飞把 FAA 的铜线换光纤升级直接推到调查中心：L3Harris 正按 FTI 合同把全美 FAA 设施的老旧铜线替换为高速网络，相关合同累计义务已接近 21 亿美元；USA Today 报道称，交通部长表示 L3Harris 对单个路由器的操作导致了此次停飞。对 FAA 和承包商而言，一处偏远站点的路由器异常就足以干扰雷达与飞机通信，这意味着后续割接的变更控制和故障回退能力将成为该项目的实际约束。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.npr.org/2026/11/14/nx-s1-6040952/faa-ground-stop-airplane-travel">FAA ground stop ends but passengers stuck at airport : NPR</a></li>
<li><a href="https://www.cnbc.com/2026/11/14/faa-ground-stop-flights-resume-delays.html">Ground stop followed contractor upgrade to L3Harris telecom ...</a></li>
<li><a href="https://www.l3harris.com/all-capabilities/faa-telecommunications-infrastructure-fti">FAA Telecommunications Infrastructure (FTI) - L3Harris</a></li>
<li><a href="https://www.federalmediagroup.com/news/faa-adds-21-5m-to-l3harris-telecom-infrastructure-order-cumulative-obligations-approach-2-1-billion">FAA Adds $21.5M to L3Harris Telecom Infrastructure Order ...</a></li>
<li><a href="https://www.usatoday.com/story/news/nation/2026/11/14/faa-ground-stop-probe-l3harris/92780406007/">Air traffic probe looks at work of FAA contractor and a ...</a></li>

</ul>
</details>

**标签**: `#network outage`, `#router failure`, `#infrastructure reliability`, `#FAA`, `#aviation systems`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [🤖 Anthropic IPO 拒绝中国内地及香港投资者下单](https://m.economictimes.com/markets/us-stocks/news/anthropic-ipo-share-orders-from-china-are-said-to-be-rebuffed/articleshow/135809948.cms) ⭐️ 7.0/10

Anthropic&\#x27;s reported IPO is said to bar mainland Chinese and Hong Kong investors under ITAR-related restrictions, with pricing set for Nov. 18 at a $1.4 trillion valuation and a raise of up to $90.4 billion.

telegram · zaihuapd · 11月14日 10:18

**标签**: `#Anthropic IPO`, `#China/Hong Kong investors`, `#ITAR export controls`, `#AI financing`, `#IPO valuation`

---