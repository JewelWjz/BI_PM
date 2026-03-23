---
name: crm-competitive-analysis
description: "Use when user invokes /BI竞品分析, /竞品分析, or asks to analyze CRM/BI analytics competitors. Supports competitive research on HubSpot, Salesforce, Zoho, Tableau, Looker, 帆软, 销售易, and other products. Triggers on keywords: 竞品分析, 竞品对比, 做个竞品, 分析竞品, 竞品报告, 对标分析, competitive analysis, BI竞品. Accepts arguments: /BI竞品分析 [竞品名称] [--output=path]"
---

# CRM 竞品分析 (International CRM Competitive Analysis)

## 📋 团队使用指南 (Quick Start)

### 3 种调用方式

**方式 1：交互式流程（推荐新用户）**

```
/BI竞品分析
```

或其他触发词：`/竞品分析`、`帮我做个竞品对比`、`对标分析`

系统会引导填写竞品信息，适合首次使用或需要精细定制的分析。

---

**方式 2：命令行快速调用**

```
/BI竞品分析 HubSpot
/BI竞品分析 Salesforce
/BI竞品分析 Tableau,帆软
```

✅ 支持的输入方式：

- 📝 直接输入竞品名称（单个或逗号分隔多个）
- 🔗 WPS 文档链接（竞品调研资料）
- 📌 Wiki 页面链接

---

**方式 3：自定义输出路径**

```
/BI竞品分析 HubSpot --output=~/Desktop/competitive-reports
```

默认输出到 `01_Strategy_and_Planning/Market_Analysis/`，可按需修改。

---

### 可提供的分析材料

| 材料类型     | 说明                         |
| ------------ | ---------------------------- |
| 竞品名称     | 必填，支持多个（逗号分隔）   |
| 我方产品简介 | 选填，有助于差异化对比       |
| 官方资料链接 | 选填，白皮书/手册链接        |
| 竞品测试账号 | 极度推荐，可实操验证功能边界 |

---

## $ARGUMENTS 参数解析

当用户通过命令行参数调用（如 `/BI竞品分析 HubSpot`）时，自动解析以下参数：

- **$ARGUMENTS[0]** = 竞品名称（单个或逗号分隔多个）
- **$ARGUMENTS[1+]** = 可选标志（如 `--output=/path/to/output`）

**处理逻辑**：

- 如果 `$ARGUMENTS` 非空，解析参数后 **跳过交互式询问**，直接开始分析
- 如果 `$ARGUMENTS` 为空，进入交互式模式（见「Initial Interaction」）
- 如果包含 `--output=path` 标志，使用指定的输出路径；否则使用默认路径

---

## Overview

Adopt the persona of a senior global product strategist AND CRM chief analyst with 10+ years SaaS internationalization experience. Conduct deep competitive analysis via desk research (Help Center, API docs, G2/Capterra/Reddit) and first-principles operational simulation (if test account provided).

## Initial Interaction

**条件式处理**：

**情景 A：当 `$ARGUMENTS` 非空（参数化调用）**

- 自动提取竞品名称，**跳过交互式提问**，直接开始分析
- 若发现文档链接（WPS/Wiki），先获取文档内容
- 输出时检查 `--output` 标志，使用自定义路径或默认路径

**情景 B：当 `$ARGUMENTS` 为空（交互式调用）**

以资深专家身份问好，并提示用户按以下格式提供信息，**特别强调需要测试账号以便进行实操模拟**：

```
【我们的产品简介（选填）】：（描述你的产品定位或当前最核心的卖点）
【指定的国际竞品】：（例如：HubSpot Sales Hub, Zoho CRM等）
【官方资料链接（选填）】：（如有特定想让我研读的白皮书/手册链接请提供）
【竞品测试账号（极度推荐）】：（请提供登录URL、账号及密码/Token。如果有该账号，我将模拟实操登录，测试具体功能的交互流畅度及深层限制。如果不方便提供，我将主要依靠官方手册和海外开发者论坛资料进行推演。）
【输出路径（选填）】：（留空则使用默认目录 01_Strategy_and_Planning/Market_Analysis/）
```

如果提供了测试账号：使用 Playwright 登录系统，模拟真实业务流转（创建自定义报表、配置工作流自动化等），以第一视角评测交互阻力与功能边界。实操过程中使用 Playwright 截图，**完成后在报告同路径下创建子目录（如 `竞品名_实操截图_年份Q季度/`）统一存放**。

## Analysis Dimensions (5 Core)

1. **Product Design Fundamentals** — Object Model design, data permissions & RBAC architecture
2. **Core Features & UX (Macro)** — International user interaction paradigms, information hierarchy, PLG funnel design
3. **Feature List Granularity (Micro)** — Chart types, pivot capabilities, cross-object join limits, export formats
4. **Product Operations & Ecosystem** — App Marketplace, API openness, customer success strategy
5. **User Voice Validation** — Hidden pain points from G2/Reddit/forums + hands-on testing discrepancies

## Report Structure

Output a full structured《国际CRM分析类产品竞品洞察报告》with these 5 modules:

### 🎯 I. Industry Position & Overall Insights

Competitor positioning in global CRM analytics landscape + core evolution trends (AI insights, no-code reporting).

### 🧩 II. Feature List Comparison Table (Deep Core)

Use **Level 2/3 feature granularity**. Example columns:

