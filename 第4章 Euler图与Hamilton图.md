---
chapter: "第4章 Euler图与Hamilton图"
parent: "[[index]]"
tags: [MOC, 图论]
aliases: [Euler图与Hamilton图]
---

# 第4章 Euler图与Hamilton图

## 本章概览

本章研究图中的两种经典遍历问题：Euler 问题（经过每条边恰好一次）与 Hamilton 问题（经过每个顶点恰好一次）。前者已有完整的判定理论与多项式时间算法，后者则是 NP-complete 问题，仅有若干充分条件与近似算法。

## 核心概念

### Euler图
- [[Euler图]] — 存在 Euler 回路的图
- [[Euler回路]] — 经过每条边恰好一次的闭迹
- [[Euler迹]] — 经过每条边恰好一次的迹（不必闭合）
- [[Fleury算法]] — 求 Euler 回路/迹的算法

### 中国邮递员问题
- [[中国邮递员问题]] — 每条边至少走一遍的最短闭途径

### Hamilton图
- [[Hamilton图]] — 存在 Hamilton 圈的图
- [[Hamilton路]] — 经过每个顶点恰好一次的路
- [[Dirac定理]] — 最小度 $\geq n/2$ 的充分条件
- [[Ore定理]] — 不相邻顶点度数和 $\geq n$ 的充分条件
- [[Chvátal定理]] — 基于度序列的充分条件
- [[度极大非Hamilton图]] — $C_{m,n}$ 图族与极图特征

### 旅行售货员问题
- [[旅行售货员问题]] — 访问每个顶点恰好一次的最短圈（TSP）

## 重要定理
- **Euler图等价定理** — 连通图是欧拉图 $\Leftrightarrow$ 每个点度数为偶数 $\Leftrightarrow$ 边集可划分为边不重的圈（[[Euler图]]）
- **非封闭Euler迹判定** — 连通图有非封闭 Euler 迹 $\Leftrightarrow$ 恰有两个奇度顶点（[[Euler迹]]）
- **Hamilton必要条件** — $G$ 是 H 图 $\Rightarrow$ $\forall S\neq\varnothing, \omega(G-S)\leq|S|$（[[Hamilton图]]）
- **Dirac定理** (1952) — $\delta(G)\geq n/2$ $\Rightarrow$ $G$ 是 H 图（[[Dirac定理]]）
- **Ore定理** (1960) — 不相邻顶点 $d(u)+d(v)\geq n$ $\Rightarrow$ $G$ 是 H 图（[[Ore定理]]）
- **Chvátal定理** (1972) — 基于度序列的充分条件（[[Chvátal定理]]）
- **度极大非H图特征** — 非 H 图必度弱于某个 $C_{m,n}$（[[度极大非Hamilton图]]）
- **最优环游定理** — 中国邮递员问题最优性两条充要条件（[[中国邮递员问题]]）

## 前置知识
- [[第1章 图的基本概念]]
- [[第3章 图的连通度]]

## 后继章节
- [[第5章 匹配与因子分解]]

## 重难点标记
- Euler 图三个等价条件的互证
- Fleury 算法中"非割边优先"的策略
- 中国邮递员问题最优性条件的理解与验证
- Hamilton 必要条件的应用（如彼得森图、删除点判定法）
- Dirac / Ore / Chvátal 三个充分条件的层次关系与证明技巧
- $C_{m,n}$ 图的构造与度极大非 H 图特征
- TSP 边交换技术与近似比分析
- Hamilton 问题的实际应用（老鼠吃奶酪、排座位等问题建模）

## 本章概念索引

```dataview
TABLE category, file.inlinks AS "被引用"
FROM "wiki"
WHERE chapter = "第4章 Euler图与Hamilton图"
SORT category ASC, file.name ASC
```
