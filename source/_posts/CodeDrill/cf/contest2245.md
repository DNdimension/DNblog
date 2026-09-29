---
title: contest2245
categories:
  - CodeDrill
  - cf
date: 2026-09-29 21:06:56
tags:
---
# A_WhoWatchesTheWatchPig
注意到
# B_DeleteAndConcatenate
写的时候代码比较冗长  
没有必要模拟整个贪心消去过程。先变换到$c=0$的状态，然后分情况讨论可以发现，对前$max\left \{ p,\left \lceil \frac{n}{2}  \right \rceil  \right \}$个数求和即可。p为正数数量  
# C_MEXOR
A了第一个构造题  
思考后发现不妨令$n \in \left[ 2^p,2^{p+1}-1 \right]$，由于f(n-1)必然是n，先令k=k xor n。若$k<2^p$，直接构造全0+k列即可。若$k>=2^p$，讨论能否用n-1使$k<2^p$，重复上述过程，否则输出NO。显然当$k>=2^{p+1}$输出NO  
