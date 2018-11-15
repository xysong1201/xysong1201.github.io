---
layout: post
title: "Use MathJax to enable write Equations with Latex in Jekyll blogs"
---

If you are familiour with _Latex_ and you want to use it to add equations in your jekyll blog, insert the following code in the *default.html* in the *_includes* folder.
```
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  tex2jax: {
    inlineMath: [['$','$'], ['\\(','\\)']],
    processEscapes: true
  }
});
</script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.0/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

```
And now you are able to use Latex syntax to write equations.
