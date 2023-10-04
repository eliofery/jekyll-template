---
layout: steps
title: Анонс и полное содержимое
date: 2023-09-06 13:00 +0600
description: Сниппет вывода анонса и полного содержимого в Jekyll.
image: /images/cover.jpg
published: true
sitemap: true
---

# {{ page.title }}

Пример вывода анонса и полного содержимого в Jekyll.

{% highlight md %}
{% raw %}
---
layout: post
title: Заголовок
date: 2023-04-21 12:56 +0600
description: Описание
image: cover.jpg
thumbnail: cover.jpg
categories: []
tags: []
published: true
sitemap: true
excerpt_separator: <!--more-->
---

Краткое содержимое

<!--more-->

Полное содержимое
{% endraw %}
{% endhighlight %}

Затем в шаблоне.

{% highlight md %}
{% raw %}
{{ post.excerpt | markdownify | strip_html | truncatewords: 40 }}
{% endraw %}
{% endhighlight %}

Или.

{% highlight md %}
{% raw %}
{% assign separator_size = '<!--more-->' | size %}
{% assign size_excerpt = page.excerpt | size | plus: separator_size %}
{% assign size_content = page.content | size %}

{{ page.content | slice: size_excerpt, size_content }}
{% endraw %}
{% endhighlight %}
