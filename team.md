---
layout: page
title: TEAM
permalink: /team/
main_nav: true
---

<style>
  /* Add your custom styles here */
  
  .member-info {
    margin-bottom: 20px; /* Adjust bottom margin for each member-info block */
  }

  h4 {
    margin-top: 10px; /* Adjust top margin for h4 headers */
    margin-bottom: 5px; /* Adjust bottom margin for h4 headers */
  }

  p {
    margin-top: 5px; /* Adjust top margin for paragraphs */
    margin-bottom: 10px; /* Adjust bottom margin for paragraphs */
  }

.slider {
  width: 100%;
  position: relative;
}

.slider img {
  width: 100%;
  display: none;
  position: absolute;
  top: 0;
  left: 0;
}

.slider img:first-child {
  display: block;
}

  /* Add more styles as needed */

</style>

<h3>Current Group Members</h3>
{% for member in site.categories['current_member'] reversed %}
  <div class="col-lg-3 col-md-3 col-sm-3">
    <div class="member-info">
      <div class="image-container square-image">
        <img src="{{ site.baseurl }}/assets/img/{{ member.img }}" alt="{{ member.name }}">
      </div>
      <div class="text-container">
        <h4><a href="{{  member.url | prepend: site.baseurl }}">{{ member.name }}</a></h4>
        <!-- Add other text content here -->
        <p style="line-height: 1.0;">{{ member.position }}</p>
      </div>
    </div>
  </div><!-- /col-lg-3 -->
{% endfor %}

<hr>

{% comment %}
<h3>Former Graduate Students</h3>
{% for member in site.categories['former_member_grad'] reversed %}
  <li>
    <a href="{{ member.url | prepend: site.baseurl }}">{{ member.name }}</a>. {{ member.program }}, {{ member.endmonth }} {{ member.endyear }}. {{ member.thesisTitle }}
  </li>
{% endfor %}

<hr>
{% endcomment %}

<h3>Former Undergraduate Students</h3>
{% for member in site.categories['former_member_undergrad'] %}
  <div class="col-lg-3 col-md-3 col-sm-3">
    <div class="member-info">
      <div class="image-container square-image">
        <img src="{{ site.baseurl }}/assets/img/{{ member.img }}" alt="{{ member.name }}">
      </div>
      <div class="text-container">
        <h4><a href="{{  member.url | prepend: site.baseurl }}">{{ member.name }}</a></h4>
        <!-- Add other text content here -->
        <p style="line-height: 1.0;">{{ member.program }}, {{ member.term }} {{ member.year }}</p>
      </div>
    </div>
  </div><!-- /col-lg-3 -->
{% endfor %}


<hr>

<h3>Fun Photos</h3> 
<div id="imageSlider" class="slider">
    {% for image in site.static_files %}
        {% if image.path contains 'assets/img/slider' %}
            <img src="{{ site.baseurl }}/assets/img/group" alt="{{ image.name }}" {% if forloop.first %}style="display: block;"{% endif %}>
        {% endif %}
    {% endfor %}
</div>
