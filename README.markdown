## About

This is the [Octopress](http://octopress.org/docs/) source branch of [my techblog](http://blog.tknerr.de). It contains the theme, layout, styling and most importantly the posts in [markdown format](daringfireball.net/projects/markdown/) in the `source/_posts` directory.

It is hosted on [Github Pages](https://help.github.com/categories/20/articles) but with a [custom domain name](https://github.com/tknerr/tknerr.github.io/blob/source/source/CNAME). The site [regeneration and deplyoment](http://octopress.org/docs/deploying/github/) happens automatically via [travis-ci](https://travis-ci.org/) whenever something is pushed to the `source` branch (thanks to [this guide](http://rogerz.github.io/blog/2013/02/21/prose-io-github-travis-ci/)).

Eventually I might create / edit posts on [prose.io](prose.io/#tknerr/tknerr.github.io), which makes it even easier on mobile devices or else if you don't have Git / Ruby etc. installed. But usually I prefer to work locally, in which case the workflow is:

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


Credits to @trunkclub for their guide [on setting this whole thing up](http://techblog.trunkclub.com/moving-from-tumblr-to-octopress/).

## Get the Environment Up and Running in Docker

To get the environment up and running in docker, start a `ruby:1.9.3` container:

 * in interactive mode (`-it`), still you can detach from it via `ctrl-p` + `ctrl-q`, and use `docker attach` to re-attach
 * with the current directory mounted to `/repo` inside the container (`-v $(pwd):/repo`)
 * with port 4000 forwarded to http://localhost:4040 (`-p 4040:4000`)

Start it with `/bin/bash` as the entry point to get a bash session you can work in:
```
docker run -it -p 4040:4000 -v $(pwd):/repo ruby:1.9.3 /bin/bash
> cd /repo
> bundle install
> export RUBYOPT="-KU -E utf-8:utf-8"
> rake new_post["foo"]
> rake isolate["foo"]
> rake preview
> # ... write blog post
> rake integrate
> rake generate
> rake setup_github_pages["https://tknerr@github.com/tknerr/tknerr.github.io.git"]
> rake deploy
```

For a one-off command to generate the site and run it in preview mode:
```
docker run --rm -it -p 4040:4000 -v $(pwd):/repo ruby:1.9.3 /bin/bash -c 'cd /repo; export RUBYOPT="-KU -E utf-8:utf-8"; bundle install; rake generate; rake preview'
```



## What is Octopress?

Octopress is [Jekyll](https://github.com/mojombo/jekyll) blogging at its finest.

1. **Octopress sports a clean responsive theme** written in semantic HTML5, focused on readability and friendliness toward mobile devices.
2. **Code blogging is easy and beautiful.** Embed code (with [Solarized](http://ethanschoonover.com/solarized) styling) in your posts from gists, jsFiddle or from your filesystem.
3. **Third party integration is simple** with built-in support for Pinboard, Delicious, GitHub Repositories, Disqus Comments and Google Analytics.
4. **It's easy to use.** A collection of rake tasks simplifies development and makes deploying a cinch.
5. **Ships with great plug-ins** some original and others from the Jekyll community &mdash; tested and improved.

**Note**: Octopress requires a minimum Ruby version of `1.9.3-p0`.

## Documentation

Check out [Octopress.org](http://octopress.org/docs) for guides and documentation.
It should all apply to our current stable version (found in the `master`
branch). If this is not the case, [please submit a
fix to our docs repo](https://github.com/octopress/docs).

## Contributing

[![Build Status](https://travis-ci.org/imathis/octopress.png?branch=master)](https://travis-ci.org/imathis/octopress)

We love to see people contributing to Octopress, whether it's a bug report, feature suggestion or a pull request. At the moment, we try to keep the core slick and lean, focusing on basic blogging needs, so some of your suggestions might not find their way into Octopress. For those ideas, we started a [list of 3rd party plug-ins](https://github.com/imathis/octopress/wiki/3rd-party-plugins), where you can link your own Octopress plug-in repositories. For the future, we're thinking about ways to easier add them into our main releases.


## License
(The MIT License)

Copyright © 2009-2013 Brandon Mathis

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the ‘Software’), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED ‘AS IS’, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


#### If you want to be awesome.
- Proudly display the 'Powered by Octopress' credit in the footer.
- Add your site to the Wiki so we can watch the community grow.
