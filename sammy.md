---
layout: page
title: sammy
permalink: /sammy/
---
<P>
Sammy KIM  
AI designer, NLP engineering Director at. Kakaoenterprise  
formal Product Owner, Tech Strategiest at. Scatterlab, pingpong  
</p>

### tracking log
start: April 29, 2020  

total posts: {{ site.posts | size }}

{% assign number_of_posts = 0 %} {% for post in site.posts %}{% assign currnet_year = post.date | date: "%Y" %}{% assign previous_year = post.previous.date | date: "%Y" %}{% assign number_of_posts = number_of_posts | plus: 1 %}{% if currnet_year != previous_year %}

- {{ currnet_year }} : {{ number_of_posts }} {% assign number_of_posts = 0 %}{% endif %}{% endfor %}
