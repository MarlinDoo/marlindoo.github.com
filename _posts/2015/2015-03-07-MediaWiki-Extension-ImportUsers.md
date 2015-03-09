---
layout: page
title : MediaWiki 导入用户
header : Post Archive
---
最近因为项目原因，使用MediaWiki给用户搭建一个Wiki系统。随着对MediaWiki的理解一步一步深入，愈发体验到MediaWiki的灵活性与扩展性设计优势。
话不多说，导入用户干货。
【注】主要步骤来源于[http://www.mediawiki.org/wiki/Extension:ImportUsers](http://www.mediawiki.org/wiki/Extension:ImportUsers)
## 1 安装MediaWiki扩展 Extension:ImportUsers；
下载安装包 ImportUsers-1.5.1.zip，放到 /extensions目录下，并在LocalSetting.php中添加

    require_once( "$IP/extensions/ImportUsers/ImportUsers.php" );

这是访问页面 http://localhost/wiki/index.php/特殊:版本信息 可以看到已经安装成成功
|                                             特殊页面                                             |
| ------------------------ |:------------------------------------------------------------------:| --------------------------------:|
| Import Users （版本1.5.1） | Allows to import users in bulk from a UTF-8 encoded CSV file | Yuriy Ilkiv、Rouslan Zenetl 和其他 |

[注] 由于使用的是zn-cn版本，所以链接中的参数使用的是中文“特殊:版本信息”，如果使用的是英文环境，则地址为 http://localhost/wiki/index.php/Special:Version

## 2 用户数据格式
用户数据文件使用无BOM编码的UTF-8格式，其中使用逗号分隔4~5个数据项：
1. username
2. password
3. email
4. real name
5. user group (optional)

例如：
user1,pass1,user1@example.org,John Doe,editor
user2,pass2,user2@example.org,Jane Doe,editor

## 3 用户数据出现冲突时默认解决方案配置
由于MediaWiki中用户不能重复，因此在导入用户时需要选择冲突的处理方式：
1. 替换已存在的用户；
2. 忽略已存在的用户。

## 4 导入用户数据

打开下面的链接，导入用户

    http://localhost/wiki/index.php/特殊:导入用户
    http://localhost/wiki/index.php/Special:ImportUser

## 5 更新MediaWiki统计数据
进入/wiki/maintenance目录（其中有很多维护脚本），执行“php initSiteStats.php”

    cd wiki/maintenance
    php initSiteStats.php

显示结果：

    Refresh Site Statistics
    _
    Counting total edits...34
    Counting number of articles...1
    Counting total pages...10
    Counting number of users...5
    Counting number of images...0
    Counting total page views...155
    _
    Updating site statistics...done.


