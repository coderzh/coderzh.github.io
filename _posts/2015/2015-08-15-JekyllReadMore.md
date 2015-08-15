---
layout: post
title: 使用Jekyll官方的ReadMore摘要功能
category: 技术文章
---

今天才发现，Jekyll官方就支持ReadMore摘要功能，记录一下。

<!-- more -->

我之前的方法，在index.html中

```html
{% raw %} {{ post.content ||split:'<!-- more -->' | first }} {% endraw %}
```

然后在Post里，需要分隔的摘要后面加`<!-- more -->。`

```html
摘要内容...
<!-- more -->
正文内容...
```

### 官方做法: excerpt

官方的方法是，在_config.yml里，指定摘要的分隔符：

```html
excerpt_separator:  '<!-- more -->'
```

然后，在index.html中：

```html
{% raw %} {{ post.excerpt }} {% endraw %}
```

一般情况下，摘要需要去掉html标签，所以一般这样用：

```html
 {% raw %} {{ post.excerpt | strip_html }} {% endraw %}
```

然后，和前一种方法一样，在摘要后面加`<!-- more -->`  即可。


