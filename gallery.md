---
layout: page
title: Gallery
permalink: /gallery/
main_nav: true
fun_photos:
  - image: "2025-12-15_chang_AGU.jpg"
    description: "Chang presented her research at AGU 2025 (Dec 15)"
  - image: "2025-12-15_jian_AGU1.JPG"
    description: "Jian presented her research at AGU 2025 (Dec 15)"
  - image: "2025-12-15_jian_AGU2.JPG"
    description: "Jian presented her research at AGU 2025 (Dec 15)"
  - image: "2025-12-15_jian_chang_AGU.JPG"
    description: "Our team at AGU 2025 (Dec 15–19)"
  - image: "2025-06-18_chang_IWP.jpg"
    description: "Chang presented at IWA YWP Canada (Jun 18, 2025)"
  - image: "2025-06-18_jian_IWP.jpg"
    description: "Jian presented at IWA YWP Canada (Jun 18, 2025)"
  - image: "2025_04_10_ariana_dra.jpg"
    description: "Ariana received the Outstanding Research Performance Award — again! (Winter 2025)"
  - image: "2025_04_10_shahib_dra.jpg"
    description: "Shahib presented his research at the DRA event (Winter 2025)"
  - image: "2024_12_09_group_dra.jpg"
    description: "DRA Poster Presentation and Competition (Dec 9, 2024)"
  - image: "2024_12_09_ariana_dra1.jpg"
    description: "Ariana presenting her research at the DRA event (Fall 2024)"
  - image: "2024_12_09_ariana_dra2.jpg"
    description: "Ariana presenting her research at the DRA event (Fall 2024)"
  - image: "2024_12_09_ariana_dra3.jpg"
    description: "Ariana received the Outstanding Research Performance Award (Fall 2024)"
  - image: "2024_12_09_shahib_dra1.jpg"
    description: "Shahib presenting his research at the DRA event (Fall 2024)"
  - image: "2024_12_09_shahib_dra2.jpg"
    description: "Shahib presenting his research at the DRA event (Fall 2024)"
  - image: "2024_12_09_zhihong_dra1.jpg"
    description: "Zhihong presenting his research at the DRA event (Fall 2024)"
  - image: "2024_12_09_zhihong_dra2.jpg"
    description: "Zhihong presenting his research at the DRA event (Fall 2024)"
  - image: "2024_11_17_chang_geo827_1.jpg"
    description: "Chang attended the Principles of Hydrology course at the University of Saskatchewan (Oct 30 – Nov 12, 2024)"
  - image: "2024_11_17_chang_geo827_2.png"
    description: "Field excursion in the Kananaskis Valley during the Principles of Hydrology course"
  - image: "2024_11_17_chang_geo827_3.png"
    description: "Field excursion in the Kananaskis Valley during the Principles of Hydrology course"
  - image: "2024_10_31water_sustainability_summit_1.jpg"
    description: "Jian and Hongli attended the 2024 Water Sustainability Summit hosted by the University of Calgary (Lake Louise, Oct 30 – Nov 1, 2024)"
  - image: "2024_10_31water_sustainability_summit_2.jpg"
    description: "Field excursion in the Bow Valley during the 2024 Water Sustainability Summit"
  - image: "2024_07_18_alberta_water_summit.jpg"
    description: "Hongli attended the 2024 Alberta Water Summit hosted by the University of Calgary (Banff, Jul 18–19, 2024)"
  - image: "2024_05_11_marian_certificate.jpg"
    description: "Marian received the certificate for the Emerging Leaders in the Americas Program (ELAP) (May 11, 2024)"  
  - image: "2024_04_18_marian_3MT2.jpg"
    description: "Marian won prizes at the 3MT Research Symposium (Apr 18, 2024)"
  - image: "2024_04_18_marian_3MT1.jpg"
    description: "Marian presented her research at the 3MT Research Symposium (Apr 18, 2024)"
  - image: "2024_04_11_quang_dra2.jpg"
    description: "DRA Poster Presentation and Competition (Apr 11, 2024)"
  - image: "2024_04_11_quang_dra1.jpg"
    description: "Quang presenting his research at the DRA event (Winter 2024)"
  - image: "2024_02_21_marian_ISTF.jpg"
    description: "Marian represented Peru at the International Swiss Talent Forum (Feb 2024)"
  - image: "2023-12-22_first_group_meeting.png"
    description: "Our first group meeting (Dec 22, 2023)"
  - image: "2023_12_11_hannah_dra.jpg"
    description: "Hannah presented at the DRA event (Dec 11, 2023)"
  - image: "2023_12_11_umalsha_dra.jpg"
    description: "Umalsha presenting her research at the DRA event (Dec 11, 2023)"
  - image: "2023_04_10_hongli_reddeer.jpg"
    description: "Hongli conducting water-level measurements in Red Deer (Apr 10, 2023)"
  - image: "2023_04_02_hongli_reddeer.jpg"
    description: "Hongli installing monitoring equipment in Red Deer during spring melt conditions (Apr 2, 2023)"
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
  const autoSwitchInterval = 10000; // Auto switch interval in milliseconds
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
