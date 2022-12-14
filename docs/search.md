---
layout: default
title: 搜索
nav_order: 7
---

# 搜索
{: .no_toc }

## 目录
{: .no_toc .text-delta }

1. TOC
{:toc}

---

Just the Docs 利用 [lunr.js](http://lunrjs.com) 添加了客户端的搜索（由 Jekyll 生成的基于 JSON 的索引）。所有搜索结果以一个自动完成的样式界面显示（没有搜索结果页面）。默认情况下，所有生成的 HTML 页面通过下面数据点来进行索引：

- Page title
- Page content
- Page URL

## 在配置中启用搜索

在您的站点的 `_config.yml` 中启用搜索：

```yaml
# 启用或者关闭站点搜索
# 支持 true （默认）或 false
search_enabled: true
```

### 搜索力度

页面会被分成可被搜索的多个独立部分。各部分由页面的标题划分。每个部分会在不同的搜索结果中显示。

```yaml
# 将页面分为可被独立搜索的各个部分
# 支持 1 - 6，默认：2
search.heading_level: 2
```

### 搜索预览

搜索结果可预览搜索词被匹配的部分。

```yaml
# 每个搜索结果的最多预览数
# 默认：3
search.previews: 3

# 预览中匹配词前的最多显示词个数
# 默认：5
search.preview_words_before: 5

# 预览中匹配词后的最多显示词个数
# 默认：10
search.preview_words_after: 10
```

### 搜索分词器

搜索时连词符默认为分词符号：
`gem-based` 等同于 `gem based`，两个词都需要匹配。要允许使用连词符搜索：

```yaml
# 设置搜索分词器
# 默认：/[\s\-/]+/
# 示例：启用搜索词中对于连词符的支持
search.tokenizer_separator: /[\s/]+/
```

### 在搜索结果中显示 URL

```yaml
# 在搜索结果中显示相对 URL
# 支持 true (default) 或者 false 值
search.rel_url: false
```

### 显示搜索按钮

搜索按钮在屏幕的右下角显示，当点击时触发搜索输入框。

```yaml
# 启用或者关闭会出现在每个页面右下角的搜索按钮
# 支持 true 或 false （默认）
search.button: true
```

## 搜索中隐藏页面

有时有些页面您不相让它们被搜索索引也不想让人它们在检索结果中显示，例如 404 页面。
从搜索中排出一个页面，在页面的 YAML 格式元数据（Front Matter）中添加 `search_exclude: true` 参数:

#### 示例

{: .no_toc }

```yaml
---
layout: default
title: Page not found
nav_exclude: true
search_exclude: true
---

```

## 基于 Gem 生成搜索索引

如果您使用 Just the Docs 做为远程主题，您不需要下面的步骤。

如果您使用 Gem 主题，您需要初始化搜索通过与 `just-the-docs` 一起运行这个 `rake` 命令：

```bash
$ bundle exec just-the-docs rake search:init
```

此命令生成 `assets/js/zzzz-search-data.json` 文件（Jekyll 用来生成搜索索引）。
此外，您也可以手动用[这个内容]({{ site.github.repository_url }}/blob/main/assets/js/zzzz-search-data.json)生成索引。
