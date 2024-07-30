---
layout: page
# title: videos
label: 3_videos
permalink: /videos/
description:
nav: true
category: [Singing, Video Production]
---

<div class="fun">
  {% assign sorted_projects = site.videos | sort: "importance" %}
  {% for project in sorted_projects %}
    <div class="row justify-content-sm-center" id="{{ project.importance }}">
      <div class="video-title col-sm-4 mt-3 mt-md-0">
        {{ project.title }}<br>
        {% for category in project.category %}
          <span class="badge">{{ category }}</span>
        {% endfor %}
      </div>
      <div class="video-container col-sm-8 mt-3 mt-md-0">
        <iframe class="video" loading="lazy" src="{{ project.link }}" loading="auto" frameborder="0" allow="accelerometer; autoplay *; clipboard-write; encrypted-media *; gyroscope; picture-in-picture; fullscreen *"  sandbox="allow-forms allow-popups allow-same-origin allow-scripts allow-presentation allow-top-navigation-by-user-activation" allowfullscreen></iframe>
      </div>
    </div>
  {% endfor %}
</div>