---
template: default.html
title: input附加组件
excerpt: 使用以往的CSS，创建一个全屏的、自适应的输入/按钮组件对是不可能的。有了Flexbox，这变得非常的简单。
---

由于CSS中input尺寸的作用机制，我们几乎不可能为它附加或预先考虑另一个元素并使输入区域自适应以及填充剩余空间。

现在解决这个问题的方法，要么就是知道这个input输入框的确定宽度，要么就是使用如`display:table-cell`之类的属性，然而这些方法都有它们各自的问题。最值得注意的是，在某些浏览器中，把某些元素精确定位在附加组件里面是非常困难的。

有了Flexbox，这些问题都解决了，而且代码非常的简单。另外，你可以轻松地实现输入框和附加组件的等高布局。

<div class="Grid Grid--guttersLg Grid--full med-Grid--fit">
  <div class="Grid-cell">
    <h2>前面插入的附加组件</h2>
    <div class="InputAddOn">
      <span class="InputAddOn-item">Amount</span>
      <input class="InputAddOn-field">
    </div>
    <div class="InputAddOn">
      <button class="InputAddOn-item"><span class="icon icon-search"></span></button>
      <input class="InputAddOn-field">
    </div>
  </div>
  <div class="Grid-cell">
    <h2>后面插入的附加组件</h2>
    <div class="InputAddOn">
      <input class="InputAddOn-field">
      <button class="InputAddOn-item">Go</button>
    </div>
    <div class="InputAddOn">
      <input class="InputAddOn-field">
      <button class="InputAddOn-item"><span class="icon icon-star"></span></button>
    </div>
  </div>
</div>

## 两边插入的附加组件

<div class="Grid Grid--guttersLg Grid--full med-Grid--fit">
  <div class="Grid-cell">
    <div class="InputAddOn">
      <span class="InputAddOn-item"><span class="icon icon-envelope"></span></span>
      <input class="InputAddOn-field" placeholder="Example One">
      <button class="InputAddOn-item">Send</button>
    </div>
  </div>
  <div class="Grid-cell">
    <div class="InputAddOn">
      <span class="InputAddOn-item"><span class="icon icon-lock"></span></span>
      <input class="InputAddOn-field" placeholder="Example One">
      <button class="InputAddOn-item">Encrypt</button>
    </div>
  </div>
</div>

## HTML

```html
<!-- appending -->
<div class="InputAddOn">
  <input class="InputAddOn-field">
  <button class="InputAddOn-item">…</button>
</div>

<!-- prepending -->
<div class="InputAddOn">
  <span class="InputAddOn-item">…</span>
  <input class="InputAddOn-field">
</div>

<!-- both -->
<div class="InputAddOn">
  <span class="InputAddOn-item">…</span>
  <input class="InputAddOn-field">
  <button class="InputAddOn-item">…</button>
</div>
```

## CSS

```css
.InputAddOn {
  display: flex;
}

.InputAddOn-field {
  flex: 1;
  /* field styles */
}

.InputAddOn-item {
  /* item styles */
}

```

在github中查看使用了input附加组件的例子的所有[源码](https://github.com/philipwalton/solved-by-flexbox/blob/master/assets/css/components/input-add-on.css)。
