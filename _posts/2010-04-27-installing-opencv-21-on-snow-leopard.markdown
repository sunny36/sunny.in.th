---
layout: post
title: Installing OpenCV 2.1 on Snow Leopard
---

{{ page.title }}
================

Installing OpenCV 2.1 on Snow Leopard has become quite easy at least easier than 2.0. Version 2.1 can now be compiled as 64-bit library.

Before version 2.1 OpenCV used Carbon which is the old GUI interface for Mac OS. Carbon supports only 32-bit and has been deprecated by Apple. The new GUI interface for Mac OS is Cocoa. With Snow Leopard being a 64-bit kernel it would be nice if we could compile OpenCV as a 64-bit library and not not 32-bit just because of Carbon. Thanks to the OpenCV team they have added Cocoa support in version 2.1.

To install OpenCV check out the code from the svn repository and compile it. 

{% highlight bash  %}
$ svn co https://code.ros.org/svn/opencv/trunk/opencv
$ cd opencv
$ mkdir build 
$ cd build 
$ cmake .. 
{% endhighlight %}

Configure the make by 
{% highlight bash  %}
$ ccmake .
{% endhighlight %}

If you want you can build the samples as well. 

![ccmake](http://img.skitch.com/20100429-gpdgt6jp32qbt4tu6ws4xnnfq9.jpg)

Press <code>c</code> to configure, followed by <code>g</code> to generate. Next build and install OpenCV by
{% highlight bash  %}
$ make -j8
$ sudo make install
{% endhighlight %}

That's it!!! Simple right. 

If you want to use Python with OpenCV there's a little more that needs to be done. By default OpenCV copies the shared object file required by the Python interface to <code>/usr/local/lib/python2.6/site-packages/cv.so</code> which is not under Python path. 
Add the following line to your <code>.bashrc</code> or <code>.bash_profile</code> 
{% highlight bash  %}
PYTHONPATH=/usr/local/lib/python2.6/site-packages/cv.so:$PYTHONPATH
{% endhighlight %}

Trying running some <code>C</code> samples which are in <code>/usr/local/share/opencv/samples/c/</code>. The Python samples at <code>/usr/local/share/opencv/samples/python/</code> doesn't work since they are based on the old SWIG-Python interface. Try running the sample Python code which is in the <code>opencv</code> directory that was checked out from subversion. It's inside <code>samples/python</code>. 







