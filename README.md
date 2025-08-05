*Demo*

## Embedding HTML to improve our product and help us tell stories more effectively

### Overview
**Proposal:** HTML file hosting on ISW website.  

**Purpose/goals:** Be able to use HTML files in research publications to enhance the range of graphics we produce.   

**Use cases:** Interactive graphics e.g. charts, maps, network analysis, and interactive imagery comparison sliders embedded directly in the website without having to open new tabs.  

**Frequency of use:** Monthly at minimum for China team to host our monthly counts on events such as ADIZ incursions. Likely to have major projects at least once every few months that would greatly benefit from interactivity. Geoint would likely use an html embed on a weekly basis. 

**Licensing details for Software:** China team: R and RStudio are free open-source programs under the GNU General Public License. Full details at the end. 

### What are HTML files good for? 

The entire internet is run on the back of HTML, which is just a coding language designed to be displayed in a web browser. HTML files are **small** and enable researchers to create interactive graphics to enhance the reader’s understanding of complex topics.  

### Drawbacks of relying solely on static graphics (the status quo): 

Difficult to add details without making the image too dense.

<p style="text-align: center"><img src="/assets/photos/Picture1_graph.png" width="500"></p>

Limited space, especially as graphs get more datapoints.

<p style="text-align: center"><img src="/assets/photos/Picture2_graph.png" width="500"></p>

<br>

<p style="text-align: center"><img src="/assets/photos/TehranReservoirsGIF.gif" width="700"></p>

GIFs are valuable for posting on social media, but clunky and frustrating in an article in a website.  

<p style="text-align: center"><img src="/assets/photos/Picture4_strikegraph.png" width="500"></p>

So many columns! Wouldn’t it be nice to be able to interact with each one? 

<p style="text-align: center"><img src="/assets/photos/Picture5_spratly.png" width="500"></p>

Not very helpful to readers to just get the names of obscure outposts in the South China Sea with no historical context. Could move a lot of routine background info from written updates into clickable pop-ups in the map.   

### How do HTML files add extra functionality? 

Creates interactive elements that allow researchers to display more information as the user moves their mouse. 

### Graphs:
This is an interactive scatter plot on Taiwanese legislators undergoing recall elections, where each point is labelled with name and district. This example highlights the following benefits:  

<iframe src="/assets/photos/legislativerecallscatter2d.html" width="750" height="500" style="border:0;" title="Legislative Recall Scatter Plot"></iframe>

This is an interactive scatter plot on Taiwanese legislators undergoing recall elections, where each point is labelled with name and district. This example highlights the following benefits:  

1. Context: Readers who want to find particular districts/legislators don’t have to dig through electoral data themselves to further investigate the info presented in this chart.  

2. Numerical labels: Hover text eliminates the need to compromise on numerical accuracy to avoid cluttering the graph. It’s a cleaner look. 

3. Reader engagement: Likely will also enhance user interaction and improve information retention. Readers are likely to spend more time playing with the data in an interactive graph compared to a static image.  

4. Transformative analysis: We are able to present data in a more meaningful way through these methods, which enhances the depth of analysis readers take away from our work. This can improve ISW’s reputation and value.  

There are dozens of interactive graph options available that more effectively condense information compared to default options in Microsoft Excel. See more here: [https://r-graph-gallery.com/interactive-charts.html](https://r-graph-gallery.com/interactive-charts.html) 

### Interactive Image Sliders 

Instead of relying on GIFs to compare before/after imagery, we can embed a small bit of HTML
that allows readers to investigate at their own pace. This uses a small HTML script that displays these two images interactively.
(*These images are stored in imgur, which we might want a better solution for. They have to be stored somewhere, but
maybe our website has a way to upload assets that can be called by embedded HTML?*)

  <style> <!-- Imagery Slider-->
    body {
      font-family: sans-serif;
      background: #f0f0f0;
    }

    .container {
      position: relative;
      width: 600px;
      height: 450px;
      margin: 10px auto;
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
      <input type="range" id="opacitySlider" min="0" max="100" value="0">
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
<p style="text-align:center;">Drag the slider to compare imagery of Fordow</p>

### ArcGIS Interactive Maps

Arcgis Maps, which the GEOINT team uses every single day,
are actually best displayed embedded in website using HTML! 
Previously, if we wanted to include a map we were constrained to either static maps or linking to an interactive map run through an arcgis storymap page. 
Our most popular two are the [Ukraine Interactive map](https://storymaps.arcgis.com/stories/36a7f6a6f5a9448496de641cf64bd375)
and [Syria interactive map](https://storymaps.arcgis.com/stories/1933cb1d315f4db3a4f4dcc5ef40753a).
At these links, you will notice the URL is actually an ESRI website, which means the reader is now stuck outside our site.

Instead of using these Arcgis pages we can embed these maps directly in our website, keeping traffic on our page
and enhancing written work with interactive maps right there as a part of the story, not as a link to a separate page.

**For example,** we have included maps showing dollars spent by oblast as a part of the [force generation update.](https://www.understandingwar.org/backgrounder/russian-force-generation-and-technological-adaptations-update-may-7-2025)

<p style="text-align: center"><img src="/assets/photos/force_gen_example.png" width="400"></p>

Instead, we could embed an interactive map below the body text, like so. You can pan and click around!

<div style="max-width:900px; margin: 0 auto;">
  <iframe
    src="https://experience.arcgis.com/experience/758ed391e2c14c00b8e17349beade503"
    width="900"
    height="450"
    style="border:0; width:100%; max-width:900px;"
    allowfullscreen
    loading="lazy"
    title="ArcGIS Interactive Map">
  </iframe>
</div>

<br>
Or like this! This loads faster but doesn't interact with the pop-ups as well as the previous map.
<br>

<!-- Add script to the <head> of your page to load the embeddable map component -->
<script type="module" src="https://js.arcgis.com/embeddable-components/4.33/arcgis-embeddable-components.esm.js"></script>
<!-- Add custom element to <body> of your page -->
<div style="text-align: center;">
  <arcgis-embedded-map
    style="height:450px;width:750px;"
    item-id="fd6b18ab569a420b9b4d0143a50bd818"
    theme="light"
    legend-enabled
    center="91.65618642692036,65.19628797771574"
    scale="33001084.83770047"
    portal-url="https://understandingwar.maps.arcgis.com">
  </arcgis-embedded-map>
</div>
<br>

Beyond Arcgis, interactive graphics can also be constructed in R.

<iframe src="/assets/photos/interactive_map12.html" width="750" height="500" style="border:0;" title="Interactive Map"></iframe>

Taiwanese legislative recalls could have potentially had geographic patterns, so mapping out the datapoints and color-coding them is valuable. Taiwan’s population distribution makes it extremely difficult to construct a visually pleasing and informative static map.

