---
layout: steps
title: Подсветка кода
date: 2023-09-06 11:00 +0600
description: Сниппет подсветки кода в Jekyll.
image: /images/cover.jpg
published: true
sitemap: true
---

# {{ page.title }}

Пример разметки "Подсветки кода" в Jekyll, которая содержит стилизованные, форматированные данные в виде кода. Поддерживается различный формат html, js, css, php и т.п.

{% highlight js %}
{% raw %}
{% highlight js %}
const func = (b) => {
  let a += b

  return a
}
{% endhighlight %}
{% endraw %}
{% endhighlight %}
