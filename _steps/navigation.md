---
layout: steps
title: Навигация
date: 2023-09-06 14:00 +0600
description: Сниппет вывода многоуровневой навигации в Jekyll.
published: true
sitemap: true
---

# {{ page.title }}

Пример вывода многоуровневой навигации в Jekyll.

## navigation.html

{% highlight md %}
{% raw %}
{% if site.data.main-nav.items %}
<nav class="navigation">
  <ul class="navigation__list">
    {% include component/navigation/navigation-item.html items=site.data.main-nav.items %}
  </ul>
</nav>
{% endif %}
{% endraw %}
{% endhighlight %}

## navigation-item.html

{% highlight md %}
{% raw %}
{% for item in include.items %}
{% assign url = page.url | replace: '/index.html', '' %}
<li class="navigation__item {% if item.url == url %}navigation__item--active{% endif %}">
  <a class="navigation__link" href="{{ site.baseurl}}{{ item.url }}">{{ item.title }}</a>
  {% if item.links %}
  <ul class="navigation__sub-list">
    {% include component/navigation/navigation-item.html items=item.links %}
  </ul>
  {% endif %}
</li>
{% endfor %}
{% endraw %}
{% endhighlight %}
