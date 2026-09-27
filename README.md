# federalhillsouth.org
An attempt to convert the Google sites page to jekyll

## Neighborhood map

`/neighborhoods/` contains a JavaScript-free, keyboard-accessible SVG overlay
linking to six neighborhood associations. The basemap is a cropped PNG originally rendered at 1280 × 827 from an [OpenStreetMap](https://www.openstreetmap.org/) SVG export
(© OpenStreetMap contributors, [ODbL](https://www.openstreetmap.org/copyright)).
The source SVG is excluded from the published site.

The polygons are maintained directly in `assets/maps/neighborhood-boundaries.geojson`
and as SVG paths in `_data/neighborhoods.yml` (JSON syntax is valid YAML).
Both use the same geometry. The original SVG coordinate system spans 1206 × 779 with Web Mercator
bounds west -76.624, south 39.262, east -76.580, north 39.284.
No rebuild scripts are required. Styling is in `_sass/neighborhood-map.scss`;
the inline overlay is in `_includes/neighborhood-map.html`.

### Simplified boundaries

The outlines follow the supplied South Baltimore Neighborhood Association
reference image with the requested editorial limits: South Baltimore ends at
Race Street; its territory is excluded from Sharp Leadenhall; Federal Hill ends
at Covington Street; Riverside's northern arm ends at Gittings Street, with the
short Jackson Street connection to Key Highway shown in the reference. All
regions stop on the north side of I-95. These are simplified neighborhood guides,
not official association service boundaries.

### Map crop coordinates

The displayed PNG (`assets/maps/south-baltimore.png`) and source SVG both output
936 × 724 pixels. The crop history from the original 1280 × 827 PNG is:

| Crop | Offset in preceding PNG | Result |
| --- | --- | --- |
| Right 10%, top 3% | 0, 25 | 1152 × 802 |
| Right 10%, bottom 5% | 0, 0 | 1037 × 762 |
| Right 5%, bottom 5% | 0, 0 | 985 × 724 |
| Left 5% | 49, 0 | 936 × 724 |

The final rectangle in original PNG pixels is x=49, y=25, width=936, height=724.
Convert horizontal values by 1206/1280 and vertical values by 779/827 to obtain
the source SVG and overlay viewBox: `46.1671875 23.548972189 881.8875 681.978234583`.
The overlay image uses the same rectangle. SVG width/height specify the output
pixels; viewBox values retain the original drawing coordinates. `preserveAspectRatio="none"`
accounts for the original PNG's whole-pixel height rounding without letterboxing.
No SVG paths or neighborhood coordinates are rescaled or edited by this crop.
Future crops should be calculated from actual integer pixel rectangles, not
compounded percentages.
