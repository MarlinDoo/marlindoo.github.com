---
layout: page
title : How to run react native examples?
header : Post Archive
---

React native 发布第三天，刚刚看了一眼，将近9k的start，足见其影响力！
快速上手运行和调试官方提供的例子，有助于认识和理解React Native.

## You have to install node.js in your Terminal with
## 在客户端安装node.js

    brew install node

ReactNative use Node.js to build the Javascript code inside the project.
ReactNative通过Node.js来编译项目中的Javascript代码。

Then you need Watchman, a file watcher from Facebook with
## 然后，安装Wachman，Facebook发布的文件监控程序，安装命令：

    brew install watchman

React Native use Watchman to rebuild your code when there's a change in it.
React Native 通过Watchman监控代码的变化，并重新编辑。

The final thing is to install and run node with a Terminal window in the react-native folder.
## 最后，在react native文件夹中安装并运行node。

    npm install
    npm start

Now you can open a project from the react-native/Examples folder in Xcode, then build and run it.
OK，使用Xcode中打开react-native/Examples文件夹下面的项目，可以正常编译并运行。
