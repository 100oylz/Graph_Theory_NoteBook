# 图论知识库

> 基于电子科技大学图论课程的关系图谱知识库，参考 Karpathy LLM Wiki 模式构建。

## 快速开始

1. **打开总索引**：进入 [[index]] 查看课程全貌
2. **选择章节**：点击任意章 MOC（如 [[第1章 图的基本概念]]）
3. **浏览概念**：在章 MOC 底部查看自动生成的本章概念索引
4. **查看图谱**：按 `Ctrl+G` 打开 Graph View 浏览知识网络

## 目录结构

```
Graph_Theory/
├── raw/ppt/                    # 原始课件（PPT，不变）
├── wiki/                       # 概念原子页面（~60页）
│   ├── 图.md
│   ├── 树.md
│   ├── Kruskal算法.md
│   └── ...
├── templates/                  # 页面模板
│   ├── 概念.md
│   ├── 算法.md
│   ├── 定理.md
│   ├── 问题.md
│   └── 使用说明.md
├── 第1章 图的基本概念.md      # 章级 MOC
├── 第2章 树.md
├── ...
├── 第9章 有向图.md
├── MOC-算法.md                 # 跨章主题汇总
├── MOC-定理.md
├── index.md                    # 总入口
└── .claudian/                  # 配置与文档
    ├── graph-theory-kb-design.md
    └── plugin-config-guide.md
```

## 依赖插件

| 插件 | 用途 | 安装状态 |
|------|------|----------|
| **Dataview** | 动态查询与表格 | 已预配置 |
| **Breadcrumbs** | 层级面包屑导航 | 已预配置 |
| **Quick Latex** | LaTeX 快捷输入 | 已预配置 |
| **Templater**（可选） | 模板变量替换 | 推荐安装 |

> 安装方式：将 `.obsidian/plugins/` 中的插件文件夹复制到目标 vault 的相同位置，或从社区插件市场搜索安装。

## 快捷键速查

### 格式

| 快捷键 | 功能 |
|--------|------|
| `Ctrl+Shift+1~6` | 标题 H1~H6 |
| `Ctrl+B` | **粗体** |
| `Ctrl+I` | *斜体* |
| `Alt+Shift+5` | ~~删除线~~ |
| `Ctrl+Shift+H` | ==高亮== |

### 块级元素

| 快捷键 | 功能 |
|--------|------|
| `Ctrl+Shift+Q` | 引用块 `>` |
| `Ctrl+Shift+K` | 代码块 ` ``` ` |
| `Ctrl+M` | 行内公式 `$...$`（Quick Latex） |
| `Ctrl+Shift+M` | 块级公式 `$$...$$` |
| `Ctrl+Shift+T` | 插入表格 |
| `Ctrl+Alt+I` | 插入图片 |
| `Ctrl+Shift+L` | 无序列表 `-` |
| `Ctrl+Shift+O` | 有序列表 `1.` |
| `Ctrl+Shift+X` | 任务列表 `- [ ]` |

### 编辑

| 快捷键 | 功能 |
|--------|------|
| `Ctrl+/` | 切换源码模式 |
| `Ctrl+G` | 打开 Graph View |
| `Ctrl+P` | 命令面板 |

## YAML 字段规范

每个 wiki 页面的 frontmatter 必须包含以下字段：

```yaml
---
chapter: "第1章 图的基本概念"    # Dataview 筛选用（纯字符串）
parent: "[[第1章 图的基本概念]]" # Breadcrumbs 导航用（wikilink）
category: "概念"                 # 分类：概念/算法/定理/问题
tags: [图论]                     # Obsidian 标签
related: []                      # 弱关联概念（可选）
aliases: []                      # 别名（可选）
---
```

| 字段 | 格式 | 用途 |
|------|------|------|
| `chapter` | 字符串 | Dataview 按章筛选 |
| `parent` | wikilink | Breadcrumbs 层级导航 |
| `category` | 字符串 | 知识类型分类 |
| `tags` | 数组 | 全局标签检索 |
| `related` | 数组 | 弱关联关系预留 |
| `aliases` | 数组 | 多名称引用 |

## 模板使用

1. 在 `wiki/` 下新建文件（文件名即概念名）
2. 根据概念类型复制对应模板：
   - `templates/概念.md` — 定义、性质类
   - `templates/算法.md` — 算法步骤、复杂度
   - `templates/定理.md` — 定理与证明
   - `templates/问题.md` — 经典问题描述
3. 填写 `chapter` 和 `parent` 字段
4. 补充内容，在相关概念区添加 `[[wikilink]]`

## 知识库层级

```
index（总索引）
├── 第1章 图的基本概念
│   ├── 图
│   ├── 简单图
│   ├── 最短路算法
│   └── ...
├── 第2章 树
│   ├── 树
│   ├── 生成树
│   └── ...
└── ...
```

- **index** → 所有章 MOC 的 parent
- **章 MOC** → 本章所有概念页的 parent
- 概念页 → 通过 `[[wikilink]]` 横向关联

## Dataview 查询示例

每个章 MOC 底部已预置自动索引：

```dataview
TABLE category, file.inlinks AS "被引用"
FROM "wiki"
WHERE chapter = "第1章 图的基本概念"
SORT category ASC, file.name ASC
```

在 `index.md` 和 `MOC-算法.md` 中也有统计类查询，新增页面后自动更新。

## 常见问题

**Q: Dataview 表格显示为空？**
A: 检查 frontmatter 的 `chapter` 字段是否与查询条件完全匹配（包括空格）。

**Q: Breadcrumbs 显示 "No path found"？**
A: 确认 `parent` 字段是 wikilink 格式（`[[页面名]]`），且目标页面存在。

**Q: 快捷键不生效？**
A: 完全关闭 Obsidian（包括系统托盘）后重新打开。

**Q: 如何添加跨章关联？**
A: 在概念页正文中添加 `[[其他概念]]` 链接，或在 `related` 字段中填写关联文件名。

---

*配置文档详见 `.claudian/plugin-config-guide.md`*
