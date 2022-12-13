---
layout: default
title: 首页
nav_order: 1
description: "Just the Docs 是一款自适应 Jekyll 主题（内建容易定制的搜索，可以托管于 GitHub Pages）。"
permalink: /
---

# 聚焦编写漂亮文档
{: .fs-9 }

Just the Docs 用一款易定制、可在 GitHub Pages 托管的自适应 Jekyll 主题助力您的文档编写。
{: .fs-6 .fw-300 }

[即刻上手](#起步){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[在 GitHub 查看源码][Just the Docs 源码库]{: .btn .fs-5 .mb-4 .mb-md-0 }

---

{: .warning }
> 本文档所述功能基于 Just the Docs 主题的当前 `main` 分支。查看[版本备注]({{ site.baseurl }}{% link CHANGELOG.md %})可知更详细的版本、新功能和问题修复等。

Just the Docs 是一款可生成静态站点的 [Jekyll] 主题。您可以使用 [Markdown]、[Liquid] 模板语言和 HTML 来编写网页的源文件。[^1] Jekyll 通过转换所有带有 [front matter] 的文件为 HTML 从而构建站点。您的 [Jekyll 配置]文件决定了用哪个主题以及站点设置常用参数（例如主页的 URL 等）。

Jekyll 就是使用了本主题构建的 Just the Docs 主题文档。这些网页展示了当您使用此主题时网页的*默认*样子。但是您可以很容易*[定制]*主题，使其看起来完全不同！

浏览文档学习如何使用本主题。

## 起步

[Just the Docs 模板]提供了最简洁、快速、容易的方式创建启用 Just the Docs 主题的新站点。要通过创建一个新站点起步，就点击“[使用模板]”！

{: .note }
使用主题您***不***需要复制 [Just the Docs 源码库]！只有您想要在本地浏览主题文档、辅助开发主题或者基于 Just the Docs 开发新主题时才需要复制源码库。

您能很容易地通过模板创建站点然后发布到 [GitHub Pages] —— [模板 README] 文件说明了如何运行等相关细节。

如果您的计算机安装了 [Jekyll]，您可以在*本地*构建和预览创建的站点。这可以让您在提交到代码库前就可以测试修改，以免提交到 GitHub Pages 后才能看到结果。[^2]这样您也可以将您的站点部署到不止 GitHub Pages 平台。

更具体点儿，创建站点：

- 用 gem 方法，例如，用 `Gemfile` 加载 `just-the-docs` gem
- 用 [GitHub Pages / Actions workflow] 构建和发布站点到 GitHub Pages

除此之外，您还可以随意定制您用模板创建的站点。您可以轻松的修改 `just-the-docs` 和 Jekyll 的版本，添加更多的插件。

{: .note }
查看主题 [README][Just the Docs README] 获取更多不必创建新站点而以 Gem 方式使用主题的信息。

## 关于项目

Just the Docs &copy; 2017-{{ "now" | date: "%Y" }} 由 [Patrick Marsceill](http://patrickmarsceill.com) 编写。

### 许可

Just the Docs 基于 [MIT 许可](https://github.com/just-the-docs/just-the-docs/tree/main/LICENSE.txt)分发。

### 贡献

当您想要为这个代码库做贡献的时候，请先通过 Issue、电子邮件或其他方式同代码库的所有者讨论您想要做的修改。阅读更多关于成为[我们的 GitHub 代码库](https://github.com/just-the-docs/just-the-docs#contributing)的贡献者相关细节。

#### 感谢 Just the Docs 的贡献者！

<ul class="list-style-none">
{% for contributor in site.github.contributors %}
  <li class="d-inline-block mr-1">
     <a href="{{ contributor.html_url }}"><img src="{{ contributor.avatar_url }}" width="32" height="32" alt="{{ contributor.login }}"></a>
  </li>
{% endfor %}
</ul>

### 代码规范

Just the Docs 承诺培养一个友善的社区。

在我们的 GitHub 代码库[查看我们的代码规范](https://github.com/just-the-docs/just-the-docs/tree/main/CODE_OF_CONDUCT.md)。

----

[^1]: [本页源文件]使用了全部三种标记语言。

[^2]: [在 GitHub 只需十分钟就可以修改您的站点并发布](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll#creating-your-site).

[Jekyll]: https://jekyllrb.com
[Markdown]: https://daringfireball.net/projects/markdown/
[Liquid]: https://github.com/Shopify/liquid/wiki
[Front matter]: https://jekyllrb.com/docs/front-matter/
[Jekyll 配置]: https://jekyllrb.com/docs/configuration/
[本页源文件]: https://github.com/just-the-docs/just-the-docs/blob/main/index.md
[Just the Docs 模板]: https://just-the-docs.github.io/just-the-docs-template/
[Just the Docs]: https://just-the-docs.github.io/just-the-docs/
[Just the Docs 源码库]: https://github.com/just-the-docs/just-the-docs
[Just the Docs README]: https://github.com/just-the-docs/just-the-docs/blob/main/README.md
[GitHub Pages]: https://pages.github.com/
[模板 README]: https://github.com/just-the-docs/just-the-docs-template/blob/main/README.md
[GitHub Pages / Actions workflow]: https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/
[定制]: {{ site.baseurl }}{% link docs/customization.md %}
[使用模板]: https://github.com/just-the-docs/just-the-docs-template/generate
