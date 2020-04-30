---
layout: page
title: sammy
permalink: /sammy/
---

Sammy KIM :kissing_heart: , always searching for the next challenge<br>
AI designer, NLP engineering Director at. <a href="https://www.kakaoenterprise.com" target="_blank">Kakaoenterprise</a><br>
former Product Owner, Tech Strategist at. <a href="https://scatterlab.co.kr" target="_blank">Scatterlab</a>, <a href="https://pingpong.us" target="_blank">pingpong</a><br><br>


### tracking log
since April 29, 2020  
total posts: {{ site.posts | size }}
{% assign number_of_posts = 0 %} {% for post in site.posts %}{% assign currnet_year = post.date | date: "%Y" %}{% assign previous_year = post.previous.date | date: "%Y" %}{% assign number_of_posts = number_of_posts | plus: 1 %}{% if currnet_year != previous_year %}
- {{ currnet_year }} : {{ number_of_posts }} {% assign number_of_posts = 0 %}{% endif %}{% endfor %}
