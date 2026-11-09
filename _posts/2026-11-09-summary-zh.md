---
layout: default
title: "Horizon Summary: 2026-11-09 (ZH)"
date: 2026-11-09
lang: zh
---

> 从 24 条内容中筛选出 3 条重要资讯。

---

**科技新闻**
1. [KetchUp：用 Rust 和 WebGPU 构建的开源 SketchUp 替代品](#item-tech-news-1) ⭐️ 7.0/10
2. [Outlook.com 被指拒收未配置 DMARC 域名的邮件](#item-tech-news-2) ⭐️ 7.0/10
3. [高盛据报撤下银行家和交易员的 Claude Code](#item-tech-news-3) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [KetchUp：用 Rust 和 WebGPU 构建的开源 SketchUp 替代品](https://ketchup3d.github.io/app/) ⭐️ 7.0/10

KetchUp 是一个开源、基于 Rust 和 WebGPU 的浏览器端 3D 建模工具，定位为 SketchUp 的替代品，发布后在 Hacker News 上获得积极反馈。当前页面只提供应用入口，未公布版本号、许可证、文件格式兼容性或平台支持范围，因此它能在多大程度上替代 SketchUp 尚无法核实。社区用户报告其在浏览器中运行流畅，Rust 编写的界面与文字渲染表现良好。

hackernews · dcoulmbe · 11月8日 22:35 · [社区讨论](https://news.ycombinator.com/item?id=50418176)

**「背景」** SketchUp 现由 Trimble 运营，并提供基于浏览器、可免费使用的 SketchUp Free 版本，用户无需安装即可在线建模。开源的同类替代品此前也已出现，例如有视频将 IngeTrazo 介绍为面向 Linux、macOS 和 Windows 的开源 SketchUp 替代方案。KetchUp 的区别在于以 Rust 与 WebGPU 直接在浏览器中实现，不过本次提交未提供功能清单或与 SketchUp 文件格式的兼容性说明。

**「影响」** 对只需要绘制盒子或电子外壳等简单形状的 3D 打印爱好者而言，这类无需安装、直接在浏览器中运行的建模器降低了试用门槛。不过一位用户反馈，每次绘制矩形都会弹出对象命名提示，说明默认交互流程仍需调整。

**「社区讨论」** 评论整体正面：有人称其为 SketchUp 的“精神续作”，对 SketchUp 长期易主且免费程度下降表示遗憾；也有人对 Rust 界面在浏览器中的手感与文字渲染质量感到意外，并推测 Rust 可能成为跨平台 Web 与移动应用的方向。另有评论提出，与其花时间学习现有软件，不如借助 AI 编程工具按需搭建自己的建模器；这属于个人观点，并非对 KetchUp 本身的评价。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.youtube.com/watch?v=wvdVn_KX8Rs">How to Design a Kitchen in IngeTrazo ( SketchUp Alternative )</a></li>
<li><a href="https://sketchup.trimble.com/en/plans-and-pricing/sketchup-free">Free 3 D Modeling Software | 3 D Design Online | SketchUp ... | Trimble</a></li>

</ul>
</details>

**标签**: `#Rust`, `#WebGPU`, `#open-source 3D modeling`, `#SketchUp alternative`, `#browser graphics`

---

<a id="item-tech-news-2"></a>
### [Outlook.com 被指拒收未配置 DMARC 域名的邮件](https://mailroute.net/blog/outlook-rejecting-email-without-dmarc) ⭐️ 7.0/10

据 Mailroute 博客报道，Outlook.com 被指正在拒收未配置 DMARC 记录的域名所发邮件，影响向 Outlook.com 收件人发信的域名所有者和邮件管理员。报道没有给出微软的实施时间、覆盖范围、具体错误码或官方政策说明，因此这仍是一项待确认的运营变化。

hackernews · xmddmx · 11月8日 19:20 · [社区讨论](https://news.ycombinator.com/item?id=50416158)

**「背景」** DMARC 是域名所有者在 DNS 中发布的一条 TXT 策略记录，它建立在 SPF 与 DKIM 之上；只有当 SPF 或 DKIM 与邮件的 From 域对齐时，这条记录才对收件方产生实际意义。长期以来，缺少 DMARC 记录只影响邮件的信誉评分，并不构成直接的拒收理由；据 MailRoute 的 Thomas A. Johnson 与后续报道，微软的消费者邮箱服务从 2026 年 11 月 5 日起开始将“无 DMARC 记录”本身作为退信依据，小型发件人也不例外。补齐方式就是在发件域上添加一条 DNS TXT 记录。

**「影响」** 如果该拒收策略持续，未发布 DMARC 记录的域名在向 Outlook.com 用户发信时会面临退信，发送方需要先检查 DNS 中的 DMARC 记录并处理退信反馈，再排查 SPF、DKIM 或内容过滤等其他问题。

**「社区讨论」** 有评论者反驳“静默”说法，称 Outlook.com 返回的是 5xx 永久投递失败；另一名自建邮件服务器的管理员则报告，即使 SPF、DKIM 和 DMARC 都配置正确，邮件也会在日志显示已接收后未进入收件箱，而且其 VPS 段落在非公开黑名单中被整体封锁、常规流程无法解除。另有评论认为，域名发布 DMARC 早应成为基本要求，迟到的发送方不值得同情。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://mailroute.net/blog/outlook-rejecting-email-without-dmarc">Outlook.com Is Quietly Rejecting Email From Domains Without DMARC</a></li>
<li><a href="https://tosend.com/articles/outlook-rejects-email-without-dmarc/">Outlook.com now rejects email from domains without DMARC</a></li>
<li><a href="https://news.lavx.hu/article/outlook-com-rejects-some-email-from-domains-without-dmarc-records">Outlook.com Rejects Some Email From Domains Without DMARC ...</a></li>

</ul>
</details>

**标签**: `#DMARC`, `#email deliverability`, `#Microsoft Outlook`, `#email infrastructure`, `#spam filtering`

---

<a id="item-tech-news-3"></a>
### [高盛据报撤下银行家和交易员的 Claude Code](https://www.thestateofai.com/news/goldman-sachs-claude-code-traders-bankers) ⭐️ 7.0/10

据 The State of AI 报道，高盛正在撤下银行家和交易员使用的 Claude Code，不再让这些前台业务人员通过该编程智能体处理工作。报道将原因指向安全风险、合规约束和按量计费压力，但现有材料没有高盛或 Anthropic 的正式确认，也没有给出撤下时间表或替代工具细节。

hackernews · TheWiggles · 11月8日 18:16 · [社区讨论](https://news.ycombinator.com/item?id=50415628)

**「背景」** 据 The State of AI 报道，高盛早在今年 4 月就已禁止其香港投行人员使用 Claude，如今这一限制扩大到该行多数交易员和银行家，他们无法在工作中使用 AI 编码工具。同一篇报道还指出，高盛目前是 Anthropic IPO 的联席主承销商之一，这使得该行对 Anthropic 产品的使用限制更受关注。

**「影响」** 对受影响的银行家和交易员而言，直接后果是失去现有的 Claude Code 辅助，需要改用机构批准的其他工具或内部流程；报道没有说明高盛是否已提供替代方案。

**「社区讨论」** 评论者把焦点放在部署边界而非模型本身：有人主张，让半无人值守的编码智能体运行在可访问客户、交易、邮件和内部网络的金融前台工作站上，会同时暴露敏感数据、不可信内容和外联能力，风险不可接受。也有评论报告所在机构因按量计费超支而收回 Claude 权限，并称 Anthropic 无法提供固定费率、Gemini 的固定计费和限流超额处理更有吸引力；另有评论强调银行对权限、审计和数据许可的要求，以及用 AI 处理监管记录出错可能带来的合规后果。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.thestateofai.com/news/goldman-sachs-claude-code-traders-bankers">Goldman Sachs Is Pulling Claude Code From Its Bankers and...</a></li>

</ul>
</details>

**标签**: `#AI coding agents`, `#enterprise security`, `#financial services`, `#AI governance`, `#Claude Code`

---