---
layout: default
title: 定制
nav_order: 6
---

# 定制
{: .no_toc }

## 目录
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 颜色方案

{: .d-inline-block }

新
{: .label .label-green }

Just the Docs 支持两种颜色方案：亮色（默认）和暗色。

启用一个颜色方案，在您站点的 `_config.yml` 文件中设置 `color_scheme` 参数：

#### 示例
{: .no_toc }

```yaml
# Color scheme supports "light" (default) and "dark"
color_scheme: dark
```

<button class="btn js-toggle-dark-mode">预览暗色方案</button>

<script>
const toggleDarkMode = document.querySelector('.js-toggle-dark-mode');

jtd.addEvent(toggleDarkMode, 'click', function(){
  if (jtd.getTheme() === 'dark') {
    jtd.setTheme('light');
    toggleDarkMode.textContent = '预览暗色方案';
  } else {
    jtd.setTheme('dark');
    toggleDarkMode.textContent = '返回亮色方案';
  }
});
</script>

## 定制方案

### 定义一个定制方案

您可以添加定制方案。如果您想添加的定制方案叫做 `foo`（名字可以任意），只需添加一个 `_sass/color_schemes/foo.scss` 文件（当然，要用您给的名字替换掉 `foo`），在该文件中通过重写主题的变量名来修改颜色、字体、间距等。

{: .note }
由于默认颜色方案时 `light`，您的定制方案也就会基于 `light` 方案的变量名进行修改。

如果您想基于 `dark` 方案进行修改，您需要用下面的操作开始您的文件：

```scss
@import "./color_schemes/dark";
```

您可以用同样的方式基于其它定制方案定义您自己的定制方案。

可用变量在 [\_variables.scss](https://github.com/just-the-docs/just-the-docs/tree/main/_sass/support/_variables.scss) 文件中列出。

例如，修改链接颜色从紫色变为蓝色，在您的方案文件中包含下面代码：

#### 示例
{: .no_toc }

```scss
$link-color: $blue-000;
```

注意修改变量不会自动修改其他依赖的变量的值。
例如，默认链接颜色 (`$link-color`) 设定为 `$purple-000`。然而，在定制颜色方案中重新定义 `$purple-000` 并不会自动改变 `$link-color` 的颜色去匹配修改后的颜色。
相反，每个依赖以前级联值的变量必须手动通过从 `_variables.scss` 复制依赖规则才能重载实现修改。在这个示例中，需要重写 `$link-color: $purple-000;`。

_注意：_ 不推荐直接在 `_sass/support/variables.scss` 中编辑变量，可能会引起其他依赖项出错。
请用方案文件。

### 使用一个定制方案

使用定制颜色方案，只需在您的站点  `_config.yml` 文件中设置 `color_scheme` 参数：

```yaml
color_scheme: foo
```

### 可转换的定制方案

如果您想使用能够动态转换的颜色方案，例如通过 JavaScript 实现，只需添加一个文件 `assets/css/just-the-docs-foo.scss`（用您自己给的方案名字取代 `foo`），文件内容如下：

{% raw %}
    ---
    ---
    {% include css/just-the-docs.scss.liquid color_scheme="foo" %}
{% endraw %}

This allows you to switch the scheme via the following javascript.

```js
jtd.setTheme("foo")
```

## 覆盖和完全定制样式

对于没有定义的变量的样式，您可能想要修改特定的 CSS 类。
此外，您可能想要添加全部的 CSS 到您的内容里。
要想这么做，把您的样式放进 `_sass/custom/custom.scss` 文件。
这样做会使您的所有复写都放进一个单独的文件，还能保证对上游修改的应用。

例如，如果您想要添加您自己的样式来打印页面，您可以添加下面的样式。

#### 示例
{: .no_toc }

```scss
// Print-only styles.
@media print {
  .side-bar,
  .page-header {
    display: none;
  }
  .main-content {
    max-width: auto;
    margin: 1em;
  }
}
```

## 覆盖包含

您可以通过覆盖任何已提供的定制的 [Jekyll 包含](https://jekyllrb.com/docs/includes/)文件来定制主题。

要这么做，创建一个 `_includes` 目录，在创建您想要修改的特定文件——文件内容将覆盖掉主题默认内容。更多信息参阅 Jekyll 文档中[覆盖默认主题](https://jekyllrb.com/docs/themes/#overriding-theme-defaults)部分。

Just the Docs 提供下列可定制的包含文件：

### 定制 TOC 标题

`_includes/toc_heading_custom.html`

如果页面有子页面，`has_toc` 未设置 `false`，则会在页面内容最后会[自动生成子页面列表]({{ site.baseurl }}{% link docs/navigation-structure.md %}#auto-generating-table-of-contents)，而列表上边就会出现 TOC 标题——也就是目录标题。

#### 示例
{: .no_toc }

修改默认 TOC 标题为“目录”，创建 `_includes/toc_heading_custom.html`，然后添加：
```html
<h2 class="text-delta">目录</h2>
```

`text-delta` 类（可选）是标题显示为 **目录**{:.text-delta}。

### 定制 Footer

`_includes/footer_custom.html`

本内容出现在每一个主内容之后页面的最下端。更多有关此包含文件信息参阅[配置——Footer 内容]({{ site.baseurl }}{% link docs/configuration.md %}#footer-content)。

### 定制 Head

`_includes/head_custom.html`

添加到这个文件的任何 HTML 都会被插入到 `<head>` 标签关闭之前。这可能包含 `<meta>`、`<link>` 或 `<script>` 标签等。

#### 示例
{: .no_toc }

要添加一个定制的 Favicon，创建 `_includes/head_custom.html`，然后添加：
```html
<link rel="shortcut icon" type="image/png" href="{{site.baseurl}}/path/to/your/favicon.png">
```

### 定制 Header

`_includes/header_custom.html`

此文件内容出现在每个页面主内容顶部——站点搜索和 辅助链接（如果被启用）之间。如果 `search_enabled` 设置为 `false` 并且 `aux_links` 被移除，`header_custom.html` 内容将占掉每个页面顶部的所有空间。

### 定制 Nav Footer

`_includes/nav_footer_custom.html`

此文件内的任何内容都会出现在页面的左下角——站点导航之后。默认情况下显示 Just the Docs 的归属，`This site uses Just the Docs, a documentation theme for Jekyll.`。

### 定制搜索占位符

`_includes/search_placeholder_custom.html`

此文件内容去除 HTML 和前后空格之后将取代默认的搜索框占位文本（也就是其 `aria-label` 属性值）。默认情况下内容是：

{% raw %}

```liquid
Search {{site.title}}
```

{% endraw %}

覆盖此文件重新定义占位符。常见的就是国际化使用；例如，

{% raw %}

```liquid
搜索站点
```

{% endraw %}

占位符文字将变成“搜索站点”。支持[Liquid 代码](https://jekyllrb.com/docs/liquid/) (包括 [Jekyll 变量](https://jekyllrb.com/docs/variables/))。
