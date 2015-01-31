---
layout: page
title : Recusive vs. Iterative
header : Post Archive
---

## 递归算法，即函数调用自身
{% highlight javascript linenos %}
function Foo(n){
    // 迭代算法必须有终止条件
    if(n==0) return 0;
    return n+Foo(n-1);
}
{% endhighlight %}

## 迭代算法

{% highlight javascript linenos %}
function Foo(n){
    var num = 0;
    for(var i=0;i <= n;i++)
        num += i;
    return num;
}
{% endhighlight %}

## 迭代与遍历(traversal)的区别

看到上面迭代的例子，很容易想到这就是遍历嘛。迭代与遍历有什么区别呢？

* 迭代是访问线性对象中的每一个对象；
* 遍历是访问非线性结构中的每一个对象，典型的如二叉树。