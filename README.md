# Lab6Java
// STEP 1: Initialize and declare variables
var mainImage = document.querySelector('.displayed-img');
var thumbnailBar = document.querySelector('.thumb-bar');

// STEP 2: Loop 5 times to create the <img> elements
for (var i = 1; i < 6; i++) {
  var newThumbnail = document.createElement('img');
  newThumbnail.setAttribute('src', 'images/pic' + i + '.jpg');
  thumbnailBar.appendChild(newThumbnail);

  // STEP 3: Build event handler for each <img>
  newThumbnail.onclick = function(event) {
    var thumbnailSrc = event.target.getAttribute('src');
    displayMainImage(thumbnailSrc);
  }
}

// STEP 4: Function to change the src of the main <img>
function displayMainImage(value) {
  mainImage.setAttribute('src', value);
}

// STEP 5: Event Delegation
thumbnailBar.onclick = function(event) {
  // event.target is the element that was clicked
  if (event.target && event.target.nodeName === 'IMG') {
    var thumbnailSrc = event.target.getAttribute('src');
    displayMainImage(thumbnailSrc);

    // Lab 6 STEP A: Change the event.target CSS outline property to "5px solid red"
    event.target.style.outline = "5px solid red";

    // Lab 6 STEP B: Change the event.target CSS position property to "relative"
    event.target.style.position = "relative";

    // Lab 6 STEP C: Set the CSS z-index property to "10" so that the thumbnail clicked is on top of all the others
    event.target.style.zIndex = "10";

    // Lab 6 STEP G: Call the clearThumbnails() function
    clearThumbnails();
  }
};

// Lab 6 STEP D: Initialize and declare a var called 'thumbnails' using the querySelectorAll method to grab all the IMG elements inside the .thumb-bar
var thumbnails = document.querySelectorAll('.thumb-bar img');

// Lab 6 STEP E: Build a function called 'clearThumbnails()' that loops through the thumbnails array with a FOR loop
function clearThumbnails() {
  for (var i = 0; i < thumbnails.length; i++) {
    // Lab 6 STEP F: Inside the clearThumbnails function, for each thumbnail IMG element, set the CSS outline-width property to "0" and the z-index property also to "0"
    thumbnails[i].style.outlineWidth = "0";
    thumbnails[i].style.zIndex = "0";
  }
}
