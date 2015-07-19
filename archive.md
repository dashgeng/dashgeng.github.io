---
layout: page
title: 列表
---

## 日期列表

{% for post in site.posts %}
  {% capture currentyear %}{{post.date | date: "%Y"}}{% endcapture %}
  {% if currentyear != year %}
   {% unless forloop.first %}</ul>{% endunless %}
<h2>{{ currentyear }}</h2>
<ul>
    {% capture year %}{{currentyear}}{% endcapture %} 
  {% endif %}
<li>{{post.date | date: "%b %-d"}} &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
{% if site.posts.size != 0 %}</ul>{% endif %}

## 标签列表
<div id="archives">
{% for tag in site.tags %}
  <div class="archive-group">
    {% capture tag_name %}{{ tag | first }}{% endcapture %}
    <h3 id="#{{ tag_name | slugize }}">{{ tag_name }}</h3>
    <a name="{{ tag_name | slugize }}"></a>
    {% for post in site.tags[tag_name] %}
    <article class="archive-item">
      <h4><a href="{{ root_url }}{{ post.url }}">{{post.title}}</a></h4>
    </article>
    {% endfor %}
  </div>
{% endfor %}
</div>