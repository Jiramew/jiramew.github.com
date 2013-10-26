---
layout: page
title: Hanbing Yang
tagline: Welcome to Hanbing's tech-blog!
---
{% include JB/setup %}

## About myself

In `_config.yml` remember to specify your own data:
    
    title : Hanbing Tech-Blog
    
    author :
      name : Hanbing Yang
      email : hanbingflying@gmail.com
      github : jiramew
      Sina MicroBlog : <http://weibo.com/1329143471>

	  
## My CV

---
<p>This is an <a href="https://github.com/Jiramew/jiramew.github.com/raw/master/assets/CV.pdf" title="With a Title">example link</a>.</p>
---
`This is my [CV](https://github.com/Jiramew/jiramew.github.com/raw/master/assets/CV.pdf)`	
	
	
## Posts

This blog contains sample posts which help stage pages and blog data.
When you don't need the samples anymore just delete the `_posts/core-samples` folder.

    $ rm -rf _posts/core-samples

Here's the posts list,

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
