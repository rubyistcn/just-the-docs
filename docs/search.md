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

Just the Docs 使用 [lunr.js](http://lunrjs.com) 添加了客户端的由 Jekyll 生成的基于 JSON 的索引的搜索界面。所有搜索结果以一个自动完成的样式界面显示（没有搜索结果页面）。默认情况下，所有生成的 HTML 页面通过下面数据点来索引：

- Page title
- Page content
- Page URL

## 在配置中启用搜索

在您的站点的 `_config.yml` 中启用搜索：

```yaml
# Enable or disable the site search
# Supports true (default) or false
search_enabled: true
```

### Search granularity

Pages are split into sections that can be searched individually.
The sections are defined by the headings on the page.
Each section is displayed in a separate search result.

```yaml
# Split pages into sections that can be searched individually
# Supports 1 - 6, default: 2
search.heading_level: 2
```

### Search previews

A search result can contain previews that show where the search words are found in the specific section.

```yaml
# Maximum amount of previews per search result
# Default: 3
search.previews: 3

# Maximum amount of words to display before a matched word in the preview
# Default: 5
search.preview_words_before: 5

# Maximum amount of words to display after a matched word in the preview
# Default: 10
search.preview_words_after: 10
```

### Search tokenizer

The default is for hyphens to separate tokens in search terms:
`gem-based` is equivalent to `gem based`, matching either word.
To allow search for hyphenated words:

```yaml
# Set the search token separator
# Default: /[\s\-/]+/
# Example: enable support for hyphenated search words
search.tokenizer_separator: /[\s/]+/
```

### Display URL in search results

```yaml
# Display the relative url in search results
# Supports true (default) or false
search.rel_url: false
```

### Display search button

The search button displays in the bottom right corner of the screen and triggers the search input when clicked.

```yaml
# Enable or disable the search button that appears in the bottom right corner of every page
# Supports true or false (default)
search.button: true
```

## Hiding pages from search

Sometimes you might have a page that you don't want to be indexed for the search nor to show up in search results, e.g, a 404 page.
To exclude a page from search, add the `search_exclude: true` parameter to the page's YAML front matter:

#### Example

{: .no_toc }

```yaml
---
layout: default
title: Page not found
nav_exclude: true
search_exclude: true
---

```

## Generate search index when used as a gem

If you use Just the Docs as a remote theme, you do not need the following steps.

If you use the theme as a gem, you must initialize the search by running this `rake` command that comes with `just-the-docs`:

```bash
$ bundle exec just-the-docs rake search:init
```

This command creates the `assets/js/zzzz-search-data.json` file that Jekyll uses to create your search index.
Alternatively, you can create the file manually with [this content]({{ site.github.repository_url }}/blob/main/assets/js/zzzz-search-data.json).
