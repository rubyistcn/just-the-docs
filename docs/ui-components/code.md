---
layout: default
title: 代码
parent: UI 组件
has_children: true
nav_order: 6
---

# 代码
{: .no_toc }

## 目录
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 行内代码

代码可通过用单个反引号封装实现行内渲染。

<div class="code-example" markdown="1">
Lorem ipsum dolor sit amet, `<inline code snippet>` adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.

## 带`<行内代码片段>`的标题。
{: .no_toc }
</div>
```markdown
Lorem ipsum dolor sit amet, `<inline code snippet>` adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.

## Heading with `<inline code snippet>` in it.
```

---

## 语法高亮代码块

通过使用三个反引号加语言名称可以使用 Jekyll 内建的 Rouge 语法高亮代码功能：

<div class="code-example" markdown="1">
```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```
</div>
{% highlight markdown %}
```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```
{% endhighlight %}

---

## 带渲染示例的代码块

要演示前端代码，有时展示一个渲染的示例更有用。After including the styles from your project that you'll need to show the rendering, you can use a `<div>` with the `code-example` class, followed by the code block syntax. If you want to render your output with Markdown instead of HTML, use the `markdown="1"` attribute to tell Jekyll that the code you are rendering will be in Markdown format... This is about to get meta...

<div class="code-example" markdown="1">

<div class="code-example" markdown="1">

[Link button](http://example.com/){: .btn }

</div>
```markdown
[Link button](http://example.com/){: .btn }
```

</div>
{% highlight markdown %}
<div class="code-example" markdown="1">

[Link button](http://example.com/){: .btn }

</div>
```markdown
[Link button](http://example.com/){: .btn }
```
{% endhighlight %}

---

## Mermaid 图表代码块

[Mermaid](https://mermaid-js.github.io/mermaid/) 允许您通过 Markdown 代码块添加图表和可视化。**默认不支持**。然而，您可以通过在 `_config.yml` 添加一个 `mermaid` 值使其支持 Mermaid。

最小配置需要一个 `version` 值（在 [jsDelivr](https://cdn.jsdelivr.net/npm/mermaid/)匹配版本）：

```yaml
mermaid:
  # Version of mermaid library
  # Pick an available version from https://cdn.jsdelivr.net/npm/mermaid/
  version: "9.1.3"
```

更多配置选项加载可通过 `_includes/mermaid_config.js` 进行。默认情况下，文件内容是空对象：

```js
// _includes/mermaid_config.js
{}
```

这将加载默认设置。

对象内容应遵循 [Mermaid's 配置 API](https://mermaid-js.github.io/mermaid/#/./Setup?id=configuration)。例如，覆盖主题，修改 `_includes/mermaid_config.js` 为：

```js
// _includes/mermaid_config.js
{
  theme: "forest"
}
```

一旦 Mermaid 安装成功，就可以在 Markdown 文件中使用。用 Markdown 做一个简单的流程图示例应该像这样：

{% highlight markdown %}
```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```
{% endhighlight %}

渲染为：

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

*注记：基于演示原因，我们在此站点启用了 Mermaid。默认它还是关闭的，用户需要使用时还需要选择性开启。*
