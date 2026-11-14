---
layout: default
title: "Horizon Summary: 2026-11-14 (ZH)"
date: 2026-11-14
lang: zh
---

> 从 40 条内容中筛选出 7 条重要资讯。

---

**科技新闻**
1. [TorchTitan 在 384 块 GH200 上训练约 1T MoE 的实践](#item-tech-news-1) ⭐️ 8.0/10
2. [FAA 发布全国地面停飞令，空管通信故障疑为原因](#item-tech-news-2) ⭐️ 7.0/10
3. [微软 Outlook、Teams 与 Copilot 全球宕机逾 12 小时](#item-tech-news-3) ⭐️ 7.0/10
4. [DeepSeek 开放应用 API：搜索、文件、语音可单独调用](#item-tech-news-4) ⭐️ 7.0/10
5. [OpenAI 推出 ChatGPT Wallet，支持美国 Pro 用户用智能体付款](#item-tech-news-5) ⭐️ 7.0/10

**财经新闻**
1. [卢特尼克因英伟达相关争议受质询，其子执掌的 Cantor Fitzgerald 与英伟达关系深厚](#item-finance-news-1) ⭐️ 7.0/10
2. [芝加哥联储行长：美联储在通胀问题上“肯定还有工作要做”](#item-finance-news-2) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [TorchTitan 在 384 块 GH200 上训练约 1T MoE 的实践](https://www.reddit.com/r/MachineLearning/comments/1xvce5h/scaling_to_1t_moe_on_torchtitan_p/) ⭐️ 8.0/10

一位实践者发文称，其团队用 TorchTitan 在 JUPITER 的 384 块 GH200 上，以 384 路 FSDP 加 4 路专家并行（EP 限定在节点内）训练约 1T 参数 MoE，达到每 GPU 约 1,300 tokens/s，约为起点的 14 倍；这是作者自述的优化结果，并非独立复测。为提升吞吐，他们采用全量激活检查点、将检查点激活经 Grace 的 900 GB/s C2C 链路卸载并按层预取、用 Muon 替代 Adam 以支持 64k token 序列，还通过 FlexShard 按完整专家分片，使 Newton-Schulz 无需通信即可本地执行；把 Newton-Schulz 移到 GPU 后，优化器步从 42 秒降到约 2 秒，吞吐提升 35%。在通信侧，他们用 bf16 all-to-all 替换专家梯度的 fp32 reduce-scatter、在接收端做 fp32 求和，并采用 FP8 专家 all-gather 与节点内稠密权重重分片；作者称后两项改动未改变其对比运行中的 loss。作者还报告，一次软件升级后所有 rank 在约 70% HBM 利用率时触发分配器重试，原因是 FSDP 侧流上的缓存池占用约 21 GiB；将相关分配移到计算流并提前释放梯度后，重试从 384 个 rank 降为零，峰值保留内存减少 13.5 GiB，吞吐提升 21%。

reddit · r/MachineLearning · /u/f14-bertolotti · 11月13日 16:28

**「背景」** MoE 通过路由让每个 token 只经过少数专家，因此模型总参数可以远大于单次前向实际激活的参数量；FSDP 则把参数、梯度和优化器状态切片到各 GPU，并在计算前按需聚合。TorchTitan 是 PyTorch 生态中的大模型训练框架，而 GH200/JUPITER 的节点内 NVLink 与 Grace-Hopper 链路带宽明显高于节点间 InfiniBand，这使分片方式和通信路径成为关键约束。

**「对实践者的影响」** 对使用 TorchTitan 与 FSDP2 的团队来说，这次调优的部分经验已经回流到上游：把 Newton–Schulz 迭代放到 GPU 上执行后，优化器步从 42 秒降到约 2 秒、吞吐提升 35%，FlexShard 也已内置于 TorchTitan，因此类似的 MoE 训练配置可以直接复用这些改动，而不必自行绕开 FSDP 的分片限制。不过，用来解决“显存其实还空着却报 OOM”问题的 FSDP2 开关 unshard\_async\_op 目前仍是私有接口，正在转为公开 API，采用前需按具体版本确认其可用性。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://pytorch.org/blog/training-a-1t-parameter-moe-on-eu-public-infrastructure-with-pytorch-and-torchtitan/">Training a 1T-Parameter MoE on EU public ... - PyTorch</a></li>

</ul>
</details>

**标签**: `#distributed-training`, `#mixture-of-experts`, `#PyTorch/TorchTitan`, `#GPU-optimization`, `#large-language-models`

---

<a id="item-tech-news-2"></a>
### [FAA 发布全国地面停飞令，空管通信故障疑为原因](https://www.nbcnews.com/news/us-news/faa-orders-nationwide-ground-stop-departing-flights-reasons-safety-rcna609247) ⭐️ 7.0/10

美国联邦航空管理局（FAA）于 2026 年 11 月 13 日发布全国地面停飞令，暂停出发航班；有评论引用《纽约时报》报道称，该停飞令随后已被解除。关于原因，评论中转引的《华尔街日报》报道称，故障似乎影响 L3Harris Technologies 运营的电信网络，该网络承担空管员与飞行员通话所用的关键无线电频率，但是否波及雷达数据尚不清楚。素材中官方公开信息很少，停飞的具体范围、持续时间和根本原因仍未得到完整确认。

hackernews · zulln · 11月13日 21:05 · [社区讨论](https://news.ycombinator.com/item?id=50489641)

**「背景」** 美国的“地面停飞”（ground stop）是 FAA 要求地面航班暂不起飞、但允许已起飞航班继续降落的运行限制。此次事件中，FAA 先因芝加哥奥黑尔机场和中途机场的管制通信问题暂停当地航班，随后以“特殊情况”和 safety 为由将停飞范围扩大到全国，并称通信问题影响了多个空中航线交通管制中心。

**「实际影响」** 对旅客和航空公司而言，停飞直接造成出发航班取消或延误；有评论称洛杉矶国际机场自约当地时间 10:30 起没有航班起飞，旧金山机场网站因访问过载无法显示离港信息。

**「社区讨论」** 评论者最集中的不满是官方信息“少得惊人”，并围绕原因出现分歧：有人转引《华尔街日报》指向 L3Harris 的空管通信网络故障，也有人猜测这与 FAA 推广 AI 空管工具 SMART 有关，但后者没有证据支持。另有评论引用《纽约时报》称停飞令已解除，并报告了洛杉矶出发停摆和旧金山机场网站过载等现场情况。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/2026_FAA_communication_outage">2026 FAA communication outage - Wikipedia</a></li>
<li><a href="https://www.faa.gov/newsroom/faa-statement-nationwide-ground-stop">FAA Statement on Nationwide Ground Stop | Federal Aviation ...</a></li>
<li><a href="https://www.yahoo.com/news/us/article/faa-issues-nationwide-ground-stop-on-all-departing-flights-citing-communication-issue-213136811.html">FAA issues nationwide ground stop on all departing flights, citing...</a></li>
<li><a href="https://www.abc.net.au/news/2026-11-14/follow-live-us-aviation-authority-grounds-all-flights/107385742">US aviation authority grounds all departing flights, citing...</a></li>

</ul>
</details>

**标签**: `#FAA`, `#air traffic control`, `#critical infrastructure`, `#telecom outage`, `#aviation safety`

---

<a id="item-tech-news-3"></a>
### [微软 Outlook、Teams 与 Copilot 全球宕机逾 12 小时](https://www.reuters.com/technology/microsoft-365-outlook-down-thousands-us-users-downdetector-shows-2026-11-12/) ⭐️ 7.0/10

微软 Outlook、Teams 和 Copilot 在 11 月 13 日仍处于宕机状态，故障持续超过 12 小时，打乱全球企业与政府的通信。微软将原因归为服务器问题，称未发现恶意活动，已扩大修复范围并看到回稳迹象。澳大利亚、日本和美国部分政府机构受到影响，欧交所 Euronext 的邮件受阻，台湾有金融机构改用传真确认交易。这是微软 365 服务今年第二次中断。

telegram · zaihuapd · 11月13日 12:21

**「背景」** Microsoft 365 将 Outlook、Teams、Copilot 等应用作为云端服务提供，服务端异常会同时波及多个地区的用户。按来源说法，这已是微软 365 服务今年第二次中断。

**「实际影响」** 对依赖 Microsoft 365 的机构而言，此次中断迫使部分单位启用备用流程，例如台湾金融机构改用传真确认交易、欧交所邮件受阻；企业应为 Outlook 和 Teams 准备替代的通知与交易确认渠道。

**标签**: `#Microsoft 365`, `#Outlook`, `#Teams`, `#service outage`, `#cloud reliability`

---

<a id="item-tech-news-4"></a>
### [DeepSeek 开放应用 API：搜索、文件、语音可单独调用](https://mp.weixin.qq.com/s/78KBHc4-4N5b2vfL9SkutQ) ⭐️ 7.0/10

据聚合帖消息，DeepSeek 开放了“全家桶”应用 API：开发者在原有 API 中开启对应参数，就能让对话获得深度思考搜索、文件输入、阅读链接、语音等能力，工具调用与上下文拼接由服务端自动完成。V4.1-Flash 模型已在三个接口上支持这些能力，Search、Fetch、OCR、ASR、TTS 也可脱离对话单独调用。官方同时开源了前端 Demo「deepseek-ai/chat-demo」，可导入历史对话，让人基于 API 在本地部署 DeepSeek 网页端，并提供了在线体验地址。需要说明的是，该帖为简短聚合信息，未公布定价、调用限额或接口技术细节，上述能力也未获独立验证。

telegram · zaihuapd · 11月13日 14:27

**「背景」** DeepSeek 的 V4.1-Flash 并非全新模型：官方此前宣布，将用更快、更便宜的 V4.1-Flash 逐步替代 V4-Pro，并从 2026 年 9 月 14 日 04:00 UTC 起，把所有 V4-Pro 请求转由 V4.1-Flash 处理，直至 V4.1-Pro 推出。此次开放的应用 API 就以该模型为底层支撑之一。

**「对开发者的直接影响」** 已接入的开发者无需改动端点：模型名可继续用 deepseek-flash，旧名 deepseek-v4-flash 与 deepseek-v4-flash-vision-exp 虽然仍被接受，但请求会转由 V4.1-Flash-1017 处理，并按 Flash 价格计费。若把 OCR、ASR 等批量任务安排到非高峰时段运行，则可省下一半费用；高峰时段为 UTC 周一至周五 01:00–04:00 和 06:00–10:00。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.deepseek.com/en/news/deepseek-v4-1-flash/">DeepSeek | Introducing DeepSeek-V4.1-Flash: smarter, faster ...</a></li>
<li><a href="https://api-docs.deepseek.com/quick_start/pricing/?article_id=article_1779470751466_8">Models &amp; Pricing | DeepSeek API Docs</a></li>

</ul>
</details>

**标签**: `#DeepSeek`, `#API`, `#multimodal AI`, `#open source`, `#AI developer tools`

---

<a id="item-tech-news-5"></a>
### [OpenAI 推出 ChatGPT Wallet，支持美国 Pro 用户用智能体付款](https://openai.com/index/introducing-chatgpt-wallet/) ⭐️ 7.0/10

OpenAI 发布 ChatGPT Wallet，并称即日起在美国通过 dots 向 18 岁以上的 ChatGPT Pro 订阅用户开放，要求使用美国发行的银行卡。该钱包与美国运通、万事达、Visa 合作，让智能体在不接触用户真实卡号的情况下付款，支付网络会下发替代真实卡号的支付令牌。每笔购买仍需用户核对商品与金额，并通过 Face ID 或指纹确认。

telegram · zaihuapd · 11月13日 15:43

**「背景：支付令牌是什么」** 支付令牌是卡组织下发的替代数字串，用于在交易链路中替代真实卡号，使商户和中间环节拿不到用户的原始卡信息；这种机制此前已用于各类设备钱包等场景。ChatGPT Wallet 沿用同一思路，把令牌化卡支付接到智能体发起的购买流程上，并以逐笔生物识别确认作为放行条件。

**「影响」** 对符合条件的美国 Pro 用户，智能体代付不能跳过逐笔确认，因此不适用于无需用户在场的自动扣款；使用前还需持有美国发行的卡。

**标签**: `#OpenAI`, `#agentic payments`, `#AI agents`, `#payment security`, `#tokenization`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [卢特尼克因英伟达相关争议受质询，其子执掌的 Cantor Fitzgerald 与英伟达关系深厚](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 7.0/10

据 CNBC 对证券申报文件的分析，由美国商务部长霍华德·卢特尼克的两个儿子执掌的 Cantor Fitzgerald，在 2025 年 9 月底至 2026 年 3 月底期间报告的英伟达持股数量下降了 49%，从约 350 万股（价值 6.52 亿美元）降至 178 万股（价值 3.10 亿美元）。报道同时提到，卢特尼克在商务部内部面临对英伟达对华芯片出口管制处理方式的质询；CNBC 明确指出，目前没有证据显示存在不当行为或非公开信息共享。

rss · CNBC Finance · 11月13日 23:42

**「背景」** 卢特尼克在 2025 年出任美国商务部长前曾执掌坎托·菲茨杰拉德，而商务部正是负责执行芯片出口管制、包括把涉嫌违规企业列入实体清单的机构。英伟达 CEO 黄仁勋则在曝出与一名疑似中国间谍有婚外情等丑闻后，于周四辞职。

**「影响」** 英伟达对华销售需要得到商务部出口许可，而该部门由卢特尼克领导，因此这段被报道的持股与业务关系使相关许可决策受到更严格的审视。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Howard_Lutnick">Howard Lutnick - Wikipedia</a></li>
<li><a href="https://www.reuters.com/business/retail-consumer/nvidia-ceo-jensen-huang-step-down-big-blow-ai-boom-2026-11-12/">Nvidia CEO Jensen Huang resigns in blow to AI boom he helped ...</a></li>

</ul>
</details>

**标签**: `#Nvidia`, `#export controls`, `#conflict of interest`, `#Commerce Department`, `#Cantor Fitzgerald`

---

<a id="item-finance-news-2"></a>
### [芝加哥联储行长：美联储在通胀问题上“肯定还有工作要做”](https://www.cnbc.com/2026/11/13/chicago-feds-goolsbee-says-central-bank-has-definitely-got-work-to-do-on-inflation.html) ⭐️ 7.0/10

芝加哥联储行长古尔斯比 11 月 13 日表示，美联储在恢复抗通胀信誉方面“肯定还有工作要做”；此前公布的 10 月生产者价格指数同比上涨 6.5%，为 2022 年 11 月以来最高。据 CME Group 的 FedWatch 指标，市场已完全计入 12 月 8-9 日会议加息 25 个基点，并认为加息 50 个基点的概率超过 10%。

rss · CNBC Finance · 11月13日 14:22

**「背景」** 美联储的通胀目标是 2%，古尔斯比称通胀已近六年高于该目标、近期没有进展；生产者价格指数被视为批发价格指标。他目前不是联邦公开市场委员会（FOMC）投票委员，2027 年才将拥有投票权。

**标签**: `#Federal Reserve`, `#monetary policy`, `#inflation`, `#producer prices`, `#interest rates`

---