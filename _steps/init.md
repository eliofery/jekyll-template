---
layout: steps
title: Установка шаблона
date: 2023-09-01 13:39 +0600
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

Важно перед запуском виртуального сервера произвести первоначальную сборку шаблона командой **jekyll build**, для того чтобы критические стили подключились к шаблону. Так как первым собирается **html** и он просто не увидит файл с критическими стилями если сразу запустить команду **bundle exec jekyll serve --livereload**. Так как критические стили на этом этапе еще не будут созданыu.

4\. Перейти в браузере по ссылке.

{% highlight bash %}
http://localhost:4000
{% endhighlight %}
