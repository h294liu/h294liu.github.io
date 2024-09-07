---
layout: page
title: Gallery
permalink: /gallery/
main_nav: true
fun_photos:
  - image: "2024-06-05_minh_at_bow.jpg"
    description: "Minh, our computer science student, visited his study area Bow at Banff on June 5, 2024."
  - image: "2024_04_18_marian_3MT2.jpg"
    description: "Marian won prizes at the 3MT Research Symposium on April 18, 2024."
  - image: "2024_04_18_marian_3MT1.jpg"
    description: "Marian presented at the 3MT Research Symposium on April 18, 2024."
  - image: "2024_04_11_quang_dra1.jpg"
    description: "Quang presented at the DRA Poster Presentation and Competition on April 11, 2024."
  - image: "2024_04_11_quang_dra2.jpg"
    description: "We were at the DRA event."
  - image: "2024_02_21_marian_ISTF.jpg"
    description: "Marian represented Peru at the International Swiss Talent Forum in February 2024."
  - image: "2023-12-22_first_group_meeting.png"
    description: "Our first group meeting on December 22, 2023."
  - image: "2023_12_11_hannah_dra.jpg"
    description: "Hannah presented at the DRA Poster Presentation and Competition on December 11, 2023."
  - image: "2023_12_11_umalsha_dra.jpg"
    description: "Umalsha presented at the DRA Poster Presentation and Competition on December 11, 2023."
  - image: "2023_04_10_hongli_reddeer.jpg"
    description: "Hongli measured water levels in Red Deer on April 10, 2023."
  - image: "2023_04_02_hongli_reddeer.jpg"
    description: "Hongli installed device on April 2, 2023. Race against ice melting!"
---

<div id="funPhotoGallery" style="max-width: 1300px; margin: 0 auto; position: relative;">
  <button id="prevFunPhoto" style="position: absolute; left: 0; top: 50%; transform: translateY(-50%);">&#10094;</button>
  <div style="text-align: center;">
    <img id="currentFunPhoto" src="" alt="Fun Photo" style="max-width: 100%; max-height: 600px; width: auto; height: auto; display: inline-block;">
    <!-- Line under the photo -->
<!--     <hr style="border: none; border-top: 2px solid black; margin: 10px 0; width: 90%;"> -->
    <!-- Description under the line -->
    <div id="photoDescription" style="color: black; font-size: 16px;">
      <!-- Description will be inserted here -->
    </div>
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
