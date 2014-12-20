# ShadowDOM

在Web开发中，有这样一个经典的问题，如何封装自己的代码，使得自己的类库、组件与开发者的代码分离？

以往，为了获取一个独立的环境，浏览器只提供iFrame方案，使用起来太重，限制也很多。

现代浏览器提供了一种更强大的封装方案，ShadowDOM。

Shadow DOM是指浏览器的一种能力，它允许在文档（document）渲染时插入一棵DOM元素子树，但是这棵子树不在主DOM树中。

本例是一个Demo，用于演示ShadowDOM的基本使用方法。

样例来源于 [http://www.html5rocks.com/en/tutorials/webcomponents/shadowdom/](http://www.html5rocks.com/en/tutorials/webcomponents/shadowdom/)

## The Code like this
    <button>Hello, world!</button>
    <script>
      var host = document.querySelector('button');
      var root = host.createShadowRoot();
      root.textContent = 'hola, sombra mundo!';
    </script>

## The DOM like this

    <button>
      #shadow-root
        "hola, sombra mundo!"
      "Hello, world!"
    </button>

## Screenshots

![ShadowDOM Sample](http://www.marlindoo.com/assets/images/ShadowDOMSample.png "ShadowDOM Sample")

## Compatibility table for support of Shadow DOM in desktop and mobile browsers
![Compatibility table](http://www.marlindoo.com/assets/images/SupportOfShadowDOM.png "Compatibility table")
