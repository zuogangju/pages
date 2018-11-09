https://zuogangju369.github.io/pages/

## 什么是docsify
无需构建，写完 markdown 直接发布成文档，写说明文档的极佳选择。

## 快速上手
### 安装

> npm i docsify-cli -g

> docsify init docs

### 创建项目
新建一个空项目，接着创建一个 docs 目录并进入到 docs 目录下

> mkdir my-project && cd my-project

> mkdir docs && cd docs

### 创建入口文件
根目录下创建index.html 文件
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
  <meta name="description" content="Description">
  <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <link rel="stylesheet" href="//unpkg.com/docsify/lib/themes/vue.css">
</head>
<body>
  <div id="app"></div>
  <script>
    window.$docsify = {
		loadSidebar: true,//多页文档
		loadNavbar: true,//定制导航栏 
		subMaxLevel: 6// 显示目录最大等级
    }
  </script>
  <script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
  <script src="//unpkg.com/prismjs/components/prism-json.js"></script>
</body>
</html>
```

### 预览

> docsify serve docs

docsify自动监听3000端口，浏览器输入 http://localhost:3000

就可以看到你在README.md里面编辑的内容了

### 发布到 GitHub Page
将文档托管到github，这样就可以随时随地访问了。

新建一个仓库，在setting里面开启 GitHub Pages 功能，
选择：GitHub Pages->master branch /docs folder
浏览器输入 https://zuogangju369.github.io/pages/  就可以看到你的文档了