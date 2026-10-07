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
# D_ConstructAnArray
## vEasy
根据不等式关系建图，有点像差分约束  
写着写着漏掉了一种情况，导致以为图是二分图。。。  
用拓扑排序找出不等式的依赖关系，用拓扑序给节点赋值即可  
## vHard
本来以为要用SCC做，发现可以依据两类d进行拓扑排序  
若包含$a_i$的不等关系不等号方向一致，则$a_i$的绝对值极大。确定$a_i$之后可以给其他$a_j$删去含$a_i$的不等关系，重复上述操作即可  
