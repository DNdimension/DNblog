---
title: contest2267
categories:
  - CodeDrill
  - cf
date: 2026-11-13 20:11:19
tags:
---

> 26.11.10
# C
又被数学题拿捏了  
注意不要写O(TV)，会TLE  
## solution1
（特判x后）枚举x的因数，计算最大贡献，时间O(n$\sqrt{V}$)  
## solution2
预处理每个数的所有质因数（1e9内一个数的质因数不超过9种），时间O(wn)

> 26.11.13
# D
依旧惊人注意力才能发现的性质  
