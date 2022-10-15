---
layout: page
title: Bone Detection in Ultrasound
description: Detection of bone surface in ultrasound using combined elastography and envelope signal power
img: /assets/img/bd_cover.png
importance: 4
---

Fluoroscopy remains the primary intraoperative imaging modality for bone boundary visualization in computer assisted orthopaedic surgery systems. The associated radiation exposure posing risks to both patients and surgical teams gave rise to recent interest in safer non-ionizing real-time intraoperative imaging alternatives such as US. In US guided surgical intervention, bone localization in US images is essential for visualization and guidance, e.g., during fragment positioning in fracture reduction surgeries. Despite recent advancement in US intensity-based automatic bone segmentation, results remain unpredictable due to the high levels of speckle noise, reverberation, and signal drop out. To tackle this challenge, we proposed an effective way to extract 3-D bone surfaces using a surface growing approach that is seeded from 2-D bone contours. The initial 2-D bone contours are estimated from a combination of ultrasound strain images and envelope power images.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/bd_fig1.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Fig. 1: Schematic indicating different components of our bone surface estimation method.
</div>

<strong>Bone Surface Localization</strong>

This work has two steps: (1) At first, we estimate the 2D bone contour from a pair of RF frames taken with and without a little compression. To estimate the bone surface location in this pair of 2D images, we used a real-time strain imaging technique developed by Rivaz et al. (2011), which is based on an analytic minimization of a regularized cost function. The resulting strain image was fused with the envelope power map using a weight. The weight was selected based on an empirical analysis of the mean absolute error (MAE) between the actual and estimated bone surfaces for different weight values. The weight for which the MAE was lowest in this pilot data set was used throughout our experiments. Then we used local linear fits over the maximum intensity point along each scan line of the fused map to produce the final bone boundary. (2) Finally, having identified a seed contour in the 2D elastographic image, we next use a surface growing approach to extend this contour laterally through the 3D volume set. 

<strong>Data</strong>

We acquired eight sets ofin vivo US data, five of which were acquired for 2D evaluations from five volunteers (volunteer I: 25-y-old man, volunteer
II: 33-y-old man, volunteer III: 26-y-old man, volunteer IV: 24-y-old man, volunteer V: 27-y-old man), and three sets of data were acquired for 3-D evaluations from three volunteers (volunteer VI: 27-y-old man, volunteer VII: 26-y-old man, volunteer VIII: 29-y-old man) after obtaining informed consent. All data were acquired with freehand compression. The US images were acquired using a SonixRP (Ultrasonix Medical) scanner in the Center for Hip Health and Mobility, Vancouver Coastal Health Authority. Here also, we used a L14-5/60 linear array probe operating at 10 MHz and a 4DL14-5/38 linear 4D array probe operating at 5 MHz to collect data for the 2D and 3D implementations, respectively. The study was approved by the UBC clinical research ethics board

<strong>Results</strong>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/bd_fig2.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Fig. 2: Three-dimensional bone surface detection using in vivo data. (a–c) Bone regions scanned on each volunteer (with red rectangles). (d–f) B-Mode images. (g–i) Three-dimensional phase symmetry images estimated with the 3-D optimized phase symmetry (3DOPS) method (Hacihaliloglu et al. 2014). (j–l) Bone surface after bottom-up ray casting in (g)–(i), respectively. (m–o) Bone surfaces estimated with the 3-D strain enhancement (3DSE) method.
</div>

<strong>For Details</strong>

Please read our papers [[1](https://www.sciencedirect.com/science/article/pii/S0301562916303696?casa_token=krY2KlUluY8AAAAA:5y7hfrUvrHjJkcsVWHnUtw5g3Wa3KWuLRwL3oSu8Ggn6YjiCxEd166yYSrWmEingXL1H09FN)], [[2](https://link.springer.com/chapter/10.1007/978-3-319-10404-1_45)], [[3](https://arafathm.github.io/assets/pdf/MICCAI2014.pdf)].