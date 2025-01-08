---
layout: page
icon: fa-solid fa-pen-nib
order: 1
---


{% assign category_name = "blogs" %} <!-- Specify the category you want to filter -->
{% assign posts_found = false %} <!-- Flag to check if any posts are found -->

<div class="post-list"> <!-- Optional: add a container for styling -->
  {% for post in site.posts %}
    {% if post.categories contains category_name %}
      {% assign posts_found = true %} <!-- Set flag to true if a post is found -->
      <article>
        <h2>
          <a href="{{ post.url }}">{{ post.title }}</a>
        </h2>
         {% if post.image %}
          <div class="post-image">
            <img src="{{ post.image.path }}" alt="{{ post.image.alt }}">
          </div>
         {% endif %}
        <div class="post-content"> <!-- Added a div for styling the content -->
          {{ post.content | markdownify }} <!-- Display the full post content -->
        </div>
        <p><small>Posted on {{ post.date | date: "%B %d, %Y" }}</small></p>
      </article>
    {% endif %}
  {% endfor %}
</div>

{% unless posts_found %}
  <p>No blog posts found in this category.</p>
{% endunless %}
