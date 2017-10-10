# GL mapping tips and tricks

<h2 style="text-align: center"> &#128506;&#127912;&#10024;</h2>
 
---

# Molly Lloyd

- &#128035; [@mollymerp](twitter.com/mollymerp) 
- &#128126; github.com/mollymerp
- &#128105;&#8205;&#128187; [Mapbox GL](mapbox.com/maps)

---

# Whats new?

- heatmaps 
- client-side hillshading
- expressions
- bonus: map projection hacking

---

#  heatmaps

<h2 style="text-align: center;">&#128293; &#127878; &#128293;</h2>

---

<video src="heatmap.mov" controls width="100%"></video> 

--- 

# heatmaps

- large point datasets 
- [bivariate kernel density estimation](https://en.wikipedia.org/wiki/Multivariate_kernel_density_estimation)
- &#9889;&#65039; speedy GPU calculation
- data-driven intensity `heatmap-weight`

---
<pre>
<code>
  map.addLayer({
      id: 'starbucks',
      type: 'heatmap',
      source: {
          type: 'geojson',
          data: 'starbucks.geojson'
      },
      paint: {
          'heatmap-color': {
              stops: [

                  [0, 'rgba(27, 30, 137, 0)'],
                  [0.5, "rgba(186, 58, 134, .5)"],
                  [1, "rgb(244, 233, 65)"]
              ]
          },
          'heatmap-radius': {
            stops: [
              [0, 5],
              [10, 20]
            ]
          },
          'heatmap-intensity': {
            stops: [
              [0, 0.15],
              [13, 1]
            ]
          }
      }
  }, 'airport-label');  

</code>
</pre>

---
# raster DEM hillshade

<h2 style="text-align: center;">&#9968;&#65039;</h2>

---

Mapbox's raster DEM terrain-rgb 

---

&#10024;&#128073;&#127956;&#65039;

---

client-side hillshade in mapbox-gl-js

---

# expressions

<h2 style="text-align: center;"> &#128290;&#128105;&#8205;&#128300;&#128200; </h2>

---

# expressions: what?

---

<h1> &#128477;&#65039; </h1>

- multiple feature properties
- arithmetic &#10133;&#10134;&#10135;&#10006;&#65039;
- string manipulation 
- conditional logic
- backwards compatible &#128517;
---

# expressions: why?

---

- &#10024; data-driven styling 2.0 &#10024;
- full data access and styling control
- ergonomic for styling and labeling

---

# expressions: how?

---
# conditional logic + multiple properties

<pre>
  <code>
    "text-field": [
      //conditional expression type
      "case",
      //if
      ["has", "name_zh"],
      //then
      ["concat", ["get", "name_zh"], "\n", ["get", "name"]],
      //get name
      ["get", "name"]
    ];
  </code>
</pre>

---

# arithmetic

<pre>
  <code>
    "circle-radius": [
      // exponent expression type
      "^",
      // divide population by 10,000
      ["/", ["get", "population"], 10000],
      // take the square root
      0.5
    ]
  </code>
</pre>

---

expressions: when?

---

- &#128421;&#65039; JS: this month
- &#128241; iOS + Android: mid-Dec.
- &#127912; Mapbox Studio: early 2018


--- 


# BONUS
<h2 style="text-align: center;"> &#127881;&#127881;&#127881;</h2>

---

hacking vector data projections

---

[dirty reprojectors](http://devseed.com/dirty-reprojectors-app/) by Development Seed

---

<h2 style="text-align: center;">&#128587;&#129299;&#128506;&#65039;</h2>

contribute: 
- [github.com/mapbox/mapbox-gl-js/](github.com/mapbox/mapbox-gl-js/)
- [github.com/mapbox/mapbox-gl-native/](github.com/mapbox/mapbox-gl-native/)

slides: github.com/mollymerp/nacis-pcd-2017/
questions? [@mollymerp](twitter.com/mollymerp)
