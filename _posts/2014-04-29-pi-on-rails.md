---
layout: post
title: Pi on rails
subtitle: Install ruby on rails enviroment on Raspberry Pi
header-img: "img/post-bg-01.jpg"
autor: matbaj

---

Ruby on Rails installation on Raspberry Pi is quite simple.
Unfortunately on board we have only 512 MB RAM and slow CPU so that can complicate some things

Probably with that small memory we will can run 1 medium-small RoR application in one ruby version with one gemset.

Compiling ruby on Raspberry Pi is little time consuning task, so I would recommend use ruby available in distribution repository if that is possible.
Also there installing rvm or other ruby version menagers for one application is unnecessary

If You would like to compile ruby from sources or use rvm You can also use tutorial from website
[eLinux](http://elinux.org/RPi_Ruby_on_Rails)

###The Raspian way.###

{% highlight bash %}
sudo apt-get install ruby
{% endhighlight %}

###The Arch Linux way.###

There is the newest ruby interpreter in Arch Linux for Raspberry pi repository so we can just run:

{% highlight bash %}
sudo pacman -S ruby
{% endhighlight %}

###Any distro###
To install gems without root authorization we can in very clever way override enviroment variable
adding line to ~/.bashrc :

{% highlight bash %}
export GEM_HOME=$HOME/.gems
{% endhighlight %}

Some gems includes also commands like rake,rails
To have possibility to use theese comands without typinch all paths we need to add gem's bin path to enviroment variable PATH.
Gem's bin is in ~/.gem/ruby/(ruby version)/bin .
In system we can have commands that have that same name like gems so we will add new path on the begginng ```export PATH=(new path):$PATH``` in file ~/.bashrc .

In My uscase it was:

{% highlight bash %}
export PATH=$HOME/.gem/ruby/2.1.0/bin:$PATH
{% endhighlight %}

Raspberry Pi not always have big SD card and to save some time on installing gem we can disable generate documentation for gems
To turn of default document generation task we need to add line in ~/.gemrc (create if it doesn't exist) :

{% highlight yaml %}
gem: --no-document
{% endhighlight %}

Now just install rails gem
{% highlight bash %}
gem install rails
{% endhighlight %}


