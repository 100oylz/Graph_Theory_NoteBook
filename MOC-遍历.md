---
parent: "[[index]]"
tags: [MOC, 图论, 遍历]
aliases: [遍历与环游汇总]
---

# MOC-遍历

> 图论中**遍历问题**的汇总，涵盖 Euler 遍历（经过每条边恰好一次）和 Hamilton 遍历（经过每个顶点恰好一次），以及相关的邮递员问题和旅行售货员问题。

## 概览

遍历问题是图论中最具应用价值的问题类之一。Euler 问题已有完整的多项式时间算法，而 Hamilton 问题是经典的 NP-complete 问题，仅有若干充分条件。

```dataview
TABLE chapter AS "所属章节", category AS "类型", file.inlinks AS "被引用"
FROM "wiki"
WHERE contains([
  "Euler图", "Euler回路", "Euler迹", "Fleury算法",
  "中国邮递员问题",
  "Hamilton图", "Hamilton路", "Dirac定理", "Ore定理", "Chvátal定理",
  "度极大非Hamilton图", "旅行售货员问题"
], file.name)
SORT chapter ASC, category ASC, file.name ASC
```

## 知识地图

```
                遍历问题
                    │
        ┌───────────┼───────────┐
        ▼           ▼           ▼
      Euler      Hamilton      优化版本
        │           │           │
        ├─ 回路     ├─ 圈       ├─ 中国邮递员
        ├─ 迹       ├─ 路       └─ 旅行售货员
        ├─ 判定     ├─ 充分条件
        └─ 算法     └─ 必要条件
```

## Euler 遍历

### 核心概念

| 概念 | 说明 | 考试重点 |
|------|------|---------|
| [[Euler图]] | 存在 Euler 回路的图 | ★★★ |
| [[Euler回路]] | 经过每条边恰好一次的闭迹 | ★★★ |
| [[Euler迹]] | 经过每条边恰好一次的迹（非闭） | ★★★ |
| [[Fleury算法]] | 求 Euler 回路/迹的 $O(m)$ 算法 | ★★★ |

### 判定条件

| 条件 | 内容 | 类型 |
|------|------|------|
| Euler图 | 连通且每个顶点度数为偶数 | 充要条件 |
| 非封闭Euler迹 | 连通且恰有两个奇度顶点 | 充要条件 |

### 等价刻画
- 连通图是 Euler 图 ⟺ 每个点度数为偶数 ⟺ 边集可划分为边不重的圈

## Hamilton 遍历

### 核心概念

| 概念 | 说明 | 考试重点 |
|------|------|---------|
| [[Hamilton图]] | 存在 Hamilton 圈的图 | ★★★ |
| [[Hamilton路]] | 经过每个顶点恰好一次的路 | ★★★ |
| [[Dirac定理]] | $\delta \geq n/2$ ⟹ H 图（1952） | ★★★ |
| [[Ore定理]] | 不相邻 $d(u)+d(v)\geq n$ ⟹ H 图（1960） | ★★★ |
| [[Chvátal定理]] | 基于度序列的闭包条件（1972） | ★★★ |
| [[度极大非Hamilton图]] | $C_{m,n}$ 图族，极图特征 | ★★ |

### 判定条件

| 条件 | 内容 | 类型 |
|------|------|------|
| 必要条件 | $\forall S\neq\varnothing, \omega(G-S)\leq|S|$ | 必要非充分 |
| Dirac | $\delta(G)\geq n/2$ | 充分 |
| Ore | 不相邻顶点 $d(u)+d(v)\geq n$ | 充分 |
| Chvátal | 度序列闭包条件 | 充分 |

## 优化问题

### 核心概念

| 概念 | 说明 | 考试重点 |
|------|------|---------|
| [[中国邮递员问题]] | 每条边至少走一遍的最短闭途径 | ★★★ |
| [[旅行售货员问题]] | 访问每个顶点恰好一次的最短圈（TSP） | ★★★ |

### 中国邮递员问题解法
- 若图为 Euler 图：Euler 回路即为最优解
- 若图非 Euler 图：在奇度顶点间添加重复边，使其变为 Euler 图

### TSP
- NP-hard 问题，无已知多项式时间精确算法
- 近似算法：最近邻、最小生成树+匹配等

## 两种遍历问题的对比

| 特征 | Euler 遍历 | Hamilton 遍历 |
|------|-----------|---------------|
| 遍历对象 | 每条边恰好一次 | 每个顶点恰好一次 |
| 判定复杂度 | P（多项式时间） | NP-complete |
| 算法 | Fleury算法（$O(m)$） | 无多项式时间算法 |
| 充要条件 | 有（度数条件） | 无已知充要条件 |
| 充分条件 | 简单 | Dirac/Ore/Chvátal |
| 应用 | 路线规划、网络检查 | 旅行规划、电路板钻孔 |

## 与特殊图的关联

- **Euler图 ∩ 正则图**：偶数度正则连通图
- **Euler图 ∩ 完全图**：$K_n$（$n$ 为奇数）
- **Hamilton图 ∩ 完全图**：$K_n$（$n\geq 3$）
- **Hamilton图 ∩ 平面图**：可利用 Hamilton 圈简化平面性判定
- **树**：仅 $K_1$ 是 Euler 图；仅 $K_1, K_2$ 有 Hamilton 路

## 与连通性的关联

- Euler 图要求图连通
- Hamilton 图要求 $\kappa \geq 2$（2-连通是必要条件）
- 中国邮递员问题在连通图上求解

## 跨章节索引

```dataview
TABLE chapter AS "章节", category AS "类型"
FROM "wiki"
WHERE contains([
  "Euler图", "Euler回路", "Euler迹", "Fleury算法",
  "中国邮递员问题",
  "Hamilton图", "Hamilton路", "Dirac定理", "Ore定理", "Chvátal定理",
  "度极大非Hamilton图", "旅行售货员问题"
], file.name)
SORT chapter ASC, category ASC, file.name ASC
```
