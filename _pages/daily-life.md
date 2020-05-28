---
layout: page
permalink: /daily-life/
---

<div id="archives">
{% for category in site.categories %}
  <div class="archive-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    {% if category_name == "Plan" or category_name == "Daily Life" %}
      <div id="#{{ category_name | slugize }}"></div>
      <p></p>
      
      <h3 class="category-head">{{ category_name }}</h3>
      <a name="{{ category_name | slugize }}"></a>
      {% for post in site.categories[category_name] %}
      <article class="archive-item post-item">
        <a href="{{ site.baseurl }}{{ post.url }}">{% if post.title and post.title != "" %}{{post.title}}{% else %}{{post.excerpt |strip_html}}{%endif%}</a><span class="created-at-item">{{ post.date | date: "%b %-d, %Y"}}</span>
      </article>
      {% endfor %}
    {% endif %}
  </div>
{% endfor %}
</div>