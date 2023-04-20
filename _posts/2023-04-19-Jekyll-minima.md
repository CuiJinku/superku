---
layout: post
title: Jekyll minima
---

The site adopts the default static site generator, `Jekyll` and the default theme, `minima`.

The GitHub Pages tutorial, however, does not adopt the latest `minima` theme.

## `remote_theme`

Use the key `remote_theme` in the `_config.yml` instead of `theme`.

Set the value to a url or a repository name according to the doc of [jekyll-remote-theme](https://github.com/benbalter/jekyll-remote-theme)

The latest `minima` has various theme skins.

I set `skin: auto`.


## `MathJax`

Override the `custom-head.html` to enable `MathJax`.

Steps:

1. Create a `_includes` folder
2. Save the file `custom-head.html` with the following content[^ht]:

```HTML
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/latest.js?config=TeX-MML-AM_CHTML">
</script>
<script type="text/x-mathjax-config">
        MathJax.Hub.Config({
          extensions: ["tex2jax.js"],
          jax: ["input/TeX", "output/HTML-CSS"],
          tex2jax: {
            inlineMath: [ ['$','$'], ["\\(","\\)"] ],
            displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
            processEscapes: true
          },
          "HTML-CSS": { availableFonts: ["TeX"] }
        });
</script>
```

The latest version of `MathJax` is `2.7.7` when the post is published[^MathJax].

[^ht]: [How to add Latex to Minimal Mistakes](https://www.janmeppe.com/blog/How-to-add-mathjax-to-minimal-mistakes/)

[^MathJax]: [MathJax Documentation](https://docs.mathjax.org/en/latest/index.html)




