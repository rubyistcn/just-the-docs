---
layout: default
title: Markdown 语法展示
nav_order: 99
---

<button class="btn js-toggle-dark-mode">预览暗色系主题</button>

<script>
const toggleDarkMode = document.querySelector('.js-toggle-dark-mode');

jtd.addEvent(toggleDarkMode, 'click', function(){
  if (jtd.getTheme() === 'dark') {
    jtd.setTheme('light');
    toggleDarkMode.textContent = '预览暗色系主题';
  } else {
    jtd.setTheme('dark');
    toggleDarkMode.textContent = '返回亮色系主题';
  }
});
</script>

文字可以是 **粗体**，_斜体_，或者 ~~划线~~。

[链接到另一个页面](another-page).

两个段落之间应该留下空行。

两个段落之间应该留下空行。我们推荐包含一个 README，或者一个关于您的项目信息的文件。

# [](#标题-1)标题 1

这是一个标题下的普通段落。GitHub 是一个基于版本控制和协作的代码托管平台。它能让您随时随地都可以都可以参与到项目工作中。

## [](#标题-2)标题 2

> 这是一个标题下的块引用（blockquote）。
>
> 君子有所为有所不为。知其可为而为之，知其不可为而不为，是谓君子为与不为之道也。不知不可为而为之，愚人也；知其不可为而不为，贤人也；知其不可为而为之，圣人也。

### [](#标题-3)标题 3

```js
// 带语法高亮的 Javascript 代码
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# 带语法高亮的 Ruby 代码
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### [](#标题-4)标题 4 `带有不变形代码`

*   这是一个标题下的无序列表。
*   这是一个标题下的无序列表。
*   这是一个标题下的无序列表。

##### [](#标题-5)标题 5

1.  这是一个标题下的有序列表。
2.  这是一个标题下的有序列表。
3.  这是一个标题下的有序列表。

###### [](#标题-6)标题 6

[这是一个用来演示被封装到一起的非常非常非常长的文字描述虽然它很长很长它可能会回行但是不会导致溢出](.)的行。

- [这是一个用来演示被封装到一起的非常非常非常长的文字描述虽然它很长很长它可能会回行但是不会导致溢出](.)的列表。

| 表头 1       | 表头 2             | 3    |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### 下面是一条水平线

* * *

### 这是一个无序列表：

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### 和一个有序列表：

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### 和一个有序列表，继续：

1.  Item one
1.  Item two

一些文字

{:style="counter-reset:none"}
1.  Item three
1.  Item four

### 和一个始于 42 的有序列表：

{:style="counter-reset:step-counter 41"}
1.  Item 42
1.  Item 43
1.  Item 44

### 和一个嵌套的列表：

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### 在一个无序列表里嵌套一个有序列表，然后在有序列表里又嵌套一个无序列表

- level 1 item (ul)
  1. level 2 item (ol)
  1. level 2 item (ol)
    - level 3 item (ul)
    - level 3 item (ul)
- level 1 item (ul)
  1. level 2 item (ol)
  1. level 2 item (ol)
    - level 3 item (ul)
    - level 3 item (ul)
  1. level 4 item (ol)
  1. level 4 item (ol)
    - level 3 item (ul)
    - level 3 item (ul)
- level 1 item (ul)

### 和一个任务单

- [ ] Hello, this is a TODO item
- [ ] Hello, this is another TODO item
- [x] Goodbye, this item is done

### 嵌套的任务单

- [ ] level 1 item (task)
   - [ ] level 2 item (task)
   - [ ] level 2 item (task)
- [ ] level 1 item (task)
- [ ] level 1 item (task)

### 在一个任务列表里嵌套无序列表

- [ ] level 1 item (task)
   - level 2 item (ul)
   - level 2 item (ul)
- [ ] level 1 item (task)
- [ ] level 1 item (task)

### 在一个无序列表里嵌套任务列表

- level 1 item (ul)
   - [ ] level 2 item (task)
   - [ ] level 2 item (task)
- level 1 item (ul)
- level 1 item (ul)

### 小图

![](../../assets/images/small-image.jpg)

### 大图

![](../../assets/images/large-image.jpg)

"[Wroclaw University Library digitizing rare archival texts](https://www.flickr.com/photos/97810305@N08/9401451269)" by [j_cadmus](https://www.flickr.com/photos/97810305@N08) is marked with [CC BY 2.0](https://creativecommons.org/licenses/by/2.0/?ref=openverse).

### 标签

I'm a label
{: .label }

blue
{: .label .label-blue }
green
{: .label .label-green }
purple
{: .label .label-purple }
yellow
{: .label .label-yellow }
red
{: .label .label-red }

**bold**
{: .label }
*italic*
{: .label }
***bold + italic***
{: .label }

### 基于 HTML 语法的定义列表。

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

#### 多个描述术语和值

Term
: Brief description of Term

Longer Term
: Longer description of Term,
  possibly more than one line

Term
: First description of Term,
  possibly more than one line

: Second description of Term,
  possibly more than one line

Term1
Term2
: Single description of Term1 and Term2,
  possibly more than one line

Term1
Term2
: First description of Term1 and Term2,
  possibly more than one line

: Second description of Term1 and Term2,
  possibly more than one line

### 更多代码

```python{% raw %}
def dump_args(func):
    "This decorator dumps out the arguments passed to a function before calling it"
    argnames = func.func_code.co_varnames[:func.func_code.co_argcount]
    fname = func.func_name
    def echo_func(*args,**kwargs):
        print fname, ":", ', '.join(
            '%s=%r' % entry
            for entry in zip(argnames,args) + kwargs.items())
        return func(*args, **kwargs)
    return echo_func

@dump_args
def f1(a,b,c):
    print a + b + c

f1(1, 2, 3)

def precondition(precondition, use_conditions=DEFAULT_ON):
    return conditions(precondition, None, use_conditions)

def postcondition(postcondition, use_conditions=DEFAULT_ON):
    return conditions(None, postcondition, use_conditions)

class conditions(object):
    __slots__ = ('__precondition', '__postcondition')

    def __init__(self, pre, post, use_conditions=DEFAULT_ON):
        if not use_conditions:
            pre, post = None, None

        self.__precondition  = pre
        self.__postcondition = post
{% endraw %}```

```
如果单行的代码块很长很长时不应该封装。当单行代码太长时它们应该使呈现为水平滚动状态。本行就是要增加长度到很长很长，现在应该是足够长了，可以演示这个功能了。
```

### Mermaid 图表

当 `mermaid` 值在 `_config.yml` 里设定时，下列代码显示为一个图表。

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```


```
最后一个元素。
```
