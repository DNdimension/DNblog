---
title: contest2284
categories:
  - CodeDrill
  - cf
date: 2026-11-09 22:43:28
tags:
---
变成fvv  
# A
中学数学  
# B
显然，但是码力太蒻  
# [C1](https://codeforces.com/contest/2284/problem/C1) 
没有早点确定细究两个数的因数信息是根本不现实的，constructive题目寻求特解  
一开始没有注意到值域只有1e5，以为不能筛  
以及有点忘记线性筛的写法了。。。
最后虽然糊出解法，但是左右脑互博又否掉了，另外写了一个错误解法上去吃罚时  
终于还是被数学卡住。由于gcd(a,b)<=>gcd(b,a-b) (a>b)，反着说，只要把原序列元素弄成p，deltaX就一定和原元素互质。公式反着用就不会了。。。  
# [C2](https://codeforces.com/contest/2284/problem/C2)
雷霆  
想了半天又写了半天，写了个O(Tlog^2^m)的dp  


> $Or\ you\ can\ simply\ guess\ that\ dist(a,b)\le2\ for\ b−a\ge small\ const,\ but\ that\ is\ uninteresting.$
> $In\ fact,\ this\ problem\ in\ its\ general\ formulation\ is\ an\ open\ problem,\ and\ it\ appears\ that\ dist(a,b)\ never\ exceeds\ 3.$
> $If\ you\ discover\ a\ substantive\ proof\ to\ the\ contrary,\ feel\ free\ to\ share\ it\ in\ the\ comments.$
