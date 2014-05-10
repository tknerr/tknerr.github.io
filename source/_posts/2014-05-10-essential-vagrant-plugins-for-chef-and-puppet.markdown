---
layout: post
title: "Essential Vagrant Plugins for Chef and Puppet"
date: 2014-05-10 01:17:50 +0200
comments: true
categories: [Vagrant, Chef, Puppet]
published: true
---

Since the time I started working with Vagrant a few years ago some plugins have become really essential and indispensable for me:

1. [vagrant-cachier](https://github.com/fgrehm/vagrant-cachier) - caches packages downloaded within the VMs on the host
2. [bindler](https://github.com/fgrehm/bindler) - Bundler-like plugin management for Vagrant. Only for Vagrant < 1.4 :-((
3. [vagrant-proxyconf](https://tmatilai.github.io/vagrant-proxyconf/) - dead easy proxy configuration for the VMs

If you are using Chef or Puppet together with Vagrant, the following plugins should also be of interest for you:

<!-- more -->

## Using Vagrant with Chef

When working with Vagrant and Chef these plugins are indispensable:

1. [vagrant-omnibus](https://github.com/schisamo/vagrant-omnibus) - installs Chef into a bare OS basebox
2. [vagrant-berkshelf](https://github.com/berkshelf/vagrant-berkshelf) - resolves Chef cookbook dependencies

The first one makes sure that Chef gets installed in the desired version into a bare OS basebox, e.g. you can use the bare OS [bento baseboxes](https://github.com/opscode/bento) and have Chef being automatically installed on `vagrant up`.

The second one integrates [Berkshelf](http://berkshelf.com/), a dependency manager for Chef cookbooks with Vagrant. With that plugin  cookbook dependencies are automatically resolved on `vagrant up`.

Here is an [example Vagrantfile](https://github.com/tknerr/sample-application-cookbook/blob/master/Vagrantfile) using the two plugins.

## Using Vagrant with Puppet

Analogous to the Chef related plugins above here are their Puppet-specific counterparts:

1. [vagrant-puppet-install](https://github.com/mlazarov/vagrant-puppet-install) - installs Puppet into a bare OS basebox
2. [vagrant-librarian-puppet](https://github.com/mhahn/vagrant-librarian-puppet) - resolves Puppet module dependencies

They are working in the same way as the Chef plugins above, not much more to say.