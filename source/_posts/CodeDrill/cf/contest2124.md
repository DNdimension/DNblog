---
title: contest2124
categories:
  - CodeDrill
  - cf
date: 2026-10-29 20:51:14
tags:
---

# [D_Palindrome](https://codeforces.com/contest/2124/problem/D)
力竭了也没想出来  
首先考虑单调性，发现随区间扩增，小于t的数的数量是单调增的。只要全局小于t的数不少于k-1，就可删t  
因此可将原序列中第k小的数设为x。若可以形成回文序列，则回文序列必然有长度为k-1的回文字串，且字串必由前k-1个小的数组成。因此可以不考虑原序列前n-x个大的数  
小于等于x的数的序列产生回文的过程中，只有x是能删的。若失配且无x可删，则NO  