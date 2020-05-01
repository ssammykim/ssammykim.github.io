---
layout: page
title: sammy
permalink: /sammy/
---

<!--<figure style="width: 150px" class="align-left">
  <img src="{{ '/images/profile_page_sammy.png' | absolute_url }}" alt="">
  <figcaption>dd</figcaption>
</figure>-->

<figure style="width: 150px" class="align-center">
  <a href="#"><img src="{{ '/images/profile_page_sammy.png' | absolute_url }}" alt=""></a>
</figure> 
<center>
  <b>Sammy KIM</b> :kissing_heart: always searching for the next <b>challenge</b><br>
  AI designer, NLP engineering Director at. <a href="https://www.kakaoenterprise.com" target="_blank">Kakaoenterprise</a><br>
  former Product Owner, Tech Strategist at. <a href="https://scatterlab.co.kr" target="_blank">Scatterlab</a>, <a href="https://pingpong.us" target="_blank">pingpong</a>
</center> 
<br>
<br>
<center>
  <h3>tracking log</h3>
  <i>since April 29, 2020</i><br>
  total posts : {{ site.posts | size }}
{% assign number_of_posts = 0 %} {% for post in site.posts %}{% assign currnet_year = post.date | date: "%Y" %}{% assign previous_year = post.previous.date | date: "%Y" %}{% assign number_of_posts = number_of_posts | plus: 1 %}{% if currnet_year != previous_year %}<br>
  {{ currnet_year }} : {{ number_of_posts }} {% assign number_of_posts = 0 %}{% endif %}{% endfor %}
 </center>
