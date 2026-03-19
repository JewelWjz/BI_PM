# BI PM Skills

BI 产品经理专属 Claude Code skill 包，包含 5 个常用工作流 skill。

## 包含的 Skills

| Skill | 触发命令 | 用途 |
|---|---|---|
| `bi-feedback-analysis` | `/BI需求反馈分析` | 从用户反馈数据中挖掘深层需求，输出结构化洞察报告 |
| `bi-prd-writing` | `/BI PRD编写` | 迭代式引导提问，协作完成 PRD 草案 |
| `bi-requirements-review` | `/BI需求评审` | 三视角（PM/RD/QA）加权评审需求文档 |
| `bi-ux-design-doc` | `/BI设计文档编写` | 将 PRD 转化为 UX/UI 规范文档 |
| `crm-competitive-analysis` | `/竞品分析` | 国际 CRM/BI 产品深度竞品分析报告 |

## 安装方法

```bash
claude plugin install <本仓库地址>
```

## 依赖说明

部分 skill 会调用以下 MCP 工具，需确保团队成员已配置：
- `wps` — 读取金山文档/WPS 文档
- `query-wiki` — 读取内部 Wiki（wiki.firstshare.cn）
- `query-tapd` — 读取 TAPD 需求详情
