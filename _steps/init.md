---
layout: steps
title: Инициализация шаблона
date: 2023-08-31 13:39 +0600
description: Инструкция по инициализации шаблона Jekyll.
published: true
sitemap: false
---

# {{ page.title }}

1\. Склонировать шаблон.

{% highlight bash %}
git clone git@github.com:eliofery/jekyll-template.git
{% endhighlight %}

2\. Установить зависимости.

{% highlight bash %}
bundle install
{% endhighlight %}

3\. Запустить проект в режиме разработки.

{% highlight bash %}
jekyll build && bundle exec jekyll serve --livereload
{% endhighlight %}

4\. Перейти в браузере по ссылке.

{% highlight bash %}
http://localhost:4000
{% endhighlight %}
