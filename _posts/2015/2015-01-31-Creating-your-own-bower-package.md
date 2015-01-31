---
layout: page
title : Creating your own bower package
header : Post Archive
---

前阵子为Backbone-form表单引擎写了一个编辑组件[BackgridEditor](https://github.com/MarlinDoo/BackgridEditor)，今天准备将BackgridEditor注册成为Bower组件，需要的用户可以通过bower来安装、管理BackgridEditor。安装命令如下：
{% highlight javascript linenos %}

bower install backgrid-editor

{% endhighlight %}

注册bower包的过程不复杂，记录一下。

## 准备工作

首先，你需要有一个github的项目。Bower依赖于git，因此我们准备在Bower上注册的项目需要托管在git，可以是GitHub、Bitbucket或者其他的git服务商。

其次，包的版本需要使用git tags管理。Bower通过git tags信息来获取项目的版本号。

下面是BackgridEditor的bower.json内容

{% highlight javascript linenos %}

{
  "name": "BackgridEditor",
  "version": "0.0.2",
  "authors": [
    "garydong@outlook.com"
  ],
  "description": "An table cell editor",
  "keywords": [
    "Backbone-forms",
    "Backgrid",
    "editor"
  ],
  "license": "MIT",
  "ignore": [
    "**/.*",
    "node_modules",
    "bower_components",
    "test",
    "tests"
  ],
  "dependencies": {
    "backbone-forms": "~0.14.0",
    "backgrid": "~0.3.5",
    "bootstrap": "~3.3.1"
  }
}

{% endhighlight %}

其中，ignore部分是告诉Bower哪些内容不需要发布（只要干货就好了）。

## 使用Bower注册项目

先说一个我踩的坑吧，希望可以帮到读到这篇文章的朋友。

在BackgridEditor项目下执行
{% highlight javascript linenos %}

bower install BackgridEditor

{% endhighlight %}

提示如下：
{% highlight javascript linenos %}
-----------------------------------------
Update available: 1.3.12 (current: 1.2.8)
Run npm update -g bower to update
-----------------------------------------

bower convert       Converted https://github.com/MarlinDoo/BackgridEditor.git to git://github.com/MarlinDoo/BackgridEditor.git
bower resolve       git://github.com/MarlinDoo/BackgridEditor.git#*
bower checkout      BackgridEditor#master
[?] Registering a package will make it installable via the registry (https://bower.herokuapp.com), continue? Yes
bower register      git://github.com/MarlinDoo/BackgridEditor.git
bower EINVFORMAT    Invalid URL format

{% endhighlight %}

最后提示"bower EINVFORMAT    Invalid URL format"，无效的链接格式！
bower注册的包名称不支持驼峰命名方法，如果在Github中的项目使用驼峰命名方式，又希望命名上保持一致，则建议使用中划线分隔，如将BackgridEditor修改为backgrid-editor。

执行下面的命令继续注册
{% highlight javascript linenos %}
bower register backgrid-editor git://github.com/MarlinDoo/BackgridEditor.git
{% endhighlight %}

注册成功，这是输入下面命令查询注册信息。

{% highlight javascript linenos %}

bower info backgrid-editor

{% endhighlight %}

查询结果如下：

{% highlight javascript linenos %}

bower backgrid-editor#*         cached git://github.com/MarlinDoo/BackgridEditor.git#dfd2898707
bower backgrid-editor#*       validate dfd2898707 against git://github.com/MarlinDoo/BackgridEditor.git#*
bower backgrid-editor#*            new version for git://github.com/MarlinDoo/BackgridEditor.git#*
bower backgrid-editor#*        resolve git://github.com/MarlinDoo/BackgridEditor.git#*
bower backgrid-editor#*       download https://github.com/MarlinDoo/BackgridEditor/archive/v0.0.2.tar.gz
bower backgrid-editor#*        extract archive.tar.gz
bower backgrid-editor#*       mismatch Version declared in the json (0.0.1) is different than the resolved one (0.0.2)
bower backgrid-editor#*       resolved git://github.com/MarlinDoo/BackgridEditor.git#0.0.2

{
  name: 'BackgridEditor',
  version: '0.0.2',
  authors: [
    'garydong@outlook.com'
  ],
  description: 'An table cell editor',
  keywords: [
    'Backbone-forms',
    'Backgrid',
    'editor'
  ],
  license: 'MIT',
  ignore: [
    '**/.*',
    'node_modules',
    'bower_components',
    'test',
    'tests'
  ],
  dependencies: {
    'backbone-forms': '~0.14.0',
    backgrid: '~0.3.5',
    bootstrap: '~3.3.1'
  },
  homepage: 'https://github.com/MarlinDoo/BackgridEditor'
}

Available versions:
  - 0.0.2

You can request info for a specific version with 'bower info backgrid-editor#<version>'

{% endhighlight %}

## 版本维护

    1. 修复Bug，添加新功能；
    2. 更新bower.json文件中的版本信息；
    3. 提交更新，注意使用 --tags参数。

操作如下：

{% highlight javascript linenos %}

git tag -a v0.0.2 -m "Release version 0.0.2"
git push origin master --tags  

{% endhighlight %}

这是使用“bower info backgrid-editor”命令即可看到项目的最新信息。

使用命令
{% highlight javascript linenos %}
bower info backgrid-editor#0.0.2
{% endhighlight %}
可以看到指定版本的信息。




