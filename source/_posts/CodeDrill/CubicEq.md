---
title: CubicEq
date: 2026-06-13 16:54:48
tags: CodeDrill
---
尝试了二分，割线两种做法。割线+递归居然T了。  
宏定义传参要加括号，因为基于类似字符匹配的机制。浮点数判断大小用eps，直接比可能会寄。  
小数点后精度设置  
{% codeblock C++风格 lang:cpp line_number:false %}
#include <iomanip>
...
cout<<fixed<<setprecision(n)<<...;
{% endcodeblock %}
或者 
{% codeblock C风格 lang:c line_number:false %}
int p = n;
double k=...;
printf("%.*f",p,k);
{% endcodeblock %}