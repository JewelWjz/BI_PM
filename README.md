# BI PM Skills

BI 产品经理专属 Claude Code Skill 包，包含 5 个常用工作流 skill。

## 包含的 Skills

| Skill                         | 触发命令          | 用途                                             |
| ----------------------------- | ----------------- | ------------------------------------------------ |
| `bi-feedback-analysis`        | `/BI需求反馈分析` | 从用户反馈数据中挖掘深层需求，输出结构化洞察报告 |
| `bi-prd-writing`              | `/BI PRD编写`     | 迭代式引导提问，协作完成 PRD 草案                |
| `bi-requirements-review`      | `/BI需求评审`     | 三视角（PM/RD/QA）加权评审需求文档               |
| `bi-ux-design-doc`            | `/BI设计文档编写` | 将 PRD 转化为 UX/UI 规范文档                     |
| `crm-bi-competitive-analysis` | `/BI竞品分析`     | 国际 CRM/BI 产品深度竞品分析报告                 |

---

## 安装方法

### 方式 1：克隆仓库后手动复制（推荐）

```bash
# 1. 克隆仓库
git clone https://github.com/JewelWjz/BI_PM.git
cd BI_PM

# 2. 将所有 skill 复制到 Claude Code 的 skills 目录
cp -r skills/* ~/.claude/skills/
```

### 方式 2：只安装指定 skill

```bash
# 只安装竞品分析 skill
cp -r skills/crm-bi-competitive-analysis ~/.claude/skills/

# 只安装需求评审 skill
cp -r skills/bi-requirements-review ~/.claude/skills/
```

安装完成后，在 Claude Code 中输入对应触发命令即可使用。**无需重启**，立即生效。

---

## 更新方法

### 更新全部 skill

```bash
cd BI_PM

# 拉取最新版本
git pull origin main

# 覆盖更新所有 skill
cp -r skills/* ~/.claude/skills/
```

### 更新单个 skill

```bash
cd BI_PM
git pull origin main

# 只更新指定 skill（以竞品分析为例）
cp -r skills/crm-bi-competitive-analysis ~/.claude/skills/
```

### 查看当前已安装的版本

```bash
# 查看本地已安装的 skill 列表
ls ~/.claude/skills/

# 查看某个 skill 的版本信息（通过 git log 确认）
git log --oneline skills/crm-bi-competitive-analysis/
```

---

## 依赖说明

部分 skill 会调用以下 MCP 工具，需确保团队成员已配置：

| MCP 工具     | 用途                                | 依赖的 Skill       |
| ------------ | ----------------------------------- | ------------------ |
| `wps`        | 读取 WPS/金山文档                   | 需求评审、PRD 编写 |
| `query-wiki` | 读取内部 Wiki（wiki.firstshare.cn） | 需求评审           |

### `crm-bi-competitive-analysis` 额外依赖

该 skill 依赖本地 PDF 白皮书文件（未放入仓库），使用前请确保：

1. 已获取以下文件（联系团队负责人）：
   - `纷享销客BI智能分析平台产品白皮书（精华版）_202601.pdf`（21 MB）
   - `纷享销客BI智能分析平台产品白皮书（内部版）_202601.pdf`（67 MB）

2. `references/` 目录中已内置以下资料（安装后即可用）：
   - `BI智能分析平台全量价值清单.csv` — 功能清单权威来源
   - `官网产品手册链接地址.md` — 官网帮助文档索引

---

## 目录结构

```
BI_PM/
└── skills/
    ├── bi-feedback-analysis/
    │   └── SKILL.md
    ├── bi-prd-writing/
    │   ├── SKILL.md
    │   └── references/
    │       └── PRD_TEMPLATE.md
    ├── bi-requirements-review/
    │   ├── SKILL.md
    │   └── references/
    │       └── TEMPLATE.md
    ├── bi-ux-design-doc/
    │   └── SKILL.md
    └── crm-bi-competitive-analysis/
        ├── SKILL.md
        └── references/
            ├── BI_RESOURCES.md
            ├── BI智能分析平台全量价值清单.csv
            └── 官网产品手册链接地址.md
```
