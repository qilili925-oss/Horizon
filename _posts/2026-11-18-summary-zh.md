---
layout: default
title: "Horizon Summary: 2026-11-18 (ZH)"
date: 2026-11-18
lang: zh
---

> 从 43 条内容中筛选出 12 条重要资讯。

---

**科技新闻**
1. [OpenAI 发布 GPT‑6.2 Astra 与 Sol，Astra 降价 20%](#item-tech-news-1) ⭐️ 9.0/10
2. [Java4Shell：OpenJDK Base64 处理曝 CVE-2026-114938 远程代码执行漏洞](#item-tech-news-2) ⭐️ 8.0/10
3. [微软 ONNX Runtime 仓库从 GitHub 消失，原因未明](#item-tech-news-3) ⭐️ 8.0/10
4. [Datasette Lite 用 Service Worker 重写，可运行完整 Datasette](#item-tech-news-4) ⭐️ 8.0/10
5. [Phrack 第 73 期发布，聚焦漏洞披露与黑客文化](#item-tech-news-5) ⭐️ 7.0/10
6. [Quad9 退出法国：Cloudflare 警示 DNS 封锁风险](#item-tech-news-6) ⭐️ 7.0/10
7. [SolidJS 发布 2.0 大版本](#item-tech-news-7) ⭐️ 7.0/10
8. [Nvidia 停止披露新加坡销售，子公司外部营收达 1040 亿美元](#item-tech-news-8) ⭐️ 7.0/10
9. [外部沙箱：隔离 AI 编码代理执行的代码](#item-tech-news-9) ⭐️ 7.0/10
10. [中国完成 Q/V 频段双向 27Gbps 无线通信验证](#item-tech-news-10) ⭐️ 7.0/10

**财经新闻**
1. [英国法庭驳回索尼 PlayStation 商店约 19.7 亿英镑集体诉讼](#item-finance-news-1) ⭐️ 7.0/10
2. [工信部委托中汽协评估 17 家车企 60 天账期](#item-finance-news-2) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [OpenAI 发布 GPT‑6.2 Astra 与 Sol，Astra 降价 20%](https://openai.com/index/introducing-gpt-6-2-astra-sol/) ⭐️ 9.0/10

OpenAI 发布面向高难度任务的 GPT‑6.2 Astra 和面向日常工作的 GPT‑6.2 Sol，并称二者已在 API 中以 gpt-6.2-astra、gpt-6.2-sol 提供，LLM 0.38 也已支持。Astra 的输入和输出价格分别为每百万 token 8 美元和 40 美元，是 GPT‑6 Astra 的 10 美元和 50 美元的 80%，缓存输入价格从每百万 token 1 美元降至 0.40 美元；Sol 维持每百万 token 输入 2 美元、输出 10 美元，为 GPT‑5.6 Sol 的 4 美元和 20 美元的一半。早期反应并不一致：有基准比较称 Astra 在多项测试上不及 Claude Fable 5.2，也有用户抱怨其沟通方式；发布者的测试显示两者能完成动画任务，但把 Yonkers 变成机甲的效果不如 Fable 5.2 和 Gemini 4 Carbon。

hackernews · jasondavies · 11月17日 17:46 · [社区讨论](https://news.ycombinator.com/item?id=50535230)

**「背景」** GPT‑6.2 Astra 和 GPT‑6.2 Sol 分别接续此前的 6 Astra 与 6.1 Sol；据所给材料，6 Astra 的定价为每百万 token 输入 10 美元、输出 50 美元，6.1 Sol 为 2/10 美元。此次 Astra 的 8/40 美元定价和 0.40 美元缓存输入价格是相对 6 Astra 的下调，而 Sol 维持了 6.1 Sol 的价位。

**「对开发者的影响」** 对大量调用缓存上下文的智能体开发者，Astra 的缓存输入费用降至原来的 40%，输入和输出单价也降低 20%，可降低长会话成本；已有工作流在迁移时应重新检查提示与终止条件，因为评论者报告新模型有时会提前结束并漏掉答案。

**「社区反馈」** 有评论者用数据分析考试对比，称 Astra 成本从约 20 美元降至约 4 美元、Sol 从 2.6 美元降至 1.2 美元，准确率相近且速度很快，但同时指出模型有时提前完成而漏答。另有评论批评其办公文档、表格和幻灯片示例质量差，PacBench 结果则显示 Astra 得分略低于 Kimi K3.1 Pro 但耗时更短；这些是用户报告，并非统一基准结论。

**标签**: `#OpenAI`, `#LLM`, `#model release`, `#benchmark`, `#cost efficiency`

---

<a id="item-tech-news-2"></a>
### [Java4Shell：OpenJDK Base64 处理曝 CVE-2026-114938 远程代码执行漏洞](https://calif.io/java4shell/) ⭐️ 8.0/10

安全研究者公开了被称为 Java4Shell 的 OpenJDK 远程代码执行漏洞 CVE-2026-114938，称其无需认证，CVSS 4.0 评分为 9.2，且已潜伏近四年。影响范围包括 Java 17（17.0.6 及之后的全部 17 线）、21、25 和 27；标准 Java 8/11 通常不受影响，但 Oracle Java 8 Performance Pack 例外。该漏洞与 Base64 处理相关，利用仅限搭载 AVX-512 VBMI 的 x86-64 服务器处理器，大致对应 2021 年及以后发布的 Intel Ice Lake 及更新 Xeon、2022 年及以后发布的 AMD Zen 4 及更新 EPYC/Ryzen；ARM64 不受影响。所给材料未说明补丁或官方修复状态。

hackernews · werrett · 11月17日 21:11 · [社区讨论](https://news.ycombinator.com/item?id=50538240)

**「背景」** Base64 是 Java 应用和标准库中常见的编码格式，而 OpenJDK 的 HotSpot 运行时会根据底层 CPU 能力选择不同的优化代码路径。此次披露的漏洞只在支持 AVX-512 VBMI 的 x86-64 处理器上触发，说明它依赖与该指令集相关的 Base64 解码实现；这也解释了影响范围为何同时受 Java 版本和 CPU 代际限制。

**「影响」** 对受影响部署，排查范围可先按评论中的 Semgrep 检测脚本缩小：脚本检查五个条件，并指出只有 HotSpot VM（包括部分 OpenJDK、Oracle JDK 和 GraalVM JDK）会生成相关 stub，OpenJ9、GCJ 不受影响，Azul Prime（Zing）因替换 C2 而不同。

**「社区讨论」** 评论重点讨论远程堆布局（“Remote Heap Feng Shui”）对网络条件的敏感性：RTT 和抖动越低、越稳定，利用越可靠，研究者称已在公网 IP 环境下而非仅实验室条件验证。另有评论转述未确认的说法，称可用 -XX:UseAVX=2 规避 AVX-512 Base64 解码路径。

**标签**: `#OpenJDK`, `#Java security`, `#remote code execution`, `#CVE`, `#exploit analysis`

---

<a id="item-tech-news-3"></a>
### [微软 ONNX Runtime 仓库从 GitHub 消失，原因未明](https://github.com/microsoft/onnxruntime) ⭐️ 8.0/10

微软的 ONNX Runtime 开源仓库（约 2.2 万星）在没有任何预告的情况下从 GitHub 上无法访问，提交者称当天早上才发现，其评估流水线随即开始失败。目前公开材料中没有微软或 GitHub 的说明，仓库是临时下线、被设为私有、误操作还是与安全事件有关均未确认，也无法判断数据或代码是否受影响。该仓库是广泛使用的机器学习推理运行时，许多项目的构建与依赖直接指向这一地址。

hackernews · nvader · 11月17日 23:18 · [社区讨论](https://news.ycombinator.com/item?id=50539610)

**「背景：ONNX Runtime 是什么」** ONNX Runtime 是微软开发的跨平台推理与训练加速引擎，被广泛用作在生产环境部署深度学习模型的运行时。在该仓库无法访问后，Hacker News 的讨论中有人提到 2026 年 3 月曾发现一个解析器缺陷，恶意构造的 ONNX 模型可令 ORT 读取任意文件路径或内存地址；但这只是讨论中的说法，与仓库下线是否存在关联目前并未得到证实。

**「对构建流水线的影响」** 对直接克隆仓库或从 GitHub 源码构建 ONNX Runtime 的团队，已有评测流水线失败的报告；在仓库恢复或迁移方案明确前，这些团队需要改用受控的本地缓存或镜像，并核对替代分支的来源和改动，避免 CI 继续依赖单一上游地址。

**「社区讨论」** 在 Hacker News 上，提交者 nvader 称团队是当天早上评估任务失败后才发现仓库“变黑”，并强调事前没有任何通知。其他评论者多属推测：有人怀疑与近期某个被入侵的软件包有关，有人提到后门模型可能利用的新攻击面，也有人指出 Intel 的 onnxruntime 分支（含 OpenVINO 修改）可作为临时替代；另有评论者声称 ONNX 默认会上报应用数据且无法关闭，此说法未获独立证实。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/microsoft/onnxruntime">GitHub - microsoft /onnxruntime: ONNX Runtime : cross-platform, high...</a></li>
<li><a href="https://news.ycombinator.com/item?id=50539610">Microsoft &#x27;s ONNX Runtime has disappeared from GitHub</a></li>
<li><a href="https://wirebyte.co.in/tech/microsoft-removes-onnx-runtime-from-github-apple-services-experience-outage/">Microsoft Removes ONNX Runtime from GitHub; Apple Services ...</a></li>

</ul>
</details>

**标签**: `#ONNX Runtime`, `#Microsoft`, `#open source`, `#supply chain security`, `#GitHub`

---

<a id="item-tech-news-4"></a>
### [Datasette Lite 用 Service Worker 重写，可运行完整 Datasette](https://simonwillison.net/2026/Nov/17/datasette-lite/) ⭐️ 8.0/10

Simon Willison 发布了 Datasette Lite 的完全重写版，使用 service workers 和 Pyodide，让完整的 Datasette Python 应用在浏览器中运行；他称其现在“几乎与真实服务器端应用无异”。用户可通过 lite.datasette.io 的 URL 参数加载 SQLite 数据库、JSON、CSV 或 SQL 脚本，选择 PyPI 上已发布的 Datasette 版本或 GitHub 的 commit、tag、branch，从 100 多个 SQLite 版本中选择，并从 PyPI 或 wheel 文件 URL 安装插件，包括 JavaScript 可视化插件。重写以 service workers 取代旧版将 HTML 注入 innerHTML 的取巧方式，修复了依赖 JavaScript 的功能和插件无法运行的问题；作者已用它在 issue 中链接同一分页 bug 在 1.0a42 与修复后 1.0a43 的对比。

rss · Simon Willison · 11月17日 16:48

**「背景」** Datasette Lite 于 2022 年首次发布，最初通过 Pyodide Web Worker 运行 Datasette，模拟请求处理，再用 innerHTML 将结果注入页面。由于通过 innerHTML 插入的 script 标签不会执行，依赖 JavaScript 的功能在当时无法正常工作；此次重写改用 service worker 来承载应用请求。

**「影响」** 开发者现在可以用一条 URL 固定 Datasette 版本（例如 1.0a42 与 1.0a43）、SQLite 版本和插件，分享可复现的 bug 演示或进行中的功能演示，而无需启动完整 Web 服务器；加载远程数据库或元数据文件时，托管方仍需提供开放的 CORS 头。

**标签**: `#Datasette`, `#Pyodide`, `#WebAssembly`, `#service workers`, `#SQLite`

---

<a id="item-tech-news-5"></a>
### [Phrack 第 73 期发布，聚焦漏洞披露与黑客文化](https://phrack.org/issues/73/introduction_md) ⭐️ 7.0/10

Phrack 第 73 期已在 phrack.org 发布，这是这份长期运行的黑客与安全出版物的新一期内容。该期涉及安全研究、漏洞利用和黑客文化历史；评论者提到其中包含 Docker 逃逸漏洞，并讨论了这类漏洞是事先经过负责任披露并获得 CVE，还是直接公开。由于没有原文正文可供核对，具体文章内容和披露状态仍应以 Phrack 原文为准。

hackernews · notmine1337 · 11月17日 18:31 · [社区讨论](https://news.ycombinator.com/item?id=50535992)

**「背景」** Phrack 是一份长期出版的黑客与安全技术电子杂志，本期为第 73 期。据该期导言，杂志设有“Phrack World History”栏目，本期收录四篇回顾文章，其中包括 2000 年 SSH1 CRC32 漏洞（CVE-2001-0144）的始末——该漏洞可在默认安装上实现远程、预认证的 root 权限——以及蓝盒免费打电话、2003 年有人试图向 Linux 内核植入后门、早期“雇佣僵尸网络”等旧事。

**「社区讨论」** 评论者围绕披露规范提出疑问：本期提到的 Docker 逃逸是否经过负责任披露并分配 CVE，还是直接公开；同时有人怀念早期 Phrack 更粗粝、开放的风格，并推荐 SSH1 漏洞史等文章。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://phrack.org/issues/73/introduction_md">Introduction - phrack.org</a></li>
<li><a href="https://archives.phrack.org/dl/73/the-2000-ssh1-exploit-that-broke-the-internet.pdf">PHRACK-2026-DTP-main-content (1)</a></li>

</ul>
</details>

**标签**: `#security research`, `#exploit development`, `#responsible disclosure`, `#Phrack`, `#hacker culture`

---

<a id="item-tech-news-6"></a>
### [Quad9 退出法国：Cloudflare 警示 DNS 封锁风险](https://blog.cloudflare.com/quad9-withdrawal-from-france/) ⭐️ 7.0/10

Cloudflare 的一篇博客文章将 Quad9 因法国 DNS 封锁命令而退出法国，称为互联网监管的早期预警。该文在 Hacker News 引发讨论，但 Cloudflare 并未承诺采取具体行动，有评论者要求其明确是否会在上诉失败后也退出受影响国家。Quad9 的 CTO 在讨论中表示，自己正在参加 IETF 127，会上对其立场表示支持，并对 DNS 面临的处境普遍感到担忧。评论还批评欧洲互联网自由倒退和过度监管。

hackernews · subset · 11月17日 22:13 · [社区讨论](https://news.ycombinator.com/item?id=50538994)

**「背景」** Quad9 是一家总部位于瑞士的非营利公共 DNS 解析器，其免费解析服务此前在法国可用。法国法院应体育转播方（beIN Sports）方面的请求，命令 Quad9 对与涉嫌盗播体育内容相关的域名进行 DNS 屏蔽，并因其未执行命令而按日处以罚款；Quad9 则认为，按法院要求改写 DNS 应答在其架构下技术不可行，并据此拒绝服从。这一抗辩有先例可循：在德国，Quad9 曾尝试依据 geoIP 做地区性屏蔽，但被指出可通过 VPN 绕过，随后因藐视法庭被罚款。2026 年 10 月下旬，Quad9 宣布将撤出法国市场。

**「影响」** 对在法国依赖 Quad9 公共解析服务的用户和网络运营者而言，直接后果是需要迁移到其他解析器；此案也表明，法院命令下的 DNS 封锁可以迫使公共 DNS 提供商退出该市场。

**「社区讨论」** Quad9 的 CTO 在评论中称，IETF 127 现场对其立场“100% 支持”，但他也承认 IETF 总会有人为反对而反对，并称与会者对 DNS 的处境普遍感到担忧。另有评论者批评欧洲互联网自由倒退、监管过度，并要求 Cloudflare 明确承诺在上诉失败后是否也会退出受影响国家。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://blog.cloudflare.com/quad9-withdrawal-from-france/">Quad9’s withdrawal from France: A canary in the coal mine</a></li>
<li><a href="https://disputeindex.com/cases/quad9-france-bein-dns-blocking-withdrawal">Quad9 plans France withdrawal over beIN site-blocking orders</a></li>
<li><a href="https://reclaimthenet.org/quad9-leaving-france-over-dns-blocking-order">Quad9 to Leave France Over DNS Blocking Order - Reclaim The Net</a></li>

</ul>
</details>

**标签**: `#DNS`, `#internet regulation`, `#privacy`, `#content blocking`, `#network infrastructure`

---

<a id="item-tech-news-7"></a>
### [SolidJS 发布 2.0 大版本](https://www.solidjs.com/blog/solid-2-0-the-long-hold/) ⭐️ 7.0/10

SolidJS 发布 2.0，这是一次大版本更新；现有材料显示，变化集中在服务端集成、开发者诊断与响应式前端开发体验。评论者提到新版提供服务端 RPC 以及 live、broadcast 等能力，但这些具体功能来自社区描述，材料未给出 API、兼容范围或迁移步骤。因此，目前可以确认的是版本发布及讨论焦点，尚不足以判断实际使用中的兼容性和升级成本。

hackernews · pier25 · 11月17日 18:56 · [社区讨论](https://news.ycombinator.com/item?id=50536387)

**「背景」** Solid 2.0 是这个响应式 JavaScript 框架的下一个大版本，其改动方向此前已在 solidjs/solid 仓库的 “The Road to 2.0” 公开讨论（Discussion \#2425）中列出，其中提到涉及 createEffect 等核心 API 的调整，并讨论过现有代码迁移到 2.0 的可行性。项目官网也曾挂出 “Solid 2.0 Release Candidate is here\!” 的提示，说明在正式版之前已经历公开的候选版本阶段。

**「影响」** 对使用 Solid 的前端团队来说，2.0 把服务端 RPC 以及 live/broadcast 能力纳入框架，实时数据同步可能不再需要额外拼接独立层；有评论者认为这种用法比 LiveView、htmx/datastar 更自然，但这属于主观体验，尚缺独立验证。当前材料未列出具体破坏性变更或迁移步骤，升级前仍需核对官方说明和现有服务端集成方式。

**「社区讨论」** 有评论称，Solid 的服务端 RPC 与 live、broadcast 集成比 LiveView、htmx/Datastar 更自然，并认为 Remix 未能真正填补前后端之间的中间层；也有评论认为“为代理编写”的部分本质上只是更好的调试诊断，对手写代码同样有帮助。这些均为社区观点，而非对性能或兼容性的独立验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/solidjs/solid/discussions/2425">The Road to 2 . 0 · solidjs solid · Discussion #2425 · GitHub</a></li>
<li><a href="https://www.solidjs.com/">SolidJS · Reactive Javascript Library</a></li>

</ul>
</details>

**标签**: `#SolidJS`, `#JavaScript frameworks`, `#frontend development`, `#reactivity`, `#server RPC`

---

<a id="item-tech-news-8"></a>
### [Nvidia 停止披露新加坡销售，子公司外部营收达 1040 亿美元](https://www.ft.com/content/dbde7a30-548c-4f9d-a4be-7898a0c24dcf) ⭐️ 7.0/10

英国《金融时报》报道，英伟达（Nvidia）已停止披露新加坡销售数据，而其新加坡子公司的外部营收达到 1040 亿美元。报道称，这一披露变化发生在对芯片流向和出口管制进行审查的背景下。需要注意的是，这一数字是子公司的外部营收；现有信息不足以说明其中有多少芯片最终留在新加坡或流向其他市场。

hackernews · louiereederson · 11月17日 17:12 · [社区讨论](https://news.ycombinator.com/item?id=50534631)

**「背景」** 这一披露变化发生在对新加坡客户 Megaspeed 的审查之中：美国商务部和司法部自 2024 年起就在调查该公司是否违反出口法、将 Nvidia 的 AI 芯片转运至中国。Nvidia 董事会还设立了负责监督出口与国家安全事务的委员会。相关调查也使 Nvidia 能否有效追踪芯片出口、遵守对华先进 AI 芯片限制受到质疑。

**「影响」** 对投资者和监管者而言，地区销售披露减少意味着更难仅凭公开财报判断经新加坡实体承接的订单规模；在出口管制审查持续的情况下，这会削弱对芯片流向的可追踪性。

**「社区讨论」** 评论中，tamarind44 和 legitster 认为文章被误读：1040 亿美元是新加坡子公司的外部营收，可能包含经该实体转接的 GPU 订单，并不代表芯片最终流向或收入实际产生地，核心是会计归属问题。另有评论者将披露变化与制裁规避和高管变动直接联系起来，但未提供证据。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.theguardian.com/technology/2026/nov/17/nvidia-jensen-huang-statement">Jensen Huang says he would be ‘honored’ to return to Nvidia as CEO</a></li>
<li><a href="https://forums.hardwarezone.com.sg/threads/singapore-police-probe-nvidia-customer-megaspeed-over-alleged-china-export-violations.7162980/">Singapore police probe Nvidia customer Megaspeed over alleged...</a></li>

</ul>
</details>

**标签**: `#Nvidia`, `#semiconductors`, `#export controls`, `#AI hardware`, `#corporate disclosure`

---

<a id="item-tech-news-9"></a>
### [外部沙箱：隔离 AI 编码代理执行的代码](https://simonwillison.net/2026/Nov/17/external-sandboxes-for-coding-agents/) ⭐️ 7.0/10

Simon Willison 与 AI 研究实验室 Prime Radiant 合作，提出了“外部沙箱”（external sandbox）模式：AI 编码代理本身运行在沙箱之外，而代理要求执行的代码则进入一个专用沙箱内运行。该模式已随三个开源沙箱服务器实现一起发布：external-sandbox-v86 用 Node.js 服务器通过 v86 在 WebAssembly 中运行 Alpine Linux；external-sandbox-container 是 Python Web 服务器，在 Apple Containers 实例中运行 Alpine Linux；external-sandbox-quicksand 同样是 Python Web 服务器，使用微软的 Quicksand 沙箱库，该库把 QEMU 和 Alpine Linux 打包进一个 Python 包。三者对外提供相同的 localhost API，可配置 Pi、Claude Code 或 Codex，让它们在需要执行代码时调用该沙箱；沙箱还带有可选的 HTTP/HTTPS 允许列表代理，以及一个凭据替换机制，使代理无需持有真实密钥即可发起需要认证的 API 调用。作者的目标是降低尝试本地模型的风险，避免模型出错或遭遇提示注入时对主机造成破坏；来源未提供独立的安全评估或绕过测试结果。

rss · Simon Willison · 11月17日 22:52

**「背景」** 编码代理通常需要执行 Shell 命令或脚本；一旦模型被提示注入或判断失误，这些命令就可能以代理进程的权限直接作用在宿主机上。外部沙箱的思路是把代码执行放进独立的虚拟机、容器或模拟环境，而让代理本身留在沙箱外，从而把潜在破坏限制在沙箱内部。

**「实际影响」** 对使用 Pi、Claude Code 或 Codex 的开发者而言，现在可以把代码执行重定向到本地沙箱 API，并通过允许列表代理限制代理代码能访问的主机，再用凭据替换避免把密钥交给模型。代价是需要自行部署并配置代理指向沙箱；其中 Apple Containers 版本依赖 macOS 环境，而各实现对代理侧的兼容性尚未经过独立验证。

**标签**: `#AI coding agents`, `#sandboxing`, `#prompt injection`, `#security`, `#local models`

---

<a id="item-tech-news-10"></a>
### [中国完成 Q/V 频段双向 27Gbps 无线通信验证](https://www.news.cn/tech/20261117/d6323540dccf4e2a976c48a762795956/c.html) ⭐️ 7.0/10

中科院空天信息创新研究院等单位在丽江中国遥感卫星地面站完成 Q/V 频段高阶体制高码速率双向通信实验，实现我国该频段最高码速率无线通信验证。实验首次系统测试 64QAM 至 512QAM 多种调制模式；512QAM 下单通道双向速率为 6.75Gbps，结合双载频和极化复用提升至 27Gbps，刷新国内纪录。团队称关键指标达国内领先、国际先进水平，后续目标是超过 50Gbps。该结果属于实验验证，报道未称其为世界首次或已商用部署。

telegram · zaihuapd · 11月17日 08:45

**「背景」** Q/V 频段属于毫米波，约有 10 GHz 可用带宽，因此被视为未来 6G 通信和超高速卫星通信的关键候选频段之一。该频段的代价是传播损耗更明显，雨衰等天气因素会直接影响链路可靠性。

**「影响」** 对卫星互联网和 6G 设备研发者而言，这次实验给出了 Q/V 频段高阶调制、双载频与极化复用组合达到双向 27Gbps 的实测指标，可作为后续设备与链路设计的参考。由于验证在地面站完成，且团队下一步才争取超过 50Gbps，相关能力距离星载或商用终端部署仍有后续工程验证要做。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.asiaict.com/finance/22484.html">China&#x27;s 6G Communications Breakthrough: Q/V-Band Experiment ...</a></li>
<li><a href="https://www.rfwireless-world.com/terminology/q-v-band-satellite-communication">Q/V-Band SATCOM: Advantages &amp; Disadvantages - RF Wireless World</a></li>

</ul>
</details>

**标签**: `#Q/V频段`, `#6G`, `#卫星互联网`, `#512QAM`, `#无线通信`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [英国法庭驳回索尼 PlayStation 商店约 19.7 亿英镑集体诉讼](https://www.reuters.com/world/sony-defeats-2-billion-uk-claim-over-playstation-store-pricing-2026-11-17/) ⭐️ 7.0/10

11 月 17 日，英国竞争上诉法庭驳回一桩代表约 1220 万英国消费者、索赔约 19.7 亿英镑的针对索尼的集体诉讼，认定主机之间的竞争已限制索尼对 PlayStation 商店数字内容的定价，因此索尼未滥用市场支配地位。

telegram · zaihuapd · 11月17日 16:02

**「背景」** 这起诉讼于 2022 年 8 月提起，2023 年 11 月获准作为覆盖约 1220 万英国用户的“退出制”集体诉讼推进，当时估值最高达 50 亿英镑；英国竞争上诉法庭是专门审理竞争法案件的法庭，本次庭审持续 30 天。

**「影响」** 这起诉讼被驳回，意味着这约 1220 万英国消费者无法通过该案获得赔偿，索尼也无需就该指控承担赔偿责任。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.brickcourt.co.uk/news/detail/competition-appeal-tribunal-dismisses-2-billion-playstation-class-action-against-sony">Competition Appeal Tribunal dismisses £2 billion PlayStation ...</a></li>
<li><a href="https://www.independent.co.uk/news/business/sony-london-press-association-b3086493.html">PlayStation users’ £2bn lawsuit against Sony thrown out by ...</a></li>

</ul>
</details>

**标签**: `#Sony`, `#PlayStation Store`, `#UK Competition Appeal Tribunal`, `#class action`, `#competition law`

---

<a id="item-finance-news-2"></a>
### [工信部委托中汽协评估 17 家车企 60 天账期](http://www.caam.org.cn/chn/5/cate_68/con_5237404.html) ⭐️ 7.0/10

工信部委托中国汽车工业协会作为第三方，对 17 家重点车企的供应商账款支付情况开展调研评估，重点核查中小企业账期是否不超过 60 天、非中小企业以现金和银行承兑汇票支付的比例是否不低于 80%。评估按企业报送、专班核查、专家评议、公开发布推进，属于对账期落实情况的检查，而非新出台的支付规则。

telegram · zaihuapd · 11月18日 01:15

**「背景」** 2025 年 6 月 1 日生效的《保障中小企业款项支付条例》已规定对中小企业付款的 60 天上限；中汽协同年 9 月 15 日发布《汽车整车企业供应商账款支付规范倡议》，明确账期从车企验收合格之日起算、最长不超过 60 个自然日（含周末）。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.163.com/dy/article/K9H1VCB60527BEOF.html">中 汽 协 60 天 账 期 细则锁死漏洞 专家称要吸取房地产一刀切教训</a></li>
<li><a href="https://www.bjnews.com.cn/detail/1757900884168181.html">中 汽 协明确 车 企 “ 60 天 账 期 ” 支 付 时间自验收合格之日起算 — 新京报</a></li>
<li><a href="https://c.m.163.com/news/a/K22VDN0R05129QAF.html">车 企 集体 承 诺“ 60 天 账 期 ” 业 内： 承 兑 汇 票 等潜规则不变 账 期 仍然长</a></li>

</ul>
</details>

**标签**: `#China auto industry`, `#supply-chain finance`, `#payment terms`, `#regulatory oversight`, `#MIIT/CAAM`

---