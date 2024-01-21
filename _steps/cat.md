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

Вывод записей.

{% highlight html %}
{% raw %}
{% if paginator.posts[0] %}
{% for post in paginator.posts %}
<h2>{{ post.title }}</h2>
<time datetime="{{ post.date | date: "%Y-%m-%dT%H:%M" }}">{{ post.date | date: "%d.%m.%Y" }}</time>
<div>{{ post.description }}</div>
{% endfor %}
{% endif %}
{% endraw %}
{% endhighlight %}

Вывод пагинации.

{% highlight html %}
{% raw %}
{% if paginator.page_trail %}
  <ol>
    {% if paginator.previous_page %}
    <li>
      <a href="{{ paginator.previous_page_path }}">Предыдущее</a>
    </li>
    {% endif %}

    {% for trail in paginator.page_trail %}
    {% if page.url == trail.path %}
      {% assign active = 'page-pagination__item--active' %}
    {% else %}
      {% assign active = '' %}
    {% endif %}
    <li>
      <a href="{{ trail.path | remove: 'index.html' }}">{{ trail.num }}</a>
    </li>
    {% endfor %}
  
    {% if paginator.next_page %}
    <li>
      <a href="{{ paginator.next_page_path }}">Следующее</a>
    </li>
    {% endif %}
  </ol>
{% endif %}
{% else %}
  <p>Записей нет</p>
{% endif %}
{% endraw %}
{% endhighlight %}

Упорядоченный список категорий.

В файле **_config.yml** составить список доступных категорий в нужном порядке:

{% highlight html %}
# Порядок категорий
categories-order:
  - one
  - two
  - three
  - jekyll
{% endhighlight %}

В разметке страницы вывести список категорий с количеством записей в них:

{% highlight html %}
{% raw %}
  {% for cat in site.categories-order %}
    <a class="category-list__link" href="{{ site.baseurl }}/{{ cat }}">
      {{ cat | capitalize }} ({{ site.categories[cat].size }})
    </a>
  {% endfor %}
{% endraw %}
{% endhighlight %}

Не упорядоченный список категорий.

{% highlight html %}
{% raw %}
{% for category in site.categories %}
{% capture category_name %}{{ category | first | slugify }}{% endcapture %}
  <a class="category-list__link" href="{{ site.baseurl }}/{{ category_name }}">
    {{ category_name | capitalize }} ({{ category[1].size }})
  </a>
{% endfor %}
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
