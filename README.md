# Automotive Dealer Sales Analysis Skill / 汽车经销商销售分析

<!-- ===================== OPTION A: ENGLISH ===================== -->
 
# Automotive Dealer Sales Review Skill
 
> Turn a monthly sales spreadsheet into a plain-language answer to one question: **is our sales decline getting worse, or easing?**
 
![From a simple monthly sales table to a plain-language verdict (fictional data)](assets/example-output.svg)
 
*Fictional data, for illustration only.*
 
## The 30-second version
 
| | |
|---|---|
| **You give it** | A simple table: one row per month, with units sold. 13+ months works best; with less history it still analyzes what the data supports. |
| **You get back** | A short verdict you can use in a monthly review: is the year-over-year and month-over-month decline accelerating or easing, backed by the key numbers. With model, dealer or regional detail, it also shows what pulls the total down and what offsets it. |
| **You need** | An AI app that supports Agent Skills and can read files. The install guide below is written for VS Code + GitHub Copilot (Agent mode). No coding required. |
| **It is not** | Standalone software. It can't be double-clicked and it doesn't connect to your sales system. |
 
**[Try it on sample data (about 5 minutes) →](#quick-start)** · [Prepare your own data](#%E5%87%86%E5%A4%87%E8%87%AA%E5%B7%B1%E7%9A%84%E6%95%B0%E6%8D%AE) · [FAQ](#%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98)
 
## Who is this for?
 
- **Sales manager, preparing the monthly meeting.** "Is the decline slowing? Give me one headline and the numbers behind it."
- **Dealer-group analyst, checking before writing the report.** Confirm whether the trend is easing or worsening, and see what the data can't support, before it goes into a deck.
- **Regional or brand manager, looking for what drags the total down.** With model or regional detail, see which items account for the drop and which offset part of it. (This shows the make-up of the change, not its cause.)
- **Someone new to dealer analytics, learning the method.** The skill follows one consistent method (comparable periods, trend judgement, reconciling the parts to the total) and says so when the data is not enough, instead of guessing.
**Honest by design:** no model data means no model analysis. "The decline is easing" is never reported as "sales are recovering."
 
<!-- ===================== OPTION B: 简体中文 ===================== -->
 
# 汽车经销商销售复盘 Skill
 
> 把月度销量表变成一句大白话结论:**销量下滑是在加重,还是在放缓?**
 
![从简单的月度销量表到大白话结论(虚构数据)](assets/example-output.svg)
 
*虚构数据,仅作示意。*
 
## 30 秒看懂
 
| | |
|---|---|
| **你提供** | 一张简单的销量表:每月一行,写明销量。最好有 13 个月以上;历史不足时,也会分析数据能支持的部分。 |
| **你得到** | 一段可用于月度复盘的结论:同比、环比的下降是在加重还是放缓,并附关键数字。若有车型、门店或区域明细,还会说明哪些拉低了总量、哪些抵消了部分减量。 |
| **你需要** | 支持 Agent Skills 且能读取文件的 AI 客户端。下方安装说明按 VS Code + GitHub Copilot(代理模式)编写。无需写代码。 |
| **它不是** | 独立软件:不能双击运行,也不会自动连接你的销售系统。 |
 
**[用虚构数据试跑(约 5 分钟)→](#quick-start)** · [准备自己的数据](#%E5%87%86%E5%A4%87%E8%87%AA%E5%B7%B1%E7%9A%84%E6%95%B0%E6%8D%AE) · [常见问题](#%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98)
 
## 适合谁用?
 
- **销售经理 · 准备月度会议。**“下滑放缓了吗?给我一句结论和支撑它的数字。”
- **集团分析师 · 写报告前先核对。**先确认趋势是在放缓还是加重,并清楚数据不能支持什么,再写进报告。
- **区域／品牌负责人 · 找出拉低总量的因素。**有车型或区域明细时,看哪些减量最大、哪些抵消了部分减量。(展示的是变化的构成,不等于下降的原因。)
- **刚接触经销商分析的人 · 学习方法。**技能按固定方法分析(期间可比、趋势判断、分项与总量对账),数据不够时会明确说明,而不是猜测。
**诚实为先:**没有车型数据,就不生成车型分析;“降幅收窄”不会被说成“销量回升”。
 

## Quick start

### 1. 准备工具和下载包

本页先介绍 **VS Code + GitHub Copilot** 一条路线：

- 安装较新版本的 [VS Code](https://code.visualstudio.com/)，登录 GitHub Copilot，并确认能在聊天中使用可读取文件的代理模式（Agent）。账号权限、可用额度及组织政策以客户端为准；能访问 GitHub 不代表已经能使用 Copilot。
- 若仓库提供 Release ZIP，下载后解压；也可在 GitHub 仓库点击 **Code → Download ZIP**。找到其中的 `sales-analysis-lite` 文件夹；如果解压后直接看到 `SKILL.md`，把它所在的文件夹命名为 `sales-analysis-lite`。
- 本包不要求安装 Python、数据库驱动或其他依赖；实际数据读取和计算由 AI 客户端的可用工具执行。先用假数据，不要先放入公司文件。

### 2. 放到指定位置

在电脑上新建一个试用文件夹，例如 `sales-demo`，用 VS Code 的 **File → Open Folder（文件 → 打开文件夹）**打开它。在左侧文件区依次新建 `.github` 和它下面的 `skills` 文件夹，再将整个 `sales-analysis-lite` 文件夹复制进去。

放好后应是下面的结构，注意不要多套一层同名文件夹：

```text
sales-demo/                 ← 用 VS Code 打开的文件夹
└── .github/
    └── skills/
        └── sales-analysis-lite/
            ├── SKILL.md
            ├── README.md
            ├── LICENSE
            ├── references/
            ├── templates/
            └── assets/
                └── sample-monthly-sales.csv
```

### 3. 确认安装成功

打开 Copilot 聊天，使用 **Open Customizations → Skills** 查看技能；也可按 `F1`，搜索并运行 **Chat: Open Customizations**。列表应出现 `sales-analysis-lite`。不同版本的按钮名称可能变化，参见 [VS Code 官方技能说明](https://code.visualstudio.com/docs/copilot/customization/agent-skills)。

若没有出现，先确认 `SKILL.md` 路径和上图一致，再重新打开窗口。仍未出现时，检查客户端版本和组织设置，不要把 AI 说“已加载”当作唯一安装证据。

### 4. 复制这句话，试跑假数据

在能够读取工作区文件的代理聊天中发送：

> 请使用 sales-analysis-lite 技能，读取 `.github/skills/sales-analysis-lite/assets/sample-monthly-sales.csv`。这是虚构经销商样本，month是完整自然月，retail_units是虚构的零售销量，单位为辆，所有月份范围一致。请分析2026年10月销售：先给结论，再说明同比和环比的下降是在加重还是放缓，用关键数字支持判断；没有车型、门店、订单或客流数据，不要补造。

English prompt: Use sales-analysis-lite to read `.github/skills/sales-analysis-lite/assets/sample-monthly-sales.csv`. All rows are complete calendar months for the same fictional dealer scope; retail_units means illustrative retail units. Review October 2026, compare YoY/MoM, and explain whether the decline is accelerating or easing with supporting figures. Do not invent missing dimensions.

**核对试用结果：**应识别10月1,200辆、同比少售200辆（-14.3%）、环比少售120辆（-9.1%），并说明两项降幅较上月收窄。表述不必逐字相同，但不能说销量已经回升。找不到文件时，先核对上述路径，或用聊天的文件附件功能选择样例。

这条安装路线依据官方文档编写；包内样例已做计算核对，**不表示已经在所有客户端、版本或账号上完成安装实测**。其他支持 Agent Skills 的客户端请遵循各自的安装说明，本页不承诺跨客户端兼容性。

## 分析示例（虚构数据）

以下仅展示输出方式。月份、门店范围、车型名称及全部数字均为编造示例，不代表真实市场或业务结果；仅做算术核对，未连接真实业务数据源，也未验证真实业务来源、覆盖或口径。

> **这些数据能分析什么？**月度样例 CSV 只包含总零售量，可支持期间比较和趋势判断；不含订单流入、展厅客流或经销商明细，不能据此分析转化、车型贡献或门店排名。下方车型及外部市场表格为额外的独立虚构示例，用于展示数据齐备时可如何拆解；所有数字仍为虚构。
>
> **月度样例数据：**授权经销商样本，2026年10月整月。零售1,200辆，较9月减少120辆（环比-9.1%），较2025年10月减少200辆（同比-14.3%）。
>
> **结论：**销量同比、环比仍在下降，但降幅都较上月收窄：同比降幅从9月的17.5%收窄到10月的14.3%，环比降幅从9月的12.0%收窄到10月的9.1%。这说明下行延续、下降速度放缓，**不代表销量已经回升**。
>
> | 月份 | 零售量 | 同比增减 | 环比增减 |
> |---|---:|---:|---:|
> | 2026年8月 | 1,500 | -300（-16.7%） | -50（-3.2%） |
> | 2026年9月 | 1,320 | -280（-17.5%） | -180（-12.0%） |
> | 2026年10月 | 1,200 | -200（-14.3%） | -120（-9.1%） |
>
> 环比降幅从12.0%收窄到9.1%，即收窄2.9个百分点；同比降幅从17.5%收窄到14.3%，即收窄3.2个百分点。同比和环比基期各自独立，不能把两类降幅交叉比较。
>
> **哪些车型拉低了销量，哪些车型抵消了部分减量？（同比）**
>
> | 车型 | 上年同期 | 本期 | 变化 | 同比 |
> |---|---:|---:|---:|---:|
> | 车型A | 700 | 500 | -200 | -28.6% |
> | 车型C | 450 | 300 | -150 | -33.3% |
> | 车型B | 250 | 400 | +150 | +60.0% |
> | 净变化 | 1,400 | 1,200 | **-200** | **-14.3%** |
>
> 车型A和C合计减少350辆，车型B增加150辆抵消部分减量，净减少200辆，与总量变化对账。拆分显示变化构成，不证明下降原因。
>
> **外部市场（虚构且同口径）：**假设品牌A、品牌B和本品C覆盖相同地域、销售事件及日期窗口：
>
> | 品牌 | 2025-10-01–10-20 | 2026-10-01–10-20 | 同比增减 |
> |---|---:|---:|---:|
> | 品牌A | 2,200 | 2,000 | -200（-9.1%） |
> | 品牌B | 1,800 | 1,650 | -150（-8.3%） |
> | 本品C | 1,400 | 1,200 | -200（-14.3%） |
> | 市场合计 | 5,400 | 4,850 | -550（-10.2%） |
>
> 在这个纯示例中，本品销量降幅大于示例市场；本品在三品牌合计中的占比由25.9%降至24.7%（约-1.2个百分点，按未四舍五入的份额计算）。这组假数据用于演示市场比较和份额计算，不代表真实市场表现。
>
> **示例置信度：不可评估。**数据完全虚构，未核实来源、覆盖或口径；真实分析需先做这些检查。

### 可直接试用的样例文件

[下载虚构的15个月经销商月度零售 CSV](./assets/sample-monthly-sales.csv)。样例只包含月份和零售数量，适合试跑同比、环比和趋势判断；不含真实企业信息，也不代表任何实际市场或经营结果。每行代表一个完整自然月；未提供订单、客流、门店或车型明细。

## 准备自己的数据

先准备一张简单的销量表即可，以下仅为格式示意；两行不足以判断下降是否持续或放缓：

| 月份 | 零售销量（辆） |
|---|---:|
| 2025-10 | 1,400 |
| 2026-10 | 1,200 |

- **每行一个月，月份不重复。**不要把累计销量和单月销量混在一起；缺失不填成0。列名可以用中文，不必与样例完全相同。
- **尽量提供连续13个月以上，24个月以上更好。**13个月通常可算分析月同比，但比较本月和上月的同比降幅还需要上月的去年同期数据；历史少也能分析已有期间，不能强行判断趋势。
- **说清“销量”是什么。**例如已交付车辆数、开票数或上牌数，并说明地域、门店范围及是否含退车。各期统计方法应一致；门店开闭或范围变化要说明。
- **本月没结束就注明截止日。**想比较月内表现，需要本月、上月和去年同月相同进度的数据；只有历史整月总数，不能按天数比例当作真实同期销量。
- **想分析车型、门店或区域，再提供对应明细。**每行代表什么、车型怎么划分、门店是否改名或换归属都应说明；不清楚的可让 AI 先检查并提问。

试用后，可把获准使用的文件放入 `sales-demo`，用聊天的附件功能选中它，再发送：

> 请使用 sales-analysis-lite 分析我附上的销量表。分析月份是[年份和月份]，销量指[交付／开票／上牌等]，单位为辆，范围是[地域和门店]，数据截至[日期]，[是否含退车、是否有门店范围变化]。先检查数据能支持哪些比较，再给出销售结论。不清楚的地方先问我。

## 常见问题

**必须会写代码吗？**首次试用不用自己写代码，也不用 Git 命令。AI 可能调用计算工具，需要你按客户端提示审阅并授权；如果工具不可用，它应说明未能验证，不假装已经算过。

**可以直接用 Excel 吗？**取决于 AI 客户端是否能读取工作簿。本技能本身不提供 Excel 读取器。不确定时，将要分析的单张工作表另存为 CSV UTF-8，保留列名，去掉合并单元格、汇总行和说明行；转换后核对月份和数字是否正确。

**没有13个月数据还能用吗？**可以。但没有去年同期就不能算同比；没有足够历史就不能判断降幅是否收窄。技能应回答有依据的部分，并说明缺口。

**为什么没生成车型或门店分析？**只有总销量无法拆出车型或门店表现；即使有相关列，标签大量缺失或范围无法核对时，也可能无法可靠分析。

**可以直接上传到任意 AI 网页吗？**不能把“可上传附件”当成“支持安装技能”。普通网页聊天不一定会加载本包及其引用文件；应先查客户端是否支持 Agent Skills 和文件读取。

**公司数据会不会被上传？**本技能不保证本地处理。数据传输、存储和保留方式取决于所用 AI 客户端、模型服务及企业配置。先用假数据测试，使用真实数据前遵守公司政策，不上传客户个人信息或未经授权的经营数据。

## 文件与许可

业务用户无需先读完所有方法文件；它们供 AI 执行分析及需要核查方法的人使用。

- [SKILL.md](./SKILL.md)：技能入口和执行步骤。
- [references/methodology.md](./references/methodology.md)：期间可比性、趋势判断和汇总核对规则。
- [templates/response.md](./templates/response.md)：结论、表格和折叠证据的输出格式。
- [assets/sample-monthly-sales.csv](./assets/sample-monthly-sales.csv)：15个月纯虚构月度零售样例。
- [LICENSE](./LICENSE)：本包以 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) 发布。署名建议：**Sales Analysis Lite**，作者 **Yumi Kuan**。再分发或改编时保留署名、许可证链接，并说明是否修改。

包内只有方法、模板和虚构样例，并公开下列作者署名；不包含真实经营数据、客户或员工个人信息、内部地址、凭据或数据库连接。它不提供数据访问权限；不要把内部适配、连接信息或真实结果提交到公开包。

### 作者与 AI 协作 / Credits

- **作者与方法主导：Yumi Kuan。**
- **AI 协作：使用 VS Code 中的 GitHub Copilot 辅助整理。**协助整理分析流程、优化技能指令与说明、设计虚构示例，并核对示例计算与发布包。
- **创作纪念：**这是 Yumi Kuan 与该 AI 助手第一次共同创作的成果。业务判断、内容取舍和公开发布决定由作者主导。

建议署名：**Sales Analysis Lite — Yumi Kuan；AI-assisted collaboration with GitHub Copilot in VS Code.** 此协作说明用于记录 AI 辅助贡献，不表示 GitHub、Microsoft 或其他机构为本项目背书；许可仍为上述 CC BY 4.0。

## 维护与发布

<details>
<summary>展开仓库设置建议与发布前检查（维护者）</summary>

### GitHub repository metadata（建议）

创建公开 GitHub 仓库时，可在仓库 About 区使用以下信息，帮助按仓库名称、描述和 Topics 搜索发现：

- **Repository name:** `automotive-dealer-sales-analysis-skill`
- **Description:** `Agent Skill for automotive dealership sales reviews, monthly retail performance, YoY/MoM trend diagnosis, and model, dealer, and regional contribution analysis.`
- **Topics:** `agent-skills`, `sales-analysis`, `automotive`, `dealership`, `retail-analytics`, `business-intelligence`, `sales-operations`

仓库元数据需在 GitHub 仓库设置中单独填写；将这些建议写在 README 中不会自动设置 Topics。

### 公开发布前检查

- [ ] 确认对方法文本及衍生材料拥有公开再分发权，涉及雇主或第三方内容时先取得授权。
- [ ] 人工复核技能文件，确保没有非预期的内部业务标识、真实数据、个人信息、令牌、路径或附件。
- [ ] 单独复制本技能目录到公开项目；不要公开整个业务仓库、Git历史、缓存、日志或原始方法文档。
- [x] 已按权利人确认添加 CC BY 4.0 许可证和署名；发布前再次确认署名信息准确。
- [ ] 在目标客户端测试技能发现；分别测试整月、未完月、缺基期／零基期、缺维度和无数据场景。
- [ ] 对公开项目的暂存文件与提交历史做一次复核后再推送。本包创建不会自动提交、推送或公开仓库。

</details>
