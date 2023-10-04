---
layout: steps
title: Макет для страниц сайта
date: 2023-09-04 10:00 +0600
description: Создание макетов для страниц сайта на Jekyll.
image: /images/cover.jpg
published: true
sitemap: true
---

# {{ page.title }}

**Макеты** — это шаблоны, которые могут использоваться на любой странице вашего сайта и охватывать содержимое страницы. 

Макеты создаются в каталоге _**layouts**.

Они могут наследоваться друг от друга создавая глубоко вложенную структуру, которая позволит в процессе написания материала на сайте, не отвлекаться на разметку, а сконцентрироваться только на содержимом.

## Пример создания родительского "Макета"

Создадим самый основной и первоначальный макет от которого будут наследоваться другие макеты **default.html**.

У основного макета **default.html** нет конструкции **front matter** или как я его называю **разделителя**, который обозначится символами **- - - &nbsp; - - -** со свойством **layout**. Так как через данное свойство происходит наследование, а в данном случае основному макету не нужно ни от кого наследоваться.

### Простой вариант

В простом варианте у нас есть некоторая основная разметка без использования конструкции **include** о которой речь пойдет в следующей статье или конструкции {% raw %}**{% contentblock content %}**{% endraw %}.

Здесь мы просто используем служебную переменную {% raw %}**{{ content }}**{% endraw %}, в которой находится содержимое записи различных типов, которые наследуются от этого шаблона.

{% highlight html %}
<html class="no-js" lang="{{ page.lang | default: site.lang | default: 'ru' }}">
<head>
  <title>Title</title>
</head>
<body>
<div>Some markup</div>

<div class="layout">
  <header>Header</header>

  <main class="layout__main">
    <div class="container">
      {% raw %}{{ content }}{% endraw %}
    </div>
  </main>

<footer>Footer</footer>
</div>

<script>console.log('Hello world')</script>
</body>
</html>
{% endhighlight %}

### Сложный вариант

В сложном варианте уже могут использоваться конструкции **include**, которая подключает файлы с отдельно вынесенное версткой. И конструкция {% raw %}**{% contentblock &lt;name&gt; %}**{% endraw %}, которая резервирует область для определенного контента.

{% highlight html %}
<html class="no-js" lang="{{ page.lang | default: site.lang | default: 'ru' }}">
<head>
  {% raw %}{% include base/head.html %}{% endraw %}
</head>
<body>
{% raw %}{% include base/body-top.html %}{% endraw %}

<div class="layout">
  {% raw %}{% contentblock header %}{% endraw %}

  <main class="layout__main">
    <div class="container">
      {% raw %}{% contentblock content %}{% endraw %}
    </div>
  </main>

  {% raw %}{% contentblock footer %}{% endraw %}
</div>

{% raw %}{% contentblock script %}{% endraw %}
</body>
</html>
{% endhighlight %}

## Пример создания дочернего "Макета"

Создадим дочерний базовый макет **base.html**, который каким либо образом дополняет содержимое основного макета **default.html**.

У базового макета **base.html** уже должна присутствовать конструкция **front matter**, которая обозначится символами **- - - &nbsp; - - -** со свойством **layout**. Так как через данное свойство происходит наследование, и в данном случае базовому макету **base.html** нужно наследоваться от основного **default.html**.

Наследование от **default.html** происходит благодаря конструкции **layout: default**, где **default** имя шаблона.

### Простой вариант

В простом варианте мы дополняем то место в макете **default.html** где прописана конструкция {% raw %}**{{ content }}**{% endraw %}. Именно на ее место будет вставлено содержимое файла **base.html**. 

В свою очередь файл **base.html** так же имеет конструкцию {% raw %}**{{ content }}**{% endraw %} на место которой подставится содержимое, наследуемое макет **base.html**. Это может быть либо тип записи, либо другой макет. Так как вложенность макетов друг в друга безгранична. 

{% highlight html %}
---
layout: default
---

<div class="layout__content">
  {% raw %}{{ content }}{% endraw %}
</div>

{% endhighlight %}

### Сложный вариант

