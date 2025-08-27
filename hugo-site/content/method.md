---
title: "Model Selection and Results"
---

![Model Selection and Results](/bk_images/model-selection-results.png)

## Model Architecture

We use **YOLOv11m-OBB** (Oriented Bounding Boxes) for accurate detection of brick kilns in satellite imagery. This model is specifically optimized for:

- Object detection in aerial imagery with irregular orientations
- Handling varying kiln shapes and sizes  
- High precision in dense manufacturing areas
- Efficient processing of large-scale satellite imagery

## Performance Metrics

We utilize YOLO-OBB models provided by Ultralytics for our experiments. These models deliver performance comparable to state-of-the-art OBB detection frameworks. YOLO's algorithm enables faster inference by detecting objects in a single forward pass, making it well-suited for scaling predictions across large geographic areas.

**Table 3: Performance of various models on the initial dataset**

| Model | CFCBK | FCBK | Zigzag | Weighted mAP |
|-------|-------|------|--------|--------------|
| yolov8l-obb | 0.61 | 0.58 | 0.83 | 0.62 |
| yolov8x-obb | 0.63 | 0.55 | 0.82 | 0.63 |
| yolov11x-obb | 0.66 | 0.57 | 0.80 | 0.66 |
| yolov11l-obb | 0.68 | 0.51 | 0.76 | 0.66 |
| yolov8m-obb | 0.68 | 0.54 | 0.79 | 0.66 |
| **yolov11m-obb** | **0.73** | **0.61** | **0.83** | **0.71** |

yolov11m-obb model is yielding the best 'Weighted mAP' among all models, and thus, we use it for brick kiln detection.

## Training Process

1. **Data Annotation**: Manual labeling of brick kilns in high-resolution imagery
2. **Label Transfer**: Mapping annotations from Esri to Planet imagery  
3. **Model Training**: YOLOv11m-OBB training with oriented bounding boxes
4. **Validation**: Cross-validation with ground truth surveys
5. **Deployment**: Large-scale inference across five states

## Results and Validation

Our model successfully detected **30,638 brick kilns** across the Indo-Gangetic Plain. Results were validated through:

- Ground truth surveys and field verification
- Comparison with existing literature and government data
- Cross-referencing with local knowledge and expert input  
- Statistical validation of detection patterns

**Table 4: Brick kilns dataset across 5 states of Indo-Gangetic plain, India**
*We extract this data by covering 520,000 km² area with 448 million population.*

| State | CFCBK | FCBK | Zigzag | Total |
|-------|-------|------|---------|-------|
| Uttar Pradesh | 1450 | 9933 | 5952 | 17335 |
| Bihar | 40 | 1584 | 4424 | 6048 |
| West Bengal | 33 | 1105 | 1967 | 3105 |
| Haryana | 1 | 130 | 1948 | 2079 |
| Punjab | 0 | 305 | 1766 | 2071 |
| **Total** | **1524** | **13057** | **16057** | **30638** |

### Geographic Distribution of Detected Kilns

CFCBKs are most densely located in Punjab and Haryana, with fewer present in other states. FCBKs are most prevalent in Uttar Pradesh and West Bengal. Zigzag kilns are also present in all states and are densely located in Bihar and the area close to Delhi National Capital Region (Delhi-NCR).

<table style="width: 100%; border-collapse: collapse;">
  <tr>
    <th><img src="/bk_images/kiln_locations_CFCBK.png" alt="CFCBK locations" style="width: 250px;"></th>
    <th><img src="/bk_images/kiln_locations_FCBK.png" alt="FCBK locations" style="width: 250px;"></th>
    <th><img src="/bk_images/kiln_locations_Zigzag.png" alt="Zigzag locations" style="width: 250px;"></th>
  </tr>
  <tr align="center">
    <td>CFCBKs</td>
    <td>FCBKs</td>
    <td>Zigzag kilns</td>
  </tr>
</table>

### External Validation

In 2023, the Uttar Pradesh Pollution Control Board (UPPCB) conducted a comprehensive field survey and prepared a report for judicial proceedings. This report provides district-wise counts of operational brick kilns, revealing a total of 19,671 brick kilns in Uttar Pradesh as of 2022.

Below, we present a district-wise comparison of brick kiln counts derived from the UPPCB survey and our dataset. Notably, our study is the first to validate a machine-learning-derived brick kiln dataset using independently collected survey data.

<table style="width: 100%; border-collapse: collapse;">
  <tr align="center">
    <td><img src="/bk_images/brick_kilns_survey_counts.png" alt="Survey counts" style="width: 250px;">(a)</td>
    <td><img src="/bk_images/brick_kilns_our_counts.png" alt="Our counts" style="width: 250px;">(b)</td>
    <td><img src="/bk_images/brick_kilns_comparison.png" alt="Comparison" style="width: 250px;">(c)</td>
  </tr>
</table>

**Fig 3:** District-wise brick kiln counts in Uttar Pradesh as per (a) UPPCB 2023 survey (19671 kilns) and (b) our hand-validated data (17335 kilns). A Comparison between our counts and the survey counts is shown in (c). Our counts have a Pearson correlation coefficient of 0.94 with the survey counts.