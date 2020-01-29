---
layout: page
title: "Catégories"
permalink: /posts/
main_nav: true
---

{% for category in site.categories %}
  {% capture cat %}{{ category | first }}{% endcapture %}
  <h2 id="{{cat}}">{{ cat | capitalize }}</h2>
  {% for desc in site.descriptions %}
    {% if desc.cat == cat %}
      <p class="desc"><em>{{ desc.desc }}</em></p>
    {% endif %}
  {% endfor %}
  <ul class="posts-list">
  {% for post in site.categories[cat] %}
    <li>
      <strong>
        <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      </strong>
      <span class="post-date">- Posté le {% assign m = post.date | date: "%-m" %}
{{ post.date | date: "%-d" }}
{% case m %}
  {% when '1' %}Janvier
  {% when '2' %}Février
  {% when '3' %}Mars
  {% when '4' %}Avril
  {% when '5' %}Mai
  {% when '6' %}Juin
  {% when '7' %}Juillert
  {% when '8' %}Août
  {% when '9' %}Septembre
  {% when '10' %}October
  {% when '11' %}Novembre
  {% when '12' %}Decembre
{% endcase %} {{ post.date | date: "%Y" }}</span>
    </li>
  {% endfor %}
  </ul>
  {% if forloop.last == false %}<hr>{% endif %}
{% endfor %}
<br>
