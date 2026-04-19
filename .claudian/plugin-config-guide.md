# Dataview & Breadcrumbs 插件配置指南

## 配置概述

本知识库已预配置两个核心插件，分别负责**动态查询**和**层级导航**。

| 插件 | 功能 | 配置状态 |
|------|------|----------|
| **Dataview** | 基于 YAML 动态生成表格/列表 | ✅ 已配置 |
| **Breadcrumbs** | 页面顶部面包屑导航 | ✅ 已配置 |

---

## Dataview

### 已完成的配置

- **空结果警告**：已关闭（`warnOnEmptyResult: false`）
- **自动刷新**：开启（每 2500ms 刷新）
- **内联查询**：支持 `=` 前缀和 `$=` 前缀的 JS 查询

### 工作原理

Dataview 读取所有 Markdown 文件的 **YAML frontmatter**，根据字段值筛选和排序，渲染为表格或列表。

### 现有查询示例

#### 1. 章 MOC 中的本章概念索引

每个章 MOC 页面底部已嵌入：

```dataview
TABLE category, file.inlinks AS "被引用"
FROM "wiki"
WHERE chapter = "第1章 图的基本概念"
SORT category ASC, file.name ASC
```

**效果**：自动列出 `wiki/` 目录下所有 `chapter = 第1章 图的基本概念` 的页面，按类别和名称排序。

#### 2. 总索引页知识库统计

```dataview
TABLE length(rows) AS "概念数"
FROM "wiki"
GROUP BY category AS "类别"
SORT length(rows) DESC
```

**效果**：按 category 分组统计，显示每类概念的数量。

#### 3. 算法汇总页自动索引

```dataview
TABLE chapter AS "所属章节", file.inlinks AS "被引用"
FROM "wiki"
WHERE category = "算法"
SORT chapter ASC, file.name ASC
```

**效果**：自动提取所有 `category = 算法` 的页面。

### 常用查询语法速查

| 语法 | 含义 |
|------|------|
| `FROM "wiki"` | 从 wiki/ 目录查询 |
| `WHERE chapter = "xxx"` | 筛选 chapter 字段 |
| `WHERE category = "算法"` | 筛选类别 |
| `SORT file.name ASC` | 按文件名升序 |
| `SORT file.mtime DESC` | 按修改时间倒序 |
| `LIMIT 10` | 只显示前 10 条 |
| `GROUP BY category` | 按字段分组 |
| `file.inlinks` | 引用该页面的其他页面 |
| `file.outlinks` | 该页面引用的其他页面 |
| `file.mtime` | 文件修改时间 |

---

## Breadcrumbs

### 已完成的配置

- **层级字段**：`up: ["chapter", "parent"]` — 读取 frontmatter 中的 `chapter` 或 `parent` 字段作为父级
- **显示位置**：笔记正文顶部（notes: true）+ 左侧边栏（ribbon: true）
- **路径格式**：网格视图（grid），默认深度 3
- **隐式关系**：启用传递闭包（如果 A 的 up 是 B，B 的 up 是 C，则 A 也能看到 C）

### 工作原理

Breadcrumbs 读取 frontmatter 中的 `parent` 字段（wikilink 格式），建立页面间的层级关系，在页面顶部渲染面包屑导航。

### 层级结构

```
index（总索引）
├── 第1章 图的基本概念
│   ├── 图
│   ├── 简单图
│   ├── 子图
│   └── ...
├── 第2章 树
│   ├── 树
│   ├── 生成树
│   └── ...
└── ...
```

### 使用方式

1. **面包屑导航**：打开任意概念页，页面顶部自动显示 `index > 第X章 XXX > 概念名`
2. **点击跳转**：点击面包屑中的任意节点可快速跳转
3. **左侧边栏**：点击 Breadcrumbs 图标，展开完整层级树

### 页面中的显示效果

在 `wiki/图.md` 页面顶部，你将看到：

```
index > 第1章 图的基本概念 > 图
```

### 如果面包屑不显示

1. 确认插件已启用（设置 → 社区插件 → Breadcrumbs）
2. 确认页面 frontmatter 中有 `parent: "[[第X章 XXX]]"`
3. 按 `Ctrl+P` → `Breadcrumbs: Rebuild Graph` 重建图关系
4. 重启 Obsidian

---

## 字段对照表

| 字段 | 格式 | 用途 | 插件 |
|------|------|------|------|
| `chapter` | 字符串 `第1章 图的基本概念` | Dataview 筛选 | Dataview |
| `parent` | wikilink `[[第1章 图的基本概念]]` | 层级导航 | Breadcrumbs |
| `category` | 字符串 `概念/算法/定理/问题` | 分类筛选 | Dataview |
| `tags` | 数组 `[图论, 算法]` | 全局标签 | Obsidian |
| `related` | 数组 `[概念A, 概念B]` | 弱关联 | 预留 |
| `aliases` | 数组 `[别名1]` | 页面别名 | Obsidian |

---

## 故障排查

### Dataview 查询显示为空

1. 检查 frontmatter 语法是否正确（YAML 格式）
2. 确认 `chapter` 字段值与查询条件完全匹配（包括空格）
3. 按 `Ctrl+P` → `Dataview: Force Refresh All Views and Blocks`

### Breadcrumbs 显示 "No path found"

1. 确认 `parent` 字段是 wikilink 格式（`[[页面名]]`）
2. 确认 parent 指向的页面真实存在
3. 重建图：`Ctrl+P` → `Breadcrumbs: Rebuild Graph`

### 插件未生效

1. 完全关闭 Obsidian（包括托盘图标）
2. 重新打开
3. 检查设置 → 社区插件 → 是否已启用
