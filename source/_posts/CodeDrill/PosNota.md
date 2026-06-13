---
title: PosNota
date: 2026-06-13 11:19:17
tags: CodeDrill
mathjax: true
---

从 [提高第一题](https://www.luogu.com.cn/training/318391#problems) 开始复健，第一题进制转换以前没做过，遂尝试做出来。  
一看是负进制数，便有些手足无措。先是对着负二进制想了半天，仍然没什么理解，没有意识到直接从幂级数理解，套用辗转相除法即可。  
过了一个半小时还是蒙，于是转向十进制转正整数进制的常规题目，秒切。看题解发现构造类似下面的字符串可直接利用余数为索引，比ascii＋余数的方法更成系统。
{% codeblock lang:cpp line_number:false %}  
"0123...89ABCD..."
{% endcodeblock %}
随后意识到仍然可以使用辗转相除，但此时以为由于是负基数，除数的正负也需要交替。这样写出来发现过不了第一个样例，随后把-16进制样例（较短）以幂级数展开书写，模拟过程，才发现除数一直就是负的基数。  
后面又被涉及负数的取模问题卡了一会。在辗转相除时需要余数为正，但cpp的%运算得出的是绝对值最小的余数。  
$$
\begin{aligned}
    k &= pR+r \\
    k &\equiv r \mod R \\
    -k &\equiv -r \mod R \\
    -k &\equiv R-r \mod R
\end{aligned}
$$  

判别并操作后过了  