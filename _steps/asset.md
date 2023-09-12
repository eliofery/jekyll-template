---
layout: steps
title: Ресурсы шаблона
date: 2023-09-05 12:00 +0600
description: Разберем Scss стили и другие ресурсы в Jekyll.
published: true
sitemap: true
---

# {{ page.title }}

**Ресурсы шаблона** - различные ресурсы шаблона такие как стили, скрипты, картинки, иконки, шрифты и т.п.

Ресурсы шаблона находятся в каталоге **assets**, а так же **_scss** для стилей формата **scss**.

В целом в разделе [архитектура шаблона]({{ site.baseurl }}/steps/architecture.html){:target="_blank"}{:rel="nofollow"} содержимое каталога **assets** было описано. Здесь лишь разберем **scss** стили.

## Scss стили

Все стили хранятся в каталоге **_scss**, данный каталог настроен в конфигурационном файле **_config.yml**.

{% highlight yml %}
# настройки расширения jekyll-sass-converter
sass:
  # каталог где хранятся scss стили
  sass_dir: _scss

  # минифицировать конечный css файл
  style: compressed
{% endhighlight %}

Подключаются стили из каталога **_scss** в каталоге **assets/css**. В каталоге **assets/css** содержатся два файла, первый с критическими стилями, второй с основными стилями.

Критические стили из файла **assets/css/critical.scss** подключаются в файле **_includes/base/head.html**.

{% highlight html %}
{% raw %}
{% assign path = '_site/assets/css/critical.css' %}
{% capture fileExists %}{% file_exists {{ path }} %}{% endcapture %}
{% if fileExists == 'true' %}
{% capture critical %}{% root_include {{ path }} %}{% endcapture %}
<style>{{ critical | scssify }}</style>
{% endif %}
{% endraw %}
{% endhighlight %}

Основные стили из файла **assets/css/style.scss** подключаются в файле **_includes/base/head.html**. 

{% highlight html %}
{% raw %}
<link rel="preload" as="style" href="{{ '/assets/css/style.css?v=' | relative_url }}{{ site.version | default: '0.0.1' }}" onload="this.rel='stylesheet'">
<noscript><link rel="stylesheet" href="{{ '/assets/css/style.css?v=' | relative_url }}{{ site.version | default: '0.0.1' }}"></noscript>
{% endraw %}
{% endhighlight %}

При создании новых стилей в каталоге **_scss** важно не забывать подключать их в файле **assets/css/style.scss** либо  **assets/css/critical.scss**.
