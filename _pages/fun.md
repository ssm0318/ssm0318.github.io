---
layout: page
title: 🎵🎶♪
label: fun
permalink: /fun/
description:
nav: true
nav_order: 100
category: [Singing, Video Production]
---

<div class="fun">
  {% assign sorted_projects = site.fun | sort: "importance" %}
  {% for project in sorted_projects limit: 20 %}
    <div class="row justify-content-sm-center video-row" id="{{ project.importance }}">
      <div class="video-title col-sm-4 mt-3 mt-md-0">
        {{ project.title }}<br>
        {% for category in project.category %}
          <span class="badge">{{ category }}</span>
        {% endfor %}
      </div>
      <div class="video-container col-sm-8 mt-3 mt-md-0">
        <iframe class="video lazy-video" width="100%" loading="lazy" data-src="{{ project.link }}" frameborder="0" allow="accelerometer; autoplay *; clipboard-write; encrypted-media *; gyroscope; picture-in-picture; fullscreen *" sandbox="allow-forms allow-popups allow-same-origin allow-scripts allow-presentation allow-top-navigation-by-user-activation" allowfullscreen></iframe>
      </div>
    </div>
  {% endfor %}
  
  <div id="hidden-videos" style="display: none;">
    {% for project in sorted_projects offset: 20 %}
      <div class="row justify-content-sm-center video-row" id="{{ project.importance }}">
        <div class="video-title col-sm-4 mt-3 mt-md-0">
          {{ project.title }}<br>
          {% for category in project.category %}
            <span class="badge">{{ category }}</span>
          {% endfor %}
        </div>
        <div class="video-container col-sm-8 mt-3 mt-md-0">
          <iframe class="video lazy-video" width="100%" loading="lazy" data-src="{{ project.link }}" frameborder="0" allow="accelerometer; autoplay *; clipboard-write; encrypted-media *; gyroscope; picture-in-picture; fullscreen *" sandbox="allow-forms allow-popups allow-same-origin allow-scripts allow-presentation allow-top-navigation-by-user-activation" allowfullscreen></iframe>
        </div>
      </div>
    {% endfor %}
  </div>
  
  <div>
    <p>
      These are music covers I led and worked on with about 30 friends from my college. Most of us weren’t pros in music or video, but we came together to create everything ourselves---from the vocals and live instrumentals to mixing, mastering, and video production. With support from Seoul City’s Youth Hub, we wanted to show that with the right group of people, anything can become art.
    </p>
  </div>

  {% if sorted_projects.size > 20 %}
    <div class="row justify-content-sm-center mt-4">
      <button id="load-more-btn" class="btn btn-primary">Load More</button>
    </div>
  {% endif %}
</div>

<script>
document.addEventListener("DOMContentLoaded", function() {
    const lazyVideos = document.querySelectorAll(".lazy-video");
    const batchSize = 2;
    let currentBatch = 0;

    loadNextBatch();

    function loadNextBatch() {
        const start = currentBatch * batchSize;
        const end = start + batchSize;

        for (let i = start; i < end && i < lazyVideos.length; i++) {
            let video = lazyVideos[i];
            video.src = video.dataset.src;
        }

        currentBatch++;
        
        if (currentBatch * batchSize < lazyVideos.length) {
            setTimeout(loadNextBatch, 200);
        }
    }

    const loadMoreBtn = document.getElementById("load-more-btn");
    const hiddenVideos = document.getElementById("hidden-videos");

    if (loadMoreBtn) {
        loadMoreBtn.addEventListener("click", function() {
            hiddenVideos.style.display = "block";
            loadMoreBtn.style.display = "none";
            loadNextBatch();
        });
    }
});
</script>
