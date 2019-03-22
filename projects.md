<!-- ---
layout: landing
title: Projects
description: Lorem ipsum dolor est
image: assets/images/floor3_v5.jpg
nav-menu: true
--- -->

<section>
  <div class="filter inner">
    <ul class="blog-tags-list">
      {% assign sorted_tags = site.tags | sort %}
      {% for tag in sorted_tags %}
        {% assign t = tag | first %}
        {% assign posts = tag | last %}
        <li class="blog-tag-item" id="{{ t }}-item">
          <a class="button primary small" href onclick="filter('{{ t }}'); return false;">{{ t }}</a>
        </li>
      {% endfor %}
    </ul>
  </div>
</section>


{% for tag in site.tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}
<section class="filter-tiles blog-list-container hidden" id="{{ t }}-container">
  <div class="inner">
    <div class="">
      <div class="blog-list">
        {% for post in posts %}
          {% if post.tags contains t %}
            <article>
              <span class="image">
                <img src="{{ post.image }}" alt="" />
              </span>
              <header class="major">
                <h3><a href="{{ post.url | relative_url  }}" class="link">{{ post.title }}</a></h3>
                <p>{{ post.description }}</p>
              </header>
            </article>
          {% endif %}
        {% endfor %}
      </div>

      {% assign numPosts = posts | size %}
      {% if numPosts == 1 %}
        <p>{{ posts | size }} projects containing <b>{{ t }}</b></p>
      {% else %}
        <p>{{ posts | size }} projects containing <b>{{ t }}</b></p>
      {% endif %}
    </div>
  </div>
</section>
{% endfor %}
