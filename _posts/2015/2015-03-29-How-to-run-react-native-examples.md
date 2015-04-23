---
layout: page
title : How to run react native examples?
header : Post Archive
---

React native 发布第三天，刚刚看了一眼，将近9k的start，足见其影响力！
快速上手运行和调试官方提供的例子，有助于认识和理解React Native.

## 在客户端安装node.js

    brew install node

ReactNative通过Node.js来编译项目中的Javascript代码。

## 然后，安装Wachman，Facebook发布的文件监控程序，安装命令：

    brew install watchman

React Native 通过Watchman监控代码的变化，并重新编辑。

## 最后，在react native文件夹中安装并运行node。

    npm install     (使用sudo npm install)
    npm start

OK，使用Xcode中打开react-native/Examples文件夹下面的项目，可以正常编译并运行。
