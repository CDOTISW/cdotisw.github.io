*Demo*

## Embedding HTML to improve our product and help us tell stories more effectively

### Overview
**Proposal:** HTML file hosting on ISW website.  

**Purpose/goals:** Be able to use HTML files in research publications to enhance the range of graphics we produce.   

**[Use cases:](#UseCases)** Interactive graphics e.g. charts, maps, network analysis, and interactive imagery comparison sliders embedded directly in the website without having to open new tabs.  

**Frequency of use:** Monthly at minimum for China team to host our monthly counts on events such as ADIZ incursions. Likely to have major projects at least once every few months that would greatly benefit from interactivity. Geoint would likely use an html embed on a weekly basis. 

**[Licensing details for Software:](#Licensing)** China team: R and RStudio are free open-source programs under the GNU General Public License. Full details at the end. 

### What are HTML files good for? 

The entire internet is run on the back of HTML, which is just a coding language designed to be displayed in a web browser. HTML files are **small** and enable researchers to create interactive graphics to enhance the reader’s understanding of complex topics.  

### Drawbacks of relying solely on static graphics (the status quo): 

<p style="text-align: center"><img src="/assets/photos/Picture1_graph.png" width="600"></p>

- Difficult to add details without making the image too dense.

<p style="text-align: center"><img src="/assets/photos/Picture2_graph.png" width="600"></p>

- Limited space, especially as graphs get more datapoints.
<br>

<p style="text-align: center"><img src="/assets/photos/TehranReservoirsGIF.gif" width="500"></p>

- GIFs are valuable for posting on social media, but clunky and frustrating in an article in a website.  

<p style="text-align: center"><img src="/assets/photos/Picture4_strikegraph.png" width="600"></p>

- So many columns! Wouldn’t it be nice to be able to interact with each one? 

<p style="text-align: center"><img src="/assets/photos/Picture5_spratly.png" width="600"></p>

- Not very helpful to readers to just get the names of obscure outposts in the South China Sea with no historical context. Could move a lot of routine background info from written updates into clickable pop-ups in the map.   

### <a id="UseCases"></a>How do HTML files add extra functionality? 

Create interactive elements that allow researchers to display more information as the user moves their mouse. 

### Graphs:
This is an interactive scatter plot on Taiwanese legislators undergoing recall elections, where each point is labelled with name and district. This example highlights the following benefits:  

<iframe src="/assets/photos/legislativerecallscatter2d.html" width="750" height="500" style="border:0;" title="Legislative Recall Scatter Plot"></iframe>

This is an interactive scatter plot on Taiwanese legislators undergoing recall elections, where each point is labelled with name and district. This example highlights the following benefits:  

- Context: Readers who want to find particular districts/legislators don’t have to dig through electoral data themselves to further investigate the info presented in this chart.  

- Numerical labels: Hover text eliminates the need to compromise on numerical accuracy to avoid cluttering the graph. It’s a cleaner look. 

- Reader engagement: Likely will also enhance user interaction and improve information retention. Readers are likely to spend more time playing with the data in an interactive graph compared to a static image.  

- Transformative analysis: We are able to present data in a more meaningful way through these methods, which enhances the depth of analysis readers take away from our work. This can improve ISW’s reputation and value.  

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



Contrast the interactive version with this static version. 

The population is heavily concentrated along the coast so it is very difficult to represent. The icons for legislative seats either overlap or must be set to a really small size. The map below shows the maximum dot size possible to represent each legislative seat, and the color coding is indiscernible at that size. 

China team is also planning to create an interactive network where readers can explore connections between purged members of the People’s Liberation Army and understand how they are connected in the command-structure.  

This type of product is simply impossible to meaningfully condense into a static form. This is a forthcoming research product that will be used for internal reference at minimum, but it would be a shame if we couldn’t publish it due to website constraints.

Sample method to create network charts: [https://r-graph-gallery.com/network-interactive.html](https://r-graph-gallery.com/network-interactive.html)

## Implementing HTML Logistics: 

This is a reference website on the feature this proposal seeks permission to use: [Custon HTML block - Wordpress.com Support](https://wordpress.com/support/wordpress-editor/blocks/custom-html-block/)

### Steps to use the Custom HTML block: 
1. Upload the HTML file into some online hosting software. 
  - China team has successfully used GitHub, which is a free platform that hosts open source projects. GitHub has unlimited storage for public repos. A potential drawback to consider is that the HTML code we host on GitHub and our account history is available to the public. All of the data and coding methods we use is open-source anyways, so the only concern here is from an organizational standpoint on allowing the public to access code from ISW researchers.  

2. Use the HTML code block feature in WordPress to embed it into the website.  
  - Karina has successfully used the code block on the AEI website and it takes about a minute to embed after one is familiar with how to do it.  
    - Embed code: 
    ```
<iframe class="mobile-hide" src="URL GOES HERE" width="100%" height="776"></iframe> 
  ```

  - It takes approximately 5 minutes to walk someone new through the process, and Karina is generally available to troubleshoot if there are tech difficulties.  

Note: Complex projects such as the interactive map (2000 lines of code) are too much for the WordPress built-in HTML code editor to handle. It crashes the website. This is why we need GitHub – need to get an external site to host the code so the ISW site simply calls on the URL.  

Karina created an interactive map integrated with the China Team update in the way described above via the AEI WordPress account to demonstrate what she hopes to do on ISW’s website: [China-Taiwan Weekly Update, July 24, 2025 | American Enterprise Institute - AEI](https://www.aei.org/articles/china-taiwan-weekly-update-july-24-2025/)

## Unique advantages afforded through the GitHub/WordPress method: 
1. Quick and easy to train ER staff to use. The researcher will handle the HTML file hosting, so ER would only need to plug in the URL from the researcher into the code block provided above. 
2. Free and no new installations. GitHub is free and we already have the WordPress HTML code editor feature on our new site. 
3. Displays interactive features without having to open a new tab. This is unlike our current ArcGIS maps. Otherwise, most readers probably aren’t going to bother clicking. 
4. Low website resource usage. HTML files aren’t particularly complicated and they load quickly. **It’s faster than booting up the ArcGIS interactive maps.**

### Proposed usage frequency: 
- Monthly at minimum for China team ADIZ incursion updates. Karina plans to convert this graph into an interactive style that displays more nicely. This would also open the door to more creative visualizations as we are currently severely constrained by our website capabilities. Taiwanese legislative recalls are still ongoing and there may be further room for analysis with interactive maps. China team is also looking to publish an interactive network of purged PLA officials in the coming months.  
- GEOINT would use these features monthly at a minimum, and would mostly use it to supplement less-frequent publications like the occupation update, as opposed to the daily Russian update. As more staff are trained and more ideas are developed, the frequency could increase. 

## Next Steps: 
- Gain approval to host HTML code on the new ISW site.  
- Gain approval to continue using GitHub to host HTML code.  
- Gain permission to test how much HTML code the ISW website can handle before crashing.  
- Upgrade existing routine graphics to take advantage of interactive capabilities.  
- Begin brainstorming new graphics and train staff or interns on these newfound capabilities. 

### Licensing details: 
R and Rstudio (used by Karina): 

_This software is distributed under the terms of the GNU General Public License, either Version 2, June 1991 or Version 3, June 2007._ 
_The terms of version 2 of the license are in a file called COPYING which you should have received with_
_this software and which can be displayed by RShowDoc("COPYING"). Version 3 of the license can be displayed by RShowDoc("GPL-3")._

_Copies of both versions 2 and 3 of the license can be found at https://www.R-project.org/Licenses/._

*A small number of files (the API header files listed in R_DOC_DIR/COPYRIGHTS) are distributed under the*
_LESSER GNU GENERAL PUBLIC LICENSE, version 2.1 or later. This can be displayed by RShowDoc("LGPL-2.1"),_
_or obtained at the URI given._ 
_Version 3 of the license can be displayed by RShowDoc("LGPL-3")._

_'Share and Enjoy.'_