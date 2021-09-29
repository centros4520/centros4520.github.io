---
layout: page
title: Event List
permalink: /events/
---
<!-- Html Elements for Search -->
<!-- <header class="post-header">
    <h1 class="section-title ">{{ page.title | escape }}</h1>
</header>  -->
<section class="project__section">
  {% assign projects = site.events | sort: 'date' | reverse %} 
  {% for project in projects %} 
  {% capture this_year %} {{ project.date  | date: "%Y" }} {% endcapture %} 
  {% capture next_year %} {{ project.previous.date | date: "%Y" }} {% endcapture %} 
  {% if forloop.first %}
  <div class="project__container">
  <h4 class="project__year" id="{{ this_year }}-ref">Year {{this_year}}</h4>
  <div class="project__list">
  {% endif %}
    <a class='project__item' href="{{ base }}{{ project.url | replace: ".html", "" }}">
        <div class='project__date'><time datetime="{{ project.date | date_to_xmlschema }}">{{ project.date  | date: "%B"  }}</time></div>
        <div class='project__title'>{{ project.title | strip_html | truncatewords:18 | escape  }}</div>
        <div class='project__excerpt'>{{ project.blurb | strip_html }} </div>
      </a>
        
  {% if forloop.last %}
  </div>
  </div><!--End of project__container-->
  {% else %} {% if this_year != next_year %}
  </div>
  </div><!--End of project__container-->
  <div class="project__container__next">
  <h4 class="project__year project__year__next" id="{{ next_year }}-ref">Year {{next_year}}</h4>
  <div class="project__list">
    {% endif %} 
    {% endif %} 
  {% endfor %}
</section>
