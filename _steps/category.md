---
layout: steps
title: Категории
date: 2023-09-03 06:00 +0600
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
