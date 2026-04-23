---
chapter: "第4章 Euler图与Hamilton图"
parent: "[[第4章 Euler图与Hamilton图]]"
category: "定理"
tags:
  - 图论
  - 定理
related:
  - "[[Hamilton图]]"
  - "[[Dirac定理]]"
  - "[[Ore定理]]"
  - "[[Hamilton路]]"
aliases:
  - Chvátal's theorem
---
# Chvátal定理

> **定理 (Chvátal, 1972)**：设简单图 $G$ 的度序列是 $(d_1, d_2, \ldots, d_n)$，其中 $d_1 \leq d_2 \leq \ldots \leq d_n$ 且 $n\geq 3$。若对任意的 $k < n/2$，或有 $d_k > k$，或有 $d_{n-k} \geq n-k$，则 $G$ 是 Hamilton 图。

![[file-20260422214920063-Chvátal定理.png]]

## 证明

若不然，设 $G$ 是一个满足定理条件的**极大非 H 图**。

显然，$G$ 不能是完全图。断言：$G$ 中任意两个不相邻的点 $u$ 与 $v$ 均满足 $d(u)+d(v) < n$。

令 $u$ 与 $v$ 是 $G$ 中不相邻且度数之和最大的一对顶点。不妨假设 $k = d(u) \leq d(v)$。因为 $d(u)+d(v) < n$，所以 $k < n/2$。

由于 $d(v) < n-d(u) = n-k$，所以在 $G$ 中至少有 $k$ 个点与 $v$ 不相邻。由 $u$ 与 $v$ 的取法知：在与 $v$ 不相邻的点中，$u$ 的度数最大。因此，在 $G$ 中至少有 $k$ 个点的度不大于 $k$，从而 $d_k \leq k$。

另一方面，由 $k$ 的定义知，在 $G$ 中有 $n-1-k$ 个点与 $u$ 不相邻。在这些点中，$v$ 的度数最大。这意味着：所有与 $u$ 不相邻的 $n-1-k$ 个点的度数均小于等于 $v$ 的度数。由于 $d(v) < n-d(u) = n-k$，以及 $u$ 的度数不超过 $v$ 的度数知，$G$ 中至少有 $n-k$ 个点的度数严格小于 $n-k$，从而 $d_{n-k} < n-k$。

与已知条件矛盾。从而 $G$ 是 H 图。

## 例子

求证下图 $G$ 是 H 图。

在 $G$ 中有 $d_1=d_2=d_3=3, d_4=d_5=5, d_6=6, d_7=7, d_8=d_9=8$。

因 $d_1>1, d_2>2, d_6\geq 6, d_4>4$，$G$ 满足 Chvátal 定理的条件，因此是 H 图。

## 相关概念

- [[Hamilton图]]
- [[Dirac定理]]
- [[Ore定理]]
- [[Hamilton路]]

## 所属章节

[[第4章 Euler图与Hamilton图]]
