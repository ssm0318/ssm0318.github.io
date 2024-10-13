---
layout: page
title: 🎵
label: fun
permalink: /fun/
description:
nav: true
nav_order: 100
category: [Singing, Video Production]
---

<div class="fun">
  {% assign sorted_projects = site.fun | sort: "importance" %}
  {% for project in sorted_projects %}
    <div class="row justify-content-sm-center video-row" id="{{ project.importance }}">
      <div class="video-title col-sm-4 mt-3 mt-md-0">
        {{ project.title }}<br>
        {% for category in project.category %}
          <span class="badge">{{ category }}</span>
        {% endfor %}
      </div>
      <div class="video-container col-sm-8 mt-3 mt-md-0">
        <iframe class="video lazy-video" loading="lazy" data-src="{{ project.link }}" frameborder="0" allow="accelerometer; autoplay *; clipboard-write; encrypted-media *; gyroscope; picture-in-picture; fullscreen *" sandbox="allow-forms allow-popups allow-same-origin allow-scripts allow-presentation allow-top-navigation-by-user-activation" allowfullscreen></iframe>
      </div>
    </div>
  {% endfor %}
</div>

<script>
document.addEventListener("DOMContentLoaded", function() {
    const lazyVideos = document.querySelectorAll(".lazy-video");
    const batchSize = 2;  // Number of videos to load at a time
    let currentBatch = 0;

    // Load initial two videos
    loadNextBatch();

    // Function to load the next batch of videos
    function loadNextBatch() {
        const start = currentBatch * batchSize;
        const end = start + batchSize;

        // Iterate over the next batch of videos and load them
        for (let i = start; i < end && i < lazyVideos.length; i++) {
            let video = lazyVideos[i];
            video.src = video.dataset.src; // Set the real video source from data-src
        }

        currentBatch++;
        
        // If there are more videos to load, set a delay for the next batch
        if (currentBatch * batchSize < lazyVideos.length) {
            setTimeout(loadNextBatch, 200);  // Delay of 0.5 seconds
        }
    }
});
</script>
