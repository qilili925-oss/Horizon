---
layout: default
title: "Horizon Summary: 2026-11-12 (ZH)"
date: 2026-11-12
lang: zh
---

> 从 52 条内容中筛选出 11 条重要资讯。

---

**科技新闻**
1. [用电压毛刺解锁矿卡中的 A100 级能力](#item-tech-news-1) ⭐️ 8.0/10
2. [AWS 发布 Rust 编写的官方本地模拟器 aws-emulator](#item-tech-news-2) ⭐️ 8.0/10
3. [Jane Street 纽约数据中心误报烟雾警报事件复盘](#item-tech-news-3) ⭐️ 7.0/10
4. [《Python 之禅》作者 Tim Peters 去世](#item-tech-news-4) ⭐️ 7.0/10
5. [线性规划能否实现语言模型的权重空间编辑？](#item-tech-news-5) ⭐️ 7.0/10
6. [谷歌发布 Gemini Decisions API，支持音视频与 PDF 输入](#item-tech-news-6) ⭐️ 7.0/10
7. [Anthropic 路演视频披露四类芯片与算力乘数策略](#item-tech-news-7) ⭐️ 7.0/10
8. [字节跳动拟数周内发布类 Muse 智能体，目标 2030 年前追平 OpenAI](#item-tech-news-8) ⭐️ 7.0/10
9. [The Information 调查指黄乐协助 24 万颗英伟达芯片入华](#item-tech-news-9) ⭐️ 7.0/10

**财经新闻**
1. [古尔斯比称 10 月通胀报告“近乎令人不安”，美联储权衡进一步加息](#item-finance-news-1) ⭐️ 8.0/10
2. [离岸信托收益征税过渡期结束，税务总局称累计申报个税逾 1600 亿元](#item-finance-news-2) ⭐️ 8.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [用电压毛刺解锁矿卡中的 A100 级能力](https://blog.kate.land/posts/using-voltage-glitching-to-unlock-the-a100/) ⭐️ 8.0/10

一篇技术博客描述了如何用电压毛刺（voltage glitching）在矿卡上解锁 A100 级能力，目标是把原本受限的硬件重新用于通用 GPU 计算。该做法属于针对单张显卡的实验性硬件改装，并非 NVIDIA 官方支持的功能，实际可复现性和风险仍取决于具体卡型与硬件状态。

hackernews · lae · 11月11日 10:48 · [社区讨论](https://news.ycombinator.com/item?id=50451903)

**「背景」** NVIDIA 的 CMP 170HX 是面向加密货币挖矿的专用卡，其核心是与 A100 相同的 GA100 芯片，但出厂时用熔丝（fuse）关闭了大部分 SM 和 HBM 容量；对应的 A100 数据中心卡则是 108 个 SM、最高 80GB 显存的配置。所谓电压毛刺（voltage glitching）属于故障注入攻击：在芯片运行或校验的瞬间短暂拉低核心电压，使熔丝相关逻辑出错，从而绕开本应只读的硬件限制并重新烧写熔丝。这篇博文正是用这一手段，去解锁被熔丝禁用的计算单元与显存。

**「对买卡复现者的实际代价」** 对打算买 CMP 170HX 复现这一解锁的人来说，代价是不可逆的：该方法依赖烧断熔丝，一旦操作失败显卡可能直接报废，而评论者 notenchange 称自己用纯软件方式尝试解锁 80GB 已两周仍未成功。二手价格也同步抬高了试错成本：评论者 roger\_ 表示几个月前 1,000 美元还算划算、更早只要约 200 美元，检索到的商品与行情页面同样显示该卡价格已涨至上千美元区间。

**「社区讨论」** 评论者追问熔丝到底是为了屏蔽有制造缺陷的 A100，还是纯粹出于市场分层；有评论者认为前者更可能，因为数据中心产品利润更高。也有人报告正尝试用软件方式解锁 CMP 170HX 的 80GB 显存但两周未成功，并提醒博客针对的是 8GB 型号，而 10GB 型号此前只能通过较慢的 CPU 内存拷贝访问大显存。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://news.lavx.hu/article/kate-uses-voltage-glitching-to-turn-a-cmp-170hx-mining-card-into-an-a100-class-gpu">Kate uses voltage glitching to turn a CMP 170HX mining card ...</a></li>
<li><a href="https://sitem.co/public/summary/7050/voltage-glitching-unlocks-nvidia-ga100-die-transforming-cmp-170hx-mining-cards-into-high-performance-a100-equivalents">Voltage Glitching Unlocks NVIDIA GA100 Die: Transforming CMP ...</a></li>
<li><a href="https://blog.kate.land/posts/using-voltage-glitching-to-unlock-the-a100/">Using voltage glitching to unleash the A100 in my mining card</a></li>
<li><a href="https://www.ebay.com/itm/276736911721">Used NVIDIA CMP 170HX 8GB Card GPU 164MH/s - eBay Cmp 170hx for sale | eBay Nvidia Cmp 170 Hx for sale - eBay Where to Buy a CMP 170HX | amoghmunikote/170th-Street | DeepWiki NVIDIA CMP 170HX 8/10 GB Prices Explode From $100 to Over ... NVIDIA CMP 170HX Prices Surge Past $1,000 After Tool Unlocks ...</a></li>

</ul>
</details>

**标签**: `#voltage glitching`, `#GPU hardware hacking`, `#NVIDIA A100`, `#hardware security`, `#mining cards`

---

<a id="item-tech-news-2"></a>
### [AWS 发布 Rust 编写的官方本地模拟器 aws-emulator](https://simonwillison.net/2026/Nov/11/aws-emulator/) ⭐️ 8.0/10

AWS 发布了官方 aws-emulator，让开发者在本地针对 AWS 服务的克隆运行测试，无需配置付费 API key。该项目用 Rust 编写；据 Simon Willison 转述，项目前三周产生了 29,684 次提交，由大规模 agent swarm 完成，AWS 工程师 Swaminathan Sivasubramanian 在 Werner Vogels 博客的客座文章中介绍了其由来。目前在 macOS 和 Windows 上运行仍需要 Docker。

rss · Simon Willison · 11月11日 21:18

**「背景」** 本地模拟器用服务克隆替代对真实 AWS API 的调用，让测试不必连接云端，也无需开通付费 API key。aws-emulator 是 AWS 官方推出的这类工具；在此之前，开发者要在本地测试依赖 AWS 服务的代码，通常得自行准备云凭证。该工具目前在 macOS 和 Windows 上仍需通过 Docker 运行。

**「本地测试可以省掉 API 密钥，但安全断言仍须回到真实 AWS」** 把测试迁到 aws-emulator 时，依赖“拒绝”行为的用例必须留在真实 AWS 环境：官方说明明确不应用于测试 IAM 策略与权限边界、S3 桶策略等基于资源的策略、KMS 密钥策略、跨账户或跨区域访问，以及其他安全控制；部分服务虽会评估模拟器内创建的 IAM 用户和角色策略，但评估方式与 AWS 不同，且模拟器从不会拒绝用自身密钥签名的请求。此外在 macOS 与 Windows 上目前仍需 Docker，尚无单二进制分发，跨语言、跨平台测试套件的集成方式受到限制。

**「社区讨论」** 有评论者怀疑该项目只是实验，还是会被长期维护的真实产品，并推荐 Floci 和 Testcontainers 作为替代方案。另有评论引用安全文档指出，不应使用该模拟器测试 IAM 策略、资源策略、KMS 密钥策略或跨账户、跨区域访问，因为其 IAM 评估方式与 AWS 并不一致。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/aws/aws-emulator">GitHub - aws / aws - emulator : AWS Emulator is a local emulator of the...</a></li>
<li><a href="https://news.ycombinator.com/item?id=50456631">AWS emulator | Hacker News</a></li>

</ul>
</details>

**标签**: `#aws`, `#cloud-emulation`, `#local-testing`, `#ai-agents`, `#rust`

---

<a id="item-tech-news-3"></a>
### [Jane Street 纽约数据中心误报烟雾警报事件复盘](https://michael.bacarella.com/2026/11/10/false-smoke-alarm-jane-street-datacenter/) ⭐️ 7.0/10

文章作者复盘了 Jane Street 在纽约唯一的数据中心遭遇误报烟雾警报、并一度接近严重事故的经过。这是一篇针对具体事件的运营复盘，而非产品发布；评论者随后围绕 EPO、烟雾报警联动以及 CRAC 是否应在报警时停机展开技术讨论。由于原始正文未提供，警报时间、设备型号、实际处置动作和最终影响均无法独立确认。

hackernews · mbac32768 · 11月11日 16:38 · [社区讨论](https://news.ycombinator.com/item?id=50455394)

**「背景：烟感联动与机房制冷」** 这类事故的背景是机房消防联动：烟感报警通常联动关闭空调机组（CRAC），以免把烟雾扩散到其他区域，但遇到误报时制冷随之中断，机房温度会快速攀升，逼近喷淋启动条件。据 Zeli 收录的报道，Jane Street 这次警报由施工人员产生的粉尘触发，系统工程师赶到现场、在温度超过 150°F 之前拔掉了所有电源线；事后团队用 OCaml 写了一个监控，每分钟汇总服务器板载温度，并在整个机群温度上升时告警。

**「运营影响」** 对运营同类机房的组织，可操作的检查点是确认 EPO 是否可在现场触发、烟雾报警是否会联动断电或停机 CRAC，以及这些逻辑是否经过演练；否则一次误报就可能把是否断电的判断压到现场人员身上。

**「社区讨论」** 评论者 rdl 质疑该机房为何至少没有室内物理 EPO 按钮以及烟雾报警到断电的联动。rainbowzootsuit 则提出不同设计实践：其经手的数据大厅特意不在烟雾报警时关闭 CRAC，并称《国际机械规范》允许单空间、风量超过 2000 cfm 的空气处理机组这样做，因为不会把烟雾扩散到整栋建筑。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://michael.bacarella.com/2026/11/10/false-smoke-alarm-jane-street-datacenter/">How a false smoke alarm almost drowned Jane Street’s only NYC ...</a></li>
<li><a href="https://proomt.com/item/how-a-false-smoke-alarm-almost-drowned-jane-street-s-only-nyc-datacenter-37986aa2-b738-4757-9fd0-3cd51ca264bb">How a false smoke alarm almost drowned Jane Street&#x27;s only NYC ...</a></li>

</ul>
</details>

**标签**: `#datacenter operations`, `#incident response`, `#infrastructure reliability`, `#fire suppression`

---

<a id="item-tech-news-4"></a>
### [《Python 之禅》作者 Tim Peters 去世](https://discuss.python.org/t/in-memoriam-tim-peters-1952-2026/110028) ⭐️ 7.0/10

Python 社区正在悼念长期贡献者 Tim Peters（1952–2026）。他以《Python 之禅》和 Timsort 等工作为人熟知；运行 \`import this\` 就会显示他署名的这篇短文。当前帖子本身主要是悼念链接，未提供完整生平等细节，因此关于其贡献的描述主要来自社区回忆。

hackernews · ayhanfuat · 11月11日 07:03 · [社区讨论](https://news.ycombinator.com/item?id=50450488)

**「背景」** 《Python 之禅》是 Python 解释器中执行 \`import this\` 后显示的那组设计格言，作者正是 Tim Peters；他还设计并实现了 Timsort 排序算法，并作为核心开发者长期参与 Python 语言的演进。据 Guido van Rossum 在 Python 官方论坛发布的讣告，Peters 已于 2026 年 7 月 15 日去世，帖文称很难高估他对 Python 的影响。

**「影响」** 对 Python 开发者而言，这次事件不涉及版本升级、兼容性变更或代码迁移；最直接的可见遗留是 \`import this\` 仍会输出他撰写的《Python 之禅》，日常开发中的排序实现也继续受 Timsort 影响。

**「社区讨论」** 评论者以个人经历纪念他：有人贴出 \`import this\` 全文，有人回忆从 python-dev、bugs.python.org 和《Python Cookbook》第 2 版中受教，并称他为“Uncle Timmy”。关于 SpamBayes，评论者称 Tim Peters 与 Gary Robinson 把 pg 的《A Plan for Spam》文章变成了可用的 SpamBayes 程序，随后又补充 Robert Woodhead 也应列入贡献者，说明相关署名仍有讨论。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://discuss.python.org/t/in-memoriam-tim-peters-1952-2026/110028">In Memoriam: Tim Peters 1952–2026 - Core Development ...</a></li>
<li><a href="https://grokipedia.com/page/Tim_Peters_%28software_engineer%29">Tim Peters (software engineer) — Grokipedia</a></li>

</ul>
</details>

**标签**: `#Python`, `#open source`, `#software engineering`, `#community`, `#obituary`

---

<a id="item-tech-news-5"></a>
### [线性规划能否实现语言模型的权重空间编辑？](https://nathan.rs/posts/weight-space-lp/) ⭐️ 7.0/10

一篇博客分析提出，对关注模型编辑的研究者而言，可以把语言模型的行为修改表述为对权重方向的线性约束，再用线性规划求解稀疏的权重空间编辑。文章以基于 LLM 的权重编辑方法为对照，但相关主张尚未经过独立验证，也不等同于已发布的编辑工具或模型能力。Hacker News 评论则建议把这一思路用于权重空间蒸馏、训练时正则化，并考察其在更大模型和多变量奖励下的可行性。

hackernews · emschwartz · 11月11日 12:30 · [社区讨论](https://news.ycombinator.com/item?id=50452655)

**「背景」** 权重空间编辑指不经过常规梯度微调，直接改动模型参数来改变行为；此前的 Astra 演示把这类操作交给 LLM：据相关页面描述，它被要求在不使用梯度的情况下提升 Qwen 3.5-0.8B 的数学能力，并改动了约 0.016% 的权重，另一例则只改最后一层 MLP 的 down\_proj（约 8910 万个权重，占模型 0.32%）。这篇博客把“消除某行为、保留另一行为”表述为对权重方向的线性约束，进而考察线性规划求解器能否完成类似的稀疏权重编辑。

**「对权重编辑实践的影响」** 对尝试直接编辑模型权重的开发者来说，这篇分析给出的具体含义是：原本靠手调搜索完成的稀疏权重修改，可以改写成一个线性规划问题并用现成求解器求解。据第三方摘要转述，作者在 Qwen3.5-0.8B 修复“思考循环”的案例上约一分钟即可求解，在 MATH-500、GSM8K 和 IFEval 上取得与原编辑相当的结果，同时改动的权重少 8 倍。不过这些数字来自个人博客及其转述，尚无独立复现，演示规模也仅限 0.8B 小模型；在迁移到更大模型前，需要自行验证目标行为与保留行为是否仍能写成可解的线性约束。

**「社区讨论」** 多位评论者认为该思路值得推进：有人建议把线性约束作为 Astra 类权重编辑的引导，有人主张直接在训练中通过正则化实现，还有人提出迭代式权重空间蒸馏。讨论同时留下疑问：这种方法能否扩展到更大模型和多变量奖励场景，仍缺少证据。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://huggingface.co/jarrodwatts/Qwen3.8-27B-Astra-Stop">jarrodwatts/ Qwen 3.8-27B- Astra -Stop · Hugging Face</a></li>
<li><a href="https://honnibal.dev/blog/astra-read-write-misleading">The &#x27; Astra can read and write weights to improve Qwen &#x27; post is...</a></li>
<li><a href="https://proomt.com/item/can-a-linear-program-do-weight-space-programming-d1a13007-a589-44d0-b87e-067ea543171c">Can a Linear Program Do Weight-Space Programming? · proomt</a></li>

</ul>
</details>

**标签**: `#machine-learning`, `#weight-editing`, `#linear-programming`, `#llm`, `#model-interpretability`

---

<a id="item-tech-news-6"></a>
### [谷歌发布 Gemini Decisions API，支持音视频与 PDF 输入](https://simonwillison.net/2026/Nov/11/gemini-decisions-api/) ⭐️ 7.0/10

谷歌发布 Gemini Decisions API，搭载新模型 Gemini Decision 1，加入此前由 Jev 和 OpenAI 的 GPT-6 Luna 占据的决策模型品类；据 Telegram 频道介绍，该 API 现已在 Google AI Studio 提供。它支持是/否、多选和评分量表三类问题，输入覆盖文本、图像、音频、视频和 PDF，而 Jev 仅限文本与 JSON、OpenAI 支持文本和图像。定价为每百万输入 token 0.10 美元、输出不收费，与 GPT-6 Luna 持平，但高于 Jev 的每百万 4.2 美分；Telegram 频道称其比基于 Gemini 3.5 Flash-Lite 的方案便宜近 5 倍，单次最多可提交 1000 个问题。Simon Willison 用一段机器人视频实测，模型对“视频中有机器人”给出 0.923 的概率、对“有龙”给出 0.0498，而 Jev 和 OpenAI 对是/否问题只返回 1.0 或 0.0。

rss · Simon Willison · 11月11日 22:03

**「背景」** 所谓决策模型，是一类专门回答封闭式问题的 API：输入可以是文本或多模态内容，输出是对若干预设问题（是/否、多选、评分量表）的概率或分数，而不是自由生成的文本。据本文所述，在 Gemini Decision 1 之前，该领域已有 Jev 和 OpenAI 的 GPT-6 Luna 决策模型；Gemini 沿用 Jev 的题型设计，并把输入范围从纯文本扩展到图像、音频、视频和 PDF。

**「影响」** 对需要在视频、音频或 PDF 上做判定的开发者，Gemini Decision 1 是目前三家中唯一覆盖这些输入的选择；但它的是/否结果是概率而非 1.0/0.0，接入方需自行设定阈值和回退逻辑，为 Jev 或 GPT-6 Luna 写的二值判断代码不能直接复用。

**标签**: `#Gemini`, `#API`, `#decision models`, `#multimodal AI`, `#AI pricing`

---

<a id="item-tech-news-7"></a>
### [Anthropic 路演视频披露四类芯片与算力乘数策略](https://simonwillison.net/2026/Nov/11/anthropic-ipo-roadshow/) ⭐️ 7.0/10

Anthropic 在 IPO 路演视频中披露了此前未公开的多芯片计算策略细节：Claude 的训练与推理现已覆盖 AWS Trainium、Google TPU、NVIDIA GPU 和 AMD GPU 四个芯片家族。联合创始人 Tom Brown 称，这源于公司早期对多芯片策略的押注；他举例说，今年首次接入 AMD GPU 时，Mythos 在几乎无人工干预的情况下用三天让 Claude 运行起来，Claude 编写或移植了近 100% 的 kernel。这些均为路演中的公司说法，尚未独立验证。Simon Willison 指出视频没有官方文字记录，并用 MacWhisper 提取了记录；他还提到 Anthropic 宣称通过不断发现“算力乘数”来扩大有效算力，并认为未来可能走向递归自我改进。

rss · Simon Willison · 11月11日 15:11

**「背景」** 训练和部署大模型通常深度绑定单一芯片平台，因为每类芯片都需要专门的编译器与推理栈，跨平台移植成本很高。Simon Willison 指出，Anthropic 的多芯片路线此前只露出过一点线索：该公司在《三起近期问题的复盘》中描述过仅影响其 TPU 部署的缺陷。此次路演视频是 Anthropic 首次系统说明这套跨芯片策略。

**标签**: `#Anthropic`, `#AI infrastructure`, `#AI chips`, `#IPO`

---

<a id="item-tech-news-8"></a>
### [字节跳动拟数周内发布类 Muse 智能体，目标 2030 年前追平 OpenAI](https://www.bloomberg.com/news/articles/2026-11-11/bytedance-prepares-muse-like-agent-in-push-to-close-ai-gap) ⭐️ 7.0/10

据彭博社报道，字节跳动计划在未来数周内发布一款类似 Meta Muse 的 AI 助手，以巩固其在 AI 视频领域的领先地位，并缩小与美国顶尖实验室的差距。联合创始人张一鸣在内部全员会上向 AI 团队提出，公司至少要到 2029 或 2030 年才能在前沿模型领域与 Anthropic、OpenAI 比肩。报道还称，字节跳动将最多投入 700 亿美元打造 Seedance 视频 AI 平台，且不主张依赖模型蒸馏。上述内容均为报道中的计划与内部表态，产品尚未发布，也没有技术细节或独立验证。

telegram · zaihuapd · 11月11日 12:31

**「背景」** Meta 于 2026 年 9 月发布 Muse，并将其描述为能替用户执行任务的个人 AI 智能体，而不仅仅是回答问题的聊天机器人。据 Meta 及媒体报道，Muse 可跨对话记住用户信息，并支持浏览网页和完成购买，这为理解字节跳动所筹备的“类 Muse”助手提供了参照。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://about.fb.com/news/2026/09/introducing-muse-personal-ai-agent/">Introducing Muse : The World’s First Personal AI Agent Built for...</a></li>
<li><a href="https://www.vktr.com/ai-platforms/meta-launches-muse-a-personal-ai-agent-that-browses-the-web-makes-purchases/">Meta Launches Muse , a Personal AI Agent That Browses the Web...</a></li>

</ul>
</details>

**标签**: `#AI industry`, `#ByteDance`, `#AI agents`, `#frontier model competition`, `#video generation`

---

<a id="item-tech-news-9"></a>
### [The Information 调查指黄乐协助 24 万颗英伟达芯片入华](https://www.tomshardware.com/tech-industry/policy/alice-huang-reportedly-instrumental-in-securing-over-usd7-5-billion-of-nvidia-ai-gpu-imports-during-three-year-relationship-with-jensen-huang-helped-move-240-000-banned-chips-into-china-mostly-h100-and-h200) ⭐️ 7.0/10

The Information 的一项调查报道称，Alice Huang（黄乐）借助与英伟达 CEO 黄仁勋的关系，协助约 24 万颗受出口管制的英伟达 AI GPU 进入中国，主要为 H100 和 H200，涉及进口金额约 75 亿美元。报道点名上海世纪利通和新加坡 Megaspeed 等公司参与相关流转。该消息来自 Tom&\#x27;s Hardware 对这项调查的简短转述，属于尚未得到独立确认的指控；源报道的细节和各方回应未在材料中给出。

telegram · zaihuapd · 11月11日 14:41

**「背景：受管制的芯片与新加坡中转渠道」** 美国出口管制长期禁止英伟达向中国出售 H100、H200 等旗舰数据中心 GPU，这类芯片因此只能通过第三地转口等途径流入。据 Tom&\#x27;s Hardware 与 Invezz 报道，Alice Huang（与黄仁勋无亲属关系）曾在总部位于新加坡的 Megaspeed International 担任高管；调查所称的约 24 万颗芯片（含 H100、H200 与 A100）即经由该网络以及上海世纪利通流转。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.tomshardware.com/tech-industry/policy/alice-huang-reportedly-instrumental-in-securing-over-usd7-5-billion-of-nvidia-ai-gpu-imports-during-three-year-relationship-with-jensen-huang-helped-move-240-000-banned-chips-into-china-mostly-h100-and-h200">Alice Huang reportedly instrumental in securing over... | Tom&#x27;s Hardware</a></li>
<li><a href="https://invezz.com/news/2026/11/10/nvidia-stock-slides-6-as-chip-probe-puts-jensen-huang-under-pressure/">Nvidia stock slides 6% as chip probe puts Jensen Huang under pressure</a></li>
<li><a href="https://cryptobriefing.com/shanghai-century-litong-nvidia-chips-china/">Shanghai Century Litong reportedly moved $7.5 billion in Nvidia chips...</a></li>

</ul>
</details>

**标签**: `#Nvidia`, `#AI chips`, `#export controls`, `#China`, `#semiconductor industry`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [古尔斯比称 10 月通胀报告“近乎令人不安”，美联储权衡进一步加息](https://www.cnbc.com/2026/11/11/goolsbee-october-inflation-fed-rates-disturbing-distressing.html) ⭐️ 8.0/10

芝加哥联储主席古尔斯比称 10 月 CPI 报告“近乎令人不安”：该指数经季节调整后环比上涨 0.4%，高于经济学家预期，且为连续第三个月大幅上涨，令美联储 12 月是否进一步加息成为焦点。

rss · CNBC Finance · 11月11日 16:49

**「背景」** 美联储 9 月已加息 25 个基点（0.25 个百分点），把利率目标区间提高到 3.75%-4%，10 月则维持不变；今年有投票权的官员现在争论 12 月加息 25 还是 50 个基点。

**「影响」** 据 CME FedWatch，报告和官员表态后，联邦基金利率期货一致预期 12 月加息，押注 50 个基点（0.5 个百分点）加息的概率为 15%。

**标签**: `#Federal Reserve`, `#inflation`, `#interest rates`, `#monetary policy`, `#CPI`

---

<a id="item-finance-news-2"></a>
### [离岸信托收益征税过渡期结束，税务总局称累计申报个税逾 1600 亿元](https://www.news.cn/20261111/9bcce99c779b4a6197ff45bbbc3e4c50/c.html) ⭐️ 8.0/10

税务总局 11 月 11 日表示，离岸信托收益征税的 90 天过渡期已结束，累计申报个人所得税超过 1600 亿元，其中 10 月入库超过 1200 亿元，并称这带动当月全国个人所得税收入增长近 90%。

telegram · zaihuapd · 11月11日 10:35

**「背景」** 此前，财政部、税务总局于 2026 年 7 月 24 日发布公告，要求居民个人就 2026 年 1 月 1 日前离岸信托存续期间取得的收益，按“利息、股息、红利所得”在 90 天内（至 10 月 22 日）申报缴纳个人所得税，按期缴纳不加收滞纳金。

**「影响」** 未主动申报或申报不实的离岸信托收益纳税人将面临补缴税款和滞纳金，仍不改正的会被立案稽查，直接影响相关高净值人群的税务安排。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://t.me/zaihuapd/45068">在花 科技圈 – Telegram</a></li>
<li><a href="https://news.creaders.net/china/2026/10/20/3060337.html">截止前三 天 ，北京突然又打了6 个 补丁！ -中国瞭望-万维读者网（电脑版）</a></li>
<li><a href="https://www.giffordchen.com/blog/chinapersonalincometaxontrust2026">重磅消息：关于离 岸 信 托个 人 所 得 税有关事项 - 信 托</a></li>

</ul>
</details>

**标签**: `#离岸信托`, `#个人所得税`, `#税收征管`, `#财税政策`, `#中国`

---