---
layout: steps
title: Установка шаблона
date: 2023-09-01 10:00 +0600
description: Инструкция по инициализации шаблона Jekyll.
image: /images/cover.jpg
published: true
sitemap: true
---

# {{ page.title }}

**1\. Склонировать шаблон.**

{% highlight bash %}
git clone git@github.com:eliofery/jekyll-template.git
{% endhighlight %}

**2\. Установить зависимости.**

{% highlight bash %}
bundle install
{% endhighlight %}

**3\. Запустить проект в режиме разработки.**

{% highlight bash %}
jekyll build && bundle exec jekyll serve --livereload
{% endhighlight %}

Важно перед запуском виртуального сервера произвести первоначальную сборку шаблона командой **jekyll build**, для того чтобы критические стили подключились к шаблону. Так как первым собирается **html** и он просто не увидит файл с критическими стилями если сразу запустить команду **bundle exec jekyll serve --livereload**. Так как критические стили на этом этапе еще не будут созданы.

**3.1\. Смена окружения проекта.**

Для того чтобы запустить проект, используя настройки другого окружения введите команду.

{% highlight bash %}
jekyll build && bundle exec jekyll serve --livereload --config _config.yml,_config_dev.yml
{% endhighlight %}

Возьмутся настройки шаблона, прописанные в файле **_config.yml** и затем нужные параметры переопределятся настройками файла **_config_dev.yml**.

Это пригодится для разработки на локальном компьютере, когда нужно будет иметь локальный домен.

**4\. Перейти в браузере по ссылке.**

{% highlight bash %}
http://localhost:4000
{% endhighlight %}
