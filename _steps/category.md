---
layout: steps
title: Категория
date: 2023-09-06 10:00 +0600
description: Сниппет страницы категории в Jekyll.
image: /images/cover.jpg
published: true
sitemap: true
---

# {{ page.title }}

Пример разметки страницы "Категория", которая содержит список статей или коллекций.

{% highlight html %}
---
layout: blog
title: Заголовок
description: Описание

# настройка пагинации
pagination:
  # включить пагинацию
  # пагинация будет выводить все записи из всех категорий
  enabled: true
---
{% endhighlight %}

{% highlight html %}
---
layout: category
title: Заголовок
description: Описание
permalink: /program

# настройка пагинации
pagination:
  # включить пагинацию
  enabled: true

  # пагинация будет выводить записи только категории program
  category: program
---
{% endhighlight %}

{% highlight html %}
---
layout: collection
title: Заголовок
description: Описание
permalink: /steps

# настройка пагинации
pagination:
  # включить пагинацию
  enabled: true

  # пагинация будет выводить записи только коллекции steps
  collection: steps
---
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

Вывод пагинации

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
