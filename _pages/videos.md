---
layout: page
title: videos
label: 3_videos
permalink: /videos/
description:
nav: true
category: [Singing, Video Production]
---

<!-- https://langrsoft.com/2020/03/26/filtering-blog-posts-by-category-with-jekyll/ -->

<div class="fun">
  {% assign sorted_projects = site.videos | sort: "importance" %}
  {% for project in sorted_projects %}
    <div class="row justify-content-sm-center" id="{{ project.importance }}">
      <div class="video-title col-sm-4 mt-3 mt-md-0">
        {{ project.title }}<br>
        {% for category in project.category %}
          <button class="badge" onclick="filterUsingCategory('{{ category }}')">{{ category }}</button>
        {% endfor %}
      </div>
      <div class="video-container col-sm-8 mt-3 mt-md-0">
        <iframe class="video" loading="lazy" src="{{ project.link }}" loading="auto" frameborder="0" allow="accelerometer; autoplay *; clipboard-write; encrypted-media *; gyroscope; picture-in-picture; fullscreen *"  sandbox="allow-forms allow-popups allow-same-origin allow-scripts allow-presentation allow-top-navigation-by-user-activation" allowfullscreen></iframe>
      </div>
    </div>
  {% endfor %}
</div>

<script type="text/javascript">
  function filterUsingCategory(selectedCategory) {
    var id = 0;
    {% for post in site.videos %}
      var tags = {{ post.category | jsonify }};

      var postDiv = document.getElementById(({{ post.importance }}).toString());
      postDiv.style.display =
        (selectedCategory == 'ALL' || tags.includes(selectedCategory)) 
          ? 'flex'
          : 'none';
    {% endfor %}
    
    var catButtons = document.getElementsByClassName("category-button");
    for (let i in catButtons) {
      let button = catButtons[i];
      if (button.id == selectedCategory) {
        button.classList.add("active");
      } else {
        button.className = "category-button";
      }
    }
  }
</script>