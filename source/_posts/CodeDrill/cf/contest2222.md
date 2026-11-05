---
title: contest2222
categories:
  - CodeDrill
  - cf
date: 2026-11-03 20:12:11
tags:
---

# D_PermuConstru  
用前缀和考虑（反正总是要用到的），\(i,j\)逆序对的val即是pre[j-1]-pre[i-1]，因此只要pre[j-1]尽量大，j就可以尽量小。i同理  
