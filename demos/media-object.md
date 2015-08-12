---
template: default.html
title: 媒体对象
excerpt: 无论是创建固定大小还是尺寸不定的媒体对象，都无需考虑溢出，清除浮动或者块级格式化上下文的兼容性样式。
---

[媒体对象](http://www.stubbornella.org/content/2010/06/25/the-media-object-saves-hundreds-of-lines-of-code)是面向对象的CSS(OOCSS)的典型代表。他的简单有效促使很多CSS开发者（包括我）转变成使用OOCSS的方法

然而正如大部分的CSS布局技术，媒体对象的实现必须依赖某些小技巧和兼容性样式。

媒体对象的主体必须防止文字通过创建[块级格式化上下文](http://www.stubbornella.org/content/2013/07/31/re-visiting-the-secret-power-of-block-fomatting-context/)或者使用左margin、相等的padding来包裹着下面的图片。媒体对象也需要通过设置`overflow:hidden`或者使用伪元素来清除自身的浮动。

有了Flexbox，这些问题都能被解决。另外，Flexbox可以让我们随心所欲地垂直对齐媒体对象。我们也可以轻松地右对齐元素，无需改变源码顺序。

## 基本例子

<div class="Grid Grid--guttersLg Grid--full large-Grid--fit">
  <div class="Grid-cell">
    <div class="Demo Demo--spaced">
      <div class="Media">
        <img class="Media-figure Image" src="{{ site.baseUrl }}images/kitten.jpg" alt="Kitten">
        <div class="Media-body">
          <h3 class="Media-title">标准媒体对象</h3>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur ac nisl quis massa vulputate adipiscing. Vivamus sit amet risus ligula. Nunc eu pulvinar augue.</p>
        </div>
      </div>
    </div>
    <div class="Demo Demo--spaced">
      <div class="Media">
        <img class="Media-figure Image" src="{{ site.baseUrl }}images/kitten.jpg" alt="Kitten">
        <div class="Media-body">
          <h3 class="Media-title">标准媒体对象</h3>
          <p>Donec imperdiet sem leo, id rutrum risus aliquam vitae. Cras tincidunt porta mauris, vel feugiat mauris accumsan eget.</p>
        </div>
      </div>
    </div>
  </div>
  <div class="Grid-cell">
    <div class="Demo Demo--spaced">
      <div class="Media Media--reverse">
        <img class="Media-figure Image" src="{{ site.baseUrl }}images/kitten.jpg" alt="Kitten">
        <div class="Media-body">
          <h3 class="Media-title">颠倒的媒体对象</h3>
          <p>Phasellus vel felis purus. Aliquam consequat pellentesque dui, non mollis erat dictum sit amet. Curabitur non quam dictum, consectetur arcu in, vehicula justo. Donec tortor massa, eleifend nec viverra in, aliquet at eros. Mauris laoreet condimentum mauris, non tempor massa fermentum ut. Integer gravida pharetra cursus. Nunc in suscipit nunc.</p>
        </div>
      </div>
    </div>
  </div>
</div>

## 无图片

<div class="Grid Grid--guttersLg Grid--full large-Grid--fit">
  <div class="Grid-cell">
    <div class="Demo Demo--spaced">
      <div class="Media">
        <figure class="Media-figure"><span class="icon-comments icon-big"></span></figure>
        <div class="Media-body">
          <h3 class="Media-title">使用图标</h3>
          <p>Donec imperdiet sem leo, id rutrum risus aliquam vitae. Vestibulum ac turpis non lacus dignissim dignissim eu sed dui.</p>
        </div>
      </div>
    </div>
  </div>
  <div class="Grid-cell">
    <div class="Demo Demo--spaced">
      <div class="Media Media--center">
        <figure class="Media-figure"><span class="icon-info-sign icon-big"></span></figure>
        <div class="Media-body">
          <h3 class="Media-title">垂直居中的对象</h3>
          <p>Nunc nec fermentum dolor. Duis at iaculis turpis. Sed rutrum elit ac egestas dapibus. Duis nec consequat enim.</p>
        </div>
      </div>
    </div>
  </div>
</div>

## 嵌套的媒体对象

<div class="Grid Grid--guttersLg Grid--full large-Grid--fit">
  <div class="Grid-cell">
    <div class="Demo Demo--spaced">
      <div class="Media">
        <img class="Media-figure Image" src="{{ site.baseUrl }}images/kitten.jpg" alt="Kitten">
        <div class="Media-body">
          <h3 class="Media-title">媒体对象标题</h3>
          <p>Phasellus vel felis purus. Aliquam consequat pellentesque dui, non mollis erat dictum sit amet. Curabitur non quam dictum, consectetur arcu in, vehicula justo.</p>
          <div class="Demo Demo--spaced u-smaller">
            <div class="Media">
              <figure class="Media-figure">
                <img class="Image Image--tiny" src="{{ site.baseUrl }}images/kitten.jpg" alt="Kitten">
              </figure>
              <p class="Media-body">
                Mauris porta arcu id magna adipiscing lacinia at congue lacus. Vivamus blandit quam quis tincidunt egestas. Etiam posuere lectus sed sapien malesuada molestie.
              </p>
            </div>
          </div>
          <div class="Demo Demo--spaced u-smaller">
            <div class="Media">
              <figure class="Media-figure">
                <img class="Image Image--tiny" src="{{ site.baseUrl }}images/kitten.jpg" alt="Kitten">
              </figure>
              <div class="Media-body">
                <p>Vestibulum ac turpis non lacus dignissim dignissim eu sed dui. Proin a ligula sit amet massa malesuada mattis eu a ante. Nunc porttitor sed quam quis sollicitudin. Vestibulum ac turpis non lacus dignissim dignissim eu sed dui.</p>
                <div class="Media Media--center">
                  <span class="Media-figure icon-thumbs-up-alt"></span>
                  <p class="Media-body">Rutrum risus aliquam vitae.</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="Grid-cell">
    <div class="Demo Demo--spaced">
      <div class="Media">
        <img class="Media-figure Image" src="{{ site.baseUrl }}images/kitten.jpg" alt="Kitten">
        <div class="Media-body">
          <h3 class="Media-title">媒体对象标题</h3>
          <p>Phasellus vel felis purus. Aliquam consequat pellentesque dui, non mollis erat dictum sit amet. Curabitur non quam dictum, consectetur arcu in, vehicula justo. Donec tortor massa, eleifend nec viverra in, aliquet at eros. Mauris laoreet condimentum mauris, non tempor massa fermentum ut.</p>
          <div class="Media Media--center u-smaller">
            <span class="Media-figure icon-thumbs-up-alt"></span>
            <p class="Media-body">Donec imperdiet sem leo, id rutrum risus aliquam vitae.</p>
          </div>
          <div class="Demo Demo--spaced u-smaller">
            <div class="Media">
              <figure class="Media-figure">
                <img class="Image Image--tiny" src="{{ site.baseUrl }}images/kitten.jpg" alt="Kitten">
              </figure>
              <p class="Media-body">
                Mauris porta arcu id magna adipiscing lacinia at congue lacus. Vivamus blandit quam quis tincidunt egestas. Etiam posuere lectus sed sapien malesuada molestie. Aliquam vitae pharetra dolor. Nullam non mattis nunc.
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

## HTML

```html
<div class="Media">
  <img class="Media-figure" src="" alt="">
  <p class="Media-body">&hellip;</p>
</div>
```

## CSS

```css
.Media {
  display: flex;
  align-items: flex-start;
}

.Media-figure {
  margin-right: 1em;
}

.Media-body {
  flex: 1;
}
```

在github中查看使用了`媒体`组件的例子的完整[源码](https://github.com/philipwalton/solved-by-flexbox/blob/master/assets/css/components/media.css)。
