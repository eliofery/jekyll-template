---
layout: steps
title: Архитектура шаблона
date: 2023-09-02 13:39 +0600
description: Описание назначения каталогов и файлов шаблона.
published: true
sitemap: true
---

# {{ page.title }}

Здесь можно ознакомиться с назначением каталогов и файлов шаблона. Не стесняйтесь изменять данную структуру под свои нужды и видения. Представленная ниже структура это всего лишь пример того как может выглядеть шаблон для **Jekyll**. 

{% highlight bash %}
.
# ресурсы шаблона (картинки, стили, скрипты и т.п.)
├── assets
     # стили
│    ├── css
           # критические стили
│    │     ├── critical.scss
           # основные стили
│    │     └── style.scss
     # иконка для вкладки браузера под различные устройства
│    ├── favicons
│    │     ├── apple-touch-icon.png
│    │     ├── favicon.ico
│    │     ├── icon-192.png
│    │     ├── icon-512.png
│    │     └── icon.svg
     # нестандартные шрифты
│    ├── fonts
│    │     └── roboto
│    │         ├── roboto-light.woff
│    │         ├── roboto-light.woff2
│    │         ├── roboto-medium.woff
│    │         ├── roboto-medium.woff2
│    │         ├── roboto-regular.woff
│    │         └── roboto-regular.woff2
     # svg иконки
│    ├── icons
           # svg иконки черно-белые
│    │     ├── mono
│    │     │     └── .gitkeep
           # svg иконки цветные
│    │     └── multi
│    │         ├── .gitkeep
│    │         └── icon-jekyll.svg
     # картинки шаблона (не путать с картинками статей, для них имеется отдельный каталог)
│    ├── images
│    │     └── cover.jpg
     # javascript скрипты
│    └── js
│        └── main.js
# конфигурационный файл с настройками проекта
├── _config.yml
# структурированные данные, на подобии json
├── _data
│    └── main-nav.yml
# черновики (не опубликованный материал)
├── _drafts
│    └── .gitkeep
# конфигурационный файл с настройками для редактора кода
├── .editorconfig
# зависимости шаблона
├── Gemfile
# зависимости шаблона с зафиксированными используемыми версиями
├── Gemfile.lock
# конфигурационный файл для git 
├── .gitattributes
# конфигурационный файл для git
├── .gitignore
# картинки статей (не путать с картинками шаблона, для них имеется отдельный каталог)
├── images
     # оригинальная картинка (на основе оригинальной картинки могут быть созданные 
     # картинку различного разрешения)
│    ├── original
           # год статьи
│    │     └── 2023
               # месяц статьи
│    │         └── 09
                     # название статьи (внутри данного каталога будут располагаться 
                     # все картинки этой статьи)
│    └──             └── welcome-to-jekyll
# подключаемые файлы, компоненты (содержат разметку, вынесенную в отдельные файлы)
├── _includes
     # базовые конструкции для всего шаблона
│    ├── base
           # содержит разметку noscript для Google Analytic и Yandex Metrika, svg спрайтов,
           # уведомление об отключенном JS и устаревшем браузере
│    │     ├── body-top.html
│    │     └── head.html
     # отдельные компоненты шаблона
│    ├── component
           # навигация
│    │     ├── navigation
│    │     │     ├── navigation.html
│    │     │     └── navigation-item.html
           # картинка формата jpg, png и webp
│    │     └── picture.html
     # секции шаблона (что-то большое, содержат в себе компоненты)
│    ├── section
│    │     ├── footer.html
│    │     └── header.html
     # svg спрайты
│    └── sprite
         # черно-белые 
│        ├── mono.svg
         # цветные
│        └── multi.svg
# шаблоны для страницы
├── _layouts
│    ├── base.html
│    ├── blog.html
│    ├── default.html
│    └── steps.html
# конфигурационный файл
├── manifest.json
# npm зависимости
├── package.json
├── package-lock.json
# страницы
├── _pages
│    ├── 404.html
│    ├── about.html
│    ├── blog.html
│    └── index.html
# пользовательские расширения
├── _plugins
     # проверка файла на существование 
│    ├── file_exists.rb
     # подключение файла по абсолютному пути
│    ├── include_absolute.rb
     # обновленная версия для создания картинок определенного разрешения 
│    └── jekyll_minimagick.rb
# статьи
├── _posts
│    └── 2023
│        └── 09
│            └── 2023-09-06-welcome-to-jekyll.md
# описание шаблона
├── README.md
# конфигурационный файл для поисковых роботов
├── robots.txt
# стили шаблона
├── _scss
     # стили для всего шаблона
│    ├── core
           # базовые стили для всего шаблона
│    │     ├── base
                 # базовые стили 
│    │     │     ├── _base.scss
                 # стили центровщика
│    │     │     ├── _container.scss
                 # подключение нестандартных шрифтов
│    │     │     └── _fonts.scss
           # вспомогательные настройки
│    │     └── helpers
               # функции
│    │         ├── _functions.scss
               # миксины
│    │         ├── _mixins.scss
               # переменные
│    │         └── _variables.scss
     # стили секций и компонентов
│    └── scaffolds
         # стили компонентов
│        ├── components
│        │     ├── .gitkeep
│        │     ├── _hightlight.scss
│        │     ├── _logo.scss
│        │     └── _navigation.scss
         # стили секций
│        └── sections
│            ├── _browser-upgrade.scss
│            ├── _footer.scss
│            ├── _header.scss
│            └── _layout.scss
# коллекция с содержимым статей, содержащих инструкцию по использованию шаблона 
└── _steps
    ├── architecture.md
    ├── index.md
    └── init.md
{% endhighlight %}
