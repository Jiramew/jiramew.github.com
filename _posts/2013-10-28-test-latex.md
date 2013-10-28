---
layout: post
title: "Test Latex"
description: ""
category: 
tags: [Test]
---
{% include JB/setup %}

<p> \begin{equation} f(x)=3x+7,\sigma \end{equation} </p>

<p> $f(x)=x^2+1$ </p>

<script type="text/javascript">
    /* * * CONFIGURATION VARIABLES: EDIT BEFORE PASTING INTO YOUR WEBPAGE * * */
    var disqus_shortname = 'shenfeng-blog'; // required: replace example with your forum shortname

    /* * * DON'T EDIT BELOW THIS LINE * * */
    (function() {
        var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
        dsq.src = 'http://' + disqus_shortname + '.disqus.com/embed.js';
        (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
<a href="http://disqus.com" class="dsq-brlink">blog comments powered by <span class="logo-disqus">Disqus</span></a>
<script>
  var post = document.getElementsByClassName('post')[0];
  if(post && post.querySelectorAll) {
    var links = post.querySelectorAll('a');
    for(var i = 0; i < links.length; i++) {
      var a = links[i];
      a.setAttribute('target', '_blank');
    }
  }
</script>
<!-- MathJax Section -->
 
<script type="text/javascript"
src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
<script>
 MathJax.Hub.Config({
          tex2jax: {
		  inlineMath: [["$", "$"], ["\\\\(", "\\\\)"]],displayMath: [["$$", "$$"], ["\\[", "\\]"]],
		  skipTags: ['script', 'noscript', 'style', 'textarea', 'pre']
          }
    });
    MathJax.Hub.Queue(function() {
        var all = MathJax.Hub.getAllJax(), i;
        for(i=0; i < all.length; i += 1) {
            all[i].SourceElement().parentNode.className += ' has-jax';
        }
    });
</script>