В сложном варианте мы так же используем конструкции **include**, а так же {% raw %}**{% contentfor &lt;name&gt;  %}**{% endraw %}, которая подставляет содержимое внутри этой конструкции в зарезервированную область по имени в макете **default.html**.

{% highlight html %}
---
layout: default
---

{% raw %}{% contentfor header %}{% include section/header.html %}{% endcontentfor %}{% endraw %}

{% raw %}{% contentfor content %}{% endraw %}
<div class="layout__content">
  {% raw %}{{ content }}{% endraw %}
</div>

{% raw %}{% contentblock more-links %}{% endraw %}
{% raw %}{% endcontentfor %}{% endraw %}

{% raw %}{% contentfor footer %}{% include section/footer.html %}{% endcontentfor %}{% endraw %}

{% raw %}{% contentfor script %}{% endraw %}
<script src="{{ '/assets/js/main.js?v=' | relative_url }}{{ site.version | default: '0.0.1' }}" type="module"></script>
{% raw %}{% endcontentfor %}{% endraw %}
{% endhighlight %}

## Вложенности нет предела

Как уже ранее говорилось мы можем иметь неограниченную вложенность со сложной структурой, позволяющую обеспечивать гибкость соответствующей потребностям нашей верстки.

Для примера создадим еще один макет **steps.html**, который будет наследоваться от макета **base.html**.

{% highlight html %}
---
layout: base
---

{% raw %}{{ content }}{% endraw %}

{% raw %}{% contentfor more-links %}{% endraw %}
<div class="layout__more-links">
  <h2>Другие статьи</h2>

  <ol>
    {% raw %}{% assign collection = site.steps %}{% endraw %}

    {% raw %}{% for article in collection limit: 20 offset: 0 %}{% endraw %}
    {% raw %}{% unless page.url == article.url %}{% endraw %}
    <li><a href="{{ article.url }}">{{ article.title }}</a></li>
    {% raw %}{% endunless %}{% endraw %}
    {% raw %}{% endfor %}{% endraw %}
  </ol>
</div>
{% raw %}{% endcontentfor %}{% endraw %}
{% endhighlight %}

На место {% raw %}**{{ content }}**{% endraw %} будет подставляться содержимое типа записи, которое наследует шаблон **steps**.

Область {% raw %}**{% contentfor more-links %}**{% endraw %} подставится на место зарезервированной области в макете **base.html**, так как именно его наследует макет **steps**.

## Запись

Замыкающим в этой цепи наследования является тип записи страница, статья либо коллекция.

Например:

{% highlight md %}
---
layout: steps
title: Установка шаблона
date: 2023-09-01 13:39 +0600
description: Инструкция по инициализации шаблона Jekyll.
published: true
sitemap: true
---

# {% raw %}{{ page.title }}{% endraw %}

Склонировать шаблон.

{% raw %}{% highlight bash %}{% endraw %}
git clone git@github.com:eliofery/jekyll-template.git
{% raw %}{% endhighlight %}{% endraw %}

Установить зависимости.

{% raw %}{% highlight bash %}{% endraw %}
bundle install
{% raw %}{% endhighlight %}{% endraw %}

Запустить проект в режиме разработки.

{% raw %}{% highlight bash %}{% endraw %}
jekyll build && bundle exec jekyll serve --livereload
{% raw %}{% endhighlight %}{% endraw %}

Важно перед запуском виртуального сервера произвести первоначальную сборку шаблона командой **jekyll build**, для того чтобы критические стили подключились к шаблону. Так как первым собирается **html** и он просто не увидит файл с критическими стилями если сразу запустить команду **bundle exec jekyll serve --livereload**. Так как критические стили на этом этапе еще не будут созданы.

Перейти в браузере по ссылке.

{% raw %}{% highlight bash %}{% endraw %}
http://localhost:4000
{% raw %}{% endhighlight %}{% endraw %}
{% endhighlight %}

Как видно в записи у нас нет ни какой разметки, а только сам материал в формате **Markdown**. Вся разметка находится в других файлах которые запись наследует каскадом.
