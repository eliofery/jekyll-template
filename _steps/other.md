---
layout: steps
title: Разные конструкции
date: 2023-09-08 10:00 +0600
description: Сниппет вывода различных конструкций в Jekyll.
published: true
sitemap: true
---

# {{ page.title }}

Пример вывода различных конструкций в Jekyll.

Фильтры Jekyll [официальная документация](https://jekyllrb.com/docs/liquid/filters/#standard-liquid-filters){:target="_blank"}{:rel="nofollow"}.

{% highlight md %}
{% raw %}
# данные записей
{{ post.title }}
{{ post.url }}
{{ post.date }}
{{ post.description }}
{{ post.excerpt }}

# вывод контента с обрезкой в 20 символов
{{ post.content | default: post.excerpt | markdownify | strip_html | truncatewords: 15 }}

# экранирование строк
{{ "Have you read 'James & the Giant Peach'?" | escape }} 

# подключить файл по указанному пути
{% root_include {{ path }} %}

# условие
{% if page.url == article.url %} ... {% endif %}

# условие отрицание
{% unless page.url == article.url %} ... {% endunless %}
{% unless page.url == '/' %} href="/" {% else %} href {% endunless %} -

# дата
{{ post.date | date: '%d' }} - день
{{ post.date | date: '%m' }} - месяц
{{ post.date | date: '%Y' }} - год
{{ site.time | date: '%Y' }} - год

# путь файла включая baseurl
{{ '/assets/favicon.ico' | relative_url }}

# простая переменная
{% assign myvar = "joe" %}

# создание сложной переменной related_posts в которую поместится {{ page.categories }}
{% capture related_posts %}
  {{ page.categories }}
{% endcapture %} 

# оборачивает ссылку в rel='nofollow' target='_blank'
{% extlink Текст ссылки https://link %}

# svg icon
{% svg assets/img/icons/car.svg width=24 foo="bar" %}
{% svg {{site.data.svg.car}} width=24 foo="bar" %}

# адаптивное изображение
# требуется расширение jekyll-responsive-image
{% responsive_image path: assets/my-file.jpg %}

# ключ индекс цикла
{{ forloop.index }}
{% endraw %}
{% endhighlight %}
