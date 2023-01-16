---
layout: page
title: Mean volume error to Sørensen-Dice
description: Mean volume error to Sørensen-Dice Conversion
img: /assets/img/volume_2_dice_cover.png
importance: 2
category: Machine Learning
---

Many machine and deep learning models predict continuous value instead of categorical classification. In medical imaging, continuous value prediction is more often seen, for example, in predicting the area or volume of an organ/tumor. However, this type of task is often performed by adopting segmentation techniques, though the same goal can be achieved often by bypassing segmentation. The problem arises when comparing the performance of such a task is to be done between a segmentation-based approach and a segmentation-free approach. Segmentation approaches produce pixel/voxel-level masks and then do post-processing to produce a combined value (e.g., volume or area of an organ/tumor), thus able to use Dice coefficient for performance evaluation, while segmentation-free approaches directly produce the final value (i.e., volume or area of an organ/tumor) without producing pixel/voxel-level masks, thus unable to use Dice coefficient rather use mean volume error. Therefore, we defined an approach to convert mean volume/area error to the Dice coefficient. 

<strong>Mean volume error to Sørensen-Dice Conversion</strong>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/volume_2_dice_figure.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>




<strong>For Details</strong>

Please read our papers [[1](https://marafathussain.github.io/assets/pdf/tmi2021.pdf)].
