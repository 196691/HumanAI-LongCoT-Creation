# HumanAI-LongCoT-Creation

## Chinese Human-AI Collaborative Long-Horizon Creation Trajectories, Governance Scripts, and Experimental Archives
## 中文人机协同长程创作全轨迹数据、治理脚本与实验档案

**Real human-in-the-loop feedback · Single-session long-horizon creation · Turn-level process preservation · Reproducible governance scripts and samples**

> **真实人类在环｜单窗口长程创作｜逐轮过程保留｜可复现治理脚本与样例**

This repository releases three Chinese human-AI collaborative creation trajectories, together with public materials concerning full-dataset governance, training experiments, and evidence recalculation. The research focus is not only the final draft, but also how inspiration, trial and error, human correction, and repeated revision develop into that draft.

> 本仓库开放3份中文人机协同创作全过程样例，以及与全量数据治理、训练实验和证据复算相关的公开材料。研究对象不只是最终定稿，而是“定稿怎样从灵感、试错、纠偏和反复修改中形成”。

The original datasets, experimental records, evaluation reports, and governance documents are preserved in Chinese. This bilingual README provides an international overview without rewriting the underlying records.

> 原始数据、实验记录、评审报告和治理文件均保留中文原貌。本中英对照说明用于国际展示与中文核对，不改写底层原始材料。

### Project access｜项目入口

