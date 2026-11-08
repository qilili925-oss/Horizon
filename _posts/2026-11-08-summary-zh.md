---
layout: default
title: "Horizon Summary: 2026-11-08 (ZH)"
date: 2026-11-08
lang: zh
---

> 从 39 条内容中筛选出 11 条重要资讯。

---

**科技新闻**
1. [Asahi Linux 首次同日交付 Fedora Asahi Remix](#item-tech-news-1) ⭐️ 8.0/10
2. [SemiAnalysis 实地探访内蒙古 800MW AI 数据中心园区](#item-tech-news-2) ⭐️ 8.0/10
3. [GitHub 新 Git 存储架构 Rubicon 进入有限私有预览](#item-tech-news-3) ⭐️ 8.0/10
4. [微软研究院 AI Frontiers 研究组据报结束，Langford 离职](#item-tech-news-4) ⭐️ 7.0/10
5. [Coldframe：伪装超市冷柜控制器的 Python 蜜罐](#item-tech-news-5) ⭐️ 7.0/10
6. [浏览器版《极品飞车：地下狂飙 2》支持在线多人](#item-tech-news-6) ⭐️ 7.0/10
7. [Claude Code 的“不再询问”被指与 1,122 个公开文件中的凭据暴露有关](#item-tech-news-7) ⭐️ 7.0/10
8. [MaxxBench 质疑 DeepSWE 高分：变换任务规格后分数还成立吗](#item-tech-news-8) ⭐️ 7.0/10
9. [文章称 Mac 自 2022 年起内置未公开个人知识图谱守护进程](#item-tech-news-9) ⭐️ 7.0/10

**财经新闻**
1. [伯克希尔第三季度回购翻倍至 96 亿美元，整体利润下降 28%](#item-finance-news-1) ⭐️ 7.0/10
2. [软银与 ABB 拟分拆中国机器人业务以挽救 54 亿美元交易](#item-finance-news-2) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Asahi Linux 首次同日交付 Fedora Asahi Remix](https://asahilinux.org/2026/11/progress-report-7-3/) ⭐️ 8.0/10

Asahi Linux 的 7.3 进度报告显示，Fedora Linux 45 于 11 月 3 日发布当天，Fedora Asahi Remix 也同步交付，这是该项目首次做到与上游 Fedora 同日发布。报告同时谈到 Linux 在 Apple Silicon 上的持续开发挑战；社区评论指出，USB-C 外接显示器支持仍然缺失，成为部分用户暂不安装的原因。还有评论引述报告称，项目曾遭遇他人利用其宽松许可证试图劫持工作并商业化的行为。

hackernews · ackyshake · 11月7日 05:20 · [社区讨论](https://news.ycombinator.com/item?id=50401867)

**「背景」** Asahi Linux 是社区为 Apple Silicon Mac 逆向开发 Linux 支持的项目，Fedora Asahi Remix 则是其面向 Fedora 用户的成品发行版。项目方此前已就宽松许可证被利用发出警告，称有人试图借许可证接管项目并把 Apple Silicon 上的 Linux 商业化。

**「影响」** 对 Fedora Asahi Remix 用户来说，同日交付意味着不必等待移植版本单独追赶，就能随 Fedora 45 获得上游更新；但需要 USB-C 外接显示器的 MacBook Air 用户仍无法获得该功能，安装前应确认外设兼容性。

**「社区讨论」** 社区讨论集中在功能优先级：有用户表示，缺少 USB-C 外接显示器支持是他们迟迟不安装 Asahi Linux 的主要原因，并对项目优先支持较新 CPU 感到意外。还有评论猜测报告提到的许可证被利用一事是否指向 Omarchy，但只是提问，没有给出证据。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://asahilinux.org/2026/11/progress-report-7-3/">Progress Report: Linux 7.3 - Asahi Linux</a></li>

</ul>
</details>

**标签**: `#Asahi Linux`, `#Apple Silicon`, `#Linux kernel`, `#Fedora`, `#open source`

---

<a id="item-tech-news-2"></a>
### [SemiAnalysis 实地探访内蒙古 800MW AI 数据中心园区](https://newsletter.semianalysis.com/p/we-visited-chinas-stargate-in-inner) ⭐️ 8.0/10

SemiAnalysis 刊出 9 月对内蒙古乌兰察布 Galaxy 数据中心的实地探访：该园区由可再生能源系统集成商远景集团（Envision）拥有，规划 IT 容量最高 800MW，规模约与得州 Abilene 的 Stargate 核心园区相当，首个 120MW 阶段在一年内交付，建设成本约为美国同类项目的五分之一。园区四个阶段均为两家互联网巨头的定制建设，探访时其余部分仍在施工；据当地报道，所在的察哈尔高新区有 22 个数据中心项目、近 3 万名建筑工人同时作业。远景的垂直整合覆盖自建风电场与专用供电线路、园区对面的风机叶片工厂，以及自行设计集成的低压功率模块、800V 系统、用于平滑负载的储能和参与联合设计的预制变电站。上述数字来自该机构的现场报道，文中未披露具体成本金额与两家客户名称。

rss · Semianalysis · 11月7日 19:01

**「背景」** Stargate Abilene 是位于得克萨斯州、为 OpenAI 建设的吉瓦级园区，常被视作美国 AI 基建的标杆；内蒙古则是中国增长最快的 AI 数据中心区域。SemiAnalysis 此次探访的 Galaxy 园区位于乌兰察布，由可再生能源系统集成商远景集团拥有，后者已在全球安装超过 100GW 风机。

**「对成本基准的含义」** 对评估 AI 基建成本的开发者和投资者而言，这篇报道提供了一个可比的单点基准：在劳动力充足、且中国数据中心很少采用全模块化施工的前提下，该园区仍把造价压到美国水平的约五分之一，远景自建风电、专用线路与预制变电站的垂直整合是这一成本结构的一部分。这是单一站点的案例，报道本身未给出可用于推算全行业平均成本的数据。

**标签**: `#AI infrastructure`, `#data centers`, `#China AI`, `#datacenter economics`, `#vertical integration`

---

<a id="item-tech-news-3"></a>
### [GitHub 新 Git 存储架构 Rubicon 进入有限私有预览](https://github.blog/engineering/architecture-optimization/inside-githubs-new-git-storage-architecture/) ⭐️ 8.0/10

GitHub 公布了代号 Rubicon 的新 Git 存储架构，面向大量 AI 智能体并发操作同一仓库的场景，目前处于有限私有预览阶段，并将逐步扩大推广范围。该架构把 Git 对象存入 Azure Blob Storage，由 Ref-CAS 管理引用状态，并通过虚拟副本处理读写、后台节点压缩数据包。GitHub 称内部测试中支持 5000 个智能体同时协作、每秒处理 7200 次推送，读取延迟保持在较低水平；这些是厂商内部测试指标，尚缺独立验证和公开的正式可用时间。

telegram · zaihuapd · 11月7日 14:12

**「背景」** Git 通常把对象打包成 packfile、把引用存为独立文件，因此对同一仓库的高频并发写入容易在引用更新与压缩环节形成争用。GitHub 的 Rubicon 把对象存入 Azure Blob Storage、引用状态交给 Ref-CAS，并将写副本与后台压缩拆开处理；有报道将其概括为把 refs、packs 和 compaction 分层。

**「影响」** 目前只有有限私有预览的参与者可能用到 Rubicon，普通开发者无法申请或迁移；在 GitHub 公布更广的可用范围和兼容性细节前，不应把每秒 7200 次推送的指标视为所有仓库都可获得的能力。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.startuphub.ai/ai-news/technology/2026/github-rebuilt-git-for-7-200-pushes-a-second">GitHub rebuilt Git for 7,200 pushes a second | StartupHub.ai</a></li>
<li><a href="https://stack-archive.com/blog/github-rubicon-git-storage-architecture-agents-2026/">GitHub Rubicon: Git Storage Built for 5,000 Concurrent Agents</a></li>

</ul>
</details>

**标签**: `#GitHub`, `#Git 存储`, `#系统架构`, `#AI 智能体`, `#Azure Blob Storage`

---

<a id="item-tech-news-4"></a>
### [微软研究院 AI Frontiers 研究组据报结束，Langford 离职](https://hunch.net/?p=13764006) ⭐️ 7.0/10

据 Hacker News 帖子所链接的报道，微软研究院的 AI Frontiers 研究组被宣告结束，研究员 John Langford 同时离职。该组被描述为专注于 AI 基础性进展，而不是单纯扩展现有模型；报道使用了“declared”这一说法，但给定材料中没有微软的正式确认，也没有人员安置或项目去向的说明。

hackernews · srean · 11月7日 18:02 · [社区讨论](https://news.ycombinator.com/item?id=50406563)

**「背景」** AI Frontiers 是微软研究院内部一个由 John Langford 参与组织、试图把研究整合为连贯工作的团队；Langford 是微软研究院纽约的 partner researcher manager，研究方向为机器学习和学习理论。Langford 在博文中称，该团队曾主动尝试组织连贯的研究工作，随后他宣告团队结束并离开微软。

**「影响」** 对微软研究院内部从事探索性 AI 研究的人员来说，这一变化意味着原本独立的基础研究组不再作为组织单位存在；报道未说明成员是否转入其他团队，相关项目和合作安排因此悬而未决。

**「社区讨论」** 评论者围绕这是否反映全行业押注 transformer 规模化展开争论：一种观点认为大公司正把资源集中到这条可预测的路线，探索其他 AI 方法的空间被压缩；另一种观点强调研究与规模化应并行，担心短期确定性损害长期探索。还有评论者称，微软内部“做好研究就会有好结果”的长期默契已被现任领导层打破，并认为这会破坏研究文化。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/John_Langford_%28computer_scientist%29">John Langford (computer scientist) - Wikipedia</a></li>
<li><a href="https://businessexaminer.ca/victoria-articles/item/microsoft-researcher-john-langford-exits-as-ai-frontiers-group-is-declared/">Microsoft Researcher John Langford Exits as AI Frontiers Group ...</a></li>
<li><a href="https://hunch.net/?p=13764006">The End of AI Frontiers – Machine Learning (Theory)</a></li>

</ul>
</details>

**标签**: `#Microsoft Research`, `#AI research strategy`, `#transformer scaling`, `#industry restructuring`, `#Hacker News`

---

<a id="item-tech-news-5"></a>
### [Coldframe：伪装超市冷柜控制器的 Python 蜜罐](https://github.com/hedgerow-dev/coldframe) ⭐️ 7.0/10

安全研究者 hedgerow-dev 发布开源单文件 Python 蜜罐 Coldframe，仅用标准库模拟 Danfoss AK-SM 800A 和 Dixell XWEB 超市制冷控制器，供 OT/IoT 研究者观察针对暴露设备的攻击。作者称其依据真实设备的 Shodan 记录，复刻了响应头顺序、页面标题、证书字段和 TLS 版本。例如，Danfoss 人设按真实设备顺序发送 nginx 头；Dixell 人设不发送 Server 头，页面固定为 8,202 字节。它能识别 CVE-2025-41450（Danfoss“当日代码”登录绕过），记录提交的代码当天是否正确，也会标记针对另外三个 Danfoss CVE 和 XWEB 漏洞的尝试。默认口令可进入带除霜按钮的假后台；两个实例上线一天只见到通用扫描器和 Shodan 爬虫 refrigerator.census.shodan.io。

hackernews · hedgerow-dev · 11月7日 17:27 · [社区讨论](https://news.ycombinator.com/item?id=50406292)

**「背景」** Danfoss AK-SM 800A 的嵌入式 Web 管理界面此前已被 Claroty 的 Team82 研究出多个漏洞；Danfoss 安全公告 DSA-2025-03-01 将 CVE-2025-41450 描述为 AK-SM8xxA 系列的认证不当问题，可导致认证绕过，并建议安装 4.2 补丁。Coldframe 之所以能识别 Danfoss 的“code of the day”登录绕过，正是针对这类暴露在公网的真实控制器接口。

**「影响」** 部署者借助默认口令后的假后台，可以把观察从首轮扫描延伸到攻击者的二次操作；但人设细节取自 Shodan 样本，若不用实体控制器校准，记录的交互未必能代表现场设备。

**「社区讨论」** supriyo-biswas 质疑把 Shodan 记录当作设备保真度基准：他表示自己复刻 Wi-Fi 摄像头时发现，网上多数样本要么本身是蜜罐，要么已被入侵并篡改页面，建议先取得真实漏洞设备再探测。xrd 则追问此前大范围冷柜故障究竟是否被确认为攻击，还是可能由同时段软件更新造成；作者回应称超市通常没有安全团队，补丁、VPN 和强密码应默认由厂商或安装商提供。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://claroty.com/team82/research/freeze-the-controller-defrost-the-food-uncovering-vulnerabilities-in-danfoss-refrigeration-controllers">Freeze the Controller, Defrost the Food: Uncovering ...</a></li>
<li><a href="https://www.danfoss.com/en/service-and-support/coordinated-vulnerability-disclosure/danfoss-security-advisories/dsa-2025-03-01/">DSA-2025-03-01 | Danfoss</a></li>

</ul>
</details>

**标签**: `#honeypots`, `#industrial-control-systems`, `#IoT-security`, `#open-source`, `#Python`

---

<a id="item-tech-news-6"></a>
### [浏览器版《极品飞车：地下狂飙 2》支持在线多人](https://nfsu2.xyz/) ⭐️ 7.0/10

一个可在浏览器中在线多人游玩的《极品飞车：地下狂飙 2》版本出现在 nfsu2.xyz，依靠 WebGPU 运行，并在 Hacker News 上引发讨论。评论者称手机端也能正常游玩，Linux 上的 Chromium 则需要启用不安全的 WebGPU 功能；这些属于用户体验反馈，并非项目方公布的兼容性清单。项目的分发方式和版权状态并不明确，评论中有人称该站点不合法并预计可能被下架，也有人将其视为已停售 abandonware 的保存项目。

hackernews · fluxusars · 11月7日 09:36 · [社区讨论](https://news.ycombinator.com/item?id=50403052)

**「背景」** 这个项目通过逆向工程把老赛车游戏《极品飞车：地下狂飙 2》搬进浏览器，并加入在线多人对战；其运行前提是浏览器支持 WebGPU。社区评论指出，Linux 上的 Chromium 还需手动启用不安全的 WebGPU 特性，而原零售版在现代 PC 上往往已难以直接运行。

**「实际影响」** 对玩家而言，这款 2004 年 PC 版可在支持 WebGPU 的当前 Chrome 或 Firefox 中直接打开，无需安装器或 EA 账号；其自由漫游和 Online 菜单连接的是项目自建服务器，线上功能不依赖 EA 的官方服务。

**「社区讨论」** 有评论者认为在浏览器中复活已停售的 abandonware 很有价值，也有人质疑为受版权保护的内容接受捐赠不妥；另有用户称该站不合法、走红后可能被下架。讨论中还分享了手机端可正常运行，以及 Linux 上需启用 Chromium 不安全 WebGPU 功能的经验。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://underground2revived.com/">Underground 2 Revived: Play NFSU 2 in Browser</a></li>
<li><a href="https://portedgames.com/need-for-speed-underground-2-browser/">NFS Underground 2 Browser Game: Play NFSU 2 Online at nfsu 2 . xyz</a></li>

</ul>
</details>

**标签**: `#browser gaming`, `#WebGPU`, `#reverse engineering`, `#abandonware`, `#online multiplayer`

---

<a id="item-tech-news-7"></a>
### [Claude Code 的“不再询问”被指与 1,122 个公开文件中的凭据暴露有关](https://apiiro.com/blog/coding-agents-leaking-secrets-github-dont-ask-again) ⭐️ 7.0/10

一项安全研究称，Claude Code 的“不再询问”（Don&\#x27;t Ask Again）权限审批与 1,122 个公开 GitHub 文件中出现凭据有关。有评论者指出，单独点击该选项不会泄露密码；实际路径是用户把手动创建、包含已批准命令（这些命令里带有密钥或密码）的 .claude/settings.local.json 提交到公开仓库。Claude Code 团队的 Boris 回应称，该文件本应只保留在本地，Claude 创建时会自动将其加入 gitignore，这次涉及的文件是手动创建并检入的；团队过去未做密钥清理，正在研究防止此类暴露的措施。

hackernews · shmulc · 11月7日 20:45 · [社区讨论](https://news.ycombinator.com/item?id=50407882)

**「背景：本地设置文件为何会被提交」** 按设计，Claude Code 的“Don&\#x27;t Ask Again”会把用户批准的完整命令原样写入项目的 \`.claude/settings.local.json\`，该文件本应只留在本地、不进入版本控制。Apiiro 的扫描对象正是那些被提交到公开仓库的这类设置文件，并在其中的命令字符串里发现了密码与密钥。

**「影响」** 对使用 Claude Code 的开发者来说，具体风险是把 .claude/settings.local.json 纳入版本控制：一旦其中记录了带有明文密钥或密码的批准命令，公开仓库就会暴露这些值。应检查并移除已提交到仓库的本地设置文件，避免在该文件中保存秘密。

**「社区讨论」** 评论者批评标题误导：Aurornis 认为，单点“不再询问”本身不会暴露密码，只有提交包含密钥命令的本地设置并公开，才会造成暴露。另有开发者介绍用隔离虚拟机配合 --dangerously-skip-permissions 和受限 API 代理，或把凭据放在 1Password、通过需要指纹确认的 op CLI 调用，以限制代理权限。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://madrobot.blog/2026/11/07/claude-code-dont-ask-again-secrets-github/">Claude Code “Don’t ask again” left secrets in 1,122 GitHub files</a></li>

</ul>
</details>

**标签**: `#security`, `#secrets-management`, `#ai-coding-agents`, `#claude-code`, `#github`

---

<a id="item-tech-news-8"></a>
### [MaxxBench 质疑 DeepSWE 高分：变换任务规格后分数还成立吗](https://maxxbench.unlap.ai/research/why-maxxbench/) ⭐️ 7.0/10

MaxxBench 公布了一项针对 DeepSWE 编程基准的元评估，直接追问高分是否等于真实能力。其方法是改变任务规格并观察分数如何变化，以检验基准成绩能否泛化。现有材料没有给出具体分数、模型版本或实验规模，因此无法确认该评估覆盖了哪些模型，也无法判断其结论强度。

hackernews · antiuniverse · 11月7日 17:19 · [社区讨论](https://news.ycombinator.com/item?id=50406222)

**「背景」** DeepSWE 是评估编码智能体的长周期软件工程基准，包含 113 个原创任务，覆盖 91 个仓库和 5 种语言，并使用隔离任务环境与程序化验证器评分 \[tool-2-1\]。其官方材料称，任务提示长度约为 SWE-bench Pro 的一半，但解法所需代码量约为后者的 5.5 倍、输出 token 数约为 2 倍 \[tool-2-2\]。

**「影响」** 对使用 DeepSWE 或类似编程基准的评估者而言，单次榜单分数不足以作为能力结论；更稳妥的做法是像 MaxxBench 那样改变任务规格并报告分数波动，先确认成绩对规格变化是否敏感，再用于模型选型或训练决策。

**「社区讨论」** 评论区对原因存在分歧：kqr 认为检验泛化只需变动一个参数并观察分数变化，peri-cl 则指出图中分数下滑最明显的是较小模型，并提醒 GLM-5.3 与 GLM-5.3-flash 属于不同模型谱系，不能按同族对比。Systemerror7A69 还提到 DeepSWE 存在 bug，并把“不要使用 max 模式”视为实用结论；rao-v 则怀疑问题更多出在实验室构建的 RL 环境过于单一，导致小模型过拟合。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://benchlm.ai/benchmarks/deepswe">DeepSWE Leaderboard &amp; Scores — September 2026 | BenchLM.ai</a></li>
<li><a href="https://deepswe.datacurve.ai/">DeepSWE measures frontier coding agents on original, long-horizon...</a></li>

</ul>
</details>

**标签**: `#LLM benchmarks`, `#evaluation methodology`, `#DeepSWE`, `#AI research`, `#benchmark robustness`

---

<a id="item-tech-news-9"></a>
### [文章称 Mac 自 2022 年起内置未公开个人知识图谱守护进程](https://8rank.ai/game/apple-intelligence-personal-knowledge-graph) ⭐️ 7.0/10

一篇调查式文章声称，自 2022 年以来出货的每台 Mac 都带有一对未在文档中说明的守护进程，用于构建关于用户及其联系人的个人知识图谱，记录用户是谁、认识谁、彼此如何关联以及如何通信。该文把这些组件描述为覆盖面广且默认存在，但现有材料没有提供 Apple 的确认或独立验证，因此这仍是一项由作者调查得出的指控，而非已证实的产品说明。文章在 Hacker News 引发大量讨论，焦点集中在隐私、知情同意以及系统在用户不知情时推断人际关系的边界。

hackernews · infwhispers · 11月7日 09:46 · [社区讨论](https://news.ycombinator.com/item?id=50403097)

**「背景」** 按该研究文章的说明，负责构建个人知识图谱的这对守护进程自 2022 年、即 macOS 13 起就随系统提供，受影响的包括 Intel 与 Apple 芯片机型（tool-2-1）。这一时间点早于 Apple 以「Apple Intelligence」之名推广端侧 AI 与新一代 Siri 的阶段，后者目前的官方页面列出 iOS 27、iPadOS 27、macOS Golden Gate、watchOS 27 与 visionOS 27 等版本（tool-2-2）。需要说明的是，上述系统组件与版本范围均出自研究者本人的描述，目前尚未见到独立验证。

**「实际影响」** 对 macOS 用户而言，最直接的后果是联系人、通信对象和人际关系可能已被系统用于本地推断，却难以从公开文档中确认这些守护进程的数据范围以及是否可控。开发者和企业管理员若需评估合规风险，也只能依赖逆向分析或等待 Apple 说明，而不能把现有文档当作完整的数据流清单。

**「社区讨论」** 评论中，一位用户认为这类数据若为自愿选择或许有趣，但更担心日常交谈被默认记录所带来的社会后果；另一位则指出 Photos 已能识别人脸和宠物，并认为这类图谱可为本地 Siri 或大模型消歧提供上下文。作者本人出现在讨论中邀请提问，并链接了后续研究，但这些都未构成对原始指控的独立验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://8rank.ai/game/apple-intelligence-personal-knowledge-graph">Anatomy of Apple &#x27;s Personal Knowledge Graph — Eighth Rank</a></li>
<li><a href="https://www.apple.com/apple-intelligence/">Apple Intelligence and Siri - Apple</a></li>

</ul>
</details>

**标签**: `#apple`, `#macos`, `#privacy`, `#reverse-engineering`, `#personal-knowledge-graph`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [伯克希尔第三季度回购翻倍至 96 亿美元，整体利润下降 28%](https://www.cnbc.com/2026/11/07/berkshire-hathaway-q3-2026-earnings-buybacks.html) ⭐️ 7.0/10

伯克希尔·哈撒韦（Berkshire Hathaway）在 2026 年第三季度回购了 96 亿美元自家股票，规模超过第二季度 45 亿美元的两倍，使年内回购总额达到约 144 亿美元。同期，反映旗下全资业务盈利的营业利润同比下降 5.8%至 127.05 亿美元，纳入股票投资组合损益的整体利润则下降 28%至 221.12 亿美元。

rss · CNBC Finance · 11月7日 15:23

**「背景」** Greg Abel（格雷格·阿贝尔）自 2026 年 1 月起担任伯克希尔·哈撒韦首席执行官，此前沃伦·巴菲特于 2025 年 5 月宣布了交班计划。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://en.wikipedia.org/wiki/Greg_Abel">Greg Abel - Wikipedia</a></li>
<li><a href="https://www.fool.com/investing/2026/10/25/berkshire-hathaway-started-buying-back-its-own-stock-again-this-year-should-you-buy-it-at-a-record-high/">Berkshire Hathaway Started Buying Back Its Own... | The Motley Fool</a></li>

</ul>
</details>

**标签**: `#Berkshire Hathaway`, `#share buybacks`, `#Q3 earnings`, `#insurance underwriting`, `#cash reserves`

---

<a id="item-finance-news-2"></a>
### [软银与 ABB 拟分拆中国机器人业务以挽救 54 亿美元交易](https://www.bloomberg.com/news/articles/2026-11-07/softbank-abb-weigh-china-carve-out-to-salvage-robotics-deal) ⭐️ 7.0/10

软银与 ABB 正考虑将 ABB 机器人业务的中国部分分拆为独立实体，以挽救本周四被中国外商投资安全审查叫停的 54 亿美元收购，但知情人士称该方案可能失败。

telegram · zaihuapd · 11月7日 11:24

**「背景」** 中国的外商投资安全审查机制由发改委等牵头，可出于供应链安全等考虑叫停外资收购；据 FT 报道，软银近期被告知该 54 亿美元交易将被阻止。

**「影响」** 若分拆方案未能过关，ABB 可能需为中国机器人业务另寻买家，知情人士给出的该部分估值为 20 亿至 30 亿美元，其最终归属仍取决于中国外资安全审查结果。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.ft.com/content/f10c3e24-45e4-47ff-bde2-24a8de90aec4?syn-25a6b1a6=1">China blocks SoftBank’s $5.4bn takeover of ABB’s robotics ...</a></li>
<li><a href="https://supplychaindigital.com/news/china-blocks-softbanks-us-5-37bn-bid-for-abb-robotics">China blocks SoftBank’s US$5.37bn bid for ABB Robotics</a></li>

</ul>
</details>

**标签**: `#SoftBank`, `#ABB`, `#robotics`, `#China FDI screening`, `#cross-border M&amp;A`

---