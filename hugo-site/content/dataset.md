---
title: "Brick Kiln Dataset"
---

![Brick Kiln Dataset](/brick-kilns/bk_images/brick.svg)

## Initial Dataset Selection

An initial labeled dataset is required to train the object detection models. We select the regions for initial labeling with the following criteria:

- **i) highly polluted**
- **ii) highly populated** (highly impacted by brick kilns) 
- **iii) high likelihood of kilns** (as suggested by an air quality expert)
- **iv) non-attainment cities**

### Regional Descriptions

**(1) Delhi Airshed, India**: Delhi, India's capital, is highly populated and consistently ranks among the world's most polluted cities. While no brick kilns are located within Delhi due to strict regulations, the surrounding region has a dense concentration of kilns. We selected an 80×80 grid over Delhi with a 0.01-degree resolution, as defined by Guttikunda.

**(2) Lucknow Airshed, Uttar Pradesh, India**: Lucknow, the capital of Uttar Pradesh (India's most populous state), is classified as a non-attainment city under NCAP. A 60×60 airshed grid with 0.01-degree resolution was chosen for annotation, following the definition by Guttikunda.

**(3) West Bengal Small Airshed, West Bengal**: A small airshed near the Haldi River in West Bengal was selected due to the high density of brick kilns in the area. A 639 km² region surrounding the identified kilns was annotated.

**(4) Ahmedabad Buffer Region**: Ahmedabad, a non-attainment city, was studied in collaboration with the Gujarat Pollution Control Board (GPCB). Following the Environment (Protection) Amendment Rules, 2022, we geo-located brick kilns within a 10 km buffer of Ahmedabad city.

## Initial Data Preparation

We initiated our study by collecting geospatial coordinates of brick kilns from published literature, focusing on regions with high concentrations of brick manufacturing activities. We then used these coordinates to extract high-resolution imagery patches and manually annotated brick kilns.

Across these four regions, we manually scanned over 15,018 km² area and identified 1,621 brick kilns, completing the annotations in 125 hours.

**Table 2: Statistics of initial dataset**

| Airshed | Area (km²) | CFCBK | FCBK | Zigzag | Total Kilns | Annotation time (hours) |
|---------|------------|-------|------|---------|-------------|-------------------------|
| Delhi Airshed | 6937 | 2 | 35 | 746 | 783 | 58 |
| Lucknow Airshed | 3962 | 26 | 225 | 241 | 492 | 33 |
| West Bengal Small | 639 | 0 | 89 | 110 | 199 | 5 |
| Ahmedabad 10 km buffer | 3480 | 38 | 108 | 1 | 147 | 29 |
| **Total** | **15018** | **66** | **457** | **1098** | **1621** | **125** |

### Annotation Process

The annotation process involves labeling brick kilns with oriented bounding boxes (OBBs) and assigning a category to represent the kiln's technology. A custom labeling interface using Leafmap was developed, utilizing the Esri Wayback Satellite Imagery WMS layer. The region of interest was divided into a 1 km² grid, and each grid cell was manually inspected. OBBs were drawn around the identified kilns, and the labeled data were overlaid onto cropped, geo-referenced Planet images. This process ensured accurate and undistorted annotations during reprojection from Esri to Planet imagery.

### Illustration of the labeling process

<img src="/brick-kilns/bk_images/labeling_grid.png" alt="Grid for annotation" style="width: 45%; margin-right: 5%;">
<img src="/brick-kilns/bk_images/labeling_kiln.png" alt="Labeling a kiln" style="width: 45%;">

**Fig 1:** (a) Grid for annotation (b) Labeling a kiln

## Iterative Dataset Building Process

We develop a comprehensive dataset containing a total of **30,638 hand-validated brick kilns** with oriented bounding boxes.

### Brick Kiln Examples by Category

<table style="width: 100%; border-collapse: collapse;">
  <tr>
    <th><img src="/brick-kilns/bk_images/CFCBK_106.png" alt="CFCBK 1" style="width: 100px;"></th>
    <th><img src="/brick-kilns/bk_images/CFCBK_12.png" alt="CFCBK 2" style="width: 100px;"></th>
    <th><img src="/brick-kilns/bk_images/CFCBK_131.png" alt="CFCBK 3" style="width: 100px;"></th>
    <th><img src="/brick-kilns/bk_images/CFCBK_39.png" alt="CFCBK 4" style="width: 100px;"></th>
    <th><img src="/brick-kilns/bk_images/CFCBK_5.png" alt="CFCBK 5" style="width: 100px;"></th>
    <th><img src="/brick-kilns/bk_images/CFCBK_50.png" alt="CFCBK 6" style="width: 100px;"></th>
  </tr>
  <tr>
    <th><img src="/brick-kilns/bk_images/FCBK_0.png" alt="FCBK 1" style="width: 100px;"></th>
    <th><img src="/brick-kilns/bk_images/FCBK_1.png" alt="FCBK 2" style="width: 100px;"></th>
    <th><img src="/brick-kilns/bk_images/FCBK_10.png" alt="FCBK 3" style="width: 100px;"></th>
    <th><img src="/brick-kilns/bk_images/FCBK_13.png" alt="FCBK 4" style="width: 100px;"></th>
    <th><img src="/brick-kilns/bk_images/FCBK_14.png" alt="FCBK 5" style="width: 100px;"></th>
    <th><img src="/brick-kilns/bk_images/FCBK_17.png" alt="FCBK 6" style="width: 100px;"></th>
  </tr>
  <tr>
    <th><img src="/brick-kilns/bk_images/Zigzag_11.png" alt="Zigzag 1" style="width: 100px;"></th>
    <th><img src="/brick-kilns/bk_images/Zigzag_16.png" alt="Zigzag 2" style="width: 100px;"></th>
    <th><img src="/brick-kilns/bk_images/Zigzag_18.png" alt="Zigzag 3" style="width: 100px;"></th>
    <th><img src="/brick-kilns/bk_images/Zigzag_2.png" alt="Zigzag 4" style="width: 100px;"></th>
    <th><img src="/brick-kilns/bk_images/Zigzag_20.png" alt="Zigzag 5" style="width: 100px;"></th>
    <th><img src="/brick-kilns/bk_images/Zigzag_22.png" alt="Zigzag 6" style="width: 100px;"></th>
  </tr>
</table>

**Fig. 2:** A few samples of predicted brick kilns of each brick kiln category from our model. The first, second, and third rows show samples of CFCBK, FCBK, and Zigzag in that order. Imagery © 2024 Planet Labs Inc.

## Dataset Statistics

- **Total Kilns Detected**: 30,638
- **Geographic Coverage**: Five states across Indo-Gangetic Plain
- **Area Covered**: Over 520,000 km² (15.8% of India)
- **Image Resolution**: 4.77 meters (Planet Labs)
- **Detection Method**: YOLOv11m-OBB model

## Geographic Coverage

The analysis covers five Indo-Gangetic states:
- Uttar Pradesh
- Bihar
- West Bengal  
- Punjab
- Haryana

## Applications

This dataset enables research in:
- Environmental monitoring and compliance tracking
- Air quality modeling and emission inventories
- Policy development and enforcement
- Economic analysis of the brick sector