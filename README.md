# Urban Heat Island — GIS

A GIS analysis of **urban sprawl and the Urban Heat Island (UHI) effect in Bangalore (Bengaluru), India**,
comparing **2000 and 2025**. Produced for the GIS II final project (MA, 3rd semester). The project pairs
**GHSL built-up layers** (to map the growth of the built environment) with **Landsat-derived land surface
temperature** (to map thermal hotspots), then overlays the two to examine where new urban sprawl coincides
with elevated surface temperatures.

## Project contents

- **`Final_Project_Bangalore.qgz`** — the QGIS project file (layers, symbology, and processing)
- **Reports**
  - `Urban_Sprawl_UHI.pdf` — full report with detailed method and steps
  - `Urban_Sprawl_UHI_Short.pdf` — short summary version
- **Derived vector layers**
  - `Bangalore_boundary.*`, `Bangalore_dissolved.*`, `Bangalore_fixed_geometry.*` — study-area boundary
  - `built_2000_only.*`, `built_2025_only.*`, `builtmask_*_poly.*` — extracted built-up areas per year
- **Derived rasters** (small)
  - `New_Builtup_2000_2025.tif`, `sprawl_2000_2025.tif`, `builtmask_*.tif` — sprawl / built-up change masks
  - `Sprawl_UHI_Overlap.tif` — overlap of new sprawl with UHI hotspots
- **Other outputs** — `Bangalore.geojson`, `stats_2000.html`, `stats_2025.html`, `urban sprawl .xlsx`,
  and SAGA grids (`BUILT_*_BLR.*`)

## Method (overview)

1. Extract built-up extent for 2000 and 2025 from the GHSL built-up rasters.
2. Difference the two years to map **urban sprawl** (newly built-up areas).
3. Derive **land surface temperature (LST)** from Landsat thermal bands for each year.
4. Identify UHI hotspots from the LST surfaces.
5. Overlay new sprawl with UHI hotspots to find where growth coincides with heat.

Full details are in `Urban_Sprawl_UHI.pdf` (detailed) and `Urban_Sprawl_UHI_Short.pdf` (summary).

## Data sources

The raw datasets are **not redistributed in this repository** — they are large and publicly available
from their original providers. Download them directly from the sources below.

| Data | Source | Link |
|------|--------|------|
| GHSL Built-up (2000, 2025) | EC JRC Global Human Settlement Layer | https://ghsl.jrc.ec.europa.eu/ |
| Landsat 7 ETM+ (2000) | USGS Earth Explorer | https://earthexplorer.usgs.gov/ |
| Landsat 8 OLI/TIRS (2025) | USGS Earth Explorer | https://earthexplorer.usgs.gov/ |
| Bangalore Boundary | Public GIS datasets (BBMP), via DataMeet | https://github.com/datameet/Municipal_Spatial_Data/tree/master/Bangalore |

## Requirements

- [QGIS](https://qgis.org/) (3.x recommended)


## Note on large files

Source rasters (the GHSL built-up GeoTIFFs and Landsat thermal bands) reach several GB and exceed
GitHub's 100 MB file limit, so they are intentionally excluded via `.gitignore`. This repository holds
the **project, reports, and small derived layers** only; use the links above to obtain the source data.
