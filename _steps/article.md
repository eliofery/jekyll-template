---
layout: steps
title: Список записей
date: 2023-09-06 12:00 +0600
description: Сниппет вывода различных типов записей в Jekyll.
image: /images/cover.jpg
published: true
sitemap: true
---

# {{ page.title }}

Пример вывода различных типов записей в Jekyll.

## Вывод записей типа "Коллекция"

{% highlight html %}
{% raw %}
{% for step in site.steps limit: 10 offset: 0 | sort: 'date' | reverse %}
  <h2>{{ step.title }}</h2>
  <p>{{ step.content | markdownify }}</p>
{% endfor %}
{% endraw %}
{% endhighlight %}

## Вывод записей типа "Статья"

{% highlight html %}
{% raw %}
{% for post in site.posts limit: 10 offset: 0 | sort: 'date' | reverse %}
  <h2>{{ post.title }}</h2>
  <p>{{ post.content | markdownify }}</p>
{% endfor %}
{% endraw %}
{% endhighlight %}

## Вывод записей типа "Страница"

{% highlight html %}
{% raw %}
{% for page in site.pages limit: 10 offset: 0 | sort: 'date' | reverse %}
  <h2>{{ page.title }}</h2>
  <p>{{ page.content | markdownify }}</p>
{% endfor %}
{% endraw %}
{% endhighlight %}
