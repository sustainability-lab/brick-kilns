---
title: "Big Data Resources"
---

![Big Data Resources](bk_images/big-data.png)

## Satellite Imagery

Selecting suitable satellite imagery requires balancing cost and computational efficiency. High-resolution commercial imagery, such as Maxar (30-50 cm) and Airbus products, offers detailed views but is often too expensive for research. Brick kilns, on average, cover 150 meters in latitude and longitude and thus span approximately 15 × 15 pixels in Sentinel-2 imagery. Hence we utilized freely available moderate-resolution imagery (4.77 meters) under a research license.

### Planet Labs

We utilize satellite imagery from Planet Labs in this work. Our study area spans five Indian states, covering over 520,000 km² (15.8% of India). The large 4096 × 4096 sized images are divided into overlapping 640 × 640 sized crops with a 64-pixel overlap (≈300 meters), ensuring that brick kilns do not get cut at the image edges. We selected imagery from the first quarter of 2024. We annotated high-resolution imagery and transferred the labels to Planet imagery, as detailed in the next section.

### Esri Wayback Imagery

Esri, a leading provider of GIS technology delivers high-resolution basemaps (up to 30 cm) through a Web Map Service (WMS). We utilized Esri imagery from February 8, 2024, to align with the first-quarter Planet mosaic of 2024.

## OpenStreetMap

OpenStreetMap (OSM), a community-driven initiative, offers a vast array of geographic datasets contributed by volunteers globally. Using the Geofabrik platform, we extracted geometry data for features such as railway tracks, highways, rivers, schools, and habitation then utilize this data for distance-based compliance monitoring.

### Table 1: Datasets extracted from OpenStreetMap and filters applied to extract them

| Shapefile | Data | Filters |
|-----------|------|---------|
| gis_osm_landuse_a_free_1.shp | Habitation | fclass="residential" |
| gis_osm_landuse_a_free_1.shp | Orchards | fclass="orchard" |
| gis_osm_landuse_a_free_1.shp | Nature reserves | fclass="nature_reserve" |
| gis_osm_buildings_a_free_1.shp | Schools | type="school" |
| gis_osm_buildings_a_free_1.shp | Hospitals | type="hospital" |
| gis_osm_buildings_a_free_1.shp | Religious places | type="temple" or "mosque" or "church" |
| gis_osm_roads_free_1.shp | National & Express highways | ref starts with "NH" or "NE" |
| gis_osm_roads_free_1.shp | State highways | ref starts with "SH" |
| gis_osm_roads_free_1.shp | District highways | ref starts with "MDR" |
| gis_osm_water_a_free_1.shp | Wetland | fclass="wetland" |
| gis_osm_waterways_free_1.shp | Rivers | fclass="river" |
| gis_osm_railways_free_1.shp | Railway tracks | No filter |

## Government Data

We obtained geolocation data for 165,000 hospitals and nursing homes from the Indian Government's data portal. This dataset supports distance-based compliance monitoring of brick kilns.

## Population Data

We used the LandScan 2023 global population dataset, produced by Oak Ridge National Laboratory, at a resolution of 0.0083 degrees. We utilize this dataset to analyze population exposure due to brick kilns' air pollution.