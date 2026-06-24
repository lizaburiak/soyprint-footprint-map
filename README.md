# Brazilian soy land-use footprint — interactive map

An interactive map of the **land-use footprint of Brazilian soy** (hectares) embodied in
international consumption, by **municipality of origin**, 2010–2022.

Live: **https://lizaburiak.github.io/soyprint-footprint-map/**

- **Destination dropdown** — Total, the regional aggregates (EU-27, Rest of Asia, Rest of
  world, Brazil-domestic), and **every individual importing country**.
- **Year slider + ▶ play** — watch the footprint expand across the decade.
- **Hover** a municipality for its footprint in hectares.

Built with **MapLibre GL JS** (WebGL): the municipal geometry loads once; selecting a
destination fetches only that destination's small values file and recolours on the GPU, so
it stays fast with all ~190 destinations. Colour is a shared square-root scale.

From the open, reproducible SOYPRINT pipeline (municipality → FABIO → consumer).

## Files
- `index.html` — the MapLibre app.
- `municipios.geojson` — simplified municipal boundaries (loaded once).
- `data/index.json` — destination list + shared colour `vmax`.
- `data/<KEY>.json` — per-municipality footprint by year for each destination (ISO3 for
  countries; `total`, `r_eu27`, `r_asia`, `r_row`, `r_bra` for aggregates).

## Regenerate / update
In the SOYPRINT repo:
```bash
Rscript code/prep_web_data.R         # per-destination JSON -> web/data/
.venv/bin/python code/build_web_geometry.py   # -> web/municipios.geojson
# then copy web/{index.html,municipios.geojson,data} here, commit, push
```
