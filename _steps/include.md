---
layout: steps
title: Включаемые области
date: 2023-09-04 11:00 +0600
description: Создание включаемых областей для страниц сайта на Jekyll.
image: /images/cover.jpg
published: true
sitemap: true
---

# {{ page.title }}

**Включаемые области** позволяют включать содержимое из другого файла. Включения полезны для наличия единого источника исходного кода, который повторяется на сайте, или для улучшения читаемости.

Включаемые области создаются в каталоге **_includes**.

Рассмотрим пример использования включаемых областей на примере компонента **icon**.

## Компонент icon.html

Создадим в каталоге **_includes** подкаталог **component** и внутри него файл **icon.html**, который будет содержать разметку.

{% highlight html %}
{% raw %}
<svg class="{{ include.class | default: '' }}" width="{{ include.width | default: 16 }}"
     height="{{ include.height | default: 16 }}" aria-hidden="{{ include.aria-hidden | default: true }}" {{ include.other | default: '' }}>
  <use xlink:href="#{{ include.icon }}"></use>
</svg>
{% endraw %}
{% endhighlight %}

Теперь в любом файле где нам потребуется использовать иконку, чтобы постоянно не писать один и тот же пласт разметки, вставим следующую конструкцию.

{% highlight html %}
{% raw %}{% include component/icon.html class='icon icon-arrow' width=24 height=24 aria-hidden='false' icon='arrow' %}{% endraw %}
{% endhighlight %}

Разберем подробней, что означает каждый параметр.

{% highlight md %}
# подключаем файл из каталога _includes/component/icon.html
# include подключает файлы только в каталоге _includes, но не за ее пределами
include component/icon.html

# это пользовательские параметры которые могут быть названы как угодно и иметь произвольные значения
# эти значения будут попадать внутрь подключаемого файла _includes/component/icon.html
# и там использоваться
class='icon 
icon-arrow' 
width=24 
height=24 
aria-hidden='false' 
icon='arrow'
{% endhighlight %}

Внутри файла **icon.html**, чтобы получить значение переданных параметров используется конструкция **include.&lt;param&gt;**. Например **include.class**, **include.icon**, **include.width** и т.д.
