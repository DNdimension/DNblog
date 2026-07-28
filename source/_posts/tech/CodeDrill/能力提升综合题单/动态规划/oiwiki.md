---
title: 阅读oiwiki_dp部分
categories:
  - tech
  - CodeDrill
  - 能力提升综合题单
  - 动态规划
date: 2026-07-27 18:23:02
tags:
---
# 递推vs递归的记忆化搜索
递推记录的值是当前状态之前的，递归的记忆化数组记录的值是当前状态之后的  

# STL二分查找
主要是lower_bound(),upper_bound()两个函数  
## 参数格式
lower_bound(begin,end,val[,cmp]) 返回值:存在val?val_addr:last  
upper_bound同理  
## 定义
默认情况下，对于一个从小到大排序的序列  
lower_bound:第一个不小于val的数的地址  
upper_bound:第一个大于val的数的地址  
## 直观理解
若序列中val重复多次，区间[lower,upper)包含所有val
## 传入cmp时
lower_bound:[](const T& element,int val) {element_val < val}  
当cmp为false时停止  
upper_bound:[](int val,const T& element) {val < element_val}
当cmp为true时停止  
此时仍有直观理解的结论  
