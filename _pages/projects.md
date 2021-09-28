---
layout: page
title: projects
label: 2_projects
permalink: /projects/
description: A growing collection of your cool projects.
nav: true
display_categories: false
horizontal: false
---

<div class="projects">
  <div class="categories">
    <button id="ALL" class="category-button active" onclick="filterUsingCategory('ALL')">ALL</button>
    {% assign site_categories = site.projects | map: "category" | compact | uniq %}
    {% for category in site_categories %}
      <button id="{{ category }}" class="category-button" onclick="filterUsingCategory('{{ category }}')">{{ category }}
        {% assign sel = site.projects | where_exp:"item", "item.category contains category" %}
        ({{ sel.size }})</button>
    {% endfor %}
  </div>

  {% assign sorted_projects = site.projects | sort: "importance" %}
  <div class="container">
    <div class="row">
    {% for project in sorted_projects %}
      {% include projects_horizontal.html %}
    {% endfor %}
    </div>
  </div>
</div>

<script type="text/javascript">
  function filterUsingCategory(selectedCategory) {
    var id = 0;
    {% for post in site.projects %}
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