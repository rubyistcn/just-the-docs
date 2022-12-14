---
layout: default
title: 配置
nav_order: 2
---

# 配置
{: .no_toc }

Just the Docs 有些特定参数可在您的 Jekyll 站点的 \_config.yml 文件中配置。
{: .fs-6 .fw-300 }

## 目录
{: .no_toc .text-delta }

1. TOC
{:toc}

---

查看本站 [\_config.yml](https://github.com/just-the-docs/just-the-docs/tree/main/_config.yml) 文件可做为一个示范。

## 站点 Logo

```yaml
# Set a path/url to a logo that will be displayed instead of the title
logo: "/assets/images/just-the-docs.png"
```

## 搜索

```yaml
# Enable or disable the site search
# Supports true (default) or false
search_enabled: true

search:
  # Split pages into sections that can be searched individually
  # Supports 1 - 6, default: 2
  heading_level: 2
  # Maximum amount of previews per search result
  # Default: 3
  previews: 3
  # Maximum amount of words to display before a matched word in the preview
  # Default: 5
  preview_words_before: 5
  # Maximum amount of words to display after a matched word in the preview
  # Default: 10
  preview_words_after: 10
  # Set the search token separator
  # Default: /[\s\-/]+/
  # Example: enable support for hyphenated search words
  tokenizer_separator: /[\s/]+/
  # Display the relative url in search results
  # Supports true (default) or false
  rel_url: true
  # Enable or disable the search button that appears in the bottom right corner of every page
  # Supports true or false (default)
  button: false
```

## Mermaid 图表

最低配置也需要在 `_config.yml` 中设定 `version` ([from jsDelivr](https://cdn.jsdelivr.net/npm/mermaid/)) 的值:

```yaml
mermaid:
  # Version of mermaid library
  # Pick an available version from https://cdn.jsdelivr.net/npm/mermaid/
  version: "9.1.3"
```

查阅[代码相关文档]({{ site.baseurl }}{% link docs/ui-components/code.md %}#mermaid-diagram-code-blocks)获取更多配置选项和信息。

## 辅助链接

```yaml
# Aux links for the upper right navigation
aux_links:
  "Just the Docs on GitHub":
    - "//github.com/just-the-docs/just-the-docs"

# Makes Aux links open in a new tab. Default is false
aux_links_new_tab: false
```

## 标题锚点链接

```yaml
# Heading anchor links appear on hover over h1-h6 tags in page content
# allowing users to deep link to a particular heading on a page.
#
# Supports true (default) or false
heading_anchors: true
```

## 外部导航类链接

外部链接可以通过 `nav_external_links` 选项添加到导航。查阅[导航结构]({{ site.baseurl }}{% link docs/navigation-structure.md %}#external-navigation-links)获取更多信息。

## Footer 内容

```yaml
# Footer content
# appears at the bottom of every page's main content
# Note: The footer_content option is deprecated and will be removed in a future major release. Please use `_includes/footer_custom.html` for more robust markup / liquid-based content.
footer_content: "Copyright &copy; 2017-2020 Patrick Marsceill. Distributed by an <a href=\"https://github.com/just-the-docs/just-the-docs/tree/main/LICENSE.txt\">MIT license.</a>"

# Footer last edited timestamp
last_edit_timestamp: true # show or hide edit time - page must have `last_modified_date` defined in the frontmatter
last_edit_time_format: "%b %e %Y at %I:%M %p" # uses ruby's time format: https://ruby-doc.org/stdlib-2.7.0/libdoc/time/rdoc/Time.html

# Footer "Edit this page on GitHub" link text
gh_edit_link: true # show or hide edit this page link
gh_edit_link_text: "Edit this page on GitHub."
gh_edit_repository: "https://github.com/just-the-docs/just-the-docs" # the github URL for your repo
gh_edit_branch: "main" # the branch that your docs is served from
# gh_edit_source: docs # the source that your files originate from
gh_edit_view_mode: "tree" # "tree" or "edit" if you want the user to jump into the editor immediately
```

_注记_：`footer_content` 已经被声明弃用，但是现在还支持。更好的体验我们已经将其移入一个叫做 `_includes/footer_custom.html` 的文件（该文件允许更强标记系统——基于 Liquid 的内容）。_

- “页面最后修改”数据只有当页面有叫做 `last_modified_date` 的值时才显示，数据格式使用可读日期格式
- `last_edit_time_format` 使用 Ruby 的 DateTime 格式；查阅示例和更多信息[在此链接](https://apidock.com/ruby/DateTime/strftime)。
- `gh_edit_repository` 是项目 GitHub 源码库的 URL
- `gh_edit_branch` 是文档站点服务来自哪个分支；默认是 `main`
- `gh_edit_source` 是您的项目文件存储(应该类似于 [site.source](https://jekyllrb.com/docs/configuration/options/))的源文件目录
- `gh_edit_view_mode` 默认是 `"tree"`，会带用户到 GitHub 页面；启用 `"编辑"` 会带用户进入编辑模式

## 色系

```yaml
# Color scheme supports "light" (default) and "dark"
color_scheme: dark
```

<button class="btn js-toggle-dark-mode">预览暗色系方案</button>

<script>
const toggleDarkMode = document.querySelector('.js-toggle-dark-mode');

jtd.addEvent(toggleDarkMode, 'click', function(){
  if (jtd.getTheme() === 'dark') {
    jtd.setTheme('light');
    toggleDarkMode.textContent = '预览暗色系方案';
  } else {
    jtd.setTheme('dark');
    toggleDarkMode.textContent = '返回亮色系';
  }
});
</script>

查阅[定制]({{ site.baseurl }}{% link docs/customization.md %})获取更多信息。

## 标注

使用此功能，您需要为每一种您想使用的标注配置一个 `color` 和 `title`（可选），例如：

```yaml
callouts:
  warning:
    title: Warning
    color: red
```

本例使用颜色 `$red-000` 做标注背景色，使用颜色 `$red-300` 做 title 和盒子装饰。[^dark]您可以用 `warning` 标注美化一个段落：

```markdown
{: .warning }
A paragraph...
```

[^dark]:
    如果您使用 `dark` 色系方案，此标注用 `$red-300` 做背景色，用 `$red-000` 设定 title。

颜色 `grey-lt`、`grey-dk`、`purple`、`blue`、`green`、`yellow` 和 `red` 是预定义的；要使用定制颜色，您需要在您的 SCSS 文件中定义它的 `000` 到 `300` 层。例如，要用 `pink`，在您的 `_sass/custom/custom.scss` 文件中添加下面代码：

```scss
$pink-000: #f77ef1;
$pink-100: #f967f1;
$pink-200: #e94ee1;
$pink-300: #dd2cd4;
```

您可以覆盖默认背景色的 `opacity`，设定一个特殊的标注，例如：

```yaml
callouts:
  custom:
    color: pink
    opacity: 0.3
```

您可以修改所有标注默认的 opacity (`0.2`) ，例如：

```yaml
callouts_opacity: 0.3
```

您还可以调整标注的 overall 层。`callouts_level` 的值是 `quiet` 或 `loud`；`loud` 增加了背景的饱和度和亮度。当使用 `light` 或者定制色彩方案时默认级为 `quiet`，使用 `暗色色彩方案` 时是 `loud`。

查阅[标注]({{ site.baseurl }}{% link docs/ui-components/callouts.md %})获取更多信息。

## Google 分析

```yaml
# Google Analytics Tracking (optional)
# e.g, UA-1234567-89
ga_tracking: UA-5555555-55
ga_tracking_anonymize_ip: true # Use GDPR compliant Google Analytics settings (true by default)
```

## 文档专题

默认情况下，导航和搜索都会包括普通[页面](https://jekyllrb.com/docs/pages/)。您可以使用 [Jekyll 专题](https://jekyllrb.com/docs/collections/)聚合语义相关文档。

例如，将所有测试文件放入 `_tests` 文件夹，创建 `tests` 专题：

```yaml
# 定义 Jekyll 专题
collections:
  # 定一个叫做 "tests" 的专题，其文件都在 "_tests" 文件夹内
  tests:
    permalink: "/:collection/:path/"
    output: true

just_the_docs:
  # 定义 just-the-docs 内的专题
  collections:
    # 定义 "tests" 专题
    tests:
      # 给定专题名字
      name: Tests
      # 导航中不包括的专题
      # 支持 true 或 false （默认值）
      # nav_exclude: true
      # 导航内专题可折叠
      # 支持 true 或 false （默认值）
      # nav_fold: true
      # 搜索不包含专题
      # 支持 true 或 false （默认值）
      # search_exclude: true
```

导航默认会显示（除专题外）所有普通页面（如果有）。

您可以使用多个专题。这会用配置的名字在导航中创建分类。

```yaml
collections:
  tests:
    permalink: "/:collection/:path/"
    output: true
  tutorials:
    permalink: "/:collection/:path/"
    output: true

just_the_docs:
  collections:
    tests:
      name: Tests
    tutorials:
      name: Tutorials
```

当您的**所有**页面在一个专题中时，它的名字就不会显示了。

导航中每个专题都是其页面标题的独立命名空间：一个专题的一个页面不能是别的专题的子页面或普通页面。
