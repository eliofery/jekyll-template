# Указывает источник, из которого следует загружать расширения для проекта.
source "https://rubygems.org"

# Версия jekyll
gem "jekyll", "~> 4.3.2"

# Используемые в проекте расширения
group :jekyll_plugins do
  # RSS
  # https://github.com/jekyll/jekyll-feed
  gem "jekyll-feed", "~> 0.12"

  # Добавляет команды для создания записи, страницы или черновика.
  # https://github.com/jekyll/jekyll-compose
  # gem install jekyll-compose
  gem "jekyll-compose"

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
