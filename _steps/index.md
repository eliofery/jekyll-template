---
layout: steps
title: Установка Jekyll
date: 2023-08-31 13:39 +0600
description: Инструкция по установке Jekyll на Linux дистрибутивы семейства Debian и инициализации шаблона.
image: /images/cover.jpg
published: true
sitemap: true
---

# {{ page.title }}

1\. Установить **Ruby** и другие необходимые зависимости.

{% highlight bash %}
sudo apt install ruby-full build-essential zlib1g-dev
{% endhighlight %}

2\. Настроить переменные среды.

{% highlight bash %}
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
{% endhighlight %}

3\. Установить **Jekyll** и **Bundler**.

{% highlight bash %}
gem install jekyll bundler
{% endhighlight %}

4\. Установить **Gem** зависимости.

{% highlight bash %}
bundle install
{% endhighlight %}
