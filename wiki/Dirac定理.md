---
chapter: "第4章 Euler图与Hamilton图"
parent: "[[第4章 Euler图与Hamilton图]]"
category: "定理"
tags:
  - 图论
  - 定理
related:
  - "[[Hamilton图]]"
  - "[[Ore定理]]"
  - "[[Chvátal定理]]"
aliases:
  - Dirac's theorem
---

# Dirac定理

> **定理 (Dirac, 1952)**：对于 $n$ 阶 $(n\geq 3)$ 简单图 $G$，如果
> $$\delta(G) \geq \frac{n}{2}$$
> 那么 $G$ 是 Hamilton 图。

![[file-20260422214920056-Dirac定理.png]]

## 证明

若不然，设 $G$ 是一个满足定理条件的**极大非 H 图**。

显然 $G$ 不能是完全图，否则 $G$ 是 H 图。于是，可以在 $G$ 中任意取两个不相邻顶点 $u$ 与 $v$。考虑图 $G+uv$，由 $G$ 的极大性知：$G+uv$ 是 H 图。由于 $G$ 是非 H 图，$G+uv$ 的每一个 H 圈必然包含边 $uv$。所以，在 $G$ 中存在起点为 $u$ 而终点为 $v$ 的 H 路 $P$。

不失一般性，设 $P = v_1 v_2 \ldots v_n$，其中 $v_1 = u, v_n = v$。令
$$S = \{v_i \mid v_1 v_{i+1} \in E(G)\}, \quad T = \{v_j \mid v_j v_n \in E(G)\}$$

对于 $S$ 与 $T$，显然 $v_n \notin S \cup T$，所以 $|S \cup T| < n$。

另一方面，必有 $S \cap T = \varnothing$。否则，设 $v_i \in S \cap T$，那么由 $v_i \in S$ 可以推出 $v_1 v_{i+1} \in E(G)$；由 $v_i \in T$ 可以推出 $v_n v_i \in E(G)$。因此，可以在 $G$ 中得到 H 圈，与假设矛盾！

于是
$$d(u) + d(v) = |S| + |T| = |S \cup T| + |S \cap T| < n$$

这与已知条件"$\delta(G) \geq n/2$"矛盾！

## 说明

- Dirac 定理是 Hamilton 图的一个经典充分条件。
- 该条件仅为充分条件，而非必要条件。例如，$C_5$（5-圈）是 H 图，但 $\delta(C_5) = 2 < 5/2$。

## 相关概念

- [[Hamilton图]]
- [[Ore定理]]
- [[Chvátal定理]]

## 所属章节

[[第4章 Euler图与Hamilton图]]
