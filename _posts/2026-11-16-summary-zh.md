---
layout: default
title: "Horizon Summary: 2026-11-16 (ZH)"
date: 2026-11-16
lang: zh
---

> 从 36 条内容中筛选出 9 条重要资讯。

---

**科技新闻**
1. [MLLM 视觉编码器预训练可选，视觉专用参数不可省](#item-tech-news-1) ⭐️ 8.0/10
2. [美团开源 LongCat-2.5 智能体模型，宣称华为升腾训练](#item-tech-news-2) ⭐️ 8.0/10
3. [现代大语言模型的位置嵌入实现解析](#item-tech-news-3) ⭐️ 7.0/10
4. [Protomaps：自托管地图瓦片变得便宜且简单](#item-tech-news-4) ⭐️ 7.0/10
5. [MacBook Pro OLED 屏幕的 PWM 闪烁问题](#item-tech-news-5) ⭐️ 7.0/10
6. [工具称将 B300 上可分页 cudaMemcpy 提速约 5 倍](#item-tech-news-6) ⭐️ 7.0/10

**财经新闻**
1. [卢特尼克因英伟达“间谍”风波面临质询，其子执掌公司与英伟达存在业务往来](#item-finance-news-1) ⭐️ 7.0/10
2. [美光三星 SK 海力士 DRAM 价格操纵案撤诉动议被驳回](#item-finance-news-2) ⭐️ 7.0/10
3. [报道称中美俄领导人计划在深圳 APEC 场边举行首次三方会晤](#item-finance-news-3) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [MLLM 视觉编码器预训练可选，视觉专用参数不可省](https://www.reddit.com/r/MachineLearning/comments/1xx1k2o/meta_fair_nyu_unbundling_multimodal_vision/) ⭐️ 8.0/10

Meta FAIR 与 NYU 作者在 Reddit 公布、尚未独立复核的一项受控研究，训练了 200 多个从零开始的 MLLM（包括 LLM），在相同数据和统一算力预算下拆分视觉编码器的三项选择：单独预训练、视觉专用参数，以及把编码器放在 LLM 之前。作者报告，单独预训练最多只能与从零联合训练打平；即使预训练不计入额外算力也没有帮助。把 MetaCLIP 预训练延长 6.5 倍，可将 ImageNet 线性探针从 80.4% 提升到 84.4%，但 VQA 不变。相反，视觉专用参数不可省：无编码器模型在 0.6B–6.4B 各规模均落后，约需 3 倍算力才能追上；放置位置也可省，把零初始化的视觉专用权重加入 LLM 前 8 层，在 1.7B–6.4B 与编码器相当，首 token 时间约低 13%。

reddit · r/MachineLearning · /u/trungh98 · 11月15日 17:38

**「背景」** 多模态大模型通常把在图像-文本或自监督任务上预训练好的视觉编码器接到语言模型前，并将编码器预训练、视觉专属参数和放置位置作为一个整体设计。而已有模型在训练数据和算力上各不相同，很难单独判断这三项选择各自是否必要。

**「影响」** 按作者结论，多模态团队可把算力优先投入视觉专用容量，而不是编码器预训练；若考虑把视觉分支放入 LLM 前 8 层，应以自有数据和推理栈验证 VQA 持平与约 13% 的首 token 延迟优势能否复现。

**标签**: `#multimodal LLMs`, `#vision encoders`, `#MLLM training`, `#empirical study`, `#model architecture`

---

<a id="item-tech-news-2"></a>
### [美团开源 LongCat-2.5 智能体模型，宣称华为升腾训练](https://the-decoder.com/meituan-releases-a-1-6-trillion-parameter-agent-model-that-never-touched-an-nvidia-gpu/) ⭐️ 8.0/10

美团 LongCat 团队在正式发布一周后公开了 LongCat-2.5 的模型权重；该模型面向可自主执行长流程、多步骤任务（尤其是编程）的智能体，支持文本、图像和视频输入，并以 MIT 许可证发布、允许商用。官方称其每个 token 激活约 480 亿参数，训练全程使用华为升腾加速卡，未使用英伟达 GPU。在 Terminal Bench v2.1 上，LongCat-2.5 得分为 88.4，略低于 Claude Opus 5 的 89.1；训练硬件和基准成绩均为美团官方说法，尚未获得独立验证。

telegram · zaihuapd · 11月15日 11:08

**「背景」** LongCat-2.5 采用混合专家（MoE）架构：模型总参数量约为 1.6 万亿，但每个 token 只激活约 480 亿参数，也就是说单次推理只调用其中一部分专家网络，因此总规模与实际计算开销并不等同。该模型一周前先正式发布，随后才公开可下载的权重，因此此次开源是该发布流程的后续一步。

**「对开发与部署的影响」** 对于打算商用或自托管编程智能体的团队，MIT 许可证允许直接修改和部署，但公开的自托管部署说明面向华为升腾集群（相关介绍提到 194 张升腾卡），因此现有以英伟达为主的推理基础设施不能直接沿用，需要按升腾环境重新评估适配与容量。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://af.net/realtime/meituan-releases-open-weight-1-6t-moe-model-longcat-2-5/">Meituan Releases Open-Weight 1.6T MoE Model LongCat-2.5</a></li>

</ul>
</details>

**标签**: `#open-source AI`, `#agent models`, `#Huawei Ascend`, `#LLM training`, `#multimodal`

---

<a id="item-tech-news-3"></a>
### [现代大语言模型的位置嵌入实现解析](https://magazine.sebastianraschka.com/p/understanding-positional-embeddings) ⭐️ 7.0/10

这篇技术解释文章面向使用 Transformer 的读者，梳理现代大语言模型中位置嵌入的实现方式，重点在帮助理解已有架构，而非发布新模型或新方法。按现有信息，它属于教学性技术解释，并非突破性研究或新的实验结果。

hackernews · vismit2000 · 11月15日 12:14 · [社区讨论](https://news.ycombinator.com/item?id=50506376)

**「背景」** 位置嵌入用于让 Transformer 区分 token 在序列中的先后顺序。常见方案包括把位置向量直接加到 token 表示上，或在注意力计算中编码相对位置；RoPE 则对 query 和 key 施加与位置相关的旋转，把相对位置信息带入注意力分数。

**「社区讨论」** 评论区中，programjames 认为仅理解实现还不够，主张从群论角度把握位置嵌入：位置嵌入是群表示，并以旋转位置嵌入作为平移群表示的例子。该评论在给出的片段中未完整展开，因此其关于参数化与可学习性的具体论证无法核实。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://apxml.com/courses/how-to-build-a-large-language-model/chapter-13-positional-encoding-variations/rotary-position-embedding-rope">Rotary Position Embedding (RoPE) Explained - apxml.com</a></li>

</ul>
</details>

**标签**: `#positional-embeddings`, `#LLMs`, `#transformer-architecture`, `#deep-learning`, `#technical-explainer`

---

<a id="item-tech-news-4"></a>
### [Protomaps：自托管地图瓦片变得便宜且简单](https://bruceroettgers.eu/blog/protomaps/) ⭐️ 7.0/10

一篇技术文章称，借助 Protomaps 和 PMTiles，自托管地图瓦片已经变得便宜且容易，主要面向希望掌控地图基础设施、又不想承担商业地图服务成本的开发者和中小项目。文章把这套方案描述为可实际部署的选择，其基础数据来自 OpenStreetMap，瓦片以 PMTiles 格式分发。现有材料未提供独立的成本或性能测量。

hackernews · bcye · 11月15日 19:26 · [社区讨论](https://news.ycombinator.com/item?id=50509837)

**「背景」** Protomaps 的核心是 PMTiles：一种把整层地图瓦片打包进单个文件的归档格式，可放在 S3 等普通对象存储上，客户端通过 HTTP Range 请求按需取块，因此不需要自建瓦片后端或第三方地图服务。与按调用量计费的 Mapbox、Google Maps API 不同，这种模式把成本转为自己的存储和带宽开销，且不依赖 API key。

**「适用场景与存储边界」** 对需要自建底图的开发者而言，Protomaps 把瓦片打包成单个 PMTiles 文件放在 S3、R2 等对象存储上，客户端通过 HTTP range 请求按需取块，因此不必再维护自建的瓦片后端或第三方提供商（tool-3-1、tool-3-2）。不过评论者 motoroco 提醒，这一成本优势主要适用于矢量底图：高分辨率卫星影像随缩放级别提升体积迅速膨胀，他为自己的应用制作北美卫星镶嵌图时，因预估存储需求过大只能做到 z17。

**「社区讨论」** 评论提供了多种实际用法：有人用 Protomaps 构建按真实街道实时渲染的 Wikipedia 步行游戏，称商业地图服务会让这个副项目难以启动；也有人把 PMTiles 放在 Cloudflare R2 后面，以隐私和访问控制为目的自行托管地图基础设施。讨论还提到 OpenFreeMap 这类免费公共实例，并指出高缩放级别卫星影像的存储成本会迅速上升，以及部分大于 128MB 的瓦片和某些栅格格式在现有工具中仍会失败。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://protomaps.com/">Protomaps - The open source map in a file</a></li>
<li><a href="https://github.com/protomaps/PMTiles">GitHub - protomaps/PMTiles: Pyramids of map tiles in a single ...</a></li>
<li><a href="https://protomaps.com/about">Protomaps - The open source map in a file</a></li>
<li><a href="https://github.com/protomaps/PMTiles">GitHub - protomaps / PMTiles : Pyramids of map tiles in a single file on...</a></li>
<li><a href="https://protomaps.com/">Protomaps - The open source map in a file</a></li>

</ul>
</details>

**标签**: `#protomaps`, `#self-hosting`, `#map-tiles`, `#openstreetmap`, `#pmtiles`

---

<a id="item-tech-news-5"></a>
### [MacBook Pro OLED 屏幕的 PWM 闪烁问题](https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/) ⭐️ 7.0/10

一篇技术分析文章关注 MacBook Pro 的 OLED 屏幕为何可能让部分对闪烁敏感的用户更难使用：PWM 调光会引入闪烁，而显示效果提升并不意味着所有人都能获得更好的体验。文章讨论了调光频率与敏感性问题，评论区则对 240Hz 的结论提出复核和质疑，并推测串联 OLED 的两层以 480Hz 反相工作、在两层同时亮起时形成最高约 960Hz 的有效频率。上述频率推断尚未在给定材料中得到独立确认，受影响用户应结合自身耐受度判断。

hackernews · MacAnorak · 11月15日 13:15 · [社区讨论](https://news.ycombinator.com/item?id=50506719)

**「背景」** MacBook Pro 产品线自 2021 年起使用 Mini‑LED 屏幕；此次苹果将串联 OLED（tandem OLED）引入 MacBook Pro，并称其为“PROLED XDR Display”，同时仍继续销售 Mini‑LED 机型。OLED 常以 PWM（脉宽调制）快速开关像素来调节亮度，频率较低时，部分对闪烁敏感的用户可能感到眼疲劳或不适，这正是围绕新屏幕的争议所在。

**「对闪烁敏感用户的影响」** 对于对 PWM 闪烁敏感的用户，这块 OLED 屏可能引发眼疲劳或头痛，因此“更好”的面板未必意味着更好用。购买前最好实际试用，并在退货窗口内确认自己能否适应；调整亮度等设置未必能完全消除不适。

**「社区讨论」** 评论区的核心分歧在 PWM 频率：有评论者复核 240Hz 说法后质疑测试结论，推测串联 OLED 的两层各以 480Hz 反相调光，因此两层同时工作时有效频率可达 960Hz；这一解释仍是评论者观点。另有评论者强调，闪烁敏感不只来自 PWM，白光 LED 的显色指数和 LCD 运动模糊等也会影响部分用户。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://macanorak.com/the-macbook-pros-oled-pwm-problem-when-a-better-display-becomes-worse-to-use/">The MacBook Pro ’s OLED PWM Problem: When a ‘Better’ Display...</a></li>
<li><a href="https://www.sleepaxa.com/blogs/light-sensitivity-guide/pwm-screen-headaches-oled-flicker">PWM Sensitivity: OLED Screen Headaches &amp; What Helps (2026)</a></li>
<li><a href="https://www.appleheadlines.com/macbook-pro-oled-eye-strain-pwm-flicker/">MacBook Pro OLED Eye Strain &amp; PWM Flicker: 7 Moves - AH</a></li>

</ul>
</details>

**标签**: `#OLED`, `#PWM flicker`, `#MacBook Pro`, `#display hardware`, `#eye strain`

---

<a id="item-tech-news-6"></a>
### [工具称将 B300 上可分页 cudaMemcpy 提速约 5 倍](https://www.reddit.com/r/MachineLearning/comments/1xx2n25/making_cudamemcpy_5x_faster_on_a_b300_p/) ⭐️ 7.0/10

一位开发者发布了名为 cudamemcpy-tuner 的工具，声称在 B300 上把可分页（pageable）的 cudaMemcpy 传输从 10.2 GB/s 提升到 51.5 GB/s，约为 5 倍。帖子给出的基准是把 1 GB 的 torch.uint8 张量复制到 GPU，重复 5 次，用 \`cmt tune -- python bench.py\` 运行时得到上述数字。该结果由作者自报，帖子仅链接了技术博客与 GitHub 开源代码，尚无独立验证。

reddit · r/MachineLearning · /u/makneeee · 11月15日 18:20

**「背景」** 在 CUDA 中，可分页（pageable）主机内存一般不能直接作为异步 DMA 的源或目标，cudaMemcpy 往往需要借助内部暂存缓冲区完成传输，因此带宽通常低于页锁定（pinned）内存路径。页锁定内存可避免操作系统将相关页面换出，使 GPU 能更直接地访问主机缓冲区，这也是高性能拷贝常推荐使用 pinned memory 的原因。

**「影响」** 对需要频繁进行主机到 GPU 可分页传输的开发者，这一工具若能在自有环境复现，可缩短数据搬运时间；但在生产使用前应先在目标 GPU 和工作负载上复测，并确认 \`cmt tune\` 与现有脚本的兼容性。

**标签**: `#CUDA`, `#GPU computing`, `#memory transfers`, `#performance optimization`, `#developer tools`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [卢特尼克因英伟达“间谍”风波面临质询，其子执掌公司与英伟达存在业务往来](https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html) ⭐️ 7.0/10

据 CNBC 报道，美国商务部长霍华德·卢特尼克正面临道德质疑：其子布兰登和凯尔执掌的 Cantor Fitzgerald 一方面维持对英伟达的“增持”评级和 350 美元目标价，另一方面申报持股数量在 2025 年 9 月底至 2026 年 3 月底间减少约 49%，市值从 6.52 亿美元降至 3.10 亿美元。CNBC 称，这与他抵制打击涉嫌经新加坡 Megaspeed 向中国转运英伟达芯片的努力同时发生（该抵制由 Axios 报道）；Cantor 表示其英伟达自营头寸“始终不重大”，申报持股源于为客户掉期交易进行的常规操作，报道也明确尚无证据显示卢特尼克泄露非公开信息或该公司知情。

rss · CNBC Finance · 11月15日 19:58

**「背景」** 黄仁勋辞任英伟达 CEO 后，外界重新审视曾长期执掌坎托·菲茨杰拉德的美国商务部长卢特尼克：该公司现由其子经营，而商务部正是负责出口管制的部门。

**「直接影响」** 美国商务部掌握英伟达对华出口许可的审批权，这轮围绕卢特尼克的审查令英伟达及其中国客户面临许可被暂停或重新评估的风险；参议员已公开提出这一要求，但目前尚无政策变更。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html">Howard Lutnick&#x27;s sons&#x27; Nvidia ties amid Jensen Huang China ...</a></li>
<li><a href="https://en.fnnews.com/news/202611140900042645">&#x27;Jensen Huang Scandal&#x27; Leaves U.S. Commerce Secretary Howard ...</a></li>
<li><a href="https://www.nytimes.com/2026/11/12/us/politics/lutnick-nvidia-commerce-china-chips.html">Howard Lutnick Took Softer Line on Nvidia as Calls for Tougher...</a></li>
<li><a href="https://www.cnbc.com/2026/11/13/howard-lutnick-nvidia-jensen-huang-china-cantor-fitzgerald.html">Howard Lutnick &#x27;s sons&#x27; Nvidia ties amid Jensen Huang China spy...</a></li>

</ul>
</details>

**标签**: `#Nvidia`, `#U.S. export controls`, `#Cantor Fitzgerald`, `#conflict of interest`, `#semiconductors`

---

<a id="item-finance-news-2"></a>
### [美光三星 SK 海力士 DRAM 价格操纵案撤诉动议被驳回](https://www.tomshardware.com/tech-industry/big-tech/judge-denies-motion-to-dismiss-dram-price-fixing-lawsuit-against-micron-samsung-and-sk-hynix-says-chipmakers-acted-like-hawks-flying-in-formation-finds-evidence-of-dram-collusion-plausible-after-500-percent-price-surge) ⭐️ 7.0/10

美国法官诺埃尔·怀斯（Noël Wise）驳回美光、三星和 SK 海力士要求撤销 DRAM 价格操纵集体诉讼的动议，认为原告所称三家公司一年内四次同步限制供应、价格最高上涨 500%足以让共谋指控具备合理性。三家公司须在 12 月 7 日前回应，案件管理会议定于 2027 年 1 月；相关指控尚未经审理认定。

telegram · zaihuapd · 11月15日 16:39

**「背景」** 这起拟议集体诉讼指控三星、SK 海力士与美光自 2022 年起合谋限制 DRAM（手机与服务器常用的内存芯片）供应；此次驳回撤诉动议意味着案件可继续推进并进入取证阶段，但法院尚未认定任何一方违法。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://hoodline.com/2026/11/judge-lets-dram-price-fixing-suit-against-samsung-micron-sk-hynix-move-forward/">Judge Allows DRAM Price-Fixing Suit Vs Samsung, Micron, SK Hynix</a></li>
<li><a href="https://wccftech.com/federal-judge-rejects-memory-makers-defense-samsung-micron-sk-hynix-dram-shortage-lawsuit/">Federal Judge Rejects Memory Makers’ Defense To Advance Class ...</a></li>

</ul>
</details>

**标签**: `#DRAM`, `#antitrust`, `#semiconductors`, `#Micron/Samsung/SK Hynix`, `#litigation`

---

<a id="item-finance-news-3"></a>
### [报道称中美俄领导人计划在深圳 APEC 场边举行首次三方会晤](https://apnews.com/article/trump-xi-putin-summit-china-5fe92253ef38100bae913834a9b74d72) ⭐️ 7.0/10

据中国外交部发言人宣布，中美俄三国领导人计划于 11 月 19 日在深圳 APEC 峰会期间举行三方会晤，会晤在 APEC 场边举行，不属于 APEC 正式议程。媒体称这将是三国领导人首次专门举行三方会晤；目前未公布议程或预期成果。

telegram · zaihuapd · 11月16日 01:38

**「背景」** 亚太经合组织（APEC）2026 年领导人会议于 11 月 18 日至 19 日在深圳举行，中国是东道主；据俄罗斯总统发言人佩斯科夫称，三方已就 11 月 19 日会晤达成一致，白宫也确认了特朗普的出席。此次会晤安排在 APEC 正式议程之外，媒体称这是三国领导人首次专门举行三方会晤。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://sputnikglobe.com/20261114/putin-xi-trump-to-hold-trilateral-meeting-in-chinas-shenzhen-on-november-19---peskov-1125073196.html">Putin, Xi, Trump to Hold Trilateral Meeting in China &#x27;s Shenzhen on...</a></li>
<li><a href="https://www.aljazeera.com/news/2026/11/14/trump-xi-putin-trilateral-meeting-at-apec-what-to-expect">Trump-Xi-Putin trilateral meeting at APEC : What to expect | Al Jazeera</a></li>

</ul>
</details>

**标签**: `#geopolitics`, `#China-US-Russia`, `#APEC`, `#diplomacy`, `#market risk`

---