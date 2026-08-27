---
title: 从零开始的edgeever部署
categories:
  - tech
  - 折腾
date: 2026-08-27 19:05:56
tags:
---

# 概论
[edgeever](https://edgeever.org)是一个平替印象笔记等商业化笔记软件的项目，一个可以自托管的笔记服务，并且有数据导入方便，零成本部署，三栏UI，AI支持等特性  
# 参考文档
[edgeever的手动部署的官方教程](https://github.com/tianma-if/edgeever/blob/main/docs/deploy-cloudflare-button.zh-CN.md)在cloudflare界面更新之后读起来已经有些吃力
# fork仓库
登录github，将[edgeever仓库](https://github.com/tianma-if/edgeever)fork到个人
# cloudflare配置
先注册cloudflare，然后验证账户。邮件中的验证地址没有<u>下划线</u>，带<u>下划线</u>的是文档  
然后创建D1,R2数据库，创建入口不在**Compute**-**Workers & Pages**，而在**Storage & databases**下。创建**R2 Object Storage**需要绑定境外交易方式，这里推荐使用*paypal*。*paypal*的注册相对容易，而且可以绑国内银行卡，如建行卡等，绑卡之前需要先打开卡的境外交易选项。
# 引入edgeever
在**Compute**-**Workers & Pages**中创建应用，选择以github继续，引入fork的edgeever仓库，接着把[官方教程](https://github.com/tianma-if/edgeever/blob/main/docs/deploy-cloudflare-button.zh-CN.md)中的脚本填入**Build command**，**Deploy command**，在Advanced选项中添加变量，name填EDGE_EVER_AUTH_PASSWORD，val填密码，登陆网站时admin的密码即为val。设置完毕点击Deploy，到此部署完成。  
# 优化访问
cloudflare提供了加速服务，如果不能正常访问部署的笔记服务可以考虑采用