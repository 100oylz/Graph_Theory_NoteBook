---
parent: "[[index]]"
tags: [MOC, 图论, 算法]
aliases: [算法汇总]
---

# MOC-算法

> 图论课程中涉及的所有算法汇总页面。

## 第1章 图的基本概念
- [[最短路算法]] — 求解图中两点间最短路径

## 第2章 树
- [[Kruskal算法]] — 最小生成树的贪心算法
- [[Prim算法]] — 最小生成树的另一贪心算法

## 第5章 匹配与因子分解
- [[匈牙利算法]] — 求解偶图最大匹配
- [[Kuhn-Munkres算法]] — 求解赋权完全偶图最优匹配

## 第6章 平面图
- [[平面性算法]] — 判定图是否为平面图（DMP 算法）
- [[哈密尔顿图的平面性判定]] — 利用哈密尔顿圈判定平面性

## 算法对比
（待补充：各算法的时间复杂度、适用场景、优缺点对比）

## 自动索引

```dataview
TABLE chapter AS "所属章节", file.inlinks AS "被引用"
FROM "wiki"
WHERE category = "算法"
SORT chapter ASC, file.name ASC
```
