# Brazilian soy land-use footprint — interactive map

An interactive choropleth of the **land-use footprint of Brazilian soy** (hectares)
embodied in international consumption, by municipality of origin, 2010–2022.

- **Year slider + ▶ play** — watch the footprint expand over the decade.
- **Destination dropdown** — Total · China · EU-27 · Rest of Asia · Rest of world.
- **Hover** a municipality for its footprint in hectares.

Colour is a shared square-root scale across all years and destinations, so a darker
municipality always means a larger footprint.

Built from the open, reproducible SOYPRINT pipeline (municipality → FABIO → consumer).
`index.html` is self-contained (loads plotly.js from a CDN).

## Republish / update

Regenerate `index.html` from the pipeline outputs:

```bash
# in the SOYPRINT repo:
Rscript code/prep_map_allyears.R      # extract per-municipality footprint, all years
.venv/bin/python code/build_web_map.py # -> web/footprint_map.html
cp web/footprint_map.html /path/to/soyprint-footprint-map/index.html
git -C /path/to/soyprint-footprint-map commit -am "update map" && git -C ... push
```
