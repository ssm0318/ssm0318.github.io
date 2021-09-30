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
    <span id="all" class="category-button active" onclick="filterUsingCategory('all')">all ({{ site.projects.size }})</span>
    <span id="research" class="category-button" onclick="filterUsingCategory('research')">research
      {% assign sel = site.projects | where_exp:"item", "item.category contains 'research'" %}
      ({{ sel.size }})</span>
    <span id="coursework" class="category-button" onclick="filterUsingCategory('coursework')">coursework
      {% assign sel = site.projects | where_exp:"item", "item.category contains 'coursework'" %}
      ({{ sel.size }})</span>
    <span id="industry" class="category-button" onclick="filterUsingCategory('industry')">industry
      {% assign sel = site.projects | where_exp:"item", "item.category contains 'industry'" %}
      ({{ sel.size }})</span>
    <span id="personal" class="category-button" onclick="filterUsingCategory('personal')">personal
      {% assign sel = site.projects | where_exp:"item", "item.category contains 'personal'" %}
      ({{ sel.size }})</span>
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
        (selectedCategory == 'all' || tags.includes(selectedCategory)) 
          ? 'unset'
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