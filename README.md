# Jekyll стартовый шаблон

Шаблоны в **Jekyll** используются для генерации статических HTML-страниц на основе данных, хранящихся в файлах **Markdown**, **HTML**. Это дает возможность добавлять новый материал на сайт не прибегая к взаимодействию с разметкой всей страницы.

Несмотря на то что в работе с шаблоном **Jekyll** не используются backend языки программирования и базы данных, его многогранный функционал позволяет создавать многостраничные сайте тематики блог, новостной портал, портфолио. Не хуже, чем это можно было бы сделать на **CMS**. При этом конечный продукт получается более производительным и менее ресурсозатратным.

Шаблон был создан в рамках [этой статьи](https://eliofery.github.io/blog/2023-09-01-startovyj-jekyll-shablon-dlya-sozdaniya-staticheskih-sajtov-frontend.html), который в последствии дополнился и улучшился. Здесь вы сможете более детально ознакомиться с его функционалом и применить его в своем проекте.

## Команды

Указание окружения
```bash
export JEKYLL_ENV=production
export JEKYLL_ENV=development
```

Сборка
```bash
# Первый билд создаст критические стили, второй билд интегрирует их в шаблон
jekyll build && jekyll build
jekyll build --config _config.yml,_config_dev.yml && jekyll build --config _config.yml,_config_dev.yml
```

Разработка
```bash
bundle exec jekyll serve --livereload
bundle exec jekyll serve --livereload --config _config.yml,_config_dev.yml
```

Автоматически открытие созданных файлов статей/портфолио в IDE
```bash
export JEKYLL_EDITOR=phpstorm
```

Создание "Коллекции"
```bash
bundle exec jekyll compose "Название работы" --collection "foobar"
```

Создание "Статьи"
```bash
bundle exec jekyll post "Название страницы"
```

Создание "Страницы"
```bash
bundle exec jekyll page "Название страницы"
```
