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

Flexbox是解决这类型问题的完美方案。虽然页面大多数以水平方向布局内容，但Flexbox同样适合垂直布局问题。你需要做的事情就是用一个弹性盒模型包裹着这些垂直节点，然后选择哪些是需要扩展的节点。他们会在他们的包裹容器里面自动地占满可用的空间。

在下面的例子中，最外层包裹容器设置为窗口的高度，里面的内容区域则按需扩展。*(注意：在垂直方向上，你需要为最外层容器指定一个高度。这不同于水平方向，水平方向会自动地填充宽度。)*

## HTML

```xml
<body class="Site">
  <header>…</header>
  <main class="Site-content">…</main>
  <footer>…</footer>
</body>
```

## CSS

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

在github中查看使用了这个组件的例子的完整[源码](https://github.com/philipwalton/solved-by-flexbox/blob/master/assets/css/components/site.css)。

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
