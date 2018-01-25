---
layout: page
title: Techy Notes
---
<ul class="techynotes">
  {% for techynotes in site.techynotes %}

    {% unless techynotes.next %}
      <h3>{{ techynotes.date | date: '%Y' }}</h3>
    {% else %}
      {% capture year %}{{ techynotes.date | date: '%Y' }}{% endcapture %}
      {% capture nyear %}{{ techynotes.next.date | date: '%Y' }}{% endcapture %}
      {% if year != nyear %}
        <h3>{{ techynotes.date | date: '%Y' }}</h3>
      {% endif %}
    {% endunless %}

    <li itemscope>
      <a href="{{ site.github.url }}{{ techynotes.url }}">{{ techynotes.title }}</a>
      <p class="techynotes-date"><span><i class="fa fa-calendar" aria-hidden="true"></i> {{ techynotes.date | date: "%B %-d" }} - <i class="fa fa-clock-o" aria-hidden="true"></i> {% include read-time.html %}</span></p>
    </li>

  {% endfor %}
</ul>
