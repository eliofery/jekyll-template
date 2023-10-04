---
layout: steps
title: Поиск по сайту
date: 2023-09-08 10:00 +0600
description: Сниппет вывода поиска в Jekyll.
image: /images/cover.jpg
published: true
sitemap: true
---

# {{ page.title }}

Пример вывода поиска в Jekyll.

Основная суть в использовании поиска для статического сайта на **Jekyll** это получение данных нужных типов записей в виде **Json** массива и дальнейшей его передачи **JS** скрипту, который распарсит этот массив.

Имеется [готовое решение](https://github.com/christian-fei/Simple-Jekyll-Search){:target="_blank"}{:rel="nofollow"} которое можно использовать в своем шаблоне.

{% highlight html %}
{% raw %}
<!-- подключаем скрипт -->
<script src="{{ '/assets/js/simple-jekyll-search.min.js?v=' | relative_url }}{{ site.version }}"></script>

<!-- формируем массив данных -->
<script>
  const searchJson = `[
    {% for post in site.posts %}
      {
        "title"           : "{% if post.title != "" %}{{ post.title | strip_html | escape }}{% else %}{{ post.excerpt | strip_html | escape | strip }}{%endif%}",
        "tags"            : "{{ post.tags | join: ', ' }}",
        "url"             : "{{ site.baseurl }}{{ post.url }}",
        "date"            : "{{ post.date | date: '%d.%m.%Y' | default: '' }}",
        "description"     : "{{ post.description | default: '' }}"
      },
    {% endfor %}
    {% for post in site.steps %}
      {
        "title"           : "{% if post.title != "" %}{{ post.title | strip_html | escape }}{% else %}{{ post.excerpt | strip_html | escape | strip }}{%endif%}",
        "tags"            : "{{ post.tags | join: ', ' }}",
        "url"             : "{{ site.baseurl }}{{ post.url }}",
        "date"            : "{{ post.date | date: '%d.%m.%Y' | default: '' }}",
        "description"     : "{{ post.description | default: '' }}"
      }{% unless forloop.last %},{% endunless %}
    {% endfor %}
  ]`

  // передаем данные в скрипт
  new SimpleJekyllSearch(searchJson)
</script>
{% endraw %}
{% endhighlight %}

Обязательно ознакомьтесь с документацией js скрипта **SimpleJekyllSearch**, так как в примере указана общая концепция, но не сама реализация.
