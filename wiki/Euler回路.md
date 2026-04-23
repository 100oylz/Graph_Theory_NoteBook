---
chapter: "第4章 Euler图与Hamilton图"
parent: "[[第4章 Euler图与Hamilton图]]"
category: "概念"
tags:
  - 图论
  - 概念
related:
  - "[[Euler图]]"
  - "[[Euler迹]]"
  - "[[Fleury算法]]"
aliases:
  - Euler闭迹
  - 欧拉回路
---

# Euler回路

> **定义**：经过图 $G$ 的每条边的**闭迹**称为 **Euler 闭迹**，又称为 **Euler 回路**（Euler circuit）。存在 Euler 回路的图称为 [[Euler图]]。

## 性质

- Euler 回路中每条边恰好出现一次。
- 若 $G$ 连通且所有顶点度数为偶数，则 $G$ 必存在 Euler 回路。
- Euler 回路的长度等于图的边数 $m$。
- Euler 回路必然经过图中的每一个非孤立顶点。

## 与 Euler 图的关系

Euler 回路与 Euler 图是紧密关联的概念：
- 存在 Euler 回路的图称为 [[Euler图]]
- 连通图 $G$ 是 Euler 图当且仅当 $G$ 的每个顶点的度数为偶数
- 连通图 $G$ 的边集能划分为边不重的圈的并，当且仅当 $G$ 是 Euler 图

## 相关概念

- [[Euler图]]
- [[Euler迹]]
- [[Fleury算法]]

## 所属章节

[[第4章 Euler图与Hamilton图]]
