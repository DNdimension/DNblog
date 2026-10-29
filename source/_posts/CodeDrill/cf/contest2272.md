---
title: contest2272
categories:
  - CodeDrill
  - cf
date: 2026-10-27 09:04:14
tags:
---
bad game  
# A_MaximizeOneMEX
打暴力都打半天还WA两发，糖丸了  
## 正经解法
令p=n-k+1，只考虑对mex\[p\]有贡献的交换。如果i,j都在\[1,p\]或者都在\[p+1,n\]，不会产生贡献。要使mex\[p\]尽可能大，就要使a\[1..p\]尽量小。那末把a\[1..p\]中最大的和a\[p+1..n\]中最小的交换，考察mex\[p\]的改变  

# B_FrogsJump
依旧没看清楚题目  
不\(hen\)难\(nan\)发现两个事实：
1. 对于两个分处上下行的frog（不一定在同一列），令他们改变行，是可以考虑的scheme  
2. 对于两个左右相邻的frog，令他们交换位置，也是可以考虑的scheme  
因此不妨设第一行frog数更多，那么使用2等效消去第一行的frogs，直到两行frog相差0或者1

# C_YetAnotherBlackCell
赛前写了二分搜索赛时没调出来的屑  
漏了一种考虑情况，以及下次把代码写得简单一点

# D_ConnectTheConflict
看题解优化了一下思路
