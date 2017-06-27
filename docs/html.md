
# HTML 规范

## 语法

使用四个空格的缩进，这是保证代码在各种环境下显示一致的唯一方式。

嵌套的节点应该缩进（四个空格）。

在属性上，使用双引号，不要使用单引号。

不要在自动闭合标签结尾处使用斜线 `/` - HTML5 规范 指出他们是可选的。

```
<img src="images/logo.png" alt="Company">
```

不要忽略可选的关闭标签（例如，`</li>` 和 `</body>`）。

## HTML5 doctype

在每个 HTML 页面开头使用这个简单地 doctype 来启用标准模式，使其每个浏览器中尽可能一致的展现。

虽然 doctype 不区分大小写，但是按照惯例，doctype 大写

```
<!DOCTYPE html>
```

## 语言属性

```
<html lang="en">

</html>
```

## 字符编码

通过明确声明字符编码，能够确保浏览器快速并容易的判断页面内容的渲染方式。这样
做的好处是，可以避免在 HTML 中使用字符实体标记（character entity），从而全部与
文档编码一致（一般采用 UTF-8 编码）。

```
<meta charset="UTF-8">
```

## IE 兼容模式

IE 支持通过特定的 <meta> 标签来确定绘制当前页面所应该采用的 IE 版本。除非有强烈
的特殊需求，否则最好是设置为 edge mode，从而通知 IE 采用其所支持的最新的模
式。

```
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

## 响应式

```
<meta name="viewport" content="width=device-width, initial-scale=1">
```

## 引入 CSS 和 JavaScript

根据 HTML5 规范, 通常在引入 CSS 和 JavaScript 时不需要指明 type，因为 text/css 和 text/javascript 分别是他们的默认值。

```
<!-- External CSS -->
<link rel="stylesheet" href="code-guide.css">

<!-- In-document CSS -->
<style>
    /* ... */
</style>

<!-- JavaScript -->
<script src="code-guide.js"></script>
```

## 实用高于完美

尽量遵循 HTML 标准和语义，但是不应该以浪费实用性作为代价。任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。

## 减少标签数量

在编写 HTML 代码时，需要尽量避免多余的父节点。很多时候，需要通过迭代和重构来使 HTML 变得更少。 参考下面的示例:

```
<!-- Not so great -->
<span class="avatar">
    <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```

## 属性顺序

HTML 属性应该按照特定的顺序出现以保证易读性。

1. class
2. id
3. name
4. data-*
5. src, for, type, href, value , max-length, max, min, pattern
6. placeholder, title, alt
7. aria-*, role
8. required, readonly, disabled

class 是为高可复用组件设计的，理论上他们应处在第一位。id 更加具体而且应该尽量少使用（例如, 页内书签），所以他们处在第二位。

## Boolean 属性

Boolean 属性指不需要声明取值的属性。XHTML 需要每个属性声明取值，但是 HTML5 并不需要。

一个元素中 Boolean 属性的存在表示取值 true，不存在则表示取值 false。

简而言之，不要为 Boolean 属性添加取值。

```
<input type="text" disabled>
```

## JavaScript 生成标签

在 JavaScript 文件中生成标签让内容变得更难查找，更难编辑，性能更差。应该尽量避免这种情况的出现。

