---
title: 装win11-linux mint双系统
categories:
  - tech
  - 操作系统
date: 2026-08-15 19:05:48
tags:
---

MBR  
GPT  
UEFI  
CSM  

关闭windows快速启动  
创建linux分区时不小心把C盘挂载弄掉了，以为要重装win11，结果回windows输入bitlocker密钥后又能正常进windows了  
一般先装好windows再装linux，因为windows会顶掉linux的grub界面，再配置非常麻烦。而通过grub界面也可以进入windows boot manager  
于是返回去装linux，UEFI模式的电脑需要创建EFI System Partition，与其他分区的详情如下  

|分区|大小(MB)|类型|位置|挂载点|用途|
|:----:|:----:|:----:|:----:|:----:|:----:|
|EFI分区|128-512|主分区|起始|若为FAT32则/boot/efi|EFI系统分区|
|根分区|20480+|主分区|起始|/|EXT4日志文件系统|
|交换分区|同运行内存|逻辑分区|起始| |交换空间|
|家分区| |逻辑分区|起始|/home|EXT4日志文件系统|

EFI,根,交换分区最好放在SSD上，家分区可以放在HDD上  
分区完成后走流程完成安装  
安装完成后启动会有grub界面，可以选择启动linux mint或win11  
这里回去看windows,又要数bitlocker密钥，索性直接解除了bitlocker。解到D盘的时候似乎卡住了，用chkdsk检查，居然会提示考虑卸载盘，稍不留神数据就会没。用命令行操作bitlocker解锁  

{% codeblock bat lang:bat %}
manage-bde -status D:  ::查看解密状态
manage-bde -pause D:  ::暂停解密工作
manage-bde -resume D:  ::恢复解密工作
{% endcodeblock %}

解除bitlocker之后进windows就方便多了  
返回linux mint，设置了主题和字号，图标大小。字号通过dpi调整，面板的高度和图标大小都可以通过首选项调整，右键桌面空白区域即可设置桌面图标大小  
设置快照，可以放在home分区中  
默认使用firefox浏览器，访问体验还行  
可以在软件管理器通过交互界面安装软件，先装了个vlc。后面通过deb包装了vscode。这里想部署博客，用apt装了个npm，结果发现版本很低。彻底删除软件包比较麻烦  
  
{% codeblock bash lang:bash %}
sudo apt purge nodejs npm #删除软件包  
sudo apt autoremove #清除依赖  
sudo apt autoclean  
sudo rm -rf /usr/local/lib/node_modules #清除全局npm包  
{% endcodeblock %}

通过nodejs官网下载了nodejs  
更新博客还需要配置git，先配置name和email，然后设置ssh key  

{% codeblock bash lang:bash %}
ssh-keygen -t ed25519 -C "email" #生成密钥  
cat ~/.ssh/id_ed25519.pub #查看公钥，放在github ssh keys中  
ssh -T git@github.com #测试  
{% endcodeblock %}

这里ed25519表示一种椭圆曲线加密算法  
随后clone博客到本地，安装hexo-cli和packages中的npm包，即可更新  


