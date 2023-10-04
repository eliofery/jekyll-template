---
layout: steps
title: Список категорий и тегов
date: 2023-09-06 13:00 +0600
description: Сниппет вывода списка категорий и тегов в Jekyll.
image: /images/cover.jpg
published: true
sitemap: true
---

# {{ page.title }}

## Категории

Пример вывода списка категорий в Jekyll.

{% highlight md %}
{% raw %}
{% for category in site.categories %}
  {{ category[0] }} - Название категории
  {{ category[1] }} - Посты категории

  {% for post in category[1] %}
    {{ post.url }}        - Ссылка на пост
    {{ post.title }}      - Заголовок поста
  {% endfor %}

{% endfor %}
{% endraw %}
{% endhighlight %}

Определенная категория.

{% highlight md %}
{% raw %}
{% for post in site.categories.html limit: 2 offset: 0 %} ... {% endfor %}
{% for post in site.categories.css limit: 3 offset: 2 %} ... {% endfor %}
{% endraw %}
{% endhighlight %}

## Теги

{% highlight md %}
{% raw %}
{% for tag in site.tags %}
  {{ tag }} - Название тега

  {% for post in tag[1] %}
    {{ post.url }}        - Ссылка на пост
    {{ post.title }}      - Заголовок поста
  {% endfor %}

{% endfor %}
{% endraw %}
{% endhighlight %}

Определенный тег.

{% highlight md %}
{% raw %}
{% for post in site.tags.html limit: 2 offset: 0 %} ... {% endfor %}
{% for post in site.tags.css limit: 3 offset: 2 %} ... {% endfor %}
{% endraw %}
{% endhighlight %}
