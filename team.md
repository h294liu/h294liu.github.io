---
layout: page
title: team
permalink: /team/
main_nav: true
---

---
<h4>Members</h4>
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

<h4>Group Alumni</h4>
<ul class="former-students-list">
{% assign former_students = site.categories['former_member_grad']
  | concat: site.categories['former_member_undergrad']
  | sort: 'date' %}

{% for member in former_students reversed %}
  <li>
    <strong>
      <a href="{{ member.url | prepend: site.baseurl }}">{{ member.name }}</a>
    </strong>
    — {{ member.position }}<br>
    {{ member.project }} ({{ member.term }})
  </li>
{% endfor %}
</ul>