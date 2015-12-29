---
layout: post
title:  "Emacs: Load additional dot files"
date:   2015-12-29 15:30:00 +0000
categories: emacs
---

Not the prettiest of code snippets but works for me. Before I put my emacs dot
file on github, I was sharing snippets of it to people in the
office. Unfortunately it was full of random configs of half played with
packages, configs with odd "quirks" or just plain personal data.

So i went down the path of splitting my files up and breaking them into the
following:

- .emacs (ready to share publically).
- private_dot_emacs.el (usually config that is specific to my personal setup).
- unstable_config_dot_emacs.el (packages I'm playing with but config is not
quite right yet).
- work_specific_dot_emacs.el (heavily work specific configs that don't need to
be made public).

The snippet below is at the bottom of my main
[.emacs](https://github.com/jackson15j/dot_emacs/blob/master/.emacs) file, with
the beauty that it wont blow up if you don't have these additional files
present.

{% highlight elisp %}
;; ========================
;; Load extra dot files (if they exist)
;; ========================
(let () (dolist (dot_emacs '("~/configs/emacs/private_dot_emacs.el"
                             "~/configs/emacs/unstable_config_dot_emacs.el"
                             "~/configs/emacs/work_specific_dot_emacs.el"))
          "Loading my extra emacs dot files if they exist."
          (when (file-exists-p dot_emacs)
            (message (concat "Loading external dot file: " dot_emacs))
            (load-file dot_emacs))))
{% endhighlight %}

Give me a shout if you have something similar or better. I'd be interested in
neatening up my hacked together elisp.
