---
layout: post
title:  "Hello World! Welcome to my blog!"
date:   2017-10-14 15:22:30 +0530
comments: true
categories: blog
---
This is my first blog post.
<form method="POST" action="https://api.staticman.net/v2/entry/shivendra-chauhan/shivendra-chauhan.ggithub.io/master/">
  <input name="options[slug]" type="hidden" value="{{ page.slug }}">
  <label>Name</label><input name="fields[name]" type="text">

  <label>E-mail</label><input name="fields[email]" type="email">

  <label>Message</label><textarea name="fields[message]"></textarea>


  <button type="submit">Go!</button>
</form>
