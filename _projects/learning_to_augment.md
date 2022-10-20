---
layout: page
title: Learning-to-augmented in Deep Learning
description: Learning-to-Augment-incorporated CNN for COVID-19 Detection in X-ray Images 
img: /assets/img/lta_cover.png
importance: 4
category: Machine Learning
---

Under construction........please ignore below.

<strong>Segmentation-Free Estimation of Kidney Volumes using Deep Learning</strong>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/r5_fig2.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Fig. 1: Segmentation-free kidney volume estimation using deep CNN (top) and FCN (bottom).
</div>
<b>CNN-based Approach:</b> We estimate the cross-sectional area of a kidney in each slice using a deep CNN shown in Fig. 1 (top). The CNN performs regression and has seven layers excluding the input. It has four convolutional layers, three fully connected layers, and one Euclidean loss layer. We also use dropout layers along with the first two fully connected layers in order to avoid over-fitting. As mentioned earlier, the input is a 120×120 pixel image patch and the output is the ratio of kidney pixels to the total image size. The CNN is trained by minimizing the Euclidean loss between the desired and predicted values. Once the CNN model is trained, we deploy the model to predict the kidney area in a particular image patch. Finally, the volume of a particular kidney is estimated by integrating the predicted areas in all of its image patches in the axial direction.

<b>FCN-based Approach:</b> We use an FCN (Fig. 1, bottom) to predict the crosssectional area of a kidney in each patch. Our FCN is a regression network consisting of six layers, excluding the input. It has five convolutional layers, one fully connected layer (only to generate a single activation), and one Euclidean loss layer. To avoid overfitting, we use the dropout in the last convolution layer. During inference, the FCN predicts the kidney area in a particular image patch. Finally, we calculate a particular kidney’s volume by adding the FCN-predicted areas for all of its axial image patches and multiplying by the voxel dimensions.

<strong>Data</strong>

We used 100 patients’ CT scans accessed from the Vancouver General Hospital (VGH) records with required ethics approvals by the UBC Clinical Research Ethics Board (CREB), certificate number: H15-00237. There were a total of 200 kidney samples, and we used 130 samples (from 65 randomly chosen patients) for training, 20 samples (from 10 randomly chosen patients) for validation, and the remaining 50 samples for testing. Our dataset included 12 pathological
kidney samples (with endo- and exophytic tumors), and our training and test data contained six pathological cases each. We made sure that kidneys from the same patient were not split across the training, validation, and test cases. These data were acquired using a Siemens SOMATOM Definition Flash
(Siemens Healthcare GmbH, Erlangen, Germany) CT scanner. Ground truth kidney bounding boxes were calculated from manual kidney delineation performed by an expert radiologist.

We also used 210 patients’ CT scans from the 2019 Kidney Tumor Segmentation (KiTS) Challenge database. This database contains patients’ scans accessed from the University of Minnesota Medical Center records. These patients underwent partial or radical nephrectomy for one or more kidney tumors between 2010 and 2018. We used 160 randomly chosen patients’ data for training, 15 randomly chosen patients’ data for validation, and the remaining 35 patients data (70 kidney samples) for testing. Here also, we made sure that kidneys from the same patient were not split into the training, validation, and test cases. We also collected the kidney segmentation data from the same database.

<strong>Results</strong>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/r5_fig3.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Fig. 2: Kidney volume estimation performance by different methods. The result for our dual regression-forests method (published in 2016) is shown with Red box. The result for our CNN-based method (published in 2017) is shown with Green box. The results by our latest FCN-based work (accepted in 2021) are indicated with Blue box.
</div>

<strong>For Details</strong>

Please read our papers [[1](https://ieeexplore.ieee.org/abstract/document/9358223?casa_token=rxZNi4GaP-YAAAAA:vlaAvOf6J1pKBT9goM4k0cCgPyJQ9NgOg_SSzt4iAFwHINOSelv-LsPXU44-XYmkME_wsI8)], [[2](https://link.springer.com/chapter/10.1007/978-3-319-66179-7_70)].
