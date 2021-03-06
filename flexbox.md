---
title: Flexbox
---
Flexbox 实现了帮助我们脱离 CSS 苦海（例如垂直居中）的目标，但想精通它却需要你应对一些挑战。所以，我们将通过一些动画让你直观地了解 Flexbox 的工作原理，并使用它来构建灵活的布局。

Flexbox 的基本原则是提供一种构建灵活、直观的布局方式。

为了达成这一目标，它让容器决定如何分配容器成员的大小以及空间。这听起来相当不错，那么，让我们来看看实践中它是如何工作的。

在本文中，我们将深入的探讨 Flexbox 中 5 个常见的属性。看看它们能做什么，如何使用它们，以及使用它们构建的布局是什么样的。

---

##### 属性 #1: Display: Flex
以下是示例页面：
![](https://my-owo-ink.b0.upaiyun.com/owo.ink/flexbox/675733-523dbccc41453c86.gif)

我们可以看到，在灰色的容器中，包含了 4 种不同颜色与大小的 div 元素。每个 div 元素都默认`display: block`，因此，每个四方体都占据了一行的整个宽度。

为了开始使用 Flexbox 布局，你需要将你的容器变为 Flex 容器。这很容易实现：

```
#container {
  display: flex;
}
```
![](https://my-owo-ink.b0.upaiyun.com/owo.ink/flexbox/675733-603a348d420cd823.gif)

##### 属性 #2: Flex Direction

Flexbox 容器有两根轴：主轴和垂直的交叉轴，默认情况如下：

![](https://my-owo-ink.b0.upaiyun.com/owo.ink/flexbox/675733-93f65b182a2f85d4.png)

项目默认是由主轴（从左到右）排列的，这就是你使用display: flex后，四方体以水平线排列的原因。

而`Flex-direction`决定了主轴的方向。
```
#container {
  display: flex;
  flex-direction: column;
}
```
这里有一个重要的区别：`flex-direction: column`所指的是四方体将沿主轴的垂直方向对齐。它使主轴自身从水平到垂直。

而`flex-direction`还有一些其他的值供你设置，例如：`row-reverse`与`column-reverse`.
![](https://my-owo-ink.b0.upaiyun.com/owo.ink/flexbox/675733-643ed5f305d85377.gif)
##### 属性 #3: Justify Content

`justify-content`属性定义了项目在主轴上的对齐方式。

在这里，你将更多的了解主轴与交叉轴的区别。首先，让我们回到`flex-direction: row`值上。
```
#container {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
}
```
`justify-content`属性包含了 5 个值供你使用：

> Flex-start
Flex-end
Center
Space-between
Space-around

![](https://my-owo-ink.b0.upaiyun.com/owo.ink/flexbox/675733-739ce25a66110b9e.gif)

`Space-around`与`Space-between`是两个不容易直观理解的值。`Space-between`实现了两端对齐，而四方体之间的间隔都是相等的。

`Space-around`使四方体两侧的间隔相等，这意味着四方体之间的间隔比最外边四方体与边框的间隔要大一倍。（每个四方体贡献了不重叠的等量余量，从而使空间翻倍）

最后一点：请记住 `justify-content`沿主轴对齐，而`flex-direction`决定了主轴的方向。它将决定你移动的方向。

##### 属性 #4: Align Items

当你理解了`justify-content`属性，理解`Align Items`属性就变得轻而易举了。

`justify-content`定义了项目在主轴的对齐方式，而`align-items`属性则定义了项目在交叉轴上是如何对齐的。

![](https://my-owo-ink.b0.upaiyun.com/owo.ink/flexbox/675733-82ed714fd22557a1.png)

当我们将`flex-direction`属性值重置为row后，我们的轴看上去就与上图一致。

那么，让我们深入的了解下`Align Items`属性有哪些值：
> flex-start
flex-end
center
stretch
baseline

前三个值与`justify-content`属性中的值完全一致，没有太多需要解释的地方。

但是，接下来两个值却有些不同。

`Stretch`指的是如果项目未设置高度或设为`auto`，项目将占满整个容器。而`baseline`是指项目将与段落标签的底部对齐。
![](https://my-owo-ink.b0.upaiyun.com/owo.ink/flexbox/675733-5884ef1046c04119.gif)

（请注意，对于`align-items：stretch`，我不得不将四方体的高度设置为auto，否则height属性将覆盖该stretch）

对于baseline，如果你去掉段落标签，它则会对齐四方形的底部，如下图所示：

![](https://my-owo-ink.b0.upaiyun.com/owo.ink/flexbox/675733-2c5a097f00549381.png)

为了更好地演示主轴和交叉轴的表现，在基于`justify-content`属性和`align-items`属性的值为center的情况下，让我们看看赋予`flex-direction`属性两个不同值后，它的表现如何：
![](https://my-owo-ink.b0.upaiyun.com/owo.ink/flexbox/675733-ca9a85bcbcd77fd1.gif)

我们可以看到，对于row值，四方体沿着与主轴水平方向排列，而对于column值，它们则沿着与主轴垂直的方向排列。

即使出现了同时保持水平与垂直居中的情况，两者也不可互换！

##### 属性 #5: Align Self

`align-self`属性允许你对特定的项目有与其他项目不一样的对齐方式，它可覆盖`align-items`属性。虽然它的默认值为auto，但它继承了父元素`align-items`的属性。除了auto外，其他都与`align-items`属性完全一致。

```
#container {
  align-items: flex-start;
}
.square#one {
  align-self: center;
}
// Only this square will be centered.
```
我们将在两个四方体上应用`align-self`属性，而其余的四方体则应用`align-items: center`与 `flex-direction: row`，让我们看看会发生什么：
![](https://my-owo-ink.b0.upaiyun.com/owo.ink/flexbox/675733-91938230a16c111f.gif)