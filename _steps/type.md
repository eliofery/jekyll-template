---
layout: steps
title: Типы записей
date: 2023-09-02 11:00 +0600
description: Создание различных типов записей в Jekyll.
image: /images/cover.jpg
published: true
sitemap: true
---

# {{ page.title }}

**Jekyll** поддерживает несколько типов записей, такие как страницы, статьи и коллекции. 

**Страницы** — полезны для отдельного контента (не привязан к дате или не является группой контента, например сотрудников или рецептов).

**Статьи** — полезны для связанного контента (имеет дату и категорию).

**Коллекции** — полезны для группирования связанного контента (является группой контента, имеет дату и категорию).

**Черновики** — содержит записи не опубликованные на сайте.

Все типы записей могут иметь расширение **html** либо **markdown** сокращенно **md**.

## Создание различных типов записей через терминал

Настройки для каждого типа записи находятся в файле **_config.yml** и выглядят следующим образом.

{% highlight yml %}
# настройки расширения jekyll_compose
jekyll_compose:
  # автоматическое открытие созданной записи в редакторе кода
  auto_open: true
  # определение параметров записей по умолчанию
  default_front_matter:
    # черновики - неопубликованный материал
    drafts:
      layout: base
      description:
      image: cover.jpg
      category:
      tags: []
      published: false
      sitemap: false
      excerpt_separator: <!--more-->
    # статьи
    posts:
      layout: base
      description:
      image: cover.jpg
      category:
      tags: []
      published: true
      sitemap: true
      excerpt_separator: <!--more-->
    # страницы
    pages:
      layout: base
      description:
      image: cover.jpg
      permalink:
      sitemap: true
    # коллекция с инструкцией по использованию шаблона
    steps:
      layout: base
      description:
      image: cover.jpg
{% endhighlight %}

Данный список можно пополнить своими типами записей в виде коллекций. В этих настройках можно переопределять стандартные переменные, а так же добавлять пользовательские кастомные переменные с определенным значением либо без.

Для того чтобы можно было при создании новой записи сразу приступить к редактированию ее файла нужно определить редактор кода в котором будет открываться, созданный файл. Для этого вводим в терминале команду.

{% highlight bash %}
# для IDE PhpStorm
export JEKYLL_EDITOR=phpstorm

# Или

# для редактора кода VSCode
export JEKYLL_EDITOR=code
{% endhighlight %}

### Список команд

Команды для манипулирования материалом на сайте.

{% highlight bash %}
# Создаст новую страницу
# Страницы будут создаваться в корне проекта, перенести их в каталог _page придется вручную
bundle exec jekyll page "My New Page"

# Создаст новую статью
# Статья создастся в каталоге _posts перенести ее в 2023/09 придется вручную
bundle exec jekyll post "My New Post"

# Создаст новую коллекцию
bundle exec jekyll compose "My New Post" --collection "name-collection"

# Создаст новый черновик
# Черновики создаются в каталоге _drafts
bundle exec jekyll draft "My new draft"

# Опубликует указанный черновик
bundle exec jekyll publish _drafts/my-new-draft.md

# Отправит активную статью в черновик
bundle exec jekyll unpublish _posts/2014-01-24-my-new-draft.md
{% endhighlight %}












