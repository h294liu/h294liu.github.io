---
layout: page
title: team
permalink: /team/
main_nav: true
fun_photos:
  - image: "2024_04_18_marian_3MT2.jpg"
    description: "Marian won prizes at the 3MT Research Symposium on April 18, 2024."
  - image: "2024_04_18_marian_3MT1.jpg"
    description: "Marian presented at the 3MT Research Symposium on April 18, 2024."
  - image: "2024_04_11_quang_dra1.jpg"
    description: "Quang presented at the DRA Poster Presentation and Competition on April 11, 2024."
  - image: "2024_04_11_quang_dra2.jpg"
    description: "We are so proud of you!"
  - image: "2024_02_21_marian_ISTF.jpg"
    description: "Marian represented Peru at the International Swiss Talent Forum in February 2024."
  - image: "2023-12-22_first_group_meeting.png"
    description: "Our first group meeting on December 22, 2023."
  - image: "2023_12_11_hannah_dra.jpg"
    description: "Hannah presented at the DRA Poster Presentation and Competition on December 11, 2023."
  - image: "2023_12_11_umalsha_dra.jpg"
    description: "Umalsha presented at the DRA Poster Presentation and Competition on December 11, 2023."
  - image: "2023_04_10_hongli_reddeer.jpg"
    description: "Measured water levels in Red Deer on April 10, 2023."
  - image: "2023_04_02_hongli_reddeer.jpg"
    description: "Installed the device on April 2, 2023. Race against ice melting!"
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
        <p style="line-height: 1.0;">{{ member.position }}</p>
      </div>
    </div>
  </div>
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
<div id="funPhotoGallery" style="max-width: 1000px; margin: 0 auto; position: relative;">
  <button id="prevFunPhoto" style="position: absolute; left: 0; top: 50%; transform: translateY(-50%);">&#10094;</button>
  <img id="currentFunPhoto" src="" alt="Fun Photo" style="max-width: 1000px; height: auto; display: block; margin: 0 auto;">
  <div id="photoDescription" style="position: absolute; bottom: 8px; left: 5%; background-color: rgba(0, 0, 0, 0.3); color: white; padding: 4px; width: calc(100% - 10%); box-sizing: border-box; font-size: 14px;">
    <!-- Description will be inserted here -->
  </div>
  <button id="nextFunPhoto" style="position: absolute; right: 0; top: 50%; transform: translateY(-50%);">&#10095;</button>
</div>

<script>
document.addEventListener('DOMContentLoaded', function () {
  const galleryItems = [
    {% for item in page.fun_photos %}
      { src: "{{ site.baseurl }}/assets/gallery/{{ item.image }}", description: "{{ item.description | escape }}" },
    {% endfor %}
  ];
  let currentIndex = 0;
  const autoSwitchInterval = 5000; // Auto switch interval in milliseconds
  let autoSwitchTimer; // Timer for auto switching

  function updateGalleryItem(index) {
    const photoElement = document.getElementById('currentFunPhoto');
    const descriptionElement = document.getElementById('photoDescription');
    photoElement.src = galleryItems[index].src;
    photoElement.alt = galleryItems[index].description; // Update alt text for accessibility
    descriptionElement.innerHTML = galleryItems[index].description; // Update the description
  }

  // Function to switch to the next photo
  function nextPhoto() {
    currentIndex = (currentIndex + 1) % galleryItems.length;
    updateGalleryItem(currentIndex);
  }

  // Function to switch to the previous photo
  function prevPhoto() {
    currentIndex = (currentIndex - 1 + galleryItems.length) % galleryItems.length;
    updateGalleryItem(currentIndex);
  }

  // Initialize with the first item
  updateGalleryItem(currentIndex);

  // Event listener for next button click
  document.getElementById('nextFunPhoto').addEventListener('click', function() {
    clearInterval(autoSwitchTimer); // Pause auto-switching
    nextPhoto();
    autoSwitchTimer = setInterval(nextPhoto, autoSwitchInterval); // Resume auto-switching
  });

  // Event listener for previous button click
  document.getElementById('prevFunPhoto').addEventListener('click', function() {
    clearInterval(autoSwitchTimer); // Pause auto-switching
    prevPhoto();
    autoSwitchTimer = setInterval(nextPhoto, autoSwitchInterval); // Resume auto-switching
  });

  // Automatic switching of photos
  autoSwitchTimer = setInterval(nextPhoto, autoSwitchInterval);

  // Event listener to pause auto-switching when mouse enters the image area
  document.getElementById('currentFunPhoto').addEventListener('mouseenter', function() {
    clearInterval(autoSwitchTimer); // Pause auto-switching
  });

  // Event listener to resume auto-switching when mouse leaves the image area
  document.getElementById('currentFunPhoto').addEventListener('mouseleave', function() {
    autoSwitchTimer = setInterval(nextPhoto, autoSwitchInterval); // Resume auto-switching
  });
});
</script>

