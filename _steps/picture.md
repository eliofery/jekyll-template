---
layout: steps
title: Изображение
date: 2023-09-07 12:00 +0600
description: Сниппет вывода изображения в Jekyll.
published: true
sitemap: true
---

# {{ page.title }}

Пример вывода изображения в Jekyll.

Компонент **_includes/component/picture.html**.

{% highlight md %}
{% raw %}
{% capture image %}images/{{ include.type | default: 'original' }}/{{ page.date | default: post.date | date: '%Y' }}/{{ page.date | default: post.date | date: '%m' }}/{{ include.slug }}/{{ include.img }}{% endcapture %}
{% assign webp = image | replace:'.png','.webp' | replace:'.jpg','.webp' | replace:'.jpeg','.webp' %}
{% capture size %}{% imagesize image:props %}{% endcapture %}

{% if include.fancybox == 'true' %}<a href="{{ image | relative_url }}" data-fancybox>{% endif %}
  <picture>
    <source srcset="{{ webp | relative_url }}" type="image/webp">
    <img src="{{ image | relative_url }}" {{ size }} alt="{{ include.alt | default: '' }}" loading="lazy">
  </picture>
{% if include.fancybox == 'true' %}</a>{% endif %}
{% endraw %}
{% endhighlight %}
