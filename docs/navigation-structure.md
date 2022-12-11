---
layout: default
title: 导航结构
nav_order: 5
---

# 导航结构
{: .no_toc }

<details open markdown="block">
  <summary>
    目录
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## 主导航

Just the Docs 站点的主导航在大屏幕时的左侧（小屏时的顶部）。主导航被设计成了一个可容纳多级菜单的系统（页面可以有子页面以及孙页面）。

默认情况下，所有页面在主导航中会显示为顶级页面，除非有页面被定页为父页面（参阅[带子页面的页面](#p带子页面的页面)）。

---

## 页面顺序

定义页面顺序，您可以在您的页面的 YAML 格式的元数据（Front Matter）中使用 `nav_order` 参数。

#### 示例
{: .no_toc }

```yaml
---
layout: default
title: Customization
nav_order: 4
---

```

参数值定义了顶级页面的顺序，以及具有相同父页面的子页面的顺序。您可以对子页面的子页面重复使用这些参数值（例如，从 1 开始的整数）。

参数值可以是数字（整数，小数）和（或）字符串。带有数字 `nav_order` 参数的页面总是在带有字符 `nav_order` 参数的页面前面。当省略 `nav_order` 参数时，默认使用页面标题顺序。如果您想让页面顺序不依赖页面标题，需要为每个页面设置精准的 `nav_order` 参数。所有具有精准 `nav_order` 参数的页面会出现在依赖 `title` 值排序的页面前面。

默认情况下，所有大写字母会出现在小写字母前面；您可以通过在配置文件中添加 `nav_sort: case_insensitive` 来忽略大小写。字符用引号（单引号或双引号）封闭是可选的。数字值不能用引号封闭，例如 `42`、`-1.0`；引号内的数字将会按照字符顺序排列，而不是按照数值大小排列，所以 `"10"` 会在 `"2"` 之前。

---

## 不包含页面

对于特定不想包含在主导航中的页面，例如 404 页面或者加载页面，在页面的 YAML 格式元数据中使用 `nav_exclude: true` 参数。

#### 示例
{: .no_toc }

```yaml
---
layout: default
title: 404
nav_exclude: true
---

```

`nav_exclude` 参数不影响[自动生成子页面列表](#自动生成目录)。

无 `title` 页面会自动被主导航排除。

---

## 带子页面的页面

有时您需要创建一个带有子页面（一系列相关内容）的页面。首先，推荐您将相关页面放在一个目录下……例如，在我们这个文档中，我们将所有编写文档的内容都放在了 `./docs` 目录，并且每一部分都在一个子目录下，像 `./docs/ui-components` 和 `./docs/utilities`。这样看起来组织清晰：

```
+-- ..
|-- (Jekyll files)
|
|-- docs
|   |-- ui-components
|   |   |-- index.md  (parent page)
|   |   |-- buttons.md
|   |   |-- code.md
|   |   |-- labels.md
|   |   |-- tables.md
|   |   +-- typography.md
|   |
|   |-- utilities
|   |   |-- index.md      (parent page)
|   |   |-- color.md
|   |   |-- layout.md
|   |   |-- responsive-modifiers.md
|   |   +-- typography.md
|   |
|   |-- (other md files, pages with no children)
|   +-- ..
|
|-- (Jekyll files)
+-- ..
```

在父页面上，添加 YAML 格式元数据：

- `has_children: true` （告诉我们这是一个父页面）

#### 示例
{: .no_toc }

```yaml
---
layout: default
title: UI Components
nav_order: 2
has_children: true
---

```

这里我们设置了 UI 组件加载页（位置在 `/docs/ui-components`），该页有子页面，在主导航的顺序为第二位。

### 子页面

{: .text-gamma }

在子页面里设置 YAML 格式元数据 `parent:` 参数，说明父页面标题，设置导航顺序（此数字仅在同级子页面有效）。

#### 示例
{: .no_toc }

```yaml
---
layout: default
title: Buttons
parent: UI Components
nav_order: 2
---

```

Buttons 页面做为 UI 组件的子页面出现，并且是 UI 组件部分顺序是第二名。

### 子页面顺序

您可以选择添加下列 YAML 格式元数据修改子页面的默认排序为递增还是递减：

- `child_nav_order: desc`

#### 示例
{: .no_toc }
```yaml
---
layout: default
title: Descending Child Pages
child_nav_order: desc
---
```

### 自动生成目录

默认情况下，所有带有子页面的页面会自动在其页面内容之后生成子页面列表目录。关闭这个自动目录，需要在父页面的 YAML 格式元数据中设置 `has_toc: false`。

#### 示例
{: .no_toc }

```yaml
---
layout: default
title: UI Components
nav_order: 2
has_children: true
has_toc: false
---

```

### 带子页面的子页面

{: .text-gamma }

子页面也可以有子页面（孙页面），其做法同前面的模式一样，只不过是用在子页面和孙页面之上。

1. 添加 `has_children` 属性到子页面
1. 添加 `parent` 和 `grand_parent` 属性到孙页面

#### 示例
{: .no_toc }

```yaml
---
layout: default
title: Buttons
parent: UI Components
nav_order: 2
has_children: true
---

```

```yaml
---
layout: default
title: Buttons Child Page
parent: Buttons
grand_parent: UI Components
nav_order: 1
---

```

这将生成下列导航结构：

```
+-- ..
|
|-- UI Components
|   |-- ..
|   |
|   |-- Buttons
|   |   |-- Button Child Page
|   |
|   |-- ..
|
+-- ..
```

{: .note }
当前导航结构限于 3 级：孙页面不能再有子页面。

---

## 附属链接

为您的站点添加附属链接（在所有页面右上方），只需在您的站点的配置文件 `_config.yml` 中添加 `aux_links` [配置选项]({{ site.baseurl }}{% link docs/configuration.md %}#附属链接)即可。

#### 示例
{: .no_toc }

```yaml
# Aux links for the upper right navigation
aux_links:
  "Just the Docs on GitHub":
    - "//github.com/just-the-docs/just-the-docs"
```

---

## 外部导航链接

为导航添加外部链接，需要在站点配置文件 `_config.yml` 中添加 `nav_external_links` [配置]({{ site.baseurl }}{% link docs/configuration.md %})选项。
外部链接会出现在导航的普通页面链接之后，专题之前。

#### 示例
{: .no_toc }

```yaml
# External navigation links
nav_external_links:
  - title: Just the Docs on GitHub
    url: https://github.com/just-the-docs/just-the-docs
    hide_icon: false # set to true to hide the external link icon - defaults to false
```

外部链接会有一个标志链接会离开站点的装饰图标。
您可以通过设置 `hide_icon: true` 来隐藏图标。

---

## 带目录的页内导航

在您的文档页面内生成目录，您可以在 Markdown 的 `<ol>` 方法后马上使用 Kramdown 的 `{:toc}` 方法。这会自动生成一个根据页面的标题和层级相关的带有锚点链接各章节的有序列表。有些时候，有的标题您并不想让其出现在目录中，那么您就可以通过对该标题使用 `{: .no_toc }` CSS 类就可以在生成目录时忽略它。

#### 示例
{: .no_toc }

```markdown
# Navigation Structure
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
```

本示例在生成目录时忽略了页面的名字标题（`#`），同样的还有目录标题自身（`##`）（因为它对于页面内容而言是多余的）。要想得到一个无序列表，用 `- TOC` 替换 `1. TOC` 即可。

### 可折叠目录

目录用 `<details>` 和 `<summary>` 元素打造成了可折叠的，如下例。属性 `open` （目录默认是展开的）和使用样式 `{: .text-delta }` 是可选的。

```markdown
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>
```

最终效果见[本页顶部](#导航结构)（`{:toc}` 每页只能用一次）。
