---
layout: page
title: team
permalink: /team/
main_nav: true
---

---

<div class="row">
  {% for member in site.categories['current_member'] reversed %}
    <div class="col-lg-4 col-md-4 col-sm-4">
      <div class="member-info">
        <div class="square-image">
          <img src="{{ site.baseurl }}/assets/img/{{ member.img }}" alt="{{ member.name }}">
        </div>
        <div class="text-container">
          <h4><a href="{{ member.url | prepend: site.baseurl }}">{{ member.name }}</a></h4>
          <p>{{ member.position }}</p>
        </div>
      </div>
    </div>
  {% endfor %}
</div>

<hr>

<h4>Former undergraduate students</h4>
<div class="row">
<!--     {% for member in site.categories['former_member_grad'] reversed %}
      <li>
        <a href="{{ member.url | prepend: site.baseurl }}">{{ member.name }}</a>. {{ member.program }}, {{ member.endmonth }} {{ member.endyear }}. {{ member.thesisTitle }}
      </li>
    {% endfor %} -->
    
    {% for member in site.categories['former_member_undergrad'] %}
    <div class="col-lg-4 col-md-4 col-sm-4">
      <div class="member-info">
        <div class="square-image">
          <img src="{{ site.baseurl }}/assets/img/{{ member.img }}" alt="{{ member.name }}">
        </div>
        <div class="text-container">
          <h4><a href="{{ member.url | prepend: site.baseurl }}">{{ member.name }}</a></h4>
          <p>{{ member.term }}</p>
        </div>
      </div>
    </div>
  {% endfor %}
</div>
