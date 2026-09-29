---
title: "Association Map"
layout: embed
permalink: /embeds/map/
---

<div class="neighborhood-map-scroll" tabindex="0" aria-label="South Baltimore neighborhood map; scroll horizontally on small screens">
{% include neighborhood-map.html %}
</div>

## Neighborhood associations

{% for neighborhood in site.data.neighborhoods %}
- [{{ neighborhood.name }} — {{ neighborhood.association }}]({{ neighborhood.url }}){:target="_blank"}
{% endfor %}

---

Map data © OpenStreetMap contributors. [License](https://www.openstreetmap.org/copyright){:target="_blank"}
