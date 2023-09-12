---
layout: steps
title: Тип записи "Коллекция"
date: 2023-09-03 12:00 +0600
description: Создание типа записи "Коллекция" в Jekyll.
published: true
sitemap: true
---

# {{ page.title }}

**Коллекции** — полезны для группирования связанного контента (является группой контента, имеет дату и категорию).

Коллекции создаются в каталоге **_&lt;name-collection&gt;**. Каталог должен называться точно так же как параметр коллекции в конфигурационном файле **_config.yml**. Вместо _&lt;name-collection&gt; например **_steps**, коллекция будет называться **steps**.

{% highlight yml %}
# Коллекции
collections:
  # название коллекции
  steps:
    # создавать для каждой статьи коллекции steps отдельный файл 
    output: true
    # шаблон ссылки на коллекции steps
    permalink: /:collection/:name.html
    # сортировать коллекции по дате
    sort_by: date
{% endhighlight %}

Внутри параметра **collections:** может быть сколько угодно пользовательских типов записей. 

Ссылка на тип записи "Коллекция" формируется основываясь на настройках конфигурационного файла **_config.yml**, параметр шаблона ссылки **permalink: /:collection/:name.html**. Для каждого типа коллекции можно настроить свой шаблон. Можно изменить как шаблон ссылки, так и саму ссылку в файле коллекции.

## Создание записи "Коллекция"

Тип записи "Коллекция" можно создать как вручную в каталоге **_<name-collection>,** так и через терминал используя команду.

{% highlight bash %}
# Создаст новую коллекцию
bundle exec jekyll compose "My New Post" --collection "name-collection"
{% endhighlight %}


## Параметры записи "Коллекция"

Основные параметры для типа записи "Коллекция", так же можно дополнять пользовательскими параметрами.

{% highlight yml %}
---
# название шаблона
layout: base

# заголовок коллекции
title:  "Добро пожаловать в Jekyll!"

# дата добавления коллекции
date:   2023-09-03 12:02:32 +0600

# описание коллекции
description: Описание коллекции про Jekyll

# категория коллекции
category: jekyll

# теги коллекции
tags: [jekyll, html, css]

# статус публикации коллекции
published: true

# выводить ссылку на статью в карте сайта
sitemap: true

# разделитель между анонсом и полным текстом
excerpt_separator: "<!--more-->"
---
{% endhighlight %}

## Пример записи "Коллекция"

{% highlight md %}
---
layout: steps
title: Установка Jekyll
date: 2023-08-31 13:39 +0600
description: Инструкция по установке Jekyll на Linux дистрибутивы семейства Debian и инициализации шаблона.
published: true
sitemap: false
---

# {{ page.title }}

1\. Установить **Ruby** и другие необходимые зависимости.

{% raw %}{% highlight bash %}
sudo apt install ruby-full build-essential zlib1g-dev
{% endhighlight %}
{% endraw %}

2\. Настроить учетную запись пользователя.

{% raw %}{% highlight bash %}
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
{% endhighlight %}
{% endraw %}

3\. Установить **Jekyll** и **Bundler**.

{% raw %}{% highlight bash %}
gem install jekyll bundler
{% endhighlight %}
{% endraw %}

{% endhighlight %}
