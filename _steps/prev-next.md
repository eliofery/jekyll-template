---
layout: steps
title: Предыдущая, следующая запись
date: 2023-09-07 10:00 +0600
description: Сниппет вывода предыдущей и следующей записи в Jekyll.
published: true
sitemap: true
---

# {{ page.title }}

Пример вывода предыдущей и следующей записи в Jekyll.

{% highlight md %}
{% raw %}
{% if page.previous.url %}
  <a class="prev" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
{% endif %}

{% if page.next.url %}
  <a class="next" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
{% endif %}
{% endraw %}
{% endhighlight %}
