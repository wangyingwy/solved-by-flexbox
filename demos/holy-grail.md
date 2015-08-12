---
template: holy-grail.html
title: 圣杯布局
excerpt: 多年来，许多程序员都挑战过圣杯布局这个经典的问题，然而没有任何一个解决方法能够完全解决它。用flexbox，它最终成为了可能。
---

随着时间的推移，人们提出了各种解决方案来解决[圣杯布局](http://en.wikipedia.org/wiki/Holy_Grail_(web_design))这一经典问题。 如果你不了解圣杯布局的历史，这个[文章列表](http://alistapart.com/article/holygrail)提供了一个很好的总结，而且它列举了一些著名的解决方案的链接。

在其核心，圣杯布局是一种拥有页头，页脚和三栏的页面布局。中间的一栏包含着主要的内容，左右两栏包含着补充内容，如广告或者导航。

针对圣杯布局，大多数CSS解决方案是为了解决以下目标：

- 它们要有一个自适应的中间栏和固定宽度的侧边栏。
- 中间栏（主要内容）要首先出现在html代码里面。
- 无论实际上哪一栏是最高的，所有的部分都应该实现等高布局。
- 它们应该需要最小的标记。
- 在内容较少的情况下，页脚应该固定在页面的底部。

不幸的是，由于这些目标的性质以及CSS的局限性，没有任何经典解决方案能够完全满足圣杯布局的目标。

伴随着Flexbox的出现，一个完整的解决方法最终成为了可能。

## HTML

```html
<body class="HolyGrail">
  <header>…</header>
  <div class="HolyGrail-body">
    <main class="HolyGrail-content">…</main>
    <nav class="HolyGrail-nav">…</nav>
    <aside class="HolyGrail-ads">…</aside>
  </div>
  <footer>…</footer>
</body>
```

## CSS

这里使用的方法与[固定页脚]例子中(../sticky-footer/)的相同，从而使中间内容可拉伸以及使页脚固定在页面底部。唯一的不同之处在于，为了正确排列子元素，圣杯布局的中间行(`.HolyGrail-body`)需要设置`display:flex`。

```css
.HolyGrail {
  display: flex;
  min-height: 100vh;
  flex-direction: column;
}

.HolyGrail-body {
  display: flex;
  flex: 1;
}
```

要设置一个中间自适应侧边栏固定宽度的三栏等高布局就是这么简单：

```css
.HolyGrail-content {
  flex: 1;
}

.HolyGrail-nav, .HolyGrail-ads {
  /* 12em is the width of the columns */
  flex: 0 0 12em;
}

.HolyGrail-nav {
  /* put the nav on the left */
  order: -1;
}
```

### 成为响应式布局

圣杯布局诞生于一个几乎每个人都使用电脑来浏览网页的时代。但是，随着移动设备越来越多的出现以及逐渐普及的响应式设计，圣杯布局已经过时了。

不管怎样，使用Flexbox，我们能够很轻易地创造出一个移动端优先的，在移动端页面中也能友好地呈现的圣杯布局。这个方法的要点，仅仅是在移动端页面中为中间部分内容设置默认的`flex-direction:column`，然后在大屏浏览页面的时候为其设置`flex-direction:row`。

这是一个响应式的，移动端优先的完整的例子。你也可以调整浏览器大小去动态地观察它。

```css
.HolyGrail,
.HolyGrail-body {
  display: flex;
  flex-direction: column;
}

.HolyGrail-nav {
  order: -1;
}

@media (min-width: 768px) {
  .HolyGrail-body {
    flex-direction: row;
    flex: 1;
  }
  .HolyGrail-content {
    flex: 1;
  }
  .HolyGrail-nav, .HolyGrail-ads {
    /* 12em is the width of the columns */
    flex: 0 0 12em;
  }
}
```

在github中查看使用了圣杯布局的例子的完整[源码](https://github.com/philipwalton/solved-by-flexbox/blob/master/assets/css/components/holy-grail.css)。
