---
layout: page
title: "All Blog Posts"
type: blogs # This tells _layouts/page.html to use the 'blogs' section logic
---

<div class="all-posts">
  <h2>All My Articles and Insights</h2>
  <p>Here you'll find a complete archive of all my blog posts, from the newest to the oldest.</p>

  <ul class="post-list">
    {% for post in site.posts %} {# This loop iterates through ALL posts, no limit #}
      <li>
        {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
        <span class="post-meta">{{ post.date | date: date_format }}</span>
        <h3>
          <a class="post-link" href="{{ post.url | relative_url }}">
            {{ post.title | escape }}
          </a>
        </h3>
        {%- if site.show_excerpts -%}
          {{ post.excerpt }}
        {%- endif -%}
      </li>
    {% endfor %}
  </ul>
</div>