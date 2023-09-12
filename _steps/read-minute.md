---
layout: steps
title: Время чтения материала
date: 2023-09-07 12:00 +0600
description: Сниппет вывода количество минут на чтение материала в Jekyll.
published: true
sitemap: true
---

# {{ page.title }}

Пример вывода количество минут на чтение материала в Jekyll.

Компонент **_includes/component/word-length.html**.

{% highlight md %}
{% raw %}
{% assign words = include.content | default: '' | markdownify | strip_html | number_of_words %}
{% if words < 250 %} 1
{% else %} {{ words | divided_by: 250 }}
{% endif %} мин.
{% endraw %}
{% endhighlight %}