- [ModelScope — Chinese documentation, dataset preview, and public downloads｜魔搭社区：中文介绍、数据预览与开放材料下载](https://modelscope.cn/datasets/abc1966916677/HumanAI-LongCoT-Creation)
- [Zenodo international archive — DOI: 10.5281/zenodo.21968765｜Zenodo国际存档](https://doi.org/10.5281/zenodo.21968765)
- GitHub — code, documentation, version history, and collaborative discussion｜GitHub：代码、文档、版本管理与协作讨论

---

## 01｜Overview｜项目简介

A large proportion of conventional training corpora consists of conclusions or finalized outputs, such as papers, books, news articles, proposals, and question-answer pairs. This project investigates another type of material: before a final draft is produced, how does a human identify problems, reject directions, correct judgments, and guide the AI through subsequent iterations?

> 传统训练语料大量以论文、书籍、新闻、方案和问答结果等**结论或定稿形态**存在。本项目关注另一类材料：在形成定稿以前，人类如何提出问题、发现偏差、否定方向、修正判断，AI又如何回应并继续推演。

We use **full-trajectory data** to describe data that preserves the formation process while using the final draft as an anchor. It does not mean retaining drafts without conclusions, nor does it mean treating every chat record as high-quality training data. The aim is to preserve, as far as possible:

> 我们将这种以最终定稿为锚点、同时保留形成过程的数据称为**全轨迹数据**。它不是“只有草稿、没有结论”，也不是把所有聊天记录直接当作高质量训练数据，而是尽量保存：

**Human input → AI-visible reasoning trace (`thinking`) → AI formal response → Subsequent human feedback → Final draft**

**人类输入 → AI可视化推理链（thinking）→ AI正式回答 → 后续人类反馈 → 最终定稿**

The three public samples come from a thinking methodology, an urban-planning thought experiment, and a product concept. Each work-related creation process was completed within a single continuous chat session. Human inputs, AI-visible reasoning traces, and formal responses are preserved turn by turn. Missing responses or reasoning traces in the original exports are explicitly marked rather than rewritten.

> 本仓库开放的3份样例分别来自一部方法论、一份未来城市规划思想实验和一个产品构想。每份作品均在单一连续会话窗口内完成作品相关创作，逐轮保留人类输入、AI可视化推理链与正式回答；原始导出中的缺答、缺链不补写，而是显式标记。

### Public sample summary｜开放样例概况

| Sample｜样例 | Topic｜主题 | Rounds｜轮次 | Messages｜消息数 | Process text｜过程文本规模 |
|---|---|---:|---:|---:|
| W1《循环登高思维》 | Thinking-methodology development<br>思维方法论构建 | 59 | 118 | Approx. 154k Chinese characters<br>约15.4万字 |
| W2《超级都市圈》 | Urban-planning thought experiment<br>城市规划思想实验 | 47 | 94 | Approx. 104k Chinese characters<br>约10.4万字 |
| W3《个人智能创作舱》 | Product-concept development<br>产品构想设计 | 34 | 68 | Approx. 87k Chinese characters<br>约8.7万字 |
| **Total｜合计** | **Three representative creation trajectories｜3份代表性创作全过程** | **140** | **280** | **Approx. 344k Chinese characters｜约34.4万字** |

These three samples were selected from the creation archives of 30 works to demonstrate the data structure and long-horizon creation process.

> 这3份样例从项目30份作品的创作档案中选取，用于展示数据形态、字段结构和长程创作过程。

---

## 02｜Research Questions｜这种数据形态研究什么

A point-and-line metaphor may help clarify the distinction:

> 可以用“点”与“线”帮助理解：

- **Conclusion data as points:** the final paper, proposal, story, or answer is preserved.<br>**结论数据像点**：保存最终论文、方案、小说或回答。
- **Full-trajectory data as lines:** the final draft is preserved together with the inspiration, trial and error, rejection, revision, and directional changes through which it emerged.<br>**全轨迹数据像线**：在保留定稿的同时，记录灵感、试错、否定、修改和方向转折怎样逐步形成结论。

The project investigates four questions:

> 本项目重点研究四个问题：

1. **Data form:** what information is retained in finalized drafts, refined processes, and native full processes?<br>**数据形态**：定稿、精炼过程和原生全过程分别包含什么信息。
2. **Training value:** how do these forms perform under CPT, outcome-oriented SFT (结果SFT), and process-oriented SFT (过程SFT)?<br>**训练价值**：不同形态在CPT、结果SFT和过程SFT中表现如何。
3. **Governance:** how should session attribution, classification, statistics, splitting, missing-data flags, archiving, and integrity checks be performed?<br>**治理方式**：怎样进行窗口归属、分类、统计、切割、缺失标记、归档与校验。
4. **Creation evidence:** how can turn-level records, trusted timestamps, and registration materials help document the formation of a work?<br>**创作证据链**：怎样利用逐轮记录、时间存证和登记材料辅助说明作品的形成过程。

The project does not assume that all redundancy is valuable, nor that native processes must always outperform refined processes. Which elements constitute useful process signals and which are irrelevant noise must be evaluated through route-specific experiments and broader practical use.

> 本研究不预设“所有冗余都有价值”，也不主张“原生必然优于精炼”。哪些内容是有效过程信号，哪些属于无关噪声，需要通过分路线实验和更多实际应用共同判断。

---

## 03｜Released Materials｜仓库开放内容

### 3.1 Native full-process samples｜原生全过程数据样例

| File｜文件 | Contents｜内容 |
|---|---|
| `W1_循环登高思维_59轮.jsonl` | 59 rounds and 118 messages covering the methodology's development.<br>59轮、118条消息，逐轮保存方法论构建过程。 |
| `W2_超级都市圈_47轮.jsonl` | 47 rounds and 94 messages covering the continuous urban-planning thought experiment.<br>47轮、94条消息，保存城市规划思想实验的连续推演。 |
| `W3_个人智能创作舱_34轮.jsonl` | 34 rounds and 68 messages covering the product concept's proposal, correction, and refinement.<br>34轮、68条消息，保存产品构想的提出、纠偏与完善。 |

### 3.2 Governance specification, implementation records, and scripts｜数据治理规范、流程档案与脚本

| File or material｜文件或材料 | Contents｜内容 |
|---|---|
| `人机协同过程数据治理规范（草案）V1.1.pdf` | Draft principles for governance, session attribution, W/M/G classification, naming, splitting, statistics, archiving, validation, and version control.<br>治理原则、窗口归属、W／M／G分类、命名、切割、统计、归档、校验与版本管理。 |
| `过程数据治理工程实施档案_477窗.pdf` | Scope, definitions, workflow, outputs, quality control, and evidence boundaries of the 477-session governance project.<br>全量477窗治理工程的范围、口径、流程、产物、质量控制与证据边界。 |
| `过程数据治理脚本与样例包_V1.1.zip` | Three specification formats, B1–B5 general scripts, a synthetic minimal sample, and the real governance sample based on《微尘纪元》.<br>规范三格式文件、B1—B5通用脚本、合成最小样例与《微尘纪元》真实治理样例。 |

The governance package contains:

> 治理脚本与样例包包括：

- `01_规范文件` — specification V1.1 in Markdown, DOCX, and PDF.<br>规范V1.1的Markdown、DOCX和PDF版本。
- `02_附录脚本_通用版` — B1 turn segmentation and statistics; B2 dual-decision comparison and disagreement classification; B3 normalized session renaming; B4 split-conservation validation; and B5 archive-integrity validation.<br>B1轮次化与逐轮统计、B2双判比对与分歧分类、B3窗口规范化改名、B4切割守恒校验、B5归档完整性校验。
- `03_最小样例包` — a 12-session synthetic fixture with preconfigured scripts.<br>12窗合成夹具及已填参数脚本。
- `04_真实样例包_微尘纪元` — original records, final draft, attribution table, turn statistics, validation records, MD5 manifest, and N+2 archive package for three real DeepSeek sessions.<br>3个真实DeepSeek窗口的原始记录、定稿、判定总表、逐轮统计、校验记录、MD5清单与N+2归档过程包。

### 3.3 Experiment reports and original archives｜实验报告与原始档案

| File｜文件 | Contents｜内容 |
|---|---|
| `V1V2对照过程数据训练价值验证实验综合报告.pdf` | Combined report on early controlled training, V1/V2 blind evaluations, and external-model anchor evaluations.<br>前期对照训练、V1／V2盲评及外部模型锚点实验综合报告。 |
| `8·23等量对照及拓展实验报告.pdf` | Nine-group matched-scale design, five-model evaluation, score recalculation, and conclusion boundaries.<br>九组等量对照设计、五家裁判评审、评分复算与结论边界。 |
| `V1V2对照实验原始档案包.zip` | Early training configurations, evaluation questions, answers from each group, original judge reviews, and recalculation worksheets.<br>前期实验训练配置、评测题、各组答卷、裁判原始评审与复算底稿。 |
| `8·23等量对照及拓展实验原始档案包.zip` | Training configurations and logs, 13 evaluation questions, nine groups of anonymized answers, original reviews from five judges, and recalculation materials for 2,925 score points.<br>训练配置与日志、13道题库、九组盲测答卷、五家裁判原始评审及2,925个评分点复算材料。 |

Original reviews are preserved as written, and the project team did not participate in scoring. Arithmetic recalculation checks the original scores rather than replacing the original reviews with new opinions.

> 原始评审保持原貌，项目团队不参与评分。算术复算用于核对原始评分，不以新增意见替代原始评审。

---

## 04｜Data Fields and Source-State Preservation｜数据字段与原始状态

Each line is a JSON object. A dialogue round normally consists of one `user` message and one `assistant` message sharing the same `round` number.

> 每行一个JSON对象。一轮对话通常由一条`user`消息和一条`assistant`消息组成，二者共用`round`编号。

| Field｜字段 | Type｜类型 | Description｜说明 |
|---|---|---|
| `id` | int | Message index.<br>消息序号。 |
| `work`／`work_id` | string | Work title／work identifier.<br>作品名／作品编号。 |
| `round` | int | Dialogue round.<br>对话轮次。 |
| `speaker` | string | `user` or `assistant`.<br>用户或AI助手。 |
| `model` | string／null | Model associated with an assistant message; null for user messages.<br>assistant所属模型；user消息为null。 |
| `timestamp` | string | Original timestamp.<br>原始时间戳。 |
| `thinking` | string | Full AI-visible reasoning trace; empty for user messages.<br>AI可视化推理链全文；user消息为空。 |
| `response` | string | Original human input for user messages; formal AI response for assistant messages.<br>user为人类输入原文；assistant为AI正式回答。 |
| `state` | string | Heuristic process-state label for retrieval only.<br>启发式自动生成的过程状态标签，仅供检索参考。 |
| `answer_missing` | bool | True when the original export lacks an AI response; no response is fabricated.<br>原始导出缺少AI回答时为true，不补写回答。 |

### Construction and missing-data handling｜构建与缺失处理

The data were exported from real creation sessions between April and June 2026. Fault-tolerant parsing was used to address serialization defects in the original exports. Residual `\n` and `\"` sequences were restored to actual line breaks and quotation marks without rewriting the body text.

> 数据来自创作者2026年4—6月的真实创作会话导出。针对原始导出中的序列化缺陷进行容错解析，仅将残留的`\n`、`\"`还原为真实换行和引号，不改写正文。

Four missing AI responses in the three samples—W1 rounds 38 and 59, and W3 rounds 11 and 34—are marked `answer_missing: true` and were not reconstructed. Early off-topic conversation preceding the work in W3's session was excluded; the work-related dialogue is continuously preserved from round 1 onward.

> 3份样例中原始缺失的4条AI回答——W1第38、59轮及W3第11、34轮——均以`answer_missing: true`标记，未作补写。W3窗口在作品对话开始前存在其他主题的早期闲聊，该部分未收录；作品相关对话从第1轮起连续保留。

---

## 05｜Experimental Design and Findings｜实验设计与主要发现

### 5.1 Early controlled experiments and external anchors｜前期对照与外部锚点

The early experiments used the three works released in this repository as training material for the native full-process group, comparing finalized drafts, native processes, and different refined-process packaging methods.

> 前期实验以本仓库3份作品为原生全过程组训练语料，比较定稿、原生过程及不同精炼封装方式。

1. **Initial validation, May 2026:** an initial training experiment using process data at the 100k-character scale.<br>**初验（2026年5月）**：开展10万字级过程数据训练初验。
2. **Four-group comparison, July 2026, V1/V2:** matched-scale comparison of a finalized-output group, process-plus-output group, process-only group, and refined-process group. The native full-process group ranked first in all eight independent blind evaluations, and the process group's aggregate catch-up rate relative to the finalized-output group was 71.9%.<br>**四组对照（2026年7月，V1／V2两轮）**：成品组、过程＋成品组、纯过程组、精炼过程组同量对照；八场独立盲评中，原生全过程组均列第一，过程组对成品组的综合追赶率为71.9%。
3. **External anchors, August 3, 2026:** external model judging settings not involved in the earlier experimental design were introduced. The model ranked second in the DeepSeek judging setting with a score rate of 95.4%, third in the GLM setting, and fourth overall.<br>**外部锚点（2026年8月3日）**：引入未参与前期实验设计的外部模型裁判场，DeepSeek场得分率95.4%、列第二，GLM场列第三，综合排名第四。

### 5.2 August 23 nine-group matched-scale and extension experiments｜8·23九组等量对照及拓展实验

- **Base model and design:** Qwen3-30B-A3B-Base MoE with approximately 3.3B activated parameters; nine controlled groups comprising four CPT groups, two 结果SFT groups, two 过程SFT groups, and one base-model group.<br>**基座与设计**：Qwen3-30B-A3B-Base MoE基座，激活约3.3B；九组控制变量实验，包括CPT四组、结果SFT两组、过程SFT两组及基座组。
- **Evaluation and recalculation:** five independent third-party LLM judges conducted anonymized blind evaluations; 2,925 score points were recalculated individually. Ranking consistency was Kendall's W = 0.923 (midrank tie correction), χ²(8) = 36.90, p = 1.20×10⁻⁵.<br>**评审与复算**：五家相互独立的第三方大模型裁判匿名盲评，2,925个评分点逐分复算；排序一致性Kendall's W＝0.923（midrank并列校正），χ²(8)＝36.90，p＝1.20×10⁻⁵。
- **CPT result:** native full process C, refined full process D, and matched-scale finalized output B ranked C > D > B, consistently across all five judges.<br>**CPT结果**：原生全过程C、精炼全过程D、等量定稿B表现为C＞D＞B，五家裁判排序一致。
- **结果SFT result:** group G (结果SFT using refined full-process source material) ranked first overall by consensus of all five judges, with a catch-up rate of +40.3%.<br>**结果SFT结果**：G组（结果SFT×精炼全过程来源）获五家裁判一致总评第一，追赶率＋40.3%。

> **Unified conclusion and scope｜统一结论与适用边界**
>
> Process-derived material was effective in these experiments, but the value of refinement and the optimal packaging method are training-route dependent. CPT, 结果SFT, and 过程SFT should be evaluated separately; refinement cannot be universally treated as either a gain or a loss.
>
> **过程来源有效，但精炼价值与最佳封装具有训练路线依赖性。CPT、结果SFT、过程SFT应分别验证；精炼不能一概视为增益或损耗。**
>
> These findings reflect the released models, data scale, training configurations, and evaluation settings. The five LLMs served as judges; the training configurations, original records, and evaluation archives are included for inspection and further replication.
>
> 上述结果来自本次发布的模型、数据规模、训练配置和评审设置。五家大模型承担裁判角色；训练配置、原始记录与评分档案随开放材料发布，供核查和进一步复现。

---

## 06｜Governance Reproduction and Evidentiary Scope｜治理复现及其证明范围

The current public deliverable is **reproducible governance scripts and samples**, not a fully deployed software platform with a unified production interface.

> 当前公开成果定位为**可复现治理脚本及样例**，不是具有统一部署入口的完整软件平台。

- **Synthetic minimal sample:** runs B1–B5 on 12 synthetic sessions and produces their expected outputs.<br>**合成最小样例**：在12个合成窗口上运行B1—B5脚本并产生预期输出。
- **Real governance sample,《微尘纪元》:** demonstrates governance of three real sessions, containing 124 messages, 62 rounds, 263,586 Chinese characters of process text, and a 9,473-character final draft.<br>**《微尘纪元》真实治理样例**：展示3个真实窗口的治理过程，包含124条消息、62轮、263,586字过程文本及9,473字定稿。
- **477-session implementation record:** documents the scope, definitions, workflow, and outputs of the full project.<br>**477窗实施档案**：记录全量工程的范围、口径、流程和产物。

The sample packages reproduce the workflow at sample scale. Full-project totals are documented in the 477-session implementation record rather than recalculated from the synthetic minimal sample.

> 样例包用于在样例规模复现治理流程；全量统计记录在477窗实施档案中，并非由合成最小样例复算得出。

No arbitration split was triggered in the real governance sample. Examples of that mechanism are documented in the full implementation record.

> 真实治理样例未触发仲裁切割；相关机制实例见治理工程实施档案。

---

## 07｜Institutional Records and Project Context in China｜中国机构核验与项目实践背景

The project was created, governed, experimentally evaluated, registered, and introduced to data-circulation channels in China. These records show how an individual-led data project can move from research and evidence preservation into registration, platform listing, and public competition.

> 本项目在中国完成数据生产、治理、训练验证、登记与流通探索。这些经历呈现了一个个人主导的数据项目如何从研究和存证，逐步走向登记、平台上架与公开赛事。

### 7.1 Written response from the National Development and Reform Commission of China｜国家发展和改革委员会回函

In April 2026, a proposal concerning process data received a written response from the National Development and Reform Commission of China. The response stated:

> 2026年4月，过程数据相关建言获国家发展和改革委员会回函。回函指出：

> “AI creation-process data is an object type within data-property arrangements” and represents “an important scenario for data-property allocation.”
>
> “人工智能创作过程数据是数据产权的一种客体类型”，属于“数据产权配置的重要场景”。

The response places AI creation-process data within the institutional discussion of data-property allocation in China.

> 这一回函将人工智能创作过程数据纳入了中国数据产权配置的制度讨论场景。

### 7.2 Data intellectual property registrations in Jiangsu, China｜中国江苏数据知识产权登记

Two Jiangsu data intellectual property registrations have been obtained:

> 已取得两项江苏数据知识产权登记：

| Registration number｜登记号 | Registration date｜登记日期 |
|---|---|
| `SZ2026110003270.2` | June 3, 2026｜2026年6月3日 |
| `SZ2026110004980.0` | July 16, 2026｜2026年7月16日 |

Trusted timestamps, MD5 manifests, and registration certificates respectively support time evidence, file-integrity checks, and the registration and provenance evidence chain.

> 可信时间戳、MD5清单和登记证书分别用于时间存证、文件完整性校验以及登记与权属证据链。

### 7.3 Listing and selection on Juhe Data in China｜中国聚合数据平台上架与精选

The “High-Quality AI Datasets” section of Juhe Data (Tianjudihe, 2479.HK), a Chinese data platform, publicly showcases several hundred datasets. Datasets can enter commercial circulation through competitions associated with the platform's “Origin Initiative” (起源计划) or through platform review. The complete dataset has been listed in this section and received a “Selected” tag.

> 中国聚合数据（天聚地合，2479.HK）的“高质量AI数据集”板块公开展示数百个数据集，可通过“起源计划”相关比赛或平台审核上架，进入商业流通。项目完整数据集已在该板块上架，并获得“精选”标识。

Based on the author's item-by-item review of the public listings, approximately 10% of the datasets in this section carry the “Selected” tag. This is an observational count from public pages, not a fixed admission rule or selection ratio published by the platform.

> 根据作者对该板块公开页面的逐项统计，带“精选”标签的数据集约占10%。这一比例来自公开页面观察统计，并非平台公布的固定准入标准或入选比例。

### 7.4 Public data-element competition record in China｜中国数据要素赛事表现

The **2026 “Data Element X” Competition, Beijing Division** was held in China's capital and involved multiple review stages. Its expert review and guidance panel was led by six academicians. The highly competitive division brought together central state-owned enterprises, other state-owned enterprises, leading Chinese universities, and research teams.

> **2026年“数据要素×”大赛北京分赛**在中国首都北京举行，经过多阶段评审，评审与指导专家团由6位院士领衔。参赛者包括央企、国企、国内顶尖高校和团队，赛区竞争激烈。

The project reached the final of the **Science and Technology Innovation Track** and received an **Excellence Award**. Among the 18 finalists in this track, it was the only project from an enterprise based outside Beijing and the only one from a one-person company (OPC), giving it a distinctive lightweight-innovation profile.

> 项目入围**科技创新赛道决赛**并获**优秀奖**。在该赛道18个入围项目中，本项目是唯一非在京企业项目，也是唯一OPC单人创业公司项目，体现了轻量化创新主体的鲜明特点。

### 7.5 Beijing International Big Data Exchange: one registration, two certificates｜北京国际大数据交易所“一登双证”

The Excellence Award gave the project access to a green channel for the **“one registration, two certificates”** service at Beijing International Big Data Exchange. A dedicated coordinator is providing guidance, and the application is **currently in progress**.

> 北京分赛优秀奖为项目带来了北京国际大数据交易所“一登双证”绿色通道权益，并有相关专员对接指导，目前**正在办理中**。

The two certificates are a **Data Property Rights Registration Certificate** and a **Data Asset Registration Certificate**. This service can be understood within the policy framework of China's “Twenty Measures on Data” (数据二十条), which separates the rights to hold data resources, process and use data, and operate data products. The two certificates record property-rights and asset registration respectively, while the three rights form the broader institutional framework.

> “一登双证”指的是**数据产权登记证书**和**数据资产登记证书**。它可置于中国“数据二十条”提出的数据资源持有权、数据加工使用权和数据产品经营权“三权分置”框架下理解：两类证书分别记录产权登记与资产登记信息，三项权利则构成其背后的制度框架。

---

## 08｜Complete Dataset versus Public Samples｜完整数据集与开放样例的边界

The complete commercial dataset and the materials released in this repository are different levels of content. This repository provides three JSONL samples and experimental and governance materials; **it does not contain the full text of the complete commercial dataset**.

> 完整商业数据集与本仓库开放材料属于不同层级。本仓库提供3份JSONL样例及实验、治理材料，**不包含完整商业数据集全量文本**。

| Complete-dataset metric｜完整数据集指标 | Current value｜当前口径 |
|---|---:|
| Chat sessions｜会话窗口 | 477 (454 DeepSeek + 23 Kimi)<br>477窗（DeepSeek 454窗＋Kimi 23窗） |
| Messages｜消息 | 38,336 |
| Dialogue rounds｜对话轮次 | 18,744 |
| Triplets／pairs｜三元组／两元组 | 18,143 (96.8%)／601 |
| Full process text｜全量过程文本 | 46,155,043 Chinese characters｜字 |
| Final drafts｜定稿 | 30 works, 296,168 Chinese characters<br>30份，296,168字 |
| Process-to-final-draft ratio｜过程文本与定稿之比 | Approx. 156∶1｜约156∶1 |
| Work–session attribution pairs｜归属－窗配对 | 690 |
| Governance outputs｜治理产物 | 7 tables, 20,599 rows, 86 fields<br>7表、20,599行、86字段 |

Access to and commercial use of the complete dataset require separate confirmation. The license for public samples does not automatically grant commercial rights to the complete dataset.

> 完整数据集的获取与商业使用需另行确认，不因开放样例的授权而自动获得完整数据集的商业使用权。

---

## 09｜Applications and Limitations｜应用方向与局限

### Potential applications｜可探索的应用方向

- **Long-horizon agent trajectory research:** analyze cross-turn feedback, correction, and long-range dependencies within a single task.<br>**长程Agent轨迹研究**：分析单一任务中的跨轮反馈、修正和长期依赖。
- **CPT, 结果SFT, and 过程SFT:** compare same-source content under different data forms and training routes.<br>**CPT、结果SFT与过程SFT**：比较同源内容在不同数据形态和训练路线下的表现。
- **Chinese creative-domain research:** investigate collaborative creation in methodology writing, urban-planning thought experiments, and product-concept development.<br>**中文创作域研究**：研究方法论文本、城市规划思想实验和产品构想中的协同创作行为。
- **Process-data governance:** reuse methods for session attribution, normalized naming, statistics, splitting, archiving, and validation.<br>**过程数据治理**：复用窗口归属、规范化命名、统计、切割、归档和校验方法。
- **Future research:** after separately designing fields, labels, and experiments, explore process supervision, process reward models, or RLHF.<br>**未来研究探索**：在另行完成字段、标签与实验设计的前提下，探索过程监督、过程奖励模型或RLHF等方向。

### Limitations｜局限性

1. The data originate from a single creator, with pronounced individual characteristics in human-input style and task distribution.<br>数据来自单一创作者，人类输入风格与任务分布具有明显个体特征。
2. The release is best used as a deep longitudinal case and a basis for method development; broader validation calls for data from more creators and task types.<br>当前数据适合作为深度纵向案例和方法研究起点，更广泛的验证需要引入更多创作者与任务类型。
3. The `state` field is heuristic and does not constitute a manual quality label.<br>`state`字段为启发式自动标注，不构成人工质量标签。
4. AI-visible reasoning traces and formal responses are raw model outputs and have not been fact-checked individually. Their views do not represent the author's position.<br>AI可视化推理链和正式回答为模型原始输出，未经逐条事实核验，其中观点不代表作者立场。
5. Original missing states are explicitly preserved. Users should handle `answer_missing` and two-message-pair records appropriately.<br>原始缺失被显式保留，使用时应处理`answer_missing`及两元组记录。

---

## 10｜License, Citation, and Contact｜授权、引用与联系

### Open license｜开放授权

The public samples and associated materials in this repository are released under **CC BY-NC 4.0**: they may be used for non-commercial research and learning with attribution. Commercial use of the complete dataset, or any use beyond this license, requires separate confirmation with the author.

> 本仓库公开样例及说明材料采用**CC BY-NC 4.0**：可在署名前提下用于非商业研究与学习。完整商业数据集及超出该授权范围的使用，请与作者另行确认。

If the scripts are later placed under a separate software license, that license will be identified in the corresponding directory.

> 如后续对脚本采用单独软件许可，将在对应目录明确标注。

### Citation｜引用

```bibtex
@misc{humanai_longcot_creation_2026,
  author = {Qinghua Huang (皇清华)},
  title = {HumanAI-LongCoT-Creation: Human-AI Collaborative Long-Horizon Creation Process Data},
  year = {2026},
  publisher = {Zenodo},
  doi = {10.5281/zenodo.21968765},
  url = {https://doi.org/10.5281/zenodo.21968765}
}
```

### Author and contact｜作者与联系

| Item｜项目 | Information｜信息 |
|---|---|
| Author｜作者 | Qinghua Huang｜皇清华 |
| Entity｜主体 | Suzhou Guocheng Siwei Data Technology Co., Ltd.｜苏州过程思维数据科技有限公司<br>Suzhou, Jiangsu, China; sole natural-person ownership｜中国江苏苏州，自然人独资 |
| Email｜联系邮箱 | 1966916677@qq.com |
| Public-sample license｜开放样例授权 | CC BY-NC 4.0 (Attribution, NonCommercial)<br>署名、非商业 |
| Dataset and public downloads in China｜中国国内数据与开放材料下载 | [ModelScope｜魔搭社区](https://modelscope.cn/datasets/abc1966916677/HumanAI-LongCoT-Creation) |
| International archive｜国际存档 | [Zenodo DOI](https://doi.org/10.5281/zenodo.21968765) |

Research, reproduction, criticism, and collaboration concerning Chinese creative-domain data, full-trajectory data, long-horizon reasoning, data governance, and route-specific training are welcome.

> 欢迎围绕中文创作域、全轨迹数据、长程推理、数据治理及分路线训练开展研究、复现、批评与合作。
