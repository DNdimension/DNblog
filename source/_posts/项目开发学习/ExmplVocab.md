---
title: ExmplVocab
categories:
  - 项目开发学习
date: 2026-10-23 10:59:59
tags:
---
# 26.10.23
## 项目定位
ExmplVocab是一个cli应用，帮助通过句子翻译训练来学习和记忆词汇  
本地通过json文件存词汇和例句表，用户可以自行添加，也可以通过eudic摘录例句  
## 项目依赖
通过vcpkg管理项目依赖。vcpkg类似npm,pip，是cpp的包管理器  
### vcpkg的安装和配置
1. 从github下载，`git clone https://github.com/microsoft/vcpkg.git`  
2. 执行`bootstrap-vcpkg.bat`
3. 配置环境变量，`setx VCPKG_ROOT "...\vcpkg"`，`setx PATH "%VCPKG_ROOT%;%PATH%"`
### vcpkg包的存储
1. 全局包，存储在`%VCPKG_ROOT%\installed\`
2. 项目包，在项目根目录创建`vcpkg.json`，写入
```json
{
  "name": "",
  "version": "x.x.x",
  "dependencies": [
    
  ]
}
```

# 26.10.24  
## 环境配置
使用vscode\+vs build tools  
### build tools安装
安装程序类似python安装过程，本身也是包管理器  
### vscode联动
在x64的开发人员命令行中使用code \<path\>  
将命令行快捷方式复制到项目目录，在属性\-快捷方式\-目标 一栏中程序启动之前添加cd到项目目录的目录，这样就可以在项目目录启动cmd，直接输入code .就可以进入vscode
### 几个配置文件
+ `vcpkg.json` 
声明项目需要的依赖，注意name只能包含小写字母和\-
指定vcpkg的版本基线的hash
+ `CMakePresets.json`
指定构建系统生成器(本项目为Ninja)，架构和传递给CMake的变量
+ `.vscode/settings.json`
与Presets的Ninja项对应，指定`ninja.exe`的位置  
### 构建流程  
下面的命令都是vscode命令  
首先使用CMake:Select Configure Presets选定`CMakePresets.json`中声明的配置  
然后使用CMake:Configure进行配置。配置中会需要从github releases中下载一些包，如果网络不畅可以手动下载，放到对应目录。如果多次配置，可能需要删除之前生成的build目录防止干扰  
最后使用CMake:Build(或者按F7)进行生成  
## 命令行字体
有的时候默认的命令行字体不能显示中文，需要在默认值中修改字体，可以改成NSimSun等支持中文的字体
