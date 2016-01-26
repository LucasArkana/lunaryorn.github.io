---
title: Why Spacemacs?
category: emacs
---

Over the last six months I was slowly gravitating towards [Spacemacs][], an
Emacs distribution that aims to combine Emacs with VIM.  About a month ago
I finally couldn’t resist its gravitational pull anymore, and abandoned my
hand-crafted, elaborate, >3k lines personal Emacs configuration and switched to
Spacemacs.  In this post I’ll share why I think that Spacemacs is an awesome
project, and why I’m happy that I’ve made it through a bumpy start and am now
using Spacemacs full-time.

<!--more-->

[Spacemacs]: http://spacemacs.org

## You’re using a starter kit, why⁈ ##

> Spacemacs is beautiful.

What got me attracted to Spacemacs initially was the beautiful user interface,
particularly the beautiful sleek mode line.  I love beautiful things, and the
Spacemacs UI was just so much more beautiful than all that I had managed to
achieve in my own configuration.  Even as I write this post in Spacemacs, after
almost six months of using it eight hours a day for work, I still marvel at its
beauty.

> Spacemacs is not a starter kit—it’s an editor on its own!

What made me stay with Spacemacs eventually was not its beauty, though; it was
the revelation that Spacemacs—unlike Prelude, Graphene and similar projects—is
*not* a “starter kit”.  On the contrary: Spacemacs is actually an editor on its
own, with a special focus on a beautiful user interface, great user experience
and deep integration of packages.  It feels like a perfectly integrated product
made from one single piece.

## Layers below ##

As bright as Spacemacs shines on the surface, as solid are it’s underpinnings
and foundations, notably it’s excellent, well-designed and powerful
[configuration system called “layers”][layers].  A layer groups related packages
and configuration into a single unit that provides a specific feature.  Each
layer is activated as a whole.  The `git` layer for instance provides support
for the Git version control system and enables the popular [Magit][] extension
and a couple of other Git-related packages.  Activating this layer enables all
Git features at once, without any further customisation required.

> Layers are transparent.  They _never_ get in your way.

Nonetheless—and this is what’s so particularly awesome—layers are not opaque.
A layer is not a “take all or nothing” thing.  Each individual package within a
layer can be disabled in isolation without breaking the layer at large.
It’s even possible to “steal” a package from a layer, i.e. to use a layer but
with an entirely different configuration for one specific package.

> Layers enable horizontal *and* vertical customisation.

Unlike conventional starter kits, Spacemacs’ layer system succeeds at enabling
customisation in both dimensions: Horizontally by adding new layers to your
customisation, but also vertically by changing individual parts of a layer—which
is what all other starter kits fail to provide.

> Layers give structure and guidance to your personal configuration.

Spacemacs includes [many built-in layers][built-in-layers], but also lets users
define their own layers and thus gives you structure and guidance to organise
your configuration without risking the dreaded “Emacs bankruptcy”.  Spacemacs
configuration works best if you create layers early on for every additional
configuration, and leave Spacemacs’ init file (`~/.spacemacs` or
`~/.spacemacs.d/init.el`) only for Spacemacs’ own settings (as in the template)
and the list of enabled layers and excluded packages.

The **external structure** of layers helps you to group related configuration
into single “units” or larger features.  Spacemacs encourages you to follow its
own example and not create a single large layer for your entire configuration,
but rather split your configuration into small isolated layers, where each layer
works as a single unit that provides one consistent larger feature.

The **internal structure** of a layer in turn helps you to modularise your
configuration around the concept of packages, where each package provides one
individual feature of a layer (e.g. completion, compilation, syntax
highlighting, etc.).  Layer packages are mostly identical with ELPA
packages—Spacemacs will try to install packages from ELPA by default—but they
don’t have to be: Spacemacs also knows “local” packages, i.e. libraries that are
contained within a layer, which allows to keep a layer itself free from large
amounts of custom extension code.  Custom code goes into local packages, which
are then enabled in the package configuration of a layer.

[Magit]: http://magit.vc
[evil-magit]: https://github.com/justbur/evil-magit
[built-in-layers]: http://spacemacs.org/layers/LAYERS.html
[layers]: http://spacemacs.org/doc/LAYERS.html

## Dark corners ##

Even the best software has it’s dark corners, and there are some bad places in
Spacemacs as well.  Like all large projects that suck up many external
contributions Spacemacs suffers from a wildly varying quality, and some pieces
of code are downright bad.  Having seen some of these places I can’t help but
wonder how fast Spacemacs is accumulating technical debt, and whether the
project provides the structures and processes to mitigate this problem.

## But VIM? ##

Spacemacs’ banner brags about Spacemacs being “Emacs *and* VIM”, and many people
seem to choose Spacemacs for its VIM bindings only.  The work that Spacemacs has
done on providing a comprehensive and consistent set of VIM bindings for all
its included packages and modes is truly amazing, and absolutely brings Evil
Mode to the next level, but Spacemacs goes far beyond being VIM.

> VIM bindings are nice, but…

To me the VIM part was no incentive at all.  I had been using VIM for quite some
time in the past and I’m happy to have modal editing again, but it wasn’t what
sold Spacemacs to me.

> …Spacemacs’ importance goes far far beyond bindings.

I think the work and the value of Spacemacs go far, far beyond VIM bindings, and
its real selling point and major contribution to the Emacs universe is its
design (the layer system in particular), and the unique focus on building an
integrated and consistent product that immediately delivers value to end users;
a focus that many, many Emacs Lisp projects are entirely missing.

> Spacemacs puts the user first.

I admire Spacemacs for trying to put the user first, however hard that is, and
thinking about user’s needs first.  This mindset is what leads to an awesome UI,
to a great user experience, and to [superb documentation][docs], things that
many other Emacs Lisp projects are missing.

I ❤️ Spacemacs!

[docs]: http://spacemacs.org/doc/DOCUMENTATION.html
