---
layout: steps
title: Svg иконка
date: 2023-09-07 11:00 +0600
description: Сниппет вывода svg иконки в Jekyll.
published: true
sitemap: true
---

# {{ page.title }}

Пример вывода svg иконки в Jekyll.

Компонент **_includes/component/icon.html**.

{% highlight html %}
<svg class="{{ include.class | default: '' }}" width="{{ include.width | default: 16 }}"
     height="{{ include.height | default: 16 }}" aria-hidden="{{ include.aria-hidden | default: true }}" {{
     include.other | default: '' }}>
  <use xlink:href="#{{ include.icon }}"></use>
</svg>
{% endhighlight %}

Затем в разметке.

{% highlight html %}
{% raw %}
{% include component/icon.html width="20" height="20" icon="icon-arrow-top" %}
{% endraw %}
{% endhighlight %}
