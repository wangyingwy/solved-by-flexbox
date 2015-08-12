---
template: default.html
title: 更好, 更简单的栅格系统
excerpt: Flexbox带给我们那些绝大部分我们希望从一个栅格系统中开箱即用的特性。另外，尺寸和对齐只是一两个属性而已。
---

如今，大部分的栅格系统会使用如下两种布局方式：float或者inline-block。然而，这些并不是真正用于解决布局问题的方式，因此，它们往往会产生许多重大的问题和限制。

使用浮动，我们需要处理相当一部分的布局问题，最臭名昭著的就是，清除浮动有时候不得不影响到页面中该元素下面一个不相关的部分（我们以[这个问题](https://github.com/twbs/bootstrap/issues/295#issuecomment-2282969)作为例子）。此外，清除浮动通常需要用到before和after伪元素来阻止你使用别的东西。

Inline block布局必须解决[两个inline-block元素之间产生空白](http://css-tricks.com/fighting-the-space-between-inline-block-elements/)这一问题, 而且所有的这些[解决方法](http://davidwalsh.name/remove-whitespace-inline-block)都非常[麻烦](https://github.com/suitcss/grid/blob/master/grid.css#L44-L45)和[讨人厌](https://twitter.com/thierrykoblentz/status/305152267374428160)。

Flexbox不仅解决了这些问题，它还开辟了一条可以通往全新世界的道路。

## Features网格系统的特性

网格系统通常会伴随着很多调整选项，然而，绝大多数时候，你只需要两到三个元素并排显示。鉴于这种情况，为什么我们还有需要为每一个网格单元添加类名来定义尺寸呢？

下面是我对于一个理想的网格系统的一些标准条件。幸运的是，有了Flexbox，我们能自由地使用绝大部分的特性。

- 默认情况下，同一行中的每一个网格单元都等宽登高。基本上他们都适合默认大小。
- 为了更好地控制网格单元，你可以为特定的网格单元添加类名用于定义尺寸。在没有这些类名的情况下，网格单元会像往常一样简单地划分页面上的可用空间。
- 对于响应式的网格，你可以为网格单元添加类名用于特定的媒体查询。
- 特定的网格单元可以在顶部，底部或者中间垂直对齐。
- 当你希望栅格中所有的网格单元拥有相同的大小，媒体或校准值，你仅仅需要为其父元素添加一个类名去避免不必要的重复。
- 网格可以用于深层面的嵌套。

### 基本网格

下面这些网格单元并没有指定宽度，他们只是自然地扩展本身的空间已适应整个行。此外，他们也是默认的等高布局。

<div class="Grid Grid--gutters u-textCenter">
  <div class="Grid-cell">
    <div class="Demo">1/2</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">1/2</div>
  </div>
</div>

<div class="Grid Grid--gutters u-textCenter">
  <div class="Grid-cell">
    <div class="Demo">1/3</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">1/3</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">1/3</div>
  </div>
</div>

<div class="Grid Grid--gutters u-textCenter">
  <div class="Grid-cell">
    <div class="Demo">1/4</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">1/4</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">1/4</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">1/4</div>
  </div>
</div>

<div class="Grid Grid--gutters Grid--flexCells">
  <div class="Grid-cell">
    <div class="Demo">
      全高度，即使我的内容没有填满整个空间
    </div>
  </div>

  <div class="Grid-cell">
    <div class="Demo">
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum mollis velit non gravida venenatis. Praesent consequat lectus purus, ut scelerisque velit condimentum eu. Maecenas sagittis ante ut turpis varius interdum. Quisque tellus ipsum, eleifend non ipsum id, suscipit ultricies neque.
    </div>
  </div>
</div>

### 个体大小

当你不希望设置等宽布局的时候，你可以添加一个类名来定义特定尺寸的网格单元。其他没有定义该尺寸类名的网格单元会均等分割剩余空间。

下面标注着“auto”的网格单元没有添加特定的尺寸类名。

<div class="Grid Grid--gutters u-textCenter">
  <div class="Grid-cell u-1of2">
    <div class="Demo">1/2</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">auto</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">auto</div>
  </div>
</div>

<div class="Grid Grid--gutters u-textCenter">
  <div class="Grid-cell">
    <div class="Demo">auto</div>
  </div>
  <div class="Grid-cell u-1of3">
    <div class="Demo">1/3</div>
  </div>
</div>

<div class="Grid Grid--gutters u-textCenter">
  <div class="Grid-cell u-1of4">
    <div class="Demo">1/4</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">auto</div>
  </div>
  <div class="Grid-cell u-1of3">
    <div class="Demo">1/3</div>
  </div>
</div>

### 响应式

通过为网格单元或者容器添加媒体类名来实现响应式网格。当浏览器尺寸适配媒体值的时候，相应的网格自动调整。

下面的网格单元默认的情况下是完整的宽度，当屏幕尺寸缩小超过一半的时候会进行缩放。调整你的浏览器大小去动态地观察它们的变化。

<div class="Grid Grid--gutters Grid--full large-Grid--fit u-textCenter">
  <div class="Grid-cell">
    <div class="Demo">Full / Halves</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">Full / Halves</div>
  </div>
</div>
<div class="Grid Grid--gutters Grid--full large-Grid--fit u-textCenter">
  <div class="Grid-cell">
    <div class="Demo">Full / Thirds</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">Full / Thirds</div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">Full / Thirds</div>
  </div>
</div>

### 网格异常

网格组件可以无限地嵌套在其他的网格组件中

<div class="Grid Grid--gutters Grid--flexCells u-textCenter">
  <div class="Grid-cell">
    <div class="Demo">
      <div class="Grid Grid--gutters u-textCenter">
        <div class="Grid-cell u-1of3">
          <div class="Demo">1/3</div>
        </div>
        <div class="Grid-cell">
          <div class="Demo">
            <div class="Grid Grid--gutters u-textCenter">
              <div class="Grid-cell">
                <div class="Demo">1/2</div>
              </div>
              <div class="Grid-cell">
                <div class="Demo">1/2</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="Grid-cell u-1of3">
    <div class="Demo">1/3</div>
  </div>
</div>

## 对齐特性

### 顶部对齐的网格单元

<div class="Grid Grid--gutters Grid--top">
  <div class="Grid-cell">
    <div class="Demo">
      这个网格会被顶部对齐
    </div>
  </div>
  <div class="Grid-cell u-1of2">
    <div class="Demo">
      Pellentesque sagittis vel erat ac laoreet. Phasellus ac aliquet enim, eu aliquet sem. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed pulvinar porta leo, eu ultricies nunc sollicitudin vitae. Curabitur pulvinar dolor lectus, quis porta turpis ullamcorper nec. Quisque eget varius turpis, quis iaculis nibh.
    </div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">
      这个网格会被顶部对齐
    </div>
  </div>
</div>

### 底部对齐的网格单元

<div class="Grid Grid--gutters Grid--bottom">
  <div class="Grid-cell">
    <div class="Demo">
      这个网格会被底部对齐
    </div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">
      Curabitur pulvinar dolor lectus, quis porta turpis ullamcorper nec. Quisque eget varius turpis, quis iaculis nibh. Ut interdum ligula id metus hendrerit cursus. Integer eu leo felis. Aenean commodo ultrices nunc, sit amet blandit elit gravida in.
    </div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">
      这个网格会被底部对齐
    </div>
  </div>
</div>

### 垂直居中的网格单元

<div class="Grid Grid--gutters Grid--center">
  <div class="Grid-cell">
    <div class="Demo">
      这个网格会基于它右边的网格垂直居中对齐
    </div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">
      Curabitur pulvinar dolor lectus, quis porta turpis ullamcorper nec. Quisque eget varius turpis, quis iaculis nibh. Ut interdum ligula id metus hendrerit cursus. Integer eu leo felis. Aenean commodo ultrices nunc, sit amet blandit elit gravida in. Sed est ligula, ornare ac nisi adipiscing, iaculis facilisis tellus. Nullam vel facilisis libero. Duis semper lobortis elit, vitae dictum erat.</div>
  </div>
</div>

### 混合垂直对齐

<div class="Grid Grid--gutters">
  <div class="Grid-cell Grid-cell--top">
    <div class="Demo">
      这个网格单元会被顶部对齐
    </div>
  </div>
  <div class="Grid-cell">
    <div class="Demo">
      Curabitur pulvinar dolor lectus, quis porta turpis ullamcorper nec. Quisque eget varius turpis, quis iaculis nibh. Ut interdum ligula id metus hendrerit cursus. Integer eu leo felis. Aenean commodo ultrices nunc, sit amet blandit elit gravida in. Sed est ligula, ornare ac nisi adipiscing, iaculis facilisis tellus.</div>
  </div>
  <div class="Grid-cell Grid-cell--center">
    <div class="Demo">
      这个网格单元会被居中对齐
    </div>
  </div>
  <div class="Grid-cell Grid-cell--bottom">
    <div class="Demo">
      这个网格单元会被底部对齐
    </div>
  </div>
</div>

## HTML

```html
<div class="Grid">
  <div class="Grid-cell">…</div>
  <div class="Grid-cell">…</div>
  <div class="Grid-cell">…</div>
</div>
```

## CSS

### 基本网格样式

```css
.Grid {
  display: flex;
}

.Grid-cell {
  flex: 1;
}
```

### 网格样式修饰

```css
/* With gutters */
.Grid--gutters {
  margin: -1em 0 0 -1em;
}
.Grid--gutters > .Grid-cell {
  padding: 1em 0 0 1em;
}

/* Alignment per row */
.Grid--top {
  align-items: flex-start;
}
.Grid--bottom {
  align-items: flex-end;
}
.Grid--center {
  align-items: center;
}

/* Alignment per cell */
.Grid-cell--top {
  align-self: flex-start;
}
.Grid-cell--bottom {
  align-self: flex-end;
}
.Grid-cell--center {
  align-self: center;
}
```

### 响应式修饰（移动端优先的方法）

```css
/* Base classes for all media */
.Grid--fit > .Grid-cell {
  flex: 1;
}
.Grid--full > .Grid-cell {
  flex: 0 0 100%;
}
.Grid--1of2 > .Grid-cell {
  flex: 0 0 50%
}
.Grid--1of3 > .Grid-cell {
  flex: 0 0 33.3333%
}
.Grid--1of4 > .Grid-cell {
  flex: 0 0 25%
}

/* Small to medium screens */
@media (min-width: 24em) {
  .small-Grid--fit > .Grid-cell {
    flex: 1;
  }
  .small-Grid--full > .Grid-cell {
    flex: 0 0 100%;
  }
  .small-Grid--1of2 > .Grid-cell {
    flex: 0 0 50%
  }
  .small-Grid--1of3 > .Grid-cell {
    flex: 0 0 33.3333%
  }
  .small-Grid--1of4 > .Grid-cell {
    flex: 0 0 25%
  }
}

/* Large screens */
@media (min-width: 48em) {
  .large-Grid--fit > .Grid-cell {
    flex: 1;
  }
  .large-Grid--full > .Grid-cell {
    flex: 0 0 100%;
  }
  .large-Grid--1of2 > .Grid-cell {
    flex: 0 0 50%
  }
  .large-Grid--1of3 > .Grid-cell {
    flex: 0 0 33.3333%
  }
  .large-Grid--1of4 > .Grid-cell {
    flex: 0 0 25%
  }
}
```

在github中查看使用了这个网格组件的例子的完整[源码](https://github.com/philipwalton/solved-by-flexbox/blob/master/assets/css/components/grid.css) 。
