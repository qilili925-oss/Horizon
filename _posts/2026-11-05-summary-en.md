---
layout: default
title: "Horizon Summary: 2026-11-05 (EN)"
date: 2026-11-05
lang: en
---

> From 36 items, 10 important content pieces were selected

---

**Technology News**
1. [Alpine Linux advisory: OpenSSH password bypass on musl systems](#item-tech-news-1) ⭐️ 8.0/10
2. [OpenAI&\#x27;s cybersecurity team reports removing about a thousand privilege-escalation paths](#item-tech-news-2) ⭐️ 8.0/10
3. [USTC&\#x27;s structRFM RNA foundation model published in Nature](#item-tech-news-3) ⭐️ 8.0/10
4. [DialFork benchmark targets procedural hallucination in conversational agents](#item-tech-news-4) ⭐️ 7.0/10
5. [600,000 Nvidia H200 chips reportedly wait in Hong Kong for China import approval](#item-tech-news-5) ⭐️ 7.0/10

**Financial News**
1. [China blocks SoftBank&\#x27;s $5.4 billion purchase of ABB robotics unit](#item-finance-news-1) ⭐️ 8.0/10
2. [Chip selloff deepens, Nasdaq 100 falls 5%](#item-finance-news-2) ⭐️ 8.0/10
3. [Treasury yields and oil fall after Democrats win both chambers of Congress](#item-finance-news-3) ⭐️ 7.0/10
4. [Micron Pauses $4.5 Billion Taoyuan Plant Construction Amid Labor Dispute](#item-finance-news-4) ⭐️ 7.0/10
5. [Nintendo Switch 2 quarterly sales fall 41%, earnings miss estimates](#item-finance-news-5) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Alpine Linux advisory: OpenSSH password bypass on musl systems](https://alpinelinux.org/posts/2026-11-05-openssh-password-authentication-bypass/) ⭐️ 8.0/10

Alpine Linux has published a security advisory for an OpenSSH-server password-authentication bypass affecting musl-based builds. Community analysis traces the flaw to musl&\#x27;s crypt\(\) returning &quot;\*&quot; when the supplied key exceeds 256 bytes; because &quot;\*&quot; is also the stored marker for accounts without passwords, sshd&\#x27;s crypt comparison can treat a long password as a match. The reported preconditions are an sshd linked against musl, no PAM, password authentication enabled, and an account whose password hash is &quot;\*&quot;.

hackernews · pantalaimon · Nov 5, 14:44 · [Discussion](https://news.ycombinator.com/item?id=50379704)

**「Background」** Alpine Linux uses musl libc and ships an OpenSSH server built without PAM, so sshd checks shadow password entries through musl&\#x27;s crypt\(\) rather than a PAM stack. In /etc/shadow, an asterisk \(\*\) is the conventional placeholder for an account that has no usable password and should not permit password login.

**「Impact」** For hosts matching those conditions, an account that is supposed to reject password logins can instead accept a long password over SSH. Operators should check whether their sshd uses musl without PAM and whether password authentication is enabled; the reported bypass path does not apply to PAM-backed configurations described in the discussion.

**「Community discussion」** Commenters focused on the root cause: NewJazz and BoppreH criticized musl&\#x27;s use of &quot;\*&quot; as both crypt\(\)&\#x27;s error return and the passwordless-account marker, calling it risky in-band signaling, while tonnydourado argued the advisory&\#x27;s headline overstates exposure because several conditions must coincide. mpyne outlined the sshd crypt\(\) comparison that lets the collision succeed.

<details><summary>References</summary>
<ul>
<li><a href="https://alpinelinux.org/posts/2026-11-05-openssh-password-authentication-bypass/">Security advisory: openssh-server password authentication ...</a></li>
<li><a href="https://hadrian.io/vulnerability-alerts/openssh-on-musl-accepts-any-long-password-for-locked-accounts">OpenSSH on musl accepts any long password for locked accounts</a></li>

</ul>
</details>

**Tags**: `#security advisory`, `#OpenSSH`, `#Alpine Linux`, `#musl`, `#authentication bypass`

---

<a id="item-tech-news-2"></a>
### [OpenAI&\#x27;s cybersecurity team reports removing about a thousand privilege-escalation paths](https://openai.com/index/a-thousand-fewer-paths-to-root/) ⭐️ 8.0/10

OpenAI&\#x27;s cybersecurity team says it reduced roughly a thousand privilege-escalation paths, according to an OpenAI post. The available description does not identify the affected software, the vulnerability classes involved, or the method used to remove the paths, so the result remains a vendor claim that cannot be independently assessed from the supplied material.

hackernews · dangelosaurus · Nov 4, 23:33 · [Discussion](https://news.ycombinator.com/item?id=50372929)

**「Background」** Local privilege escalation is the class of Linux kernel bug that lets an unprivileged process, or code running inside a container, obtain root on the same host, so a single flaw can turn limited access into full control of the machine. Because the kernel exposes a very large surface of drivers, filesystems, and networking code to unprivileged callers, finding these paths has traditionally depended on manual auditing and fuzzing rather than exhaustive automated search.

**「Community discussion」** Commenters asked for the distribution of the vulnerabilities across subsystems, the median age of the vulnerable code, and the bug types involved before judging whether the approach would generalize to other codebases. Others questioned whether a thousand paths point to a kernel design or language-level problem, or instead reflect many variants of a smaller number of underlying vulnerabilities.

<details><summary>References</summary>
<ul>
<li><a href="https://openai.com/index/a-thousand-fewer-paths-to-root/">A thousand fewer paths to root | OpenAI</a></li>

</ul>
</details>

**Tags**: `#security`, `#vulnerability-research`, `#privilege-escalation`, `#openai`, `#kernel-security`

---

<a id="item-tech-news-3"></a>
### [USTC&\#x27;s structRFM RNA foundation model published in Nature](https://news.ustc.edu.cn/info/1048/96798.htm) ⭐️ 8.0/10

A University of Science and Technology of China \(USTC\) team has published structRFM, a structure-guided RNA foundation model, with the paper appearing online in Nature on November 5. The model incorporates base-pairing information from secondary structure into sequence pretraining and was trained on roughly 21 million sequence–structure paired records, with the team reporting frontier-level performance across multiple tasks. The team also developed MUSES, which combines several secondary-structure predictions to reduce bias, and a 3D structure prediction module called Zfold that it reports as comparable to AlphaFold 3. The data, weights, and code have all been released openly; the performance and AlphaFold 3 comparison are the authors&\#x27; reported results and have not been independently assessed here.

telegram · zaihuapd · Nov 5, 04:49

**「Background」** RNA function depends on how a sequence folds, and secondary-structure base pairing is an intermediate constraint on that folding. StructRFM&\#x27;s approach is to inject this pairing information into sequence pretraining, rather than treating RNA as sequence alone.

**「Impact」** Researchers working on RNA structure can access the released data, weights, and code, including the Zfold module, for their own prediction and fine-tuning work. Because the AlphaFold 3 comparison comes from the authors rather than an independent benchmark, groups planning to adopt Zfold should validate it on their own RNA targets before relying on it.

**Tags**: `#RNA foundation models`, `#structural biology`, `#AI for science`, `#open source`, `#Nature`

---

<a id="item-tech-news-4"></a>
### [DialFork benchmark targets procedural hallucination in conversational agents](https://www.reddit.com/r/MachineLearning/comments/1xofjrn/dialfork_a_benchmark_for_procedural_hallucination/) ⭐️ 7.0/10

An author at Idiap Research Institute, in joint work with Logitech, announced DialFork, a benchmark for “procedural hallucination” in conversational LLM agents—cases where replies are fluent and tool calls are correct but the agent skips or reorders required dialogue steps. The authors say it is the first benchmark for this axis; it covers 24 tasks across 12 domains and expands them into more than 36,000 dialogues with known drift starting points, checked by 30 human annotators and an LLM judge calibrated on their judgments. DialFork defines three tasks—finding the drift turn, measuring procedural distance between a dialogue and its drifted versions, and comparing sets of dialogues—and releases a Hugging Face leaderboard, code, dataset, and paper. The post reports initial results on all three tasks but no headline scores.

reddit · r/MachineLearning · /u/sergbur · Nov 5, 10:44

**「Why procedural hallucination is a separate evaluation axis」** Evaluations of conversational agents typically focus on factual accuracy and correct tool use, but a dialogue can satisfy both while skipping required conversational steps such as asking, confirming, or reporting a result. The DialFork paper defines this as a distinct phenomenon and decomposes it into four complementary types grounded in workflow structure, which is the gap the benchmark targets.

**「Impact」** Agent developers now have a public benchmark for testing whether a conversational agent follows a required procedure, rather than only whether its answers are factual or its tool calls are correct; the leaderboard accepts a CSV file of predictions for each task.

<details><summary>References</summary>
<ul>
<li><a href="https://arxiv.org/html/2610.21561v5">DialFork: Going Beyond Factuality to Evaluate Procedural ...</a></li>

</ul>
</details>

**Tags**: `#LLM agents`, `#benchmark`, `#hallucination`, `#dialogue systems`, `#evaluation`

---

<a id="item-tech-news-5"></a>
### [600,000 Nvidia H200 chips reportedly wait in Hong Kong for China import approval](https://www.reuters.com/world/china/nvidia-chips-pile-up-hong-kong-china-withholds-import-approval-2026-11-05/) ⭐️ 7.0/10

Reuters, citing people familiar with the matter, reported that about 600,000 Nvidia H200 chips were stuck in Hong Kong awaiting Chinese import approval. A small number of Chinese internet companies had each received about 10,000 chips in recent months, with additional small volumes entering through brokers and indirect channels. H200 is not Nvidia&\#x27;s newest model, but late-October quotes for eight-GPU H200 servers in mainland China exceeded 6 million yuan, roughly three times the price a year earlier.

telegram · zaihuapd · Nov 5, 14:42

**「Background」** NVIDIA&\#x27;s H200 is not the company&\#x27;s newest data-center GPU, but it still outperforms domestic Chinese alternatives, so Chinese buyers continue to compete for limited allocations. Reuters reports that only small batches have reached a few Chinese internet companies, while larger volumes remain stuck in Hong Kong awaiting Beijing&\#x27;s import approval.

**「Impact」** For Chinese AI companies, allocations of roughly 10,000 chips per recipient are small relative to the reported 600,000-chip backlog, so expanding H200 capacity depends on Beijing&\#x27;s import approval; meanwhile, eight-GPU servers quoted above 6 million yuan raise deployment costs.

**Tags**: `#NVIDIA H200`, `#export controls`, `#AI hardware`, `#China`, `#supply chain`

---

## Financial News

<a id="item-finance-news-1"></a>
### [China blocks SoftBank&\#x27;s $5.4 billion purchase of ABB robotics unit](https://www.bloomberg.com/news/articles/2026-11-05/china-blocks-softbank-s-acquisition-of-abb-industrial-robot-unit) ⭐️ 8.0/10

China&\#x27;s foreign investment security review has blocked SoftBank&\#x27;s roughly $5.4 billion acquisition of ABB&\#x27;s industrial robotics business, ABB confirmed on Nov. 5, saying regulators notified it that the deal may not be implemented in China. The review body cited concerns that industrial data, supply chains and core technology from the unit could move abroad and be used to train artificial intelligence models, according to the report.

telegram · zaihuapd · Nov 5, 10:44

**「Background」** SoftBank signed a definitive agreement on Oct. 8, 2025, to buy ABB’s robotics business for $5.375 billion, and China—which accounts for about 30% of that business—uses a foreign-investment security review to screen deals for national-security risks.

**「Impact」** The block directly prevents SoftBank from folding ABB&\#x27;s robotics business into its physical-AI expansion and leaves ABB&\#x27;s robotics unit—about 30% of whose business is in China—without the proposed ownership change.

<details><summary>References</summary>
<ul>
<li><a href="https://group.softbank/media/Project/sbg/sbg/news/press/2025/20251008/pdf/20251008_en.pdf">Acquisition of ABB Ltd&#x27;s Robotics Business</a></li>
<li><a href="https://economictimes.indiatimes.com/news/international/business/china-blocks-softbanks-5-4-billion-takeover-of-abbs-robotics-division-report/articleshow/135557099.cms">China blocks SoftBank&#x27;s $5.4 billion takeover of ABB&#x27;s ...</a></li>
<li><a href="https://tradersunion.com/news/companies/show/4103824-softbank-abb-robotics-china-block/">SoftBank takeover of ABB robotics unit blocked in China</a></li>

</ul>
</details>

**Tags**: `#China regulatory review`, `#SoftBank`, `#ABB robotics`, `#cross-border M&amp;A`, `#strategic technology`

---

<a id="item-finance-news-2"></a>
### [Chip selloff deepens, Nasdaq 100 falls 5%](https://www.bloomberg.com/news/articles/2026-11-04/stock-market-today-dow-s-p-live-updates) ⭐️ 8.0/10

On Nov. 4, a deepening selloff in chip stocks drove the Nasdaq 100 down 5%, while the Philadelphia Semiconductor Index stood 36% below its June peak.

telegram · zaihuapd · Nov 5, 15:39

**「Background」** The report said investors were weighing whether a Democratic sweep of Congress could lead to tighter regulation affecting AI-related stocks.

**「Impact」** The selloff pushed investors toward defensive sectors such as consumer staples and healthcare, and toward Treasuries, the yen and the Swiss franc, while bitcoin fell 5%.

**Tags**: `#semiconductor stocks`, `#Nasdaq 100`, `#market selloff`, `#AI regulation`, `#defensive rotation`

---

<a id="item-finance-news-3"></a>
### [Treasury yields and oil fall after Democrats win both chambers of Congress](https://www.cnbc.com/2026/11/03/treasury-yields-fall-as-democrats-win-big-in-us-midterm-elections.html) ⭐️ 7.0/10

The 10-year U.S. Treasury yield fell more than 6 basis points to 4.884% on Wednesday after Democrats won majorities in both the House and Senate, while U.S. West Texas Intermediate crude futures dropped 8.29% to close at $88.12 a barrel. JPMorgan traders said Wall Street was focused on &quot;reduced deficit spending&quot; as a result of the midterm outcome, according to CNBC.

rss · CNBC Finance · Nov 4, 21:18

**「Background」** The midterms were held on Nov. 3, 2026, and Democrats won majorities in both chambers of Congress, making it harder for the Trump administration to push its spending legislation through Congress.

**「Who is exposed」** JPMorgan traders said the deficit restraint investors are watching would likely come through Congress asserting power over the budget and &quot;wading through a government shutdown,&quot; a path that would directly disrupt federal agencies and the workers and contractors they pay.

<details><summary>References</summary>
<ul>
<li><a href="https://www.everythingpolicy.org/policy-briefs/the-2026-midterms">2026 Midterm Election Results: What Divided Government Means</a></li>

</ul>
</details>

**Tags**: `#US Treasuries`, `#midterm elections`, `#fiscal policy`, `#oil prices`, `#bond yields`

---

<a id="item-finance-news-4"></a>
### [Micron Pauses $4.5 Billion Taoyuan Plant Construction Amid Labor Dispute](https://www.bloomberg.com/news/articles/2026-11-05/micron-pauses-work-on-4-5-billion-taiwan-plant-after-labor-spat) ⭐️ 7.0/10

Micron has paused construction of its $4.5 billion memory-chip plant in Taoyuan, Taiwan, after executives grew concerned that an agreement with a local union could be overturned, according to people familiar with the matter; the plant had been scheduled to begin production in 2028. Micron said Taiwan remains important to its global operations and that existing operations are normal, while Taiwan accounts for about 60% of its DRAM output, the source said.

telegram · zaihuapd · Nov 5, 11:26

**「Background」** Micron has invested close to $50 billion in Taiwan over three decades, and the Taoyuan plant was planned to make high-bandwidth memory and DRAM, with production originally scheduled to start in 2028. The dispute centers on the Taoyuan union’s demand that 15% of operating profit be shared with global employees and its effort to overturn an agreement reached with the Taichung union.

**「Impact」** A prolonged halt would mainly affect the Taoyuan site&\#x27;s construction contractors and equipment suppliers, which Micron has already notified, and could delay the plant&\#x27;s planned 2028 production start—a future addition to the Taiwan base that accounts for about 60% of Micron&\#x27;s DRAM output.

<details><summary>References</summary>
<ul>
<li><a href="https://www.bloomberg.com/news/articles/2026-11-05/micron-pauses-work-on-4-5-billion-taiwan-plant-after-labor-spat">Micron Pauses Work on $4.5 Billion Taiwan Plant After Labor ...</a></li>
<li><a href="https://www.gate.com/news/detail/MU/micron-halts-taoyuan-fab-construction-amid-45b-investment-dispute-25431413">Micron Halts Taoyuan Fab Construction Amid $4.5B Investment ...</a></li>

</ul>
</details>

**Tags**: `#Micron`, `#Taiwan`, `#semiconductor manufacturing`, `#labor dispute`, `#capital investment`

---

<a id="item-finance-news-5"></a>
### [Nintendo Switch 2 quarterly sales fall 41%, earnings miss estimates](https://mp.weixin.qq.com/s/XTw5DXy2CvqFSs4WYx73Xg) ⭐️ 7.0/10

Nintendo said Switch 2 unit sales fell 41% year over year to 2.67 million in its second fiscal quarter ended Sept. 30, with revenue and net profit both below market estimates.

telegram · zaihuapd · Nov 5, 14:12

**「Background」** The company kept its target of 16.5 million Switch 2 units for the fiscal year ending March 2027, even though quarterly sales also fell from 3.82 million in the prior quarter and higher memory-chip costs led Nintendo to raise prices in several regions.

**Tags**: `#Nintendo`, `#Switch 2`, `#earnings`, `#console sales`, `#memory chip costs`

---