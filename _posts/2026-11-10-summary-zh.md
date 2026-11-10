---
layout: default
title: "Horizon Summary: 2026-11-10 (ZH)"
date: 2026-11-10
lang: zh
---

> 从 46 条内容中筛选出 9 条重要资讯。

---

**科技新闻**
1. [谷歌推出 TPU 8tx 和 8i Max 两款新芯片](#item-tech-news-1) ⭐️ 8.0/10
2. [E-means 声称以十分之一轮次超越 k-means](#item-tech-news-2) ⭐️ 7.0/10
3. [消费者版 Gemini 被指将个人 Drive 与邮件送人工审核](#item-tech-news-3) ⭐️ 7.0/10
4. [watched.earth：任意地点一周卫星过境与实拍影像](#item-tech-news-4) ⭐️ 7.0/10
5. [LingBot-Touch：以隐空间预测取代重建的触觉编码器](#item-tech-news-5) ⭐️ 7.0/10
6. [XGBoost 县级新增停电预报：PR-AUC 为预警基线 2.4 倍](#item-tech-news-6) ⭐️ 7.0/10
7. [OPPO、vivo、小米、荣耀上线安卓侧载 ADV 验证](#item-tech-news-7) ⭐️ 7.0/10
8. [欧盟草案拟限成瘾性设计并标注虚拟货币币值](#item-tech-news-8) ⭐️ 7.0/10

**财经新闻**
1. [前三季度中国新能源乘用车出口同比增长 138.8%](#item-finance-news-1) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [谷歌推出 TPU 8tx 和 8i Max 两款新芯片](https://www.bloomberg.com/news/articles/2026-11-09/google-escalates-nvidia-rivalry-with-new-versions-of-its-tpu-systems) ⭐️ 8.0/10

谷歌宣布推出两款新的张量处理单元 TPU 8tx 和 TPU 8i Max：前者面向政府机构及受严格监管行业，用于处理安全机密数据，并将与 AMD 芯片协同工作；后者面向超长上下文窗口 AI 应用，把两颗 TPU 芯片集成在同一封装内，以提供更强算力和更大内存。谷歌今年连续扩充 TPU 产品线，打破过去每两年推出一款新处理器的节奏；报道还提到苹果、Meta、甲骨文和 Anthropic 等已成为客户。该消息未给出两款芯片的性能基准、价格或上市时间，也未提供谷歌的一手确认。

telegram · zaihuapd · 11月9日 13:36

**「背景」** 谷歌过去的节奏是每两年推出一款新处理器；今年它改为针对不同应用场景连续扩充 TPU 产品线，8tx 和 8i Max 正是在这一策略下新增的专用型号。TPU 是谷歌自研的 AI 加速芯片，谷歌正试图将其打造为英伟达 GPU 之外的重要选择。

**「影响」** 受监管机构若采用 8tx，需要把与 AMD 芯片的协同工作纳入采购和兼容性验证，这会使部署评估不再只围绕谷歌单一加速器栈。

**「社区讨论」** 在 Hacker News 评论中，mekpro 称 Google Colab 目前能用到的最强 TPU 仍是 v6e-1，认为其规模不足以支撑严肃工作；ur-whale 要求公布每 token 功耗或成本，并与英伟达同价位产品对比，qntty 则追问谷歌为何不直接出售这些芯片。

**标签**: `#TPU`, `#Google`, `#AI hardware`, `#Nvidia`, `#semiconductors`

---

<a id="item-tech-news-2"></a>
### [E-means 声称以十分之一轮次超越 k-means](https://e-means.github.io/) ⭐️ 7.0/10

E-means 项目主页声称，这种新的聚类方法能在仅相当于 k-means 十分之一的迭代轮次下取得更好的聚类效果，对需要处理大规模数据的开发者具有潜在吸引力。当前证据主要来自项目自身声明和 Hacker News 上的早期试用，尚无独立基准或同行评审结果，因此“超越 k-means”还不能视为已证实的普遍结论。

hackernews · porridgeraisin · 11月9日 18:45 · [社区讨论](https://news.ycombinator.com/item?id=50429734)

**「背景」** k-means 的常用实现是 Lloyd 算法：每轮把每个点分配给最近的质心，再把质心更新为簇均值；Faiss 的默认配置要跑 25 个 epoch，在数十亿向量、数千万簇的规模下，这一循环开销很大。e-means 的论文用基于指数移动平均的 mini-batch 更新替代这套全量迭代，并报告在 1.2 至 3 个 epoch 内达到低于 25 个 epoch Lloyd 的测试损失。

**「适用场景需基准测试」** 对考虑替换 Lloyd&\#x27;s/k-means 的开发者，社区实测显示收益高度依赖负载：有评论者称在 GPU 上改造 IVF 索引获得 146 倍加速，另一项整库重建场景（如分片拆分）快 2.5 倍，但常规增量插入的总耗时变化不大；也有人将其用于球面网格松弛时效果反而更差。因此应先在自身数据分布和更新模式下做基准测试，再决定是否替换现有聚类实现。

**「社区讨论」** 有评论者报告了实际收益：real\_faxenoff 称将其适配到 GPU 上的 IVF 索引后获得 146 倍加速，kingcauchy 称对需要全量重建的索引做批量构建快 2.5 倍，但日常增量插入的总耗时变化不大。也有反例，jlhawn 尝试用于球面网格松弛后认为效果并不更好，说明该方法并非在所有场景都能替代 Lloyd 算法。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://openreview.net/pdf?id=pt14gnV3dl">E-MEANS OUTPERFORMING K MEANS IN ONE TENTH THE EPOCHS</a></li>
<li><a href="https://agihunt.info/en/papers/2611.09501">Meta FAIR&#x27;s e-means beats 25-epoch k-means loss… · AGI Hunt</a></li>
<li><a href="https://daily.dev/posts/e-means-10x-faster-k-means-at-equal-loss-wjgmcpump">E-means: 10x faster k-means at equal loss - daily.dev</a></li>

</ul>
</details>

**标签**: `#clustering`, `#machine-learning`, `#k-means`, `#algorithms`, `#performance`

---

<a id="item-tech-news-3"></a>
### [消费者版 Gemini 被指将个人 Drive 与邮件送人工审核](https://github.com/thisisme6598/gemini_files/) ⭐️ 7.0/10

Hacker News 上的一项讨论聚焦一项指控：消费者版 Google Gemini 在启用 Connected Apps 并授权 Gmail 等应用后，可能把个人 Drive 文件和邮件内容交给人工标注者查看。评论指出，Workspace 版 Gemini 及面向企业的 Workspace Intelligence 仍声称不受人工审核约束，因此消费者版与企业版的条款不能混为一谈。该讨论转述的是相关说法，所给材料中没有 Google 官方确认或独立技术验证，具体触发条件、审核范围和保留期限均不明确。

hackernews · gf74918 · 11月9日 18:24 · [社区讨论](https://news.ycombinator.com/item?id=50429426)

**「背景」** 消费者版 Gemini 与 Workspace 版适用不同的数据条款：第三方对 Google 政策的梳理称，Workspace 中的 Gemini 不用于训练、也不接受人工审阅，而独立的消费者应用默认会用交互数据改进模型，部分对话可能被人工审阅。Gemini Apps Activity 设置决定这些对话是否被保存（最长三年）并用于改进 AI 系统。

**「影响」** 对个人用户而言，是否启用 Connected Apps 并授权 Gmail 或 Drive 是决定暴露面的关键；企业客户则应依据 Workspace 的合同与数据条款单独核实，不能把消费者版的审核说明直接套用到企业部署。

**「社区讨论」** 评论者 bri3d 强调问题限于启用 Connected Apps 的消费者版 Gemini，Workspace 产品则声称不受人工审核；rustyhancock 把 Gemini 回答与其刚收到的邮件异常贴合描述为个人体验，但未提供可验证证据。另有评论者 hek2sch 认为，带人工标注的 Gemini、NotebookLM 等工具普遍存在数据被查看或泄漏的风险。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.qadar.ai/ai-tools/gemini">Is Gemini safe for work ? Privacy &amp; AI governance | Qadar AI</a></li>
<li><a href="https://proton.me/blog/turn-off-gemini-on-android">Google AI is watching: How to turn off Gemini on Android | Proton</a></li>

</ul>
</details>

**标签**: `#AI privacy`, `#Google Gemini`, `#data governance`, `#human review`, `#Hacker News`

---

<a id="item-tech-news-4"></a>
### [watched.earth：任意地点一周卫星过境与实拍影像](https://www.watched.earth/) ⭐️ 7.0/10

开源项目 watched.earth 已发布：用户输入任意地点，即可在浏览器中查询过去 7 天内所有卫星过境，并调取这些过境对应的 Sentinel-2、Landsat 和 NASA 实际影像。作者称，过境搜索基于 CelesTrak 目录运行 SGP4，约半秒完成，并与极点、反子午线及窄幅覆盖的暴力计算结果比对，未漏过一次过境；这属于作者自述的验证，尚未独立复现。站点只有在确实存在影像时才标记“watched”，且表示不存储用户位置，约 1.7 万个在轨目标通过 GPU 每帧求解开普勒方程绘制。

hackernews · a585gupt · 11月9日 17:51 · [社区讨论](https://news.ycombinator.com/item?id=50428907)

**「轨道计算背景」** SGP4 是 NORAD 的解析轨道传播模型，配合两行轨道根数（TLE）等通用摄动（GP）数据，可算出卫星的地心惯性坐标；CelesTrak 已提供此类 GP 数据四十余年，并公开 SGP4 教程和参考实现。

**「影响」** 对需要确认某地是否被卫星拍摄的用户，工具直接给出对应影像，而不只是过境预测；但作者指出，Sentinel-2 时间戳常与实际过境时刻相差 5–10 分钟，按时间比对影像时需考虑这一偏差。

**「社区讨论」** 评论集中称赞其视觉呈现与多数据源整合完成度，一位自称从事地理空间工作的用户认为能查看卫星实际拍摄的影像很有用；另有用户表示它比 Copernicus 更易用，适合规划背包旅行。这些均为用户体验和主观评价，不构成对精度或完整性的独立验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://celestrak.org/software/tutorials/sgp4.php">CelesTrak: SGP4 Software Tutorial</a></li>
<li><a href="https://celestrak.org/software/tskelso-sw.php">CelesTrak: Satellite Tracking Software by T.S. Kelso</a></li>

</ul>
</details>

**标签**: `#satellite-tracking`, `#geospatial`, `#orbital-mechanics`, `#webgl`, `#open-source`

---

<a id="item-tech-news-5"></a>
### [LingBot-Touch：以隐空间预测取代重建的触觉编码器](https://www.reddit.com/r/MachineLearning/comments/1xs05uo/latent_prediction_beats_reconstruction_for/) ⭐️ 7.0/10

Robbyant 在 Reddit 公布 LingBot-Touch：一个 JEPA 式自监督触觉编码器，它不重建原始传感器信号，而是预测被遮蔽接触的隐表示；推理代码与 checkpoint 已公开。据帖子描述，在与同尺寸 MAE、VAE 重建模型的同数据对比中，1K 小时数据下触觉到视频 top-5 召回为 32.1%（JEPA）、5.6%（MAE）、4.4%（VAE）；到 4K 小时 JEPA 升至 49.3%，MAE 仍低于 9%，VAE 反而降到 3.1%。作者解释这是因触觉片段大部分是近零背景，重建损失可以在没学到真实接触的情况下下降。另有两处设计：掩码率在 300 步内从 40% 升到 80%（一开始就高掩码会遮住稀疏信号里所有接触 taxel 并引发梯度爆炸）；磁、压阻、视触觉三类传感器经统一的指尖坐标加 5D RoPE（时间、手指、三维位置）进入同一个共享 Transformer。在 26 个真实机器人任务、4 种策略共 104 个组合中，冻结编码器特征在 89 个组合里得分最高；在预训练未见过的磁性手上，LingBot-VLA 从 57.21 提升到 75.04。以上数字来自该帖对论文的自述，尚无独立复现验证。

reddit · r/MachineLearning · /u/Zealousideal-War7154 · 11月9日 18:52

**「背景」** Robbyant 的 LingBot 系列包括视觉-语言-动作基础模型 LingBot-VLA，其预训练数据覆盖 9 种双臂机器人配置的 2 万小时真实数据。此次 LingBot-Touch 的工作把冻结的触觉编码器特征用于 LingBot-VLA，以检验触觉预训练能否迁移到预训练中未见过的灵巧手。

**「影响」** 对做触觉预训练的团队，直接后果是重建类目标可能给出误导性的低损失：在背景占主导的触觉数据上，应以接触相关的下游指标而非重建误差来判断编码器质量；同时若采用渐进掩码，需从低掩码率预热，以免稀疏接触点被全部遮蔽导致训练不稳定。帖子报告的另一个可用结论是冻结编码器特征在多数策略-任务组合中表现最好，即下游可直接复用预训练编码器，而不必逐任务微调。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/Robbyant/lingbot-vla">GitHub - Robbyant / lingbot - vla : A Pragmatic VLA Foundation Model</a></li>
<li><a href="https://technology.robbyant.com/">Technology - Robbyant</a></li>

</ul>
</details>

**标签**: `#tactile representation learning`, `#self-supervised learning`, `#JEPA`, `#dexterous manipulation`, `#robotics`

---

<a id="item-tech-news-6"></a>
### [XGBoost 县级新增停电预报：PR-AUC 为预警基线 2.4 倍](https://www.reddit.com/r/MachineLearning/comments/1xs4hq8/forecasting_new_power_outages_per_county_hourly_2/) ⭐️ 7.0/10

一位 Reddit 用户报告了一个覆盖密苏里州和伊利诺伊州 216 个县的 XGBoost 模型，它结合 HRRR 风暴相关预报、县特征、当前停电和邻县数据，预测“从现在起 2 小时后开始的 6 小时内，新增至少 5% 用户停电”的概率。模型用 2020–2024 年数据训练、2025 年留出测试，报告 PR-AUC 0.094，对比 NWS 预警加 SPC 展望基线 0.039，约为 2.4 倍（bootstrap 95% 区间 2.0–3.3 倍）；在相同警报量下，捕获率为 30% 对 17%，精确率为 15% 对 11%。作者称，仅用密苏里州和伊利诺伊州数据训练，迁移到艾奥瓦、印第安纳和密歇根三州合计时，捕获率为 31% 对 19%，并自 11 月 1 日起保存每次预报用于盲测。该结果尚未经同行评审，且仅覆盖 216 个县，因此适用范围仍有限。

reddit · r/MachineLearning · /u/CarRepresentative843 · 11月9日 21:34

**「背景」** HRRR（High-Resolution Rapid Refresh）是美国 NOAA 的高分辨率快速更新数值天气预报模式；据 Weathernerds 的说明，00、06、12、18Z 起报可覆盖 48 小时，其他起报覆盖 18 小时。该项目的评估使用预报时点已发布的 HRRR 预测场（最近 5 个起报的平均），而不是事后观测天气，并把 NWS 警报与 SPC 一日展望整理成同口径的历史基线。

**「影响」** 对电网运营和应急调度而言，这一模型可作为预警之外的补充排序工具，但在 0.5% 的县小时基础发生率下，15% 的精确率仍意味着大量误报，不能单独作为出动依据；是否采用应先看 11 月 1 日起的盲测表现，并验证其在更多辖区的迁移效果。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.weathernerds.org/models/hrrr.html">Weathernerds HRRR</a></li>

</ul>
</details>

**标签**: `#machine learning`, `#power outages`, `#weather forecasting`, `#XGBoost`, `#grid resilience`

---

<a id="item-tech-news-7"></a>
### [OPPO、vivo、小米、荣耀上线安卓侧载 ADV 验证](https://mp.weixin.qq.com/s/ZiKBASSLzvsZ6WR2AUmFeg) ⭐️ 7.0/10

OPPO、vivo、小米、荣耀已在中国大陆上线 Android 侧载应用开发者身份验证（ADV），并支持四家平台互认验证结果，目的是建立开发者与应用的可信关联，帮助用户识别应用来源和安全性。已在四家开放平台注册上架的 App 会自动提交验证，无需单独申请；未完成验证的应用在侧载安装时会显示“未验证”提示，用户需手动确认后才能继续安装。来源未披露验证的技术标准、覆盖机型或正式生效时间等细节。

telegram · zaihuapd · 11月9日 11:44

**「背景」** 谷歌此前已推出 Android 开发者验证（ADV）计划，要求开发者在安装侧载应用时完成身份核验，以提升来源可追溯性。此次 OPPO、vivo、小米、荣耀在中国大陆上线的是面向本土市场的同类机制，并通过四家厂商互认验证结果，与单一平台主导的验证体系形成区别。

**「侧载安装摩擦上升」** 对于不在四家开放平台注册上架、主要靠 APK 直接分发的开发者，应用未完成验证会让用户在侧载安装时看到“未验证”提示并需手动确认，安装摩擦随之增加；对用户而言，该提示提供了来源线索，但并非安装阻断。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://post.smzdm.com/p/a825vxmq/">安 卓 侧 载 新规进入倒计时：9月30...</a></li>

</ul>
</details>

**标签**: `#Android`, `#app security`, `#sideloading`, `#developer verification`, `#China mobile ecosystem`

---

<a id="item-tech-news-8"></a>
### [欧盟草案拟限成瘾性设计并标注虚拟货币币值](https://www.mlex.com/mlex/articles/2546584/digital-businesses-face-addictive-design-controls-under-draft-eu-consumer-law) ⭐️ 7.0/10

一份泄露的草案显示，欧盟《数字公平法案》拟限制成瘾性设计和订阅陷阱，要求数字企业允许用户关闭自动播放、连续使用奖励等诱导过度使用的功能。草案还要求在线订阅提供取消按钮、续费提醒和人工客服，并在免费试用转为付费订阅前取得用户明确同意；同时禁止面向未成年人的游戏付费抽奖、“付费获胜”和画像广告，并要求游戏虚拟货币标明真实币值。欧盟委员会计划于 11 月 11 日提交该法案，并同步改革消费者保护合作框架；违规企业最高可被罚全球营业额的 6%，但两项提案都需欧洲议会与欧盟各国政府同意才能生效。

telegram · zaihuapd · 11月9日 16:42

**「背景」** 所谓“暗黑模式”，指通过界面设计诱导用户购买或延长使用时间的手法；欧盟委员会拟用《数字公平法案》更新在线消费者保护规则，把这类设计及订阅陷阱纳入监管。Euronews 看到的草案还列出十类将被直接禁止的操纵性设计，例如虚假的库存紧张提示、预勾选附加项和反复弹窗。

**「影响」** 对在欧盟提供游戏和订阅服务的企业来说，草案若获通过，将需要改造自动续费、试用转化和取消流程，并在虚拟货币界面标注真实货币价值，面向未成年人的付费抽奖和“付费获胜”机制也会被禁止。由于文本仍属泄露草案且需议会与成员国批准，现阶段更稳妥的做法是按其方向评估产品设计，而非把它当作已生效义务。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.euronews.com/2026/11/09/eu-to-blacklist-ten-manipulative-online-design-traps-leaked-draft-shows">EU to blacklist ten manipulative online design &#x27;traps&#x27;, leaked draft s...</a></li>
<li><a href="https://www.linkedin.com/posts/andreslehtmets_the-eu-is-working-on-something-called-the-activity-7434701662272872449-FKAC">The EU is working on something called the Digital Fairness Act . Most...</a></li>

</ul>
</details>

**标签**: `#EU regulation`, `#dark patterns`, `#subscription traps`, `#virtual currency`, `#consumer tech`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [前三季度中国新能源乘用车出口同比增长 138.8%](https://finance.sina.com.cn/tech/roll/2026-10-26/doc-iniwpfnc2438186.shtml) ⭐️ 7.0/10

2026 年前三季度，中国新能源乘用车出口 388.7 万辆，同比增长 138.8%；同期国内零售量为 775.8 万辆，同比下降 12.8%，出口增长成为车企销量增长的重要支撑。

telegram · zaihuapd · 11月10日 02:56

**「背景」** 国内需求走弱被归因于购车补贴和购置税优惠调整，以及去年同期销量基数较高；出口增长则成为车企销量增长的重要支撑。

**标签**: `#China auto industry`, `#NEV exports`, `#domestic vehicle demand`, `#purchase subsidies`, `#retail sales`

---