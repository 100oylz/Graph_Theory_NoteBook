---
chapter: "第7章 图的着色"
parent: "[[第7章 图的着色]]"
category: "定理"
tags:
  - 图论
  - 定理
related:
  - "[[色数]]"
  - "[[图的点着色]]"
  - "[[次大度]]"
aliases:
  - Brooks' Theorem
---

# Brooks定理

> **定理陈述**（Brooks, 1941）：设 $G$ 是简单连通图。假定 $G$ 既不是完全图又不是奇圈，则
> $$\chi(G) \leq \Delta(G)$$

![[file-20260423113759001-Brooks定理陈述.png]]

## 形式化表述

Brooks 定理是对平凡上界 $\chi \leq \Delta + 1$ 的重要改进。它指出：对于绝大多数连通简单图，色数不超过最大度。

**等号成立的情况**：
- 完全图 $K_n$：$\chi(K_n) = n = \Delta(K_n) + 1$
- 奇圈 $C_{2k+1}$：$\chi(C_{2k+1}) = 3 = \Delta(C_{2k+1}) + 1$

这两种图是 Brooks 定理中排除的例外情形。

## 证明思路

证明中引入了**次大度** $\Delta_2(G)$ 的概念：

令 $V_2(G) = \{v \mid v \in V(G),\ N(v)\text{ 中存在点 }u\text{ 满足 }d(u) \geq d(v)\}$

定义
$$\Delta_2(G) \triangleq \max\{d(v) \mid v \in V_2(G)\}$$

简记为 $\Delta_2$。显然 $\Delta_2(G) \leq \Delta(G)$，称 $\Delta_2(G)$ 为 $G$ 的次大度。

详细证明通过分析图的连通性、最大度点的分布以及次大度的性质完成。

## 推论

对于连通简单图 $G$：
- 若 $G$ 不是完全图也不是奇圈，则 $\chi(G) \leq \Delta(G)$
- 若 $G$ 还是非正则图，则 $\chi(G) \leq \Delta_2(G) \leq \Delta(G) - 1$

## 相关概念

- [[色数]] — 正常顶点着色的最少颜色数
- [[次大度]] — $\Delta_2(G)$，与 Brooks 定理证明密切相关的参数
- [[图的点着色]] — 正常顶点着色的定义

## 所属章节

[[第7章 图的着色]]