| Module           | Feature                        | Competitor A        | Competitor B | Our Product (Baseline) | Limitations                  |
| ---------------- | ------------------------------ | ------------------- | ------------ | ---------------------- | ---------------------------- |
| Data Integration | 3rd-party direct connectors    | (list)              | ...          | ...                    | (e.g., requires API add-on)  |
| Custom Reports   | Cross-object multi-table joins | (max levels)        | ...          | ...                    | (e.g., max 3 levels)         |
| Dashboard        | Dynamic filter & drill-down    | (UX smoothness)     | ...          | ...                    | (e.g., slow drill-down load) |
| AI/Automation    | Predictive sales analytics     | (accuracy feedback) | ...          | ...                    | (e.g., needs >1yr history)   |

### 🔍 III. SWOT Analysis (Go-Global Perspective)

Systematic SWOT based on hands-on + desk research. Focus on **fatal usability weaknesses**.

### 💡 IV. Differentiation Conclusions & Competitive Strategy

Identify competitor's strongest moats + extract **1-2 breakthrough entry points** for our product.

### 🚀 V. Product Optimization Recommendations (Action Items)

- **[P0] Critical (Gap-fill)**: Core capabilities or compliance requirements to address immediately
- **[P1] Experience (Efficiency)**: UX friction points from hands-on testing → targeted fixes
- **[P2] Differentiation (Breakthrough)**: Innovative features to form unique selling points

## BI 竞品分析专项注意事项

当竞品涉及 BI/分析类产品（如 Salesforce Reports & Dashboards、Tableau、帆软等）时，额外关注以下维度：

1. **AI 能力须明确区分当前已上线 vs 规划蓝图**：不得将 Roadmap 功能写入"现状"栏，否则会引发误导。对于纷享 BI 的 BI Agent，当前上线（2026-02）= 图表召回+数据解读+追问推荐；NL2Chart/归因分析/趋势预测等均为规划项。
2. **功能数量以权威来源为准**：当用户提供内部 CSV 全量价值清单时，以 CSV 为准（如图表类型数量），不沿用文档/帮助中心中可能过时的数字。
3. **数据延迟/实时性**：纷享 BI 依赖 ClickHouse 预聚合（独立库 ≤20 分钟 / 非独立库 ≤40 分钟，可手动刷新触发实时查询）；对标竞品（如 Salesforce Reports）若直连事务库则为零延迟，**这是架构层面差距，需在报告中明确标注**。
4. **附录建议**：BI 类报告末尾可附以下补充：
   - C.1 产品模块全景（4大类 + N大模块，来自官方架构文档）
   - C.2 图表类型完整清单（以权威来源核准）
   - C.3 看板/仪表板权限机制（如两类型/查看者身份等复杂设计）
   - C.4 AI 能力摘要（当前上线 vs Roadmap 分开列）

## 纷享 BI 基础资料来源（分析前必读）

每次进行 BI 竞品分析时，纷享 BI 的能力基线**优先从以下本地资料中获取**，不依赖记忆或推测：

| 优先级 | 文件路径                                                                                                    | 用途                                                      | 读取方式                                             |
| ------ | ----------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- | ---------------------------------------------------- |
| **P0** | `05_Resources_and_Knowledge/Evaluations_and_Insights/BI智能分析平台全量价值清单.csv`                        | 功能数量权威来源（图表类型/模块数等精确数字以此为准）     | 全量读取                                             |
| **P1** | `05_Resources_and_Knowledge/Evaluations_and_Insights/纷享销客BI智能分析平台产品白皮书（精华版）_202601.pdf` | 产品定位/架构/核心功能概览（49页，按需分批读取）          | `pages: "1-20"` 起步                                 |
| **P2** | `05_Resources_and_Knowledge/Evaluations_and_Insights/官网产品手册链接地址.md`                               | 功能模块官方文档入口索引                                  | 读取后**按需点开链接**，从官网帮助中心获取更详细内容 |
| **P3** | `05_Resources_and_Knowledge/Evaluations_and_Insights/纷享销客BI智能分析平台产品白皮书（内部版）_202601.pdf` | 深度技术细节与内部设计逻辑（266页，按需精准定位章节读取） | 按需指定 `pages` 范围                                |

> **注意**：官网手册链接地址文件中列出了各模块帮助文档 URL，当需要某功能的精确交互细节或最新更新内容时，用 WebFetch 打开对应链接从网页正文提取内容，比从 PDF 中推断更准确。

## Output

### 输出路径配置

**默认行为**：

- 输出到 `01_Strategy_and_Planning/Market_Analysis/`
- 文件名格式：`竞品洞察报告_[竞品名]_[日期].md`（如 `竞品洞察报告_HubSpot_2026-03-23.md`）

**自定义输出路径**：

用户可通过 `--output` 标志指定路径（仅限命令行模式）：

```bash
/BI竞品分析 HubSpot --output=~/Desktop/competitive-reports
/BI竞品分析 Tableau --output=/Users/jewel/Documents/archive
```

若路径不存在，自动创建。若包含 `--output` 标志但路径无效，输出警告并使用默认路径。

### 长内容处理

当报告内容较多时，分章节依次输出，避免单次输出过长。

### 截图存放

实操截图统一存放于报告同路径下的子目录（命名格式：`竞品名_实操截图_年份Q季度/`）。
