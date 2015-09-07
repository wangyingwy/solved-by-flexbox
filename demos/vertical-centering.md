---
template: default.html
title: 垂直居中
excerpt: 多年来，这个经典的问题一直是前端人员的挑战，然而，目前没有任何解决方法可以完全解决它。有了Flexbox，这最终成为了可能。
---

CSS缺乏良好的方式垂直居中元素已经成为了它的污点。

更糟糕的是，那些用于垂直居中的有效方法看起来都非常的晦涩难懂，然而那些明显的选项(像是 `vertical-align:middle`)，似乎起不了作用。

目前用于[垂直居中](http://css-tricks.com/centering-in-the-unknown/)的方式非常多，比如负的margin值，`display:table-cell`还有那些荒谬的hack写法，例如全高度的为元素。然而这些方法也还是会有失效的时候。如果需要居中的元素是未知尺寸的，而且它还含有兄弟元素，那该怎么办呢？如果你可以使用伪元素的hack，但是你需要用它们来实现其它的功能，又该怎么办呢？

有了Flexbox，你可以不用担心了。你可以使用`align-items`, `align-self`, and `justify-content`这些属性(垂直或者水平)对齐任何元素。

<div class="Demo Demo--spaced">
  <div class="Aligner">
    <div class="Aligner-item Aligner-item--fixed">
      <div class="Demo">
        <h3>我居中了！</h3>
        <p contenteditable="true">这个区域已经垂直水平居中，即使这个区域里面的文字数量改变了，使整个区域变宽了或者变高了，这个区域依旧会有居中效果。点击编辑文字尝试一下吧。</p>
      </div>
    </div>
  </div>
</div>

不像其他的居中技术，使用Flexbox，兄弟元素的存在不影响他们自身垂直居中的属性。

<div class="Demo Demo--spaced">
  <div class="Aligner">
    <div class="Aligner-item Aligner-item--top">
      <div class="Demo"><strong>Top</strong></div>
    </div>
    <div class="Aligner-item">
      <div class="Demo"><strong>Centered</strong></div>
    </div>
    <div class="Aligner-item Aligner-item--bottom">
      <div class="Demo"><strong>Bottom</strong></div>
    </div>
  </div>
</div>

## HTML

```html
<div class="Aligner">
  <div class="Aligner-item Aligner-item--top">…</div>
  <div class="Aligner-item">…</div>
  <div class="Aligner-item Aligner-item--bottom">…</div>
</div>
```

## CSS

```css
.Aligner {
  display: flex;
  align-items: center;
  justify-content: center;
}

.Aligner-item {
  max-width: 50%;
}

.Aligner-item--top {
  align-self: flex-start;
}

.Aligner-item--bottom {
  align-self: flex-end;
}
```

在github上查看使用了`对齐`组件的例子的完整[源码](https://github.com/philipwalton/solved-by-flexbox/blob/master/assets/css/components/aligner.css)。
