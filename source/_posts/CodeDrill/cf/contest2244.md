---
title: contest2244
categories:
  - CodeDrill
  - cf
date: 2026-10-22 16:03:04
tags:
---

# C_StepanAndPermutation
## 概要
给定长度为n的排列和两个数x,y，要求：能swap i,j两个位置上的数当且仅当abs(i-j)==x或y。问能否把原序列变成升序
$n\le 2\cdot 10^5,x+y\le n$  
## 思路
拆分最小操作子，任何移动都可以看成ax+by的位置变化，而若ax+by又可以表示成cz，只要找到最小z即可  
## 问题
没有注意到z就是gcd\(x,y\)，傻乎乎写迭代减法  
没有注意到按升序排列之后的序列就是1,2,...,n，用了一个sort...  
