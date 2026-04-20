# 图论知识库结构设计

## 日期
2026-04-19

## 目标
构建基于 Obsidian 的关系图谱知识库，参考 Karpathy LLM Wiki 模式，组织图论课程内容。

## 目录结构

```
Graph_Theory/
├── raw/ppt/                    # 原始PPT（不变）
├── wiki/                       # 概念原子页面（~45页）
├── 第1章 图的基本概念.md        # 章级MOC
├── 第2章 树.md
├── 第3章 图的连通度.md
├── 第4章 Euler图与Hamilton图.md
├── 第5章 匹配与因子分解.md
├── 第6章 平面图.md
├── 第7章 图的着色.md
├── 第9章 有向图.md
├── MOC-算法.md                 # 跨章主题MOC
├── MOC-定理.md
└── index.md                    # 总入口
```

## 页面模板

### 概念页 (wiki/*.md)
```yaml
---
chapter: "第1章"
category: "概念"  # 概念/算法/定理/问题
tags: [图论]
related: []
---
# 概念名

> 定义：（待补充）

## 性质
（待补充）

## 相关概念
（待补充）

## 所属章节
（待补充）
```

### 章MOC (第X章 XXX.md)
```yaml
---
chapter: "第1章"
tags: [MOC, 图论]
---
# 第X章 XXX

## 本章概念
- [[概念1]]
- [[概念2]]

## 前置知识
- [[前置章节]]

## 后继章节
- [[后继章节]]
```

## 链接策略
- 章MOC → 本章所有概念页
- 概念页 → 所属章MOC
- 跨章关联通过 `related` 和正文 wikilink 预留

## 推荐插件
- Dataview（动态查询）
- Breadcrumbs（层级面包屑）
- Graph Analysis（增强图谱）
