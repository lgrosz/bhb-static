---
header-includes:
  - >
      <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
      integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY="
      crossorigin=""/>
  - >
      <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"
      integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo="
      crossorigin=""></script>
  - > 
      <script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet-gpx/2.1.0/gpx.min.js"
      crossorigin=""></script>
---

# Errors

This page contains errors in Black Hills Bouldering media.

## *Black Hills Bouldering* (ISBN-13: 9798987979815)

### Rapid City

#### Doty Dungeon

1. **Inaccurate directions**

   The previous directions were...

   > Park at the Doty Springs trailhead and head south along the trail for 450 yards. When the trail takes a U-turn, continue downhill (east) another 150 yards to reach the creek bed. Hike southbound, following the creek, 500 yards. The Doty Dungeon should be visible in at the base of the cliff. The trail to the cave isn’t well-established, and one can be easily misled by the game trails in the area.

   ... while these directions are simple and would eventually get one to the cave, it would be a miserably steep bushwack. What follows is a corrected set of directions.

   Park at the *Doty Springs* trailhead ([44.131841, -103.401384](https://maps.google.com/maps?t=k&q=loc:44.131841+-103.401384)). Pass through the gate and follow the well-defined trail south 425 yards. Instead of following the u-turn on the main trail, stay straight on FS-414.4E (marked by a brown carsonite sign as of 2024). Follow this forest service road for about 75 yards southwest and uphill toward a private driveway. *Do not hike* on the private driveway. Paralleling the driveway, hike south-southeast along the flat plateau about 350 yards. At this point, the plateau descends gently towards *Boxelder Creek*. Hike southeast another 250 yards towards the creek. One may intersect a north-south running trail adjacent to the creek. Navigate this trail, or the creek bed itself, to locate the cave in the southeastern bend of the horseshoe ([44.124619, -103.397029](https://maps.google.com/maps?t=k&q=loc:44.124619+-103.397029)). When descending from the plateau, err south as it much easier to locate the cave while walking north than walking south.

<div id="map" style="height: 360px;"></div>
<script>
    const map = L.map('map');

    var usgsTopo = L.tileLayer('https://basemap.nationalmap.gov/arcgis/rest/services/USGSTopo/MapServer/tile/{z}/{y}/{x}', {
        attribution: 'Tiles courtesy of the <a href="https://usgs.gov/">U.S. Geological Survey</a>',
        maxNativeZoom: 16,
    });

    var usgsImagery = L.tileLayer('https://basemap.nationalmap.gov/arcgis/rest/services/USGSImageryOnly/MapServer/tile/{z}/{y}/{x}', {
        attribution: 'Tiles courtesy of the <a href="https://usgs.gov/">U.S. Geological Survey</a>',
        maxNativeZoom: 16,
    });

    var tileLayers = {
        "USGS Topo": usgsTopo,
        "USGS Imagery": usgsImagery
    }

    L.control.layers(tileLayers).addTo(map);

    // Default
    usgsTopo.addTo(map);

    // URL to your GPX file or the GPX itself as a XML string.
    const url = '/9798987979815-rapid-city_doty-dungeon_1.json';

    fetch(url)
        .then(response => response.json())
        .then(data => {
            var layer = L.geoJSON(data, {
                onEachFeature: (feature, layer) => {
                    layer.bindPopup(`<p>${feature.properties.name}</p>`);
                }
            }).addTo(map);

            map.fitBounds(layer.getBounds());
        })
    .catch(error => {
            console.error('Error loading GeoJSON data:', error);
        });

    map.on('load', function () {
        var center = map.getCenter();

        L.popup()
            .setLatLng(center)
            .setContent('Click on map features for more information.')
            .openOn(map);
    });
</script>

### Breezy Point

#### North Seas

##### Gospel Boulder

###### The Deity

1. **Missing name**

   The problem is listed in the book as the sixth problem on this boulder,
   without a name. Its original name, given by the first ascensionists, is _The
   Deity_.

###### Rerighting the Gospel

1. **Incorrect start**

   In the book, the problem is described as sharing a start with _The Deity_
   \(6\) on the right side of the wash, beginning from a sit start. Originally,
   it was established using a squat/sit start, with the left hand on a
   down-pulling sloper and the right hand on a slightly lower crimp, positioned
   directly below the problem’s finish.

### Sylvan Lake

#### The Outlets

##### Eden Boulder

> [!todo]
> It appears I assumed too much about the first-ascentionists of problems on
> the Eden Boulder. Jason McNabb approached me today (2025.2.8) at the gym and
> specifically called out that what I have listed as _Modus Chode_ in the book
> (_Modous Chode as per Scott Hahn's 8a scorecard and provided hand drawn
> topo) was originally called _Modest Chode_, likely coined by someome in the
> "Spearfish crew" (Carl Gostola was mentioned by name) regarding a shirt that
> Jason wore.
>
> I pressed Jason further and it appears that he likely FAd _Ace and Gary_ and
> _Modest Chode_. Upon further review of Scott's 8a scorecard, Scott claimed FA
> of
>
> - _The Sodomite_
> - _Midget Molester_
> - _Cho Mo_
>
> Scott logged but did not state he made the FA of _The Rapist_, though I think
> it is still likely he made the FA of this problem.
>
> Jason also mentioned that Brandon and Amanda Taglioli may have discovered the
> boulder and were likely trying the _Sodomite_ prior to Scott establishing the
> line. Jason heard they were going to call the boulder or a problem on it
> "Asp," like a biblical reference.

### Report errors

To report errors, please [email me](mailto:logan.grosz@gmail.com?subject=%5BBlack%20Hills%20Bouldering Errors%5D%5B9798987979815%5D).
