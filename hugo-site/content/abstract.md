---
title: "Abstract"
---

Air pollution kills 7 million people annually. The brick kiln sector significantly contributes to economic development but also accounts for 8-14% of air pollution in India. Policymakers have implemented compliance measures to regulate brick kilns. Emission inventories are critical for air quality modeling and source apportionment studies.

However, the largely unorganized nature of the brick kiln sector necessitates labor-intensive survey efforts for monitoring. Recent efforts by air quality researchers have relied on manual annotation of brick kilns using satellite imagery to build emission inventories, but this approach lacks scalability. Machine-learning-based object detection methods have shown promise for detecting brick kilns; however, previous studies often rely on costly high-resolution imagery and fail to integrate with governmental policies.

In this work, we developed a scalable machine-learning pipeline that detected and classified 30,638 brick kilns across five states in the Indo-Gangetic Plain using free, moderate-resolution satellite imagery from Planet Labs. Our detections have a high correlation with on-ground surveys. We performed automated compliance analysis based on government policies. In the Delhi airshed, stricter policy enforcement has led to the adoption of efficient brick kiln technologies.

This study highlights the need for inclusive policies that balance environmental sustainability with the livelihoods of workers.

## Overview of All Tasks

In this study we use quarterly satellite imagery with a resolution of 4.77m from Planet Labs, we train YOLO model to detect three brick kiln variants: **i) Circular Fixed Chimney Bull's Trench Kiln (CFCBK); ii) Fixed Chimney Bull's Trench Kiln (FCBK) and iii) Zigzag kilns** and apply this model across five Indo-Gangetic states **Uttar Pradesh, Bihar, West Bengal, Punjab and Haryana** with an area of over 520,000 km².

We applied various big data resources for automated compliance monitoring, focusing on two types of compliance rules: distance-based and technology-based. **Our analysis of distance-based compliance, using OpenStreetMap data across 13 categories, revealed that 70% of brick kilns violate at least one rule.**

For technology-based compliance, we examined trends in brick kiln technologies over 12 years between 2017 and 2021. **Our findings indicate that brick kilns contribute approximately 8% to PM₂.₅ concentrations in Delhi. We determined that 30.66 million people live within 800 meters of brick kilns, violating central government regulations.**