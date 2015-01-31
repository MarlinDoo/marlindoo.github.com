---
layout: page
title : Bower 与 NPM 的不同
header : Post Archive
---

这篇文章翻译自 stackoverflow [Difference between bower and npm](http://stackoverflow.com/questions/18641899/difference-between-bower-and-npm/18652918)

npm is most commonly used for managing Node.js modules, but it works for the front-end too when combined with Browserify and/or $ npm dedupe.

npm 是管理Node.js模块最常用的工具。npm通过集成[Browserify](http://browserify.org)或者[npm dedupe](https://docs.npmjs.com/cli/dedupe)也可以用于前端包依赖管理。

Bower is created solely for the front-end and is optimized with that in mind. The biggest difference is that npm does nested dependency tree (size heavy) while Bower requires a flat dependency tree (puts the burden of dependency resolution on the user).

Bower是前端专用的包依赖管理工具，并为其做了专门的优化。二者最大的不同是，npm需要建立嵌套的树形依赖关系（这使得文件尺寸变得很大），而Bower建立的是平行依赖关系(依赖关系冲突交由用户手工解决)。
【笔者注】 树形嵌套依赖，意味着每个包自行维护自己的依赖关系。平行依赖关系，包共同依赖同一份组件包。由此，二者的尺寸差别很大，随着依赖包的增长，差距会变得更大。

A nested dependency tree means that your dependencies can have its own dependencies which can have their own, and so on. This is really great on the server where you don't have to care much about space and latency. It lets you not have to care about dependency conflicts as all your dependencies use e.g. their own version of Underscore. This obviously doesn't work that well on the front-end. Imagine a site having to download three copies of jQuery.

嵌套的树形依赖关系意味着，你的每个依赖都拥有自己的依赖关系。这一点服务端合适，并且我们并不在意其影响导致的空间占用和响应延时。所有的依赖，我们都不需要关心他们之间的依赖冲突，比如他们将使用自己的Underscore版本。显然，这种方式在前端是无法工作的。想象一下，在一个网站上下载了三份jQuery的情形。

The reason many projects use both is that they use Bower for front-end packages and npm for developer tools like Yeoman, Grunt, Gulp, JSHint, CoffeeScript, etc.

许多项目同时使用这两个工具，分工不同。利用Bower维护前端包。利用npm维护开发工具，如Yeoman, Grunt, Gulp, JSHint, CoffeeScript等。

All package managers have many downsides. You just have to pick which you can live with.

包管理工具都有其缺点，你只需要选择你能驾驭的那个。
