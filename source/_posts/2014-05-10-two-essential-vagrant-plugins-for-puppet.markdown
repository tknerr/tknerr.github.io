---
layout: post
title: "Two Essential Vagrant Plugins for Puppet"
date: 2014-05-10 01:17:50 +0200
comments: true
categories: [Vagrant, Puppet]
published: false
---

Two essential Vagrant plugins when working with Vagrant and Puppet:

1. [vagrant-puppet-install](https://github.com/mlazarov/vagrant-puppet-install)
2. [vagrant-librarian-puppet](https://github.com/mhahn/vagrant-librarian-puppet)

The first one makes sure puppet gets installed in the desired version into a bare OS basebox, e.g. you can use the bare OS [bento baseboxes](https://github.com/opscode/bento) and have puppet installed on `vagrant up` via the plugin.

The second one integrates librarian-puppet (a dependency manager for puppet modules) with Vagrant, i.e. puppet module dependencies are automatically resolved on `vagrant up`.
