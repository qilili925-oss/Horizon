---
layout: default
title: "Horizon Summary: 2026-11-17 (ZH)"
date: 2026-11-17
lang: zh
---

> 从 48 条内容中筛选出 13 条重要资讯。

---

**科技新闻**
1. [vLLM v0.34.0 发布：KV 缓存默认扩容，Model Runner V1 移除](#item-tech-news-1) ⭐️ 8.0/10
2. [Optimizely 被曝入侵并借 Zoom、GitLab 投放恶意代码](#item-tech-news-2) ⭐️ 8.0/10
3. [CMU 推出 CS Learn，在 YouTube 免费发布课程](#item-tech-news-3) ⭐️ 7.0/10
4. [Windows 11 被指收集编码代理与开发者工具遥测](#item-tech-news-4) ⭐️ 7.0/10
5. [Jiff 1.0 发布：burntsushi 的 Rust 日期时间库](#item-tech-news-5) ⭐️ 7.0/10
6. [Marimba：一次冻结 ASR 编码器前向回答多类语音查询](#item-tech-news-6) ⭐️ 7.0/10
7. [Duetto：不微调，在采样阶段引导预训练音乐 Transformer 实时伴奏](#item-tech-news-7) ⭐️ 7.0/10
8. [亚马逊称阻断 AI 代理窃取 API 密钥活动](#item-tech-news-8) ⭐️ 7.0/10
9. [美国将先进 AI 芯片出口管制延伸至远程访问](#item-tech-news-9) ⭐️ 7.0/10
10. [阿里、腾讯、月之暗面据报收紧新模型进攻性网络能力](#item-tech-news-10) ⭐️ 7.0/10

**财经新闻**
1. [卢特尼克因坎托与英伟达的关系面临审查](#item-finance-news-1) ⭐️ 8.0/10
2. [黄仁勋辞职与国会变局或重塑 AI 交易](#item-finance-news-2) ⭐️ 7.0/10
3. [英特尔及 CEO 陈立武遭股东集体诉讼](#item-finance-news-3) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [vLLM v0.34.0 发布：KV 缓存默认扩容，Model Runner V1 移除](https://github.com/vllm-project/vllm/releases/tag/v0.34.0) ⭐️ 8.0/10

vLLM 发布 v0.34.0，包含 1,061 次提交和 10 个新模型（如 Mistral Large 4、MiniMax-M3.1-Flash、Nemotron-3.5-Transcribe），并将可扩展 KV 缓存设为 CUDA/ROCm 上的默认行为：缓存在预热后按实际空闲显存分配，例如 MiniMax-M3 在 H200 上从 43.3 万增至 67.2 万 token。该版本移除了 Model Runner V1，V2 成为唯一 GPU runner；默认 block size 从 16 改为 64，ROCm 7.2 镜像不再发布，并要求 huggingface\_hub &gt;= 2.0.0。官方给出的性能提升包括 4×GB200 上 Step5 解码最高 1.95×、GLM-5.3-Flash 吞吐 1.6×、GLM-5.3 长提示 TTFT 快 1.24–1.40×；同时提示可扩展 KV 缓存可能使部分 H200 模型在并发 128 时 TPOT 上升 6–18%。

github · khluu · 11月16日 23:22

**「背景」** 在 vLLM 中，KV cache 决定可同时保留多少上下文，过去其容量主要依据 \`gpu\_memory\_utilization\` 的预留比例估算。v0.34.0 改为在 CUDA graph 捕获和 warmup 完成后按实际空闲显存分配，并把该利用率默认值从 0.9 提高到 1.0，因此显存规划需要按新口径重新评估。分页缓存还以 \`--block-size\` 指定每块的 token 数，该默认值也从 16 变为 64。

**「影响」** 升级到 v0.34.0 的运维者需要先处理兼容性：设置 VLLM\_USE\_V2\_MODEL\_RUNNER=0 会启动失败；默认 gpu\_memory\_utilization 已变为 1.0，若要沿用旧 KV 缓存估算需显式传 --gpu-memory-utilization 0.9 或 --no-enable-extensible-kv-cache；保留旧的 16 block size 需传 --block-size 16。

**标签**: `#vLLM`, `#LLM inference`, `#KV cache`, `#Model Runner`, `#release notes`

---

<a id="item-tech-news-2"></a>
### [Optimizely 被曝入侵并借 Zoom、GitLab 投放恶意代码](https://blog.report-uri.com/worlds-largest-brands-infected-with-malware-via-optimizely/) ⭐️ 8.0/10

据报道，网站优化与实验平台 Optimizely 遭到入侵，并被用来在 Zoom、GitLab 等知名站点上向访问者投放恶意代码；受到影响的是加载其第三方脚本的站点用户。事件的核心风险在于第三方脚本供应链：站点嵌入的优化或标签代码一旦被篡改，恶意内容就可能扩散到多个客户站点。讨论中引述的报道称，攻击者如何取得跨客户项目的写入权限仍不清楚，问题并不在于 CDN 缓存投毒；CDN 只是下发了被注入的代码。

hackernews · kristjansson · 11月16日 23:00 · [社区讨论](https://news.ycombinator.com/item?id=50524767)

**「背景：第三方脚本与 Optimizely 的角色」** Optimizely 是一类被网站嵌入的第三方优化/标签服务，营销或产品团队可借它向页面加入实验代码，而不必经过站点自身的发布流程；评论者 \[stickfigure\] 把这种模式追溯到 Google Tag Manager 让营销部门自行加“标签”的初衷，并称其结果之一是每篇新闻文章附带大量 JavaScript。针对本次事件，\[eax-eip\] 指出 Optimizely 的 CDN 只是分发了交给它的内容，并非 CDN 缓存投毒，Optimizely 自家页面的代码片段也带有该代码。

**「影响与应对」** 对在页面中嵌入 Optimizely 脚本的站点而言，恶意代码是通过受信任的第一方脚本标签下发的，因此仅靠 CDN 层面的防护或缓存校验无法拦截；在 Optimizely 说明注入路径并确认修复前，运维方需要把自家页面视为可能受影响，审计或暂时移除该片段，并检查同期是否有异常跳转、弹窗或凭据窃取行为。评论中也有开发者指出，事件暴露的是第三方标签“一次接入、长期免审”的流程缺陷，企业应重新评估营销标签的上线审批与回滚机制。

**「社区讨论」** 有评论者批评 Google Tag Manager 这类让市场团队绕过工程直接加标签的做法，认为它造成页面脚本臃肿并扩大了攻击面；也有人认为 Optimizely 和大型站点缺少冷却期、分阶段发布与自动安全检查等问责机制。另有评论引述报道指出，攻击者取得跨客户写入权限的途径仍未知，并强调这不是 CDN 缓存投毒。

**标签**: `#supply-chain-security`, `#web-security`, `#third-party-scripts`, `#optimizely`, `#malware-distribution`

---

<a id="item-tech-news-3"></a>
### [CMU 推出 CS Learn，在 YouTube 免费发布课程](https://www.cs.cmu.edu/learn/) ⭐️ 7.0/10

卡内基梅隆大学推出 CS Learn，开始在 YouTube 免费发布该校当前计算机科学课程完整学期的讲座视频，首批课程本周每天上线一门，并计划在明年 1 月增加更多课程。已提到的主题包括机器学习系统等；该项目由 Griffin 计算机科学学院的 Phillip Compeau 负责，他表示部分学生开发了用于自动化大量课程制作流程的工具。

hackernews · pcompeau · 11月16日 20:43 · [社区讨论](https://news.ycombinator.com/item?id=50522980)

**「背景」** 免费公开课程并不是新做法：MIT 的 OpenCourseWare 已在线提供覆盖本科与研究生课程的两千五百多门课程材料，负责运营 CS Learn 的 Phillip Compeau 也在讨论中承认 MIT 早在约 25 年前就开始了这类尝试。CMU 的 CS Learn 与之不同之处在于，它放出的是当前正在开设课程、完整一学期的授课视频；按计划，本周每天上线一门课，明年 1 月还会补充更多课程。

**「学习者当前可得内容」** 对学习者来说，现阶段能直接获得的是完整学期的讲课视频，配套的项目作业与反馈机制尚未上线：项目负责人 Phillip Compeau 表示课程材料（courseware）会在之后推出，评论者亦指出缺少项目和反馈的纯讲座效果会打折扣。课程按每天一门首播、更多课程要等到明年 1 月，因此短期内并非所有课程都能立即观看。

**「社区讨论」** 有评论者认为，在 AI 时代更应打好计算机科学基础，掌握原理后 AI 会成为更强的工具。另一位评论者则强调，仅有讲座还不够，配套项目、作业和反馈的课程材料才决定学习效果，并希望发布范围不要只停留在入门课而遗漏研究生课程。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.youtube.com/channel/UCqvooOJo8792T83va7LMMSA">CS Learn at Carnegie Mellon - YouTube</a></li>
<li><a href="https://ocw.mit.edu/stories/mostafa-fawzy/">Mostafa Fawzy | MIT OpenCourseWare | Free Online Course Materials</a></li>

</ul>
</details>

**标签**: `#computer science education`, `#CMU`, `#free courses`, `#machine learning systems`, `#online learning`

---

<a id="item-tech-news-4"></a>
### [Windows 11 被指收集编码代理与开发者工具遥测](https://xusheng.dev/posts/windows-coding-agent-telemetry/) ⭐️ 7.0/10

一篇开发者文章称，Windows 11 会收集用户运行哪些编码代理和开发者工具的信息，面向使用 Windows 的开发者和企业环境。有评论者概括文章称，这类数据在默认开启的“可选诊断数据”设置下可能被上传，关闭路径为“设置 → 隐私和安全性 → 诊断和反馈”。现有材料未提供可独立复核的采集字段或微软回应，因此这仍是报告层面的说法，而非已确认的系统行为。

hackernews · cwaffles · 11月16日 22:58 · [社区讨论](https://news.ycombinator.com/item?id=50524736)

**「背景」** Windows 11 可通过“可选诊断数据”设置上报诊断信息，相关报告会借助系统的事件追踪（ETW）机制生成。此次结论来自 Xusheng Li 对 Windows 二进制文件的逆向分析；在其测试的美国区设置中，可选诊断数据处于开启状态。

**「对开发者的直接影响」** 若报告所述的采集方式属实，开发者要在 Windows 上运行编码代理，就需要自行核查并调整“设置 → 隐私和安全性 → 诊断和反馈”中的诊断数据级别：评论者指出，相关开发工具使用信息在可选诊断数据开启（据称默认开启）时会被上报。对于统一管理开发机配置的团队，这意味着现有的隐私基线检查需要新增一项针对该诊断数据级别的核对。

**「社区讨论」** 有评论者希望这类遥测保持非侵入，并帮助微软确定功能优先级，理由是 Windows 的 AI 代理沙箱推进缓慢：MXC 于 10 月 7 日才推出，Claude Code 尚未支持该沙箱。另一些评论则把问题相对化，称 GPU 驱动、Chrome 配置和 Debian popcon 也会收集可执行文件名、路径或使用信息；也有人建议不适应者转向 Linux。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://xusheng.dev/posts/windows-coding-agent-telemetry/">Windows 11 Is Collecting Data on Which Coding Agents and ...</a></li>
<li><a href="https://news.lavx.hu/article/windows-11-collects-data-on-coding-agents-and-developer-tools-you-use">Windows 11 Collects Data on Coding Agents and Developer Tools ...</a></li>

</ul>
</details>

**标签**: `#Windows 11`, `#telemetry`, `#privacy`, `#developer tools`, `#AI coding agents`

---

<a id="item-tech-news-5"></a>
### [Jiff 1.0 发布：burntsushi 的 Rust 日期时间库](https://burntsushi.net/jiff/) ⭐️ 7.0/10

由 burntsushi 开发的 Rust 日期时间库 Jiff 发布 1.0 版本，面向需要在 Rust 中处理日期和时间的开发者。当前材料只确认了 1.0 这一版本节点，未提供具体 API、支持范围或兼容性细节。Hacker News 的讨论集中在库的 API 设计，以及它与既有 chrono 库之间的取舍。

hackernews · burntsushi · 11月16日 16:53 · [社区讨论](https://news.ycombinator.com/item?id=50519744)

**「背景」** Jiff 是 Andrew Gallant（burntsushi）开发的 Rust 日期时间库。该项目的发布说明曾表示，计划把下一次破坏性变更版本定为 Jiff 1.0，并承诺在 1.0 发布后长期维护；因此这次 1.0 不只是功能更新，也意味着项目进入长期维护承诺阶段。作者同时通过博客文章提供 1.0 的 API 导览，面向需要便捷日期时间处理的 Rust 程序员。

**「影响」** 对正在选型的 Rust 项目，Jiff 1.0 提供了 chrono 之外的一个日期时间库候选；但现有材料没有给出与 chrono 的兼容层或迁移指南，因此不能据此判断替换成本。

**「社区讨论」** 前 chrono 维护者 quodlibetor 表示，chrono 的 API 稳定性让改进遭遇阻力，自己最终因倦怠停止维护，并对 burntsushi 的工作表示感谢；也有评论者希望 Jiff 被更广泛采用，并询问其对 TAI、UT1 等时间尺度的支持。另有评论赞赏项目明确说明 Jiff 并非适用于所有场景。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/BurntSushi/jiff/releases">Releases · BurntSushi / jiff · GitHub</a></li>
<li><a href="https://burntsushi.net/jiff/">A datetime library for Rust - Andrew Gallant&#x27;s Blog</a></li>

</ul>
</details>

**标签**: `#Rust`, `#datetime`, `#open source`, `#libraries`, `#API design`

---

<a id="item-tech-news-6"></a>
### [Marimba：一次冻结 ASR 编码器前向回答多类语音查询](https://www.reddit.com/r/MachineLearning/comments/1xxsqro/marimba_a_system_one_model_for_speech_r/) ⭐️ 7.0/10

Marimba 在 arXiv 预印本中提出：对每个 8 秒音频窗口只做一次冻结的 Qwen3-ASR-0.6B 编码器前向，就能回答多类带类型的语音问题（是/否、多选、打分），并返回经过校准的概率。作者称在同一批 1,000 个公开问题上，它在 9 项测试中的 6 项追平或超过参数量大得多的 Qwen3-Omni（30B-A3B），但在 Speech Commands 上仍然落后；语种识别在 300 条 FLEURS 片段上达到 100%。局限也很具体：转轮结束检测在 Smart Turn 自有测试集上 AUROC 为 0.930，低于 Smart Turn v3.2 的 0.982（ICSI 会议数据上 0.716 对 0.712，基本持平），而且该读数头用 Smart Turn 数据训练，属同分布比较；在未见过的 CochlScene 场景分类上所有预测头都只有随机水平。权重以 Apache-2.0 发布，代码与演示已公开并可 pip install marimba-audio，但上述数字均来自作者自述，尚无独立复现。

reddit · r/MachineLearning · /u/solanotodesch · 11月16日 15:47

**「背景」** 语音分析中的关键词检测、语种识别、话轮结束检测和说话人变化检测，通常由各自独立的专用模型完成，每类任务都需要单独的训练数据和推理开销。Marimba 的命名借用“系统一”（快速直觉式判断）的概念，思路是复用 ASR 编码器产生的帧级表示，在冻结特征上接小型读出层或校准器来回答不同类型的提问。这也是作者上周 Reddit 帖子的后续，本次补充了 arXiv 论文、Apache-2.0 权重、代码与在线演示。

**「影响」** 对希望复用同一 ASR 编码器的开发者而言，单次前向服务多类查询可以省掉为词项检测、语种识别、说话人变化分别部署模型的开销；词项检测不需针对词表训练，而是对解码器贪心与 4 条 beam 假设打分后做 Platt 校准。但 CochlScene 上全部预测头只有随机水平，说明它不能当作零样本通用音频分类器使用，新任务仍需自行训练读数头并单独验证。

**标签**: `#speech recognition`, `#efficient inference`, `#model calibration`, `#audio benchmarks`, `#machine learning`

---

<a id="item-tech-news-7"></a>
### [Duetto：不微调，在采样阶段引导预训练音乐 Transformer 实时伴奏](https://www.reddit.com/r/MachineLearning/comments/1xxkyh3/steering_a_pretrained_music_transformer_at/) ⭐️ 7.0/10

Duetto 是一个面向 MIDI 键盘的实时爵士伴奏项目：它把演奏者的音符与模型生成的音符放进同一条事件序列，逐个音符（起始时间、时值、音高）续写，从而与你组成小编制乐队，负责独奏、伴奏（comping）和行走贝斯，在你停下时接过来独奏。作者 Riccardo Cataldi 表示其做法不是微调，而是直接使用预训练的 Anticipatory Music Transformer（Thickstun 等，2023），在每次采样前用规则层改写 logits：屏蔽不允许的音符（需等待的手、超出音域的音、不在拍点上的贝斯音），并提高应出现音符的概率（当前和弦音、强拍上的引导音、所引用乐句的下一个音）。乐句取自 Weimar Jazz Database 的转录独奏，按独奏者实际换气处切分，移调到曲目和弦上并在一段 chorus 内发展；在《Autumn Leaves》160 bpm 的演示中，约 61% 的独奏音符来自引用乐句或主题，其余由模型生成。作者报告的速度约为 3080 Ti 上 medium 模型 12 ms/音、large 模型 18 ms/音，Jetson Orin Nano 上 large 模型约 90 ms/音，仍足以现场演奏；服务器提前采样约 1 秒音乐，并在演奏者弹奏时重采样未播放部分以降低延迟。作者也承认目前会偏离演奏者、反应难以预测，模型想法与规则之间的平衡很脆弱——偏置过多听起来像乐句手册，过少又不像爵士；代码可免费用于非商业用途。

reddit · r/MachineLearning · /u/GGAllin43 · 11月16日 09:19

**「背景」** Duetto 使用的 Anticipatory Music Transformer 出自 Thickstun 等人 2023 年的论文；该工作把音乐事件序列作为时间点过程来生成，并提出 anticipation 方法以实现可控生成。由于模型按事件逐步采样，外部规则可以在每一步直接干预候选概率，而不必改动模型权重。

**「对实时伴奏开发者的实际取舍」** 对希望在本地实时生成伴奏的开发者而言，该项目证明不微调预训练模型也能达到可用速度：单张 3080 Ti 上约 12 ms/音符（medium）、18 ms/音符（large），Jetson Orin Nano 上 large 模型约 90 ms/音符仍够现场演奏。但代码仅限非商业使用，且作者自述存在偏离乐手、响应难以预测、规则与模型权重配比脆弱等问题，因此在商业产品或要求稳定互动的场景中落地前，需要先解决授权与可控性这两项限制。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://arxiv.org/abs/2306.08620">[2306.08620] Anticipatory Music Transformer</a></li>
<li><a href="https://www.emergentmind.com/papers/2306.08620">Anticipatory Music Transformer</a></li>

</ul>
</details>

**标签**: `#music generation`, `#inference-time control`, `#transformers`, `#real-time systems`, `#open source`

---

<a id="item-tech-news-8"></a>
### [亚马逊称阻断 AI 代理窃取 API 密钥活动](https://cybernews.com/security/amazon-autonomous-cybercrime-artex-framework/) ⭐️ 7.0/10

亚马逊称，其 MadPot 诱饵网络于 11 月 5 日阻断了一起由开源渗透测试框架 Artex 驱动的 AI 代理活动。这些代理从公网暴露的 LiteLLM、Dify 等 AI 应用窃取 API 密钥，验证后汇入共享池，用于支付更多大模型调用；该活动据称自 10 月 3 日开始。亚马逊以中等信心将行动归因于中国相关威胁组织，并称并非所有被列目标都已失陷，已通知可能受影响的 AWS 客户。

telegram · zaihuapd · 11月16日 13:00

**「背景」** MadPot 是亚马逊运营的诱饵传感器网络，既从网络传感器收集威胁情报，也借助 AWS 的网络控制并与其他互联网参与者协作来阻断攻击。亚马逊以中等信心判断，此次活动中的代理运行于开源 AI 渗透测试框架 ARTEX 之上，这有助于理解代理如何被驱动去寻找并窃取暴露 AI 应用中的密钥。

**「对自建 AI 网关运营者的直接影响」** 对于自行部署 LiteLLM、Dify、One API 等 AI 网关的团队来说，一个直接后果是，如果这些服务暴露在公网且鉴权薄弱，其中保存的上游模型提供商主密钥就可能被批量窃取，并被用于支付攻击者自己的模型调用；因此应尽快排查公网暴露面、轮换密钥，并对出站模型调用设置额度与告警。亚马逊表示已通知可能受影响的 AWS 客户，但没有披露通知数量与具体范围。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://qz.com/amazon-ai-agents-steal-provider-keys-artex-111626">Amazon captured records of AI agents trying to steal AI keys</a></li>
<li><a href="https://www.aboutamazon.com/news/aws/amazon-madpot-stops-cybersecurity-crime">How Amazon helps stop cybersecurity threats across the internet</a></li>
<li><a href="https://thehackernews.com/2026/11/amazon-uncovers-ai-agent-campaign.html">Amazon Uncovers AI Agent Campaign Targeting LiteLLM, Dify ...</a></li>
<li><a href="https://sevgiugursec.com/blog/ai-agents-target-litellm-dify-api-keys">Autonomous AI Agents Target Internet-Exposed LiteLLM and Dify ...</a></li>

</ul>
</details>

**标签**: `#AI security`, `#API key theft`, `#autonomous agents`, `#AWS`, `#cybercrime`

---

<a id="item-tech-news-9"></a>
### [美国将先进 AI 芯片出口管制延伸至远程访问](https://www.reuters.com/legal/litigation/us-issues-rule-protect-advanced-ai-chips-being-accessed-remotely-2026-11-16/) ⭐️ 7.0/10

美国商务部于 11 月 16 日发布一项临时最终规则，把先进 AI 芯片与服务器的出口管制从实体出口扩大到远程访问，意在堵住通过第三国数据中心调用受控算力的规避路径。据 The Verge 报道，新规还要求向印度尼西亚、马来西亚、新加坡、泰国和巴西再出口 AI 芯片时须申请许可。报道称该规则由财政部和国家安全委员会主导起草，可能进一步收紧中国获取先进芯片的渠道。目前公开报道只作了简短转述，尚未披露规则文本、具体生效日期和许可审查细则。

telegram · zaihuapd · 11月16日 14:44

**「背景」** 美国出口管制以芯片和服务器的跨境实物转移、再出口许可为主要抓手；第三国数据中心若向境外客户远程提供算力，芯片不必交付给最终用户，传统以货运和再出口许可为核心的管制就难以覆盖。Reason 在 11 月 16 日的报道中也指出，经第三国中转的转运长期以来难以被有效阻止。\[tool-2-2\]

**「受影响方的直接后果」** 对相关企业而言，直接后果是：向印度尼西亚、马来西亚、新加坡、泰国和巴西出口、再出口或在境内转移先进半导体（包括先进 AI 芯片与服务器）现在都需申请许可证，并适用逐案审查，审查会考量各国出口管制的执法力度。规则同时明确不适用于电商、社交媒体等商业推荐系统，因此在这些国家运营数据中心或部署算力的企业需先确认自身用途是否属于豁免范围，再安排芯片调拨或远程访问。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://reason.com/2026/11/16/trumps-new-chip-export-rule-targets-china-but-exempts-tiktoks-parent-company/">Trump’s new chip export rule exempts TikTok’s parent company</a></li>
<li><a href="https://www.nixonpeabody.com/insights/alerts/2026/11/16/bis-targets-remote-access-to-advanced-chips-through-overseas-data-centers">BIS targets remote access to advanced chips through overseas ...</a></li>
<li><a href="https://kpmg.com/us/en/taxnewsflash/news/2026/11/commerce-advanced-semiconductor-export-controls.html">U.S. Commerce restricts remote access to advanced ...</a></li>
<li><a href="https://www.datacenterdynamics.com/en/news/us-dept-of-commerce-issues-rule-to-restrict-remote-access-to-advanced-ai-chips/">US Dep’t of Commerce issues rule to restrict remote access to ...</a></li>

</ul>
</details>

**标签**: `#AI芯片`, `#出口管制`, `#美国政策`, `#半导体`, `#数据中心`

---

<a id="item-tech-news-10"></a>
### [阿里、腾讯、月之暗面据报收紧新模型进攻性网络能力](https://www.bloomberg.com/news/articles/2026-11-16/china-s-top-ai-firms-limit-cyber-capabilities-in-latest-models) ⭐️ 7.0/10

据 Bloomberg 报道，阿里巴巴、腾讯、月之暗面等中国头部 AI 公司在新一代模型中削弱了进攻性网络攻击能力，同时提升防御性表现。报道将这一调整与商务部上月公布的出口管制草案联系起来：草案拟禁止可攻击关键基础设施和政府网络的 AI 工具出口，腾讯在本月发布 Hy4 之前已削减相关网络功能。阿里最新旗舰 Qwen 未开放权重，用户无法下载并自定义完整版本。上述内容来自媒体转述，材料未披露各公司具体的削减方式、评测数据或官方确认。

telegram · zaihuapd · 11月17日 02:20

**「政策背景」** 2026 年 10 月 16 日，中国商务部与科技部联合公布《中国禁止出口限制出口技术目录》修订草案，拟新增 40 项技术，其中人工智能领域 23 项，涵盖大模型、智能体和算力集群，公开征求意见截至 11 月 15 日。草案明确，已通过开源、发表论文等方式进入公共领域的技术不纳入管理范围；这为理解企业在新模型发布时调整网络能力与开放权重策略提供了政策背景。

**「对开发者的影响」** 过去依赖 Qwen 开放权重进行本地部署或微调的开发者，在 Qwen4-Max 上将无法获得完整权重，只能通过阿里提供的接口调用；若需自行定制，仍需沿用旧版开放模型。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.mofcom.gov.cn/zwgk/zcfb/art/2026/art_0a31a3c9ac404f7a9b0e917ce3412997.html">商务部 科技部公告2026年第48号 就修订《中国禁止出口限制出口技术目...</a></li>
<li><a href="https://thenextweb.com/news/alibaba-launches-qwen4-max-flagship-ai-model-without-open-weights">Alibaba launches Qwen4-Max flagship AI model without open weights</a></li>

</ul>
</details>

**标签**: `#AI policy`, `#China AI`, `#cybersecurity`, `#open weights`, `#model releases`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [卢特尼克因坎托与英伟达的关系面临审查](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 8.0/10

美国商务部长霍华德·卢特尼克正因其子经营的坎托·菲茨杰拉德与英伟达的关系受到审查；CNBC 分析证券申报文件发现，坎托在 2025 年 9 月至 2026 年 3 月把申报持有的英伟达股票从约 350 万股降至 178 万股，降幅近 50%。在英伟达 CEO 黄仁勋周四辞职后，Axios 报道称卢特尼克同期多次抵制对涉嫌向中国走私英伟达芯片的公司采取行动，并曾收到关于黄仁勋与一名疑似中国间谍有关联的机密情报警告；相关关联尚未被证实，坎托称这些持仓是客户互换交易相关的非重大头寸。

rss · CNBC Finance · 11月16日 12:14

**「背景」** 鲁特尼克在 2025 年 2 月出任美国商务部长前执掌华尔街投行 Cantor Fitzgerald，该公司现由其子布兰登和凯尔领导，而商务部负责执行出口管制中的“实体清单”。英伟达 CEO 黄仁勋已于 11 月 12 日辞职，此前其与一名疑似中国情报人员的关联被披露。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.pcgamer.com/software/ai/trump-supports-jensen-huangs-return-as-nvidia-ceo-but-it-doesnt-sound-like-the-board-is-interested/">Trump supports Jensen Huang &#x27;s return as Nvidia CEO... | PC Gamer</a></li>

</ul>
</details>

**标签**: `#Nvidia`, `#Howard Lutnick`, `#Cantor Fitzgerald`, `#U.S.-China export controls`, `#conflict of interest`

---

<a id="item-finance-news-2"></a>
### [黄仁勋辞职与国会变局或重塑 AI 交易](https://www.cnbc.com/2026/11/14/nvidia-ai-trade-data-centers-congress.html) ⭐️ 7.0/10

英伟达 CEO 黄仁勋辞职、民主党掌控国会后，ETF 专家预计 AI 交易可能转向大型科技股和替代芯片供应商。约克维尔艾夫斯将英伟达目标价从 300 美元下调至 225 美元（仍维持买入评级），并估计国会对数据中心的审查可能使低端 10%、高端 15%至 20%的规划项目无法落地。

rss · CNBC Finance · 11月16日 12:13

**「背景」** 英伟达此前是 AI 芯片交易的核心，黄仁勋辞职和民主党在 11 月 3 日选举后掌控国会，令投资者重新评估其芯片供应与数据中心需求。

**「影响」** 据节目嘉宾，拥有现成算力的超大规模云厂商以及 AMD、博通等替代芯片供应商可能因此获得更多需求。

**标签**: `#Nvidia`, `#AI trade`, `#ETFs`, `#semiconductors`, `#US policy`

---

<a id="item-finance-news-3"></a>
### [英特尔及 CEO 陈立武遭股东集体诉讼](https://www.investing.com/news/stock-market-news/intel-sued-by-shareholders-following-29-stock-plunge-5028171) ⭐️ 7.0/10

英特尔及其 CEO 陈立武、CFO 津斯纳被股东集体诉讼，原告指其隐瞒 PC 需求疲软与库存积压；这起由密歇根州养老基金牵头的诉讼在圣何塞联邦法院提起，拟涵盖 2026 年 7 月 23 日至 10 月 29 日买入股票的投资者。公司 10 月 29 日发布的第四季度营收和利润预测不及预期，次日股价暴跌 28.6%，市值蒸发约 1400 亿美元。

telegram · zaihuapd · 11月16日 11:10

**「背景」** 这起股东集体诉讼由一家密歇根州养老基金牵头，代表在 2026 年 7 月 23 日至 10 月 29 日期间买入英特尔股票的投资者，指控公司在这段时间隐瞒了 PC 需求疲软和库存积压。

**「影响」** 这起拟议集体诉讼直接影响在上述期间买入英特尔股票的投资者，并使公司面临法律抗辩成本和潜在赔偿责任。

**标签**: `#Intel`, `#shareholder class action`, `#earnings guidance`, `#stock plunge`, `#semiconductors`

---