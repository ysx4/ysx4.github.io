---
layout: page
title: Photography
image: yang1.jpg
---
<ul class="photography">
  {% for photography in site.photography %}

    {% unless photography.next %}
      <h3>{{ photography.date | date: '%Y' }}</h3>
    {% else %}
      {% capture year %}{{ photography.date | date: '%Y' }}{% endcapture %}
      {% capture nyear %}{{ photography.next.date | date: '%Y' }}{% endcapture %}
      {% if year != nyear %}
        <h3>{{ photography.date | date: '%Y' }}</h3>
      {% endif %}
    {% endunless %}

    <li itemscope>
      <a href="{{ site.github.url }}{{ photography.url }}">{{ photography.title }}</a>
      <p class="photography-date"><span><i class="fa fa-calendar" aria-hidden="true"></i> {{ photography.date | date: "%B %-d" }} - <i class="fa fa-clock-o" aria-hidden="true"></i> {% include read-time.html %}</span></p>
    </li>

  {% endfor %}
</ul>
