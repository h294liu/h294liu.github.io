---
layout: page
title: TEAM
permalink: /team/
main_nav: true
fun_photos: 
  - image: "2023-12-22FirstGroupMeeting.png"
    description: "First Group Meeting in December 2023"
  - image: "dra_2023_hannah.jpg"
    description: "Hannah's Presentation at DRA 2023"
  - image: "dra_2023_umalsha.jpg"
    description: "Umalsha's Presentation at DRA 2023"
---

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
<div id="funPhotoGallery" style="max-width: 600px; margin: 0 auto; position: relative;">
  <img id="currentFunPhoto" src="" alt="Fun Photo" style="max-width: 600px; height: auto; display: block; margin: 0 auto;">
  <div id="photoDescription" style="position: absolute; bottom: 8px; left: 30px; background-color: rgba(0, 0, 0, 0.3); color: white; padding: 4px; width: calc(100% - 60px); box-sizing: border-box; font-size: 14px;">
    <!-- Description will be inserted here -->
  </div>
</div>
<div class="button-container" style="text-align: center;">
  <button id="prevFunPhoto">Previous</button>
  <button id="nextFunPhoto">Next</button>
</div>


<script>
document.addEventListener('DOMContentLoaded', function () {
  const galleryItems = [
    {% for item in page.fun_photos %}
      { src: "{{ site.baseurl }}/assets/gallery/{{ item.image }}", description: "{{ item.description | escape }}" },
    {% endfor %}
  ];
  let currentIndex = 0;

  function updateGalleryItem(index) {
    const photoElement = document.getElementById('currentFunPhoto');
    const descriptionElement = document.getElementById('photoDescription');
    photoElement.src = galleryItems[index].src;
    photoElement.alt = galleryItems[index].description; // Update alt text for accessibility
    descriptionElement.innerHTML = galleryItems[index].description; // Update the description
  }

  // Initialize with the first item
  updateGalleryItem(currentIndex);

  document.getElementById('prevFunPhoto').addEventListener('click', function() {
    currentIndex = (currentIndex - 1 + galleryItems.length) % galleryItems.length;
    updateGalleryItem(currentIndex);
  });

  document.getElementById('nextFunPhoto').addEventListener('click', function() {
    currentIndex = (currentIndex + 1) % galleryItems.length;
    updateGalleryItem(currentIndex);

  // Optional: If you expect the window to resize and want to maintain the alignment
  window.addEventListener('resize', updateDescriptionWidth);

  });
});
</script>
