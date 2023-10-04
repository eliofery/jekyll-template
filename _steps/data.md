---
layout: steps
title: Пользовательские данные
date: 2023-09-02 10:00 +0600
description: Инструкция по использованию каталога _data в шаблоне Jekyll.
image: /images/cover.jpg
published: true
sitemap: true
---

# {{ page.title }}

В каталоге **_data** содержатся дополнительные данные, которые **Jekyll** сможет использовать в шаблоне. Эти файлы должны быть в формате **YAML**, **JSON**, **TSV** или **CSV** (с использованием расширения .yml, .yaml, .json, .tsv, или .csv), и они будут доступны через переменную **\{\{ site.data \}\}**.

К примеру если создать файл с именем **main-nav.yml** и со следующим содержимым.

{% highlight yml %}
items:
  - title: Базовая установка
    url: /steps
    links:
    - title: Установка Jekyll
      url: /steps
    - title: Установка шаблона
      url: /steps/init.html
  
    - title: Архитектура шаблона
      url: /steps/architecture.html
  
    - title: Пользовательские данные (каталог _data)
      url: /steps/data.html
{% endhighlight %}

То доступ к содержимому файла можно получить так **\{\{ site.data.main-nav \}\}**. Для получения вложенных значений нужно так же через символ **"."** обратиться к переменной по имени **\{\{ site.data.main-nav.items \}\}**.

Пример перебора данных через цикл.

{% highlight html %}
<nav>
  {% raw %}{% if site.data.main-nav.items[0] %}
  <ul>
    {% for item in site.data.main-nav.items %}
    <li class="{% if entry.url == page.url %}active{% endif %}">
      <a href="{{ entry.url }}">{{ entry.title }}</a>
      
      {% if item.links[0] %}
      <ul>
        {% for entry in item.links %}
        <li class="{% if entry.url == page.url %}active{% endif %}">
          <a href="{{ entry.url }}">{{ entry.title }}</a>
        </li>
        {% endfor %}
      </ul>
      {% endif %}
    </li>
    {% endfor %}
  </ul>
  {% endif %}{% endraw %}
</nav> 
{% endhighlight %}



