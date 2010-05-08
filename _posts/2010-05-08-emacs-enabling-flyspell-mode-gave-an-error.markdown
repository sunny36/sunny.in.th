---
layout: post
title: "Emacs: Enabling Flyspell mode gave an error"
---

{{ page.title }}
================

I've been using Emacs with [emacs-starter-kit](http://github.com/technomancy/emacs-starter-kit) for the past few weeks and every time I open a text file or use [Org-mode](http://orgmode.org/) I keep getting the message
`Enabling Flyspell mode gave an error`. Well this doesn't tell much what the problem is. But if you run `M-x` followed by `ispell-buffer` it would tell you what the problem is. 

In my case it was looking for the program `ispell` which it couldn't find. If you google around you will find that there is another program called `aspell` which is a better and also a replacement for `ispell`

So all we need to do is install `aspell` and configure Emacs to use `aspell`

#### Installing Aspell: 
If you are on Linux this should be quite simple. Use your package manager to install aspell. Note that you will need to install the dictionary for English or the language you use else it will not work. You can find the dictionary for `aspell` in your package manager as well. 

I'm on a Mac and I prefer [Homebrew](http://github.com/mxcl/homebrew) instead of [Macports](http://www.macports.org/) so it's simple, just run:
{% highlight bash  %}
$ brew install aspell --lang=en
{% endhighlight %}

#### Configure Emacs to use aspell rather than ispell:
Add the following line to your `.emacs`. If you use emacs-starter-kit then add it in `username.el`
{% highlight cl  %}
(setq-default ispell-program-name "aspell")
{% endhighlight %}

Flyspell should now work and Emacs would be able to find spellings mistakes if you enable Flyspell mode. 

