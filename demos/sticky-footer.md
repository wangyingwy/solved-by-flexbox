---
template: default.html
title: 固定的页脚
excerpt: 使页脚在内容较少的页面中固定在页面底部是非常棘手的问题。而且如果页脚的高度是未知的，这基本上是不可能的。但现在不是这样了。
---

<div class="Demo Demo--spaced">

点击下面的按钮隐藏本页面内容。注意看，即使在没有足够的内容铺满整个页面的情况下，页脚是如何固定在页面底部的。

<button id="collapse-trigger" class="Button"><span class="icon-refresh u-spaceRS"></span> 折叠内容</button>

</div>

<div id="collapsable-content">

使页脚固定在内容较少的页面的底部是几乎所有开发人员在他们的职业生涯中都试图解决的问题。在大多数情况下，这个问题已经解决。然而，[现存的](http://ryanfait.com/resources/footer-stick-to-bottom-of-page/)[解决方案](http://ryanfait.com/resources/footer-stick-to-bottom-of-page/)都有一个很明显的缺点&mdash;在页脚高度不确定的情况下，这些方案都无效。

Flexbox是解决这类型问题的完美方案。While mostly known for laying out content in the horizontal direction, Flexbox actually works just as well for vertical layout problems. All you have to do is wrap the vertical sections in a flex container and choose which ones you want to expand. They'll automatically take up all the available space in their container.

In the example below, the container is set to the height of the window, and the content area is told to expand as needed. *(Note: in the vertical direction you need to specify a height for the container. This is different from the horizontal direction, which automatically expands to fit.)*

## The HTML

```xml
<body class="Site">
  <header>…</header>
  <main class="Site-content">…</main>
  <footer>…</footer>
</body>
```

## The CSS

```css
.Site {
  display: flex;
  min-height: 100vh;
  flex-direction: column;
}

.Site-content {
  flex: 1;
}
```

View the full [source](https://github.com/philipwalton/solved-by-flexbox/blob/master/assets/css/components/site.css) for the `Site` component used in this demo on Github.

</div>

<script class="js-allow-before-footer">
  (function() {
    var collapseTrigger = document.getElementById("collapse-trigger");
    var collapseableContent = document.getElementById("collapsable-content");
    var isCollapsed = false;
    collapseTrigger.addEventListener("click", function() {
      if (isCollapsed) {
        collapseableContent.classList.remove("u-hidden");
      } else {
        collapseableContent.classList.add("u-hidden");
      }
      isCollapsed = !isCollapsed;
    }, false);
  }());
</script>
