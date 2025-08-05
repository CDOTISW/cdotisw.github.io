Interactive Demo

## How can embedded HTML improve our product and tell stories more effectively?

### 1. Interactive Imagery Sliders

Instead of relying on GIFs to compare before/after imagery, we can embed a small bit of HTML
that allows readers to investigate at their own pace. This requires the image files to be stored
somewhere, and a small HTML script that calls the images and displays them interactively.
(these images are stored in imgur, which we might not want to always do. 
Maybe our website has a way to upload assets that can be called by embedded HTML?)

  <style>
    body {
      font-family: sans-serif;
      background: #f0f0f0;
    }

    .container {
      position: relative;
      width: 600px;
      height: 450px;
      margin: 40px auto;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
      border-radius: 0px;
      overflow: hidden;
    }

    .container img {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .overlay-slider {
      position: absolute;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      width: 60%;
    /*  background: rgba(255, 255, 255, 0.368); */
      padding: 10px;
      border-radius: 10px;
      text-align: center;
    }

    .overlay-slider input[type="range"] {
      width: 100%;
    }

    .overlay-slider label {
      font-size: 14px;
      display: block;
      margin-bottom: 5px;
      color: #333;
    }

        /* Style for WebKit browsers (Chrome, Safari, Edge) */
    input[type="range"] {
    -webkit-appearance: none;
    appearance: none;
    height: 6px;
    background: #ccc;
    border-radius: 3px;
    outline: none;
    cursor: pointer;
    }

    /* Track */
    input[type="range"]::-webkit-slider-runnable-track {
    height: 6px;
    background: rgba(184, 184, 184, 0.5); /* semi-transparent gray */
    border-radius: 3px;
    }

    /* Thumb */
    input[type="range"]::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 16px;
    height: 16px;
    background: #d6d6d6; /* change this to the thumb color */
    border-radius: 50%;
    cursor: pointer;
    border: none;
    margin-top: -5px; /* Aligns thumb with track */
    }

  </style>

  <div class="container">
    <img src="https://imgur.com/RfszeE9.jpeg" alt="Bottom Image">
    <img id="topImage" src="https://imgur.com/RqvGALd.jpeg" alt="Top Image" style="opacity: 1;">
    <div class="overlay-slider">
  <!--    <label for="opacitySlider">Adjust Top Image Opacity</label> -->
      <input type="range" id="opacitySlider" min="0" max="100" value="50">
    </div>
  </div>

  <script>
    const slider = document.getElementById('opacitySlider');
    const topImage = document.getElementById('topImage');

    slider.addEventListener('input', function () {
      const opacityValue = slider.value / 100;
      topImage.style.opacity = opacityValue;
    });
  </script>

### 2. ArcGIS Interactive Maps

Karina has shown how maps made with other software, like R, can be embedded using html.
But Arcgis Maps, which the GEOINT team uses every single day,
are actually best displayed embedded in website using HTML (an embed code)! 
Previously, to publish a map we were constrained to either static maps or interactive maps, which are run
through an arcgis storymap page. Our most popular are probably the [Ukraine Interactive map](https://storymaps.arcgis.com/stories/36a7f6a6f5a9448496de641cf64bd375)
and [Syria interactive map](https://storymaps.arcgis.com/stories/1933cb1d315f4db3a4f4dcc5ef40753a).
In these pages, you will notice the URL is actually an ESRI website, which means the reader is now stuck outside our site.

Instead of using these Arcgis pages, we should embed these maps directly in our website, keeping traffic on our page
and enhance written work with interactive maps right there as a part of the story, not as a link to a separate page.

**For example,** we have included maps showing dollars spent by oblast as a part of the [force generation update.](https://www.understandingwar.org/backgrounder/russian-force-generation-and-technological-adaptations-update-may-7-2025)

<img src="/assets/photos/force_gen_example.png" alt="Force Generation Example" style="max-width:80%; margin: 20px 0;">

Instead, we could embed an interactive map below the body text, like so: (pan and click around!)
<!-- Add script to the <head> of your page to load the embeddable map component -->
<script type="module" src="https://js.arcgis.com/embeddable-components/4.33/arcgis-embeddable-components.esm.js"></script>
<!-- Add custom element to <body> of your page -->
<arcgis-embedded-map
  style="height:600px;width:900px;"
  item-id="fd6b18ab569a420b9b4d0143a50bd818"
  theme="light"
  legend-enabled
  center="91.65618642692036,65.19628797771574"
  scale="32601084.83770047"
  portal-url="https://understandingwar.maps.arcgis.com">
</arcgis-embedded-map>

The same could be done in place of the maps showing locations of childrens camps
in [Lina's occupation update](https://www.understandingwar.org/backgrounder/russian-occupation-update-may-15-2025)
as well.  


<img src="/assets/photos/occ_example.png" alt="Occupation UPdate Example" style="max-width:80%; margin: 20px 0;">
