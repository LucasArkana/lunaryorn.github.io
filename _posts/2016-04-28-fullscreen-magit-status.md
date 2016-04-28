---
title: Show Magit Status window in fullscreen
category: emacs
tags: emacs-spotlight
layout: series-post
excerpt: |
  Show Magit’s status buffer fullscreen with `display-buffer-alist`.
---

When I moved back to my own Emacs configuration from Spacemacs one thing that
I missed most was to have [Magit][]’s status window cover the whole frame.

Luckily this feature is easy to reproduce with a simple entry
in [`display-buffer-alist`][dba]:

``` emacs-lisp
(add-to-list 'display-buffer-alist
             `(,(rx "*magit: ")
               (lunaryorn-display-buffer-fullframe)
               (reusable-frames . nil)))
```

Unfortunately there’s no built-in display function to show a window covering the
whole frame but it’s easy enough to write one:

``` emacs-lisp
(defun lunaryorn-display-buffer-fullframe (buffer alist)
  "Display BUFFER in fullscreen.

ALIST is a `display-buffer' ALIST.

Return the new window for BUFFER."
  (let ((window
         (or (display-buffer-use-some-window buffer alist)
             (display-buffer-pop-up-window buffer alist))))
    (when window
      (delete-other-windows window))
    window))
```

We simply need to get hold of any arbitrary window for the `buffer`, and then
just delete all other windows, leaving only the window for our `buffer`.

That’s it.  Enjoy and share :)

[dba]: {% post_url 2015-04-29-the-power-of-display-buffer-alist %}
[Magit]: https://magit.vc
