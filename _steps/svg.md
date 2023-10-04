---
layout: steps
title: Иконки
date: 2023-09-05 12:00 +0600
description: Загрузка и подключение иконок в шаблоне Jekyll.
image: /images/cover.jpg
published: true
sitemap: true
---

# {{ page.title }}

**Иконки** - svg иконки используемые в шаблоне.

Иконки находятся в каталоге **assets/icons**.

Иконки делятся на два вида **mono** черно-белые и **multi** цветные.

## Формат svg

Для настройки формата **svg** отредактируйте конфигурационный файл **_config.yml**.

{% highlight yml %}
# настройки расширения jekyll-inline-svg
svg:
  # оптимизировать иконки
  optimize: true
{% endhighlight %}

## Добавление иконки на сайт

Для того чтобы добавить иконку на сайт, пропишем следующую конструкцию.

{% highlight html %}
{% raw %}
{% svg /assets/icons/multi/icon-jekyll.svg class="logo__icon" width=170 height=67 aria-hidden="true" %}
{% endraw %}
{% endhighlight %}

Ознакомимся с каждым параметром.

{% highlight md %}
# подключаемая иконка
svg /assets/icons/multi/icon-jekyll.svg

# атрибуты тега как если бы это было в обычном теге
class="logo__icon" 
width=170 
height=67 
aria-hidden="true"
{% endhighlight %}
