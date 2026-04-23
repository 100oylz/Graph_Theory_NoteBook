<!-- From: /home/OuyangLinzhuo/Documents/Campus Life/Campus_Course/Graph_Theory/notebook/Graph_Theory/AGENTS.md -->
# AGENTS.md — 图论知识库

> 本文档供 AI 编码/编辑助手阅读。你正在操作的是一个 **Obsidian 关系型知识库（Markdown 笔记仓库）**，而非传统软件项目。没有 `pyproject.toml`、`package.json` 或构建脚本。所有"代码"均为 Markdown 笔记、YAML frontmatter 和 Dataview 查询。

---

## 项目概述

本项目是基于电子科技大学《图论》课程的 Obsidian 关系型笔记仓库，采用**卡片盒笔记法（Zettelkasten）**理念组织。通过 Obsidian 的双向链接（Wikilink）、图谱视图（Graph View）与 Dataview 插件，将图论知识点编织成一张可导航、可查询、可视化的概念网络。

仓库托管于 Git，可在 Obsidian 中作为本地仓库打开。

---

## 技术栈与工具链

| 工具/插件 | 用途 | 配置状态 |
|-----------|------|----------|
| [Obsidian](https://obsidian.md/) | 本地优先的 Markdown 知识库客户端 | 必需 |
| **Dataview** | 基于 YAML frontmatter 的动态查询与汇总 | ✅ 已启用并配置 |
| **Breadcrumbs** | 页面顶部面包屑层级导航 | ✅ 已启用并配置 |
| **Templater / Templates** | 笔记模板化工作流 | ✅ 模板文件夹已设置 |
| **Quick-latex** | LaTeX 公式快速输入辅助 | ✅ 已启用 |
| **Obsidian Custom Attachment Location** | 附件自动归类与重命名 | ✅ 已配置 |
| **Claudian** | Obsidian 内的 AI 助手插件 | ✅ 已启用 |
| **Juggl** | 基于 Cytoscape.js 的交互式图谱视图 | ✅ 已安装 |
| **CSS Snippets** | 自定义阅读视图样式（自适应行宽） | ✅ 已启用 |

### Obsidian 关键设置

- `strictLineBreaks: true` — 严格换行，普通换行不会生成 `<br>`
- `alwaysUpdateLinks: true` — 重命名文件时自动更新所有 wikilink
- `showLineNumber: true` — 编辑器显示行号
- 模板文件夹路径：`templates/`
- 附件文件夹路径：`raw/images/${noteFilePath}`（按笔记路径自动分子目录）
- CSS 片段路径：`.obsidian/snippets/adaptive-width.css`

---

## 目录结构

```
Graph_Theory/
├── index.md                     # 知识库总入口与导航
├── MOC-定理.md                  # 定理汇总页（Map of Content）
├── MOC-算法.md                  # 算法汇总页
├── MOC-特殊图.md                # 特殊图跨章汇总
├── MOC-连通性.md                # 连通性主题汇总
├── MOC-着色.md                  # 着色理论汇总
├── MOC-匹配.md                  # 匹配与因子汇总
├── MOC-树.md                    # 树结构汇总
├── MOC-遍历.md                  # 遍历问题汇总
├── 第1章 图的基本概念.md        # 章级 MOC（第 1–7、9 章，共 8 章）
├── 第2章 树.md
├── 第3章 图的连通度.md
├── 第4章 Euler图与Hamilton图.md
├── 第5章 匹配与因子分解.md
├── 第6章 平面图.md
├── 第7章 图的着色.md
├── 第9章 有向图.md
├── wiki/                        # 原子化笔记（概念、定理、算法、问题）
│   ├── 图.md
│   ├── 匈牙利算法.md
│   ├── Berge定理.md
│   └── ...（128 页）
├── templates/                   # 笔记模板
│   ├── 使用说明.md              # 模板使用与 YAML 字段说明
│   ├── 概念.md
│   ├── 定理.md
│   ├── 算法.md
│   └── 问题.md
├── raw/                         # 原始资源
│   ├── image/                   # 通用图片（目前为空）
│   ├── images/                  # 按笔记分子目录的图片
│   │   └── wiki/                # wiki 笔记相关图片
│   └── ppt/                     # 课程原始 PPT（第 1–7、9 章）
├── .obsidian/                   # Obsidian 配置、插件、工作区状态
│   └── snippets/                # CSS 片段
│       └── adaptive-width.css   # 阅读视图自适应行宽
├── .claude/                     # Claude Code 本地配置
└── .claudian/                   # Claudian 插件设计文档与配置
```

### 文件颜色编码（Graph View）

在 `.obsidian/graph.json` 中预定义了图谱节点颜色，**全局图与子图颜色组保持一致**：

| 标签 | 颜色 |
|------|------|
| `#MOC` | 🔴 红色 |
| `#概念` | 🔵 蓝色 |
| `#算法` | 🟢 绿色 |
| `#问题` | 🟡 黄色 |
| `#定理` | 🟣 紫色 |

> 全局图颜色组定义在 `graph.json` 的 `colorGroups` 字段，子图颜色组定义在 `localGraph.colorGroups` 字段，两者必须同步修改。

---

## 笔记规范与内容组织

### 原子化笔记原则

- **每个概念、定理、算法独立成页**，存放于 `wiki/` 目录下。
- **文件名即概念名**，后续被引用时直接显示该名称（Obsidian wikilink 特性）。
- 所有 wiki 页面必须使用对应模板，保持格式一致。

### YAML Frontmatter 标准

每个笔记文件顶部必须包含 YAML frontmatter，字段说明如下：

| 字段 | 格式 | 用途 | 消费者 |
|------|------|------|--------|
| `chapter` | 纯字符串，如 `"第1章 图的基本概念"` | Dataview 按章筛选 | Dataview |
| `parent` | wikilink，如 `"[[第1章 图的基本概念]]"` | 面包屑层级导航 | Breadcrumbs |
| `category` | `"概念"` / `"定理"` / `"算法"` / `"问题"` | 分类与图谱着色 | Dataview, Graph View |
| `tags` | 数组，如 `[图论, 概念]` | 全局标签与检索 | Obsidian, Graph View |
| `related` | 数组，如 `["[[最短路]]", "[[Dijkstra]]"]` | 弱关联概念预留 | 人工维护 |
| `aliases` | 数组，如 `["最短路径"]` | 页面别名 | Obsidian |

**重要区分**：
- `chapter` 用**纯字符串**（供 Dataview `WHERE` 查询匹配）
- `parent` 用**wikilink**格式（供 Breadcrumbs 建立层级关系）
- 两者指向同一个章节页面，但格式绝不可混用。

### 模板类型对照

| 模板 | 适用场景 | category |
|------|----------|----------|
| `概念.md` | 定义、性质类的知识点 | `概念` |
| `定理.md` | 定理陈述与证明 | `定理` |
| `算法.md` | 算法描述、伪代码、复杂度 | `算法` |
| `问题.md` | 经典问题描述与解法 | `问题` |

### Wikilink 使用规范

- 概念间引用使用 `[[概念名]]` 语法。
- 嵌入图片使用 `![[文件名.png]]` 语法。
- 链接到特定章节使用 `[[页面名#标题]]`。
- 由于 `alwaysUpdateLinks: true` 已开启，重命名文件时 Obsidian 会自动更新所有 wikilink。

---

## Dataview 查询

多个页面底部嵌入了 `dataview` 代码块，用于自动生成索引表格。常用模式：

**章级概念索引**（每个章 MOC 底部）：
```dataview
TABLE category, file.inlinks AS "被引用"
FROM "wiki"
WHERE chapter = "第X章 XXX"
SORT category ASC, file.name ASC
```

**全局分类统计**（`index.md`）：
```dataview
TABLE length(rows) AS "概念数"
FROM "wiki"
GROUP BY category AS "类别"
SORT length(rows) DESC
```

**主题汇总**（`MOC-算法.md`、`MOC-定理.md`）：
```dataview
TABLE chapter AS "所属章节", file.inlinks AS "被引用"
FROM "wiki"
WHERE category = "算法"
SORT chapter ASC, file.name ASC
```

> 修改 YAML frontmatter 后，若 Dataview 表格未刷新，在 Obsidian 中按 `Ctrl+P` → `Dataview: Force Refresh All Views and Blocks`。

---

## 图片与附件管理

- 插件 **Obsidian Custom Attachment Location** 已配置为将粘贴的图片自动存入 `raw/images/${noteFilePath}`。
- 图片文件名由插件按时间戳自动生成（如 `file-20260421141058690.png`）。
- 在笔记中引用图片使用 `![[file-xxx.png]]` 语法。
- 课程原始 PPT 存放于 `raw/ppt/`，不应被笔记直接嵌入，仅作参考源。

---

## CSS 片段

仓库已启用自适应行宽 CSS 片段（`.obsidian/snippets/adaptive-width.css`），用于优化阅读视图体验：
- 覆盖 Obsidian 默认的窄行宽限制（`--file-line-width`）
- 让阅读视图和编辑器在宽屏下占满可用空间
- 表格自动撑满容器宽度

如需调整行宽，修改 `padding-left/right` 的值即可。

---

## 编辑工作流与注意事项

### 新建笔记的标准流程

1. 在 `wiki/` 目录下新建文件，**文件名即概念名**（不要带 `.md` 后缀思考）。
2. 使用 `templates/` 中对应模板插入 frontmatter 与正文框架。
3. 填写 `chapter` 字段为完整章名（纯字符串）。
4. 填写 `parent` 字段为 `"[[第X章 XXX]]"`（wikilink 格式）。
5. 填写 `category`、`tags`、`aliases`、`related`。
6. 补充定义、证明、算法步骤等内容。
7. 在正文中通过 `[[wikilink]]` 建立与其他概念的双向关联。
8. 保存后，Obsidian 会自动更新图谱与 Dataview 索引。

### 修改现有笔记

- 保持原有 frontmatter 字段完整，不要删除 `chapter` 或 `parent`。
- 若重命名文件，Obsidian 会自动更新所有 wikilink（因为 `alwaysUpdateLinks: true`）。
- 若移动文件到不同目录，检查 `parent` 与 `chapter` 是否仍正确。

### Graph View 颜色组维护

全局图与子图的颜色组存储在 `.obsidian/graph.json` 中：
- `colorGroups` — 全局图颜色组
- `localGraph.colorGroups` — 子图颜色组

修改时请保持两者同步，避免全局图与子图颜色不一致。

### Git 提交

- `.gitignore` 已排除 `.obsidian/workspace.json`、`.claudian/sessions/`、OS 临时文件。
- 插件二进制文件（`.obsidian/plugins/*/main.js`）已纳入版本控制，以便克隆后开箱即用。
- CSS 片段（`.obsidian/snippets/`）建议纳入版本控制，确保多端同步。
- 提交信息建议使用中文，描述修改的章节或概念范围。

---

## 外部参考文档

仓库内已包含以下设计文档，可供深入理解架构时参考：

- `.claudian/graph-theory-kb-design.md` — 知识库初始结构设计
- `.claudian/plugin-config-guide.md` — Dataview 与 Breadcrumbs 详细配置指南
- `templates/使用说明.md` — 模板变量与 YAML 字段速查

---

## 对 AI 助手的特别说明

1. **不要假设这是软件项目**：没有编译、测试、包管理器。所有修改都是 Markdown 内容编辑。
2. **保持中文**：所有笔记、注释、提交信息均使用中文。
3. **尊重 frontmatter**：新建或修改笔记时，必须维持 YAML 字段的完整性与正确格式。
4. **慎用全局替换**：wikilink 和 frontmatter 字段值（尤其是 `chapter`）必须精确匹配（包括空格），全局替换容易破坏 Dataview 查询。
5. **公式支持**：笔记中大量使用 LaTeX 数学公式（`$...$` 与 `$$...$$`），编辑时保留其语法。
6. **文件命名**：`wiki/` 下的文件名直接决定其在 wikilink 中的显示名称，命名应简洁、准确、无歧义。
7. **图片路径**：粘贴图片时会自动存入 `raw/images/${noteFilePath}/`，引用时直接使用图片文件名即可（Obsidian 会自动解析路径）。
