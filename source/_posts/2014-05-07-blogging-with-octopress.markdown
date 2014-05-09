---
layout: post
title: "Blogging with Octopress"
date: 2014-05-07 21:50:25 +0200
comments: true
categories: Octopress
published: true
---

I'm happy to own a shiny new [Octopress](http://octopress.org) based blog now. It is as lean and simple, yet comfortable as it possibly can get: cms-free, git-based, markdown syntax, and with web-based editing comfort.

The articles below were both inspiring and essentially helpful for setting everything up:

* How to build [CMS-free Websites](http://developmentseed.org/blog/2012/07/27/build-cms-free-websites/) with Github Pages and Jekyll
* How trunk club [moved to Octopress + Prose + Github + Travis CI](http://techblog.trunkclub.com/moving-from-tumblr-to-octopress/)

Further am I now convinced that this is the utmost perfect and one and only acceptable solution you should ever build a blog with ;-)

<!-- more -->

## Ingredients

The basic ingredients for such a beautiful blogging platform are:

* git for version control
* github pages for hosting
* markdown for syntax
* octopress for structure / template / plugins / workflow
* travis-ci for automatically publishing changes
* prose.io for online editing (optional)

## Further Links and Documentation

Everything you need to know (documentation wise) for taming octo-blogs like these:

* Official [Octopress Docs](http://octopress.org/docs/)
* Octopress Wiki: [3rd Party Plugins](https://github.com/imathis/octopress/wiki/3rd-party-plugins)
* The [Jekyll Docs](http://jekyllrb.com/docs/home/)
* Prose Wiki: [Getting Started](https://github.com/prose/prose/wiki/Getting-Started)
* Writing in [Markdown Syntax](http://daringfireball.net/projects/markdown/syntax)
* Help with [Github Pages](https://help.github.com/categories/20/articles)

## Workflow

The workflow for creating and publishing posts is: 

1. clone repo and check out the `source` branch (never edit `master` directly!)
    * `git clone git@github.com:tknerr/tknerr.github.io.git`
    * `git checkout source`
2. create / edit the posts
    * `rake new_post["some title"]`
    * `vi source/_posts/YYYY-MM-DD-some-title.markdown`
3. preview your changes
    * `rake generate` (first time only, or whenever layout or config changes)
    * `rake preview &` (or `start /B rake preview` on windows)
4. deploy changes
    * `git add . && git commit -m "add new blog post about foo"`
    * `git push origin source`
    * *wait a minute for travis-ci to regenerate and deploy the site*

More details [here](https://github.com/tknerr/tknerr.github.io#about).