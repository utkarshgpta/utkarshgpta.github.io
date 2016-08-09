---
layout: post
title: Hosting Jekyll blog on Github
date:       2016-08-08 2:31:19
author:     Utkarsh Gupta
description:    Quick and easy step by step instructions for hosting Jekyll blog on Github.
keywords:	"blog, jekyll, hosting, github, website, utkarshgpta, utkarsh gupta, developer, iit, roorkee, iit roorkee, personal, about me"
categories: jekyll
thumbnail:  jekyll
comments: true
tags:
 - jekyll
 - blog
 - hosting
 - github
 - tutorial
 - guide
---

In the previous post, we set up a Jekyll blog on our local machine. Now its time to make it go live on the internet! All you need to do is to [push](//help.github.com/articles/pushing-to-a-remote/) all the changes made in the local repository to the remote repository on Github servers. Open the terminal window in the root directory of the blog and type in the following command :

{% highlight shell %}
git add -A
git commit -m "{your-commit-message}"
git push origin master

{% endhighlight %}

Now let Jekyll and Github Pages do the magic for you! That's it, your blog's live on the internet! You can access it by typing in the address : `your-github-username.github.io`

### Using Custom Domain Name
* * *

These days - if you're lucky to find a deal, you can find cheap domain names. If you happen to have your own domain name, you can use that domain name while hosting the site on Github for free. Just go to the root of the blog directory, add a file named `CNAME` and edit it to contain your domain address (e.g. www.exampledomain.com).

Then go to your domain name registrar, add a `CNAME DNS` record pointing your domain to Github Pages.

- type: `CNAME`
- host: `www.exampledomain.com`
- answer: `your-github-username.github.io`
- TTL: `300`

It would take some time for the changes made to DNS to propagate. Just sit back and relax for a while and changes would be applied after some time!

### Further reading :
 * [Using a custom domain with GitHub Pages](//help.github.com/articles/using-a-custom-domain-with-github-pages/)
 * [Using Jekyll as a static site generator with GitHub Pages](https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/)