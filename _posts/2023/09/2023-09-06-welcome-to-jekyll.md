---
layout: base
title:  "Добро пожаловать в Jekyll!"
date:   2023-09-03 12:02:32 +0600
description: Тестовая вступительная запись
image: /images/cover.jpg
category: jekyll
tags: [jekyll, html, css]
published: true
sitemap: false
excerpt_separator: "<!--more-->"
---

Тестовая вступительная запись

<!--more-->

Вы найдете этот пост в своем каталоге `_posts`. Отредактируйте его и перестройте сайт, чтобы увидеть изменения. Вы можете перестроить сайт разными способами, но наиболее распространенным способом является запуск `jekyll serve`, который запускает веб-сервер и автоматически восстанавливает ваш сайт при обновлении файла.

Jekyll требует, чтобы файлы сообщений блога имели имена в следующем формате:

`YEAR-MONTH-DAY-title.md`

Где `Год` — четырехзначное число, `Месяц` и `День` — двузначные числа, а `md` — это расширение файла, представляющее формат, используемый в файле. После этого добавьте необходимую вступительную часть. Взгляните на источник этого поста, чтобы получить представление о том, как это работает.

Jekyll также предлагает мощную поддержку фрагментов кода:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Проверьте [Jekyll docs][jekyll-docs] для получения дополнительной информации о том, как максимально эффективно использовать Jekyll. Сообщите обо всех ошибках/запросах на новые функции по адресу [Jekyll’s GitHub repo][jekyll-gh]. Если у вас есть вопросы, вы можете задать их на [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/

<picture>
  <source srcset="/images/thumbnail/2023/09/welcome-to-jekyll/cover.webp" type="image/webp">
  <img src="/images/thumbnail/2023/09/welcome-to-jekyll/cover.jpg" alt="">
</picture>
