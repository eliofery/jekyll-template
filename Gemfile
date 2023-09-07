# Указывает источник, из которого следует загружать расширения для проекта.
source "https://rubygems.org"

# Версия jekyll
gem "jekyll", "~> 4.3.2"

# Используемые в проекте расширения
group :jekyll_plugins do
  # SEO
  # https://github.com/jekyll/jekyll-seo-tag/blob/master/docs/installation.md
  # gem install jekyll-seo-tag
  gem "jekyll-seo-tag"

  # RSS
  # https://github.com/jekyll/jekyll-feed
  gem "jekyll-feed", "~> 0.12"

  # Добавляет sitemap
  # https://github.com/jekyll/jekyll-sitemap
  gem "jekyll-sitemap"

  # Добавляет команды для создания записи, страницы или черновика.
  # https://github.com/jekyll/jekyll-compose
  # gem install jekyll-compose
  gem "jekyll-compose"

  # Hightlight
  # https://jun711.github.io/web/how-to-highlight-code-on-a-Jekyll-site-syntax-highlighting/
  # https://bnhr.xyz/2017/03/25/add-syntax-highlighting-to-your-jekyll-site-with-rouge.html
  # rougify help style
  # rougify style monokai > _sass/scaffolds/components/_syntax.scss
  gem "kramdown"
  gem "rouge"

  # Sass/Scss конвертер
  # https://github.com/jekyll/jekyll-sass-converter
  gem 'jekyll-sass-converter'

  # Предоставляет механизм для передачи содержимого со страниц в их родительские макеты.
  # https://github.com/rustygeldmacher/jekyll-contentblocks
  # gem install jekyll-contentblocks
  #gem 'jekyll-contentblocks', path: './_plugins/jekyll-contentblocks-1.2.0'
  gem 'jekyll-contentblocks'
end

# Добавление расширений, которые предоставляют информацию и возможность работы с часовыми поясами (timezone).
# Они полезны, когда вам нужно работать с датами и временем в разных часовых поясах.
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# Ускоритель производительности для просмотра каталогов в Windows
gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]

# Заблокирует расширение `http_parser.rb` на версии `0.6.x` в сборках JRuby,
# поскольку более новые версии расширения не имеют аналога Java
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]
