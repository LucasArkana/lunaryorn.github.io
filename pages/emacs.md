---
title: My Emacs
layout: page
excerpt: |
  I use Emacs for most of my daily work and maintain Flycheck, an Emacs package
  for automatic syntax checking.
extra_feeds:
  - title: "Emacs. What else? (Emacs posts)"
    url: "/emacs.atom"
---

I use [GNU Emacs][] for most of my daily work, with an
[elaborate personal configuration][emacsd].  I maintain [Flycheck][], a popular
package for automatic syntax checking, and sometimes write about Emacs on this
blog.  These are my latest Emacs posts
([Atom feed]({{site.baseurl}}/emacs.atom)):

{% include post-list.html posts=site.categories.emacs limit=5 include_excerpt=true %}

[GNU Emacs]: http://www.gnu.org/software/emacs/
[Flycheck]: http://www.flycheck.org
[emacsd]: https://github.com/lunaryorn/.emacs.d
