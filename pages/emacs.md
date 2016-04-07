---
title: My Emacs
layout: page
excerpt: |
  I use Spacemacs for most of my daily work and maintain a couple of
  Emacs packages.
extra_feeds:
  - title: "Emacs. What else? (Emacs posts)"
    url: "/emacs.atom"
---

I use [GNU Emacs][] distribution for most of my daily work, with an
[elaborate personal configuration][emacsd].  I also maintain a couple of Emacs
packages:

* [Flycheck][] is an on-the-fly syntax checking extension, intended as
  replacement for Flymake, with better performance, more supported languages and
  cooler features.
* [Puppet Mode][] is a major mode for Puppet 3 manifests.  Puppet is a
  configuration and provisioning tool.
* [ansible-doc][] lets you read the documentation of Ansible modules in Emacs.
* [fancy-battery][] shows the battery status in the mode line.  It's like the
  built-in `display-battery-mode`, but fancier and more customisable.
* [pkg-info][] is a library to obtain information about installed
  packages.  Notably it lets you query the versions of installed packages.
* [EPL][] is a library to work with the Emacs package manager.  It lets you
  query the package database, install or remove packages, and perform upgrades.

I frequently write about Emacs; these are my latest posts
([Atom feed]({{site.baseurl}}/emacs.atom)):

{% include post-list.html posts=site.categories.emacs limit=5 include_excerpt=true %}

[GNU Emacs]: http://www.gnu.org/software/emacs/
[Flycheck]: http://www.flycheck.org
[Puppet Mode]: https://github.com/lunaryorn/puppet-mode
[ansible-doc]: https://github.com/lunaryorn/ansible-doc.el
[fancy-battery]: https://github.com/lunaryorn/fancy-battery.el
[pkg-info]: https://github.com/lunaryorn/pkg-info.el
[epl]: https://github.com/cask/epl
[emacsd]: https://github.com/lunaryorn/.emacs.d
