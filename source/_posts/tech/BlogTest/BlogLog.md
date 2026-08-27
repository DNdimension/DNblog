---
title: BlogLog
tags: test
categories:
  - tech
  - BlogTest
date: 2026-06-18 11:11:25
---
# 26.6.18
打算记录博客创建的历程与得到的经验  
## 回想26.6.12
博客创立，使用hexo+github actions&&pages  
### 初始化hexo
{% codeblock bash lang:bash %}
npm install -g hexo-cli
hexo init ./DNblog
cd DNblog
npm install
{% endcodeblock %}
### 配置路由
在根目录_config.yml添加字段：  
{% codeblock _config.yml lang:yaml %}
url: https://dndimension.github.io/DNblog
root: /DNblog/
{% endcodeblock %}
这里其实可以把其他可见的介绍信息也改了  
### 初始化git
{% codeblock bash lang:bash %}
git init
git remote add origin https://github.com/DNdimension/DNblog.git
git add .
git commit -m "初始提交"
git branch -M main
git push -u origin main
{% endcodeblock %}
不要把node_modules文件夹和public文件夹放到缓冲区  
应该是由于在电脑上操作了第二行命令，后续提交不需要token之类的东西。后来尝试在手机上更新时就需要token  
### 配置github actions工作流
配置是AI给的，给的时候没有permisssion相关，之前部署rss也出现过类似问题  
{% codeblock .github/workflows/deploy.yml lang:yaml %}
name: Deploy Hexo to GitHub Pages

on:
  push:
    branches:
      - main  # 当推送到 main 分支时触发


permissions:
  contents: write

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout 代码
        uses: actions/checkout@v4

      - name: 安装 Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'   # 和你本地版本接近即可

      - name: 安装 Hexo 依赖
        run: |
          npm install

      - name: 生成静态文件
        run: |
          npm run build   # 或者 hexo generate，但需要在 package.json 里定义
        # 或者在步骤中直接执行 hexo generate
        # 如果没有 package.json 脚本，可以用 npx hexo generate

      - name: 部署到 gh-pages 分支
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
          publish_branch: gh-pages   # 推送到 gh-pages 分支
          force_orphan: true
{% endcodeblock %}
### 配置github pages
在这里又被卡了一下，在repo-settings-pages中，选择source:deploy from branch后，应使用gh-pages分支，而非main  
### 后续更新
创建post：  
{% codeblock bash lang:bash %}
hexo new <name>
{% endcodeblock %}
或者指定创建路径：  
{% codeblock bash lang:bash %}
hexo new -p path/name 
{% endcodeblock %}
预览：  
{% codeblock bash lang:bash %}
hexo clean
hexo generate # 或者hexo g
hexo server # 或者hexo s
{% endcodeblock %}
通过git提交：  
{% codeblock bash lang:bash %}
git add .
git commit -m "更新说明"
git push origin main
{% endcodeblock %}

## 回想26.6.13
在termux上成功实现更新操作  
### 初始化
需要安装npm,git  
用npm安装hexo-cli  
用git获取仓库并完成初始化  
{% codeblock bash lang:bash %}
git clone https://github.com/DNdimension/DNblog.git
cd DNblog
npm install
{% endcodeblock %}
### 提交
先登录github,在settings-DevSettings-PersonalAccessTokens，选择生成Token(classic)  
然后配置git  
{% codeblock bash lang:bash %}
git config --global user.email "2108173756@qq.com"
git config --global user.name DNdimension
git remote set-url origin https://DNdimension:token@github.com/DNdimension/DNblog.git
git config --global credential.helper store # 记住凭证
{% endcodeblock %}
### 交替更新
存在多端更新后，要用pull同步进度  
{% codeblock bash lang:bash %}
git pull origin main
{% endcodeblock %}

## 回想26.6.14
使用next主题 
### 安装
{% codeblock bash lang:bash %}
git clone https://github.com/next-theme/hexo-theme-next themes/next
rm -rf themes/next/.git
{% endcodeblock %}
### 应用主题
修改字段：  
{% codeblock _config.yml lang:yaml %}
theme: next
{% endcodeblock %}
采用代替主题配置：  
根目录下创建_config.next.yml，在themes/next/_config.yml中找到需要更改的配置选项，复制到_config.next.yml文件中  

## 回想26.6.15  
修改了markdown渲染器，为渲染katex数学公式  

## 回想26.6.16  
使用tags  
使用menu和词云图  

# 26.6.18  
发现若执行hexo s后修改md文件，网页会自动更新  
添加了categories，archives，更改了tags。加入插件hexo-auto-category，并且修改了_config.yml对应内容 

# 26.6.24  
使用html代码之后要空一行才能继续进行书写  

# 26.6.27  
分隔符要和前一个部分之间空一行

# 26.8.27
katex行内公式，起始 $ 之后，终止 $ 之前不要打空格  
win端配置了git的ssh之后，要把项目地址改成ssh
{% codeblock bash lang:bash %}
git remote -v #查看仓库地址
git remote set-url origin git@github.com:用户名/仓库.git #更改为ssh
{% endcodeblock %}