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
  - "[[Chvátal定理]]"
aliases:
  - Ore's theorem
---
# Ore定理

> **定理 (Ore, 1960)**：对于 $n$ 阶 $(n\geq 3)$ 简单图 $G$，如果 $G$ 中任意两个不相邻顶点 $u$ 与 $v$ 满足：
> $$d(u) + d(v) \geq n$$
> 那么 $G$ 是 Hamilton 图。

![[file-20260422214920060-Ore定理.png]]

## 说明

1. 该定理证明和 [[Dirac定理]] 完全类似。
2. 该定理中的条件仅为充分条件，而非必要条件。
3. 该定理的条件是**紧的**（tight）。

## 紧性例子

设 $G$ 是由 $K_{l+1}$ 的一个顶点和另一个 $K_{l+1}$ 的一个顶点重合得到的图，那么对于 $G$ 的任意两个不相邻顶点 $u$ 与 $v$，显然有 $d(u)+d(v)=2l=n-1$，但 $G$ 不是 Hamilton 图。

## 与Dirac定理的关系

- Ore 定理推广了 Dirac 定理：若 $\delta(G) \geq n/2$，则对任意不相邻顶点 $u, v$，有 $d(u)+d(v) \geq n$，满足 Ore 定理条件。
- 因此，Dirac 定理是 Ore 定理的特例。

## 相关概念

- [[Hamilton图]]
- [[Dirac定理]]
- [[Chvátal定理]]

## 所属章节

[[第4章 Euler图与Hamilton图]]
