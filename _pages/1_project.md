---
layout: page
title: 
description: 
img: assets/img/12.jpg
importance: 1
category: work
permalink: /beyond-imagenet-accuracy/
---

<div style="text-align: center;">
    <h2 style="font-weight: bold;">ConvNet vs Transformer, Supervised vs CLIP:</h2>
    <h2 style="font-weight: bold;">Beyond ImageNet Accuracy</h2>
    <h4>
        <strong style="margin-right: 30px;"><a href="https://kirill-vish.github.io/" target="_blank" rel="noopener noreferrer">Kirill Vishniakov¹</a></strong>
        <strong style="margin-right: 30px;"><a href="https://zhiqiangshen.com/" target="_blank" rel="noopener noreferrer">Zhiqiang Shen¹</a></strong>
        <strong><a href="https://liuzhuang13.github.io/" target="_blank" rel="noopener noreferrer">Zhuang Liu²</a></strong>
    </h4>
    <div style="display: flex; justify-content: center; align-items: center; gap: 40px;">
    <div style="text-align: center; position: relative; max-width: 25%;">
    <sup style="position: absolute; left: -0.5em; top: 1.4em; padding-right: 3px; font-size: 18px; font-weight: normal;">1</sup>
    <a href="https://mbzuai.ac.ae/">
        {% include figure.html path="assets/img/beyond-imagenet-accuracy/mbzuai_logo.jpg" title="MBZUAI" class="img-fluid rounded" %}
    </a>
    </div>
    <div style="text-align: center; position: relative; max-width: 25%;">
        <sup style="position: absolute; left: -0.5em; top: -0.25em; padding-right: 3px; font-size: 18px; font-weight: normal;">2</sup>
        <a href="https://ai.meta.com/">
            {% include figure.html path="assets/img/beyond-imagenet-accuracy/meta_logo.png" title="META AI Research" class="img-fluid rounded" %}
        </a>
    </div>
</div>
</div>

<!-- Buttons container with custom styled buttons -->
<div class="buttons-container" style="text-align: center; margin-bottom: 20px;"> <!-- Increased bottom margin -->
  <!-- Paper button -->
  <a href="https://arxiv.org/pdf/2311.09215.pdf" target="_blank" rel="noopener noreferrer" class="btn">
    Paper
  </a>
  <!-- Code button -->
  <a href="https://github.com/kirill-vish/Beyond-INet" target="_blank" rel="noopener noreferrer" class="btn">
    Code
  </a>
</div>

<style>
/* CSS for the buttons to appear with white background and black stroke */
.btn {
  border: 1px solid black; /* Black stroke */
  border-radius: 15px; /* Rounded corners */
  background-color: white; /* White background */
  padding: 5px 10px; /* Reduced spacing inside the button to make it smaller */
  display: inline-block; /* To apply padding and background */
  text-decoration: none; /* Remove underline from links */
  color: black; /* Text color */
  font-size: 14px; /* Reduced text size */
  margin: 0 5px; /* Reduced margin between buttons */
  transition: background-color 0.3s, color 0.3s; /* Transition for hover effect */
}

.buttons-container {
  margin-bottom: 30px; /* Added space from the bottom */
  margin-top: -15px; /* Adjust top margin to move buttons up */
}

.btn:hover {
  background-color: black; /* Background color on hover */
  color: white; /* Text color on hover */
}
</style>

<style>
  body {
    font-weight: normal;
  }
</style>

<!-- Add this part for the abstract -->
<div class="row justify-content-sm-center">
    <div class="col-sm-12 mt-3 mt-md-0">
        <h3 style="text-align: center;"><strong>Abstract</strong></h3>
        <p>
            Modern computer vision offers a great variety of models to practitioners, and selecting a model from multiple options for specific applications can be challenging. Conventionally, competing model architectures and training protocols are compared by their classification accuracy on ImageNet. However, this single metric does not fully capture performance nuances critical for specialized tasks. In this work, we conduct an in-depth comparative analysis of model behaviors beyond ImageNet accuracy, for both ConvNet and Vision Transformer architectures, each across supervised and CLIP training paradigms. Although our selected models have similar ImageNet accuracies and compute requirements, we find that they differ in many other aspects: types of mistakes, output calibration, transferability, and feature invariance, among others. This diversity in model characteristics, not captured by traditional metrics, highlights the need for more nuanced analysis when choosing among different models.
        </p>
    </div>
</div>
<!-- End of Abstract section -->
<hr>
<!-- Image section -->
<div class="col-sm mt-3 mt-md-0 d-flex justify-content-center">
    <div style="width: 50%;">
        {% include figure.html path="assets/img/beyond-imagenet-accuracy/method.png" title="Fig 1: Overview of the Method" class="img-fluid rounded" %}
    </div>
</div>

Models are often compared only by their ImageNet accuracy, ignoring many other aspects of their behaviors. Our study shows models with similar ImageNet performance can have vastly different properties.

<!-- Horizontal line -->
<hr>

<!-- Models Section -->
<h4 style="font-weight: bold;">Models</h4>
To examine the impact of architecture and training objective on model performance, we compare Vision Transformer (ViT) with ConvNeXt, both modern architectures with comparable ImageNet-1K validation accuracies and computational requirements. Our study contrasts supervised models, represented by DeiT3-Base/16 and ConvNeXt-Base, and vision encoders of CLIP-based models from OpenCLIP.
<div class="col-sm mt-3 mt-md-0 d-flex justify-content-center">
    <div style="width: 100%;">
        {% include figure.html path="assets/img/beyond-imagenet-accuracy/models.jpg" title="Fig 1: Overview of the Method" class="img-fluid rounded" %}
    </div>
</div>
<hr>

<h4 style="font-weight: bold;">Property Analysis</h4>

Our analysis is designed to investigate model behaviors that can be evaluated without the need for further training or finetuning. This approach is particularly relevant for practitioners with limited computational resources, who often depend on pretrained models. While we recognize the value of downstream tasks like object detection, our focus is on properties that offer insights with minimal computational demands and reflect behaviors important for real-world applications.

<h5 style="font-weight: bold;">Model Mistakes</h5>

ImageNet-X is a dataset that extends ImageNet-1K with detailed human annotations for 16 factors of variation, enabling an in-depth analysis of model mistakes in image classification. It employs an error ratio metric (lower is better) to quantify model performance on specific factors relative to overall accuracy, allowing for a nuanced analysis of model mistakes. ImageNet-X results illustrate that:
<ol>
<li> CLIP models make fewer mistakes relative to their ImageNet accuracy than supervised. </li>
<li> All models suffer mostly from complex factors like occlusion. </li>
<li> Texture is the most challenging factor for all models. </li>
</ol>
<div class="col-sm mt-3 mt-md-0 d-flex justify-content-center">
    <div style="width: 100%;">
        {% include figure.html path="assets/img/beyond-imagenet-accuracy/imagenetx_clip-1.png" title="Fig: Model Mistakes in ImageNet-X with CLIP" class="img-fluid rounded" %}
        {% include figure.html path="assets/img/beyond-imagenet-accuracy/imagenetx_sup-1.png" title="Fig: Model Mistakes in ImageNet-X with Supervised Learning" class="img-fluid rounded" %}
    </div>
</div>
<hr>

<h5 style="font-weight: bold;">Shape / Texture Bias</h5>

Shape-texture bias examines if models rely on brittle texture shortcuts rather than high-level shape cues. This bias can be studied using cue-conflict images that combine shapes and textures from different classes. This approach helps to understand how much the model's decisions are based on shape compared to texture. We evaluate shape-texture bias on cue-conflict dataset, observing that CLIP models have smaller texture bias than supervised and that ViT models have higher shape bias than ConvNets. 

<div class="d-flex justify-content-center">
    <div style="width: 50%; padding-right: 10px;">
        {% include figure.html path="assets/img/beyond-imagenet-accuracy/shape_texture_clip-1.png" title="Fig: Shape/Texture Bias with CLIP" class="img-fluid rounded" %}
    </div>
    <div style="width: 50%; padding-left: 10px;">
        {% include figure.html path="assets/img/beyond-imagenet-accuracy/shape_texture_sup-1.png" title="Fig: Shape/Texture Bias with Supervised Learning" class="img-fluid rounded" %}
    </div>
</div>
<hr>


<h5 style="font-weight: bold;">Model Calibration</h5>

Calibration quantifies whether a model's predicted confidence aligns with its actual accuracy. This is assessed through metrics such as Expected Calibration Error (ECE) and visual tools including reliability diagrams and confidence histograms. We evaluate calibration on ImageNet-1K and ImageNet-R, dividing predictions into 15 bins. In our experiments we observe the following:

<ol>
<li> CLIP models are overconfident and supervised models are slightly underconfident. </li>
<li> Supervised ConvNeXt is better calibrated than supervised ViT. </li>
</ol>

<div class="col-sm mt-3 mt-md-0 d-flex justify-content-center">
    <div style="width: 100%;">
        {% include figure.html path="assets/img/beyond-imagenet-accuracy/ImageNet-1K_calibration_subplot-1.png" title="Fig: Model Calibration on ImageNet-1K" class="img-fluid rounded" %}
        {% include figure.html path="assets/img/beyond-imagenet-accuracy/gray_line-1.png"  class="img-fluid rounded" %}
        {% include figure.html path="assets/img/beyond-imagenet-accuracy/ImageNet-R_calibration_subplot-1.png" title="Fig: Model Calibration on ImageNet-R" class="img-fluid rounded" %}
    </div>
</div>
<hr>

<h5 style="font-weight: bold;">Robustness & Transferability</h5>

Model robustness and transferability are essential for adapting to data distribution shifts and new tasks. We evaluated robustness using various ImageNet variants and found that while ViT and ConvNeXt models have comparable average performances, supervised models generally outperformed CLIP on robustness except for ImageNet-R and ImageNet-Sketch. In terms of transferability, evaluated using the VTAB benchmark with 19 datasets, supervised ConvNeXt was superior to ViT almost matching the performance of CLIP models.

<div class="d-flex justify-content-center">
    <div style="width: 50%; padding-right: 10px;">
        {% include figure.html path="assets/img/beyond-imagenet-accuracy/vtab_robust_clip_abs.png" title="Fig: Robustness and Transferability with CLIP" class="img-fluid rounded" %}
    </div>
    <div style="width: 50%; padding-left: 10px;">
        {% include figure.html path="assets/img/beyond-imagenet-accuracy/vtab_robust_sup_abs.png" title="Fig: Robustness and Transferability with Supervised Learning" class="img-fluid rounded" %}
    </div>
</div>
<hr>

<h5 style="font-weight: bold;">Synthetic Data</h5>

Synthetic datasets like PUG-ImageNet allow precise control over factors like camera angles and textures, emerging as a promising research avenue, so we analyze model performance on synthetic data. PUG-ImageNet contains photorealistic ImageNet images with systematic variation in factors like pose and lighting, with performance measured by absolute top-1 accuracy. We provide results for different factors in PUG-ImageNet, finding that ConvNeXt outperforms ViT on nearly all factors. This suggests ConvNeXt is better than ViT on synthetic data, with a smaller gap for CLIP models which have lower accuracy than supervised models, likely related to inferior original ImageNet accuracy.

<div class="col-sm mt-3 mt-md-0 d-flex justify-content-center">
    <div style="width: 100%;">
        {% include figure.html path="assets/img/beyond-imagenet-accuracy/pug_imagenet_clip-1.png" title="Fig: Synthetic Data with CLIP" class="img-fluid rounded" %}
        {% include figure.html path="assets/img/beyond-imagenet-accuracy/pug_imagenet_sup-1.png" title="Fig: Synthetic Data with Supervised Learning" class="img-fluid rounded" %}
    </div>
</div>
<hr>

<h5 style="font-weight: bold;">Transformation Invariance</h5>

Transformation invariance refers to a model's ability to produce consistent representations unaffected by input transformations that preserve semantic meaning, such as scaling or shifting. This property enables models to generalize well across different but semantically similar inputs. Our methodology involves resizing images for scale invariance, shifting crops for positional invariance, and adjusting resolution with interpolated positional embeddings for the ViT model. We assess invariance to scale, shift, and resolution on ImageNet-1K by varying crop scale/location and image resolution. ConvNeXt outperforms ViT under supervised training. Overall, models are more robust to shift than scale/resolution transforms. For applications requiring high robustness to scale, shift and resolution, our results indicate supervised ConvNeXt could be the best choice.

<div class="col-sm mt-3 mt-md-0 d-flex justify-content-center">
    <div style="width: 100%;">
        {% include figure.html path="assets/img/beyond-imagenet-accuracy/invariance_all-1.png" title="Fig: Transformation Invariance" class="img-fluid rounded" %}
    </div>
</div>
<hr>

<h5 style="font-weight: bold;">Conclusions</h5>
<p>
  We found that each model can have its own distinct strengths. This suggests that model selection should depend on the target use cases, as standard performance metrics may overlook key task-specific nuances. In addition, many existing benchmarks are derived from ImageNet which biases the evaluation. Developing new benchmarks with different data distributions will be crucial for evaluating models in a more real-world representative context.
</p>
<p>
  <strong>ConvNet vs Transformer</strong><br>
</p>
<ol>
<li> We found the superior performance of
 supervised ConvNeXt over supervised ViT on many benchmarks: it is better calibrated, more invariant to data transformations, and demonstrates better transferability and robustness. </li>
 <li>  ConvNeXt outperforms ViT on synthetic data.</li> 
 <li> ViT has a higher shape bias. </li>
</ol>

<p>
  <strong>Supervised vs CLIP</strong> 
</p>
<ol>
  <li> Despite CLIP models being better at transferability, supervised ConvNeXt shows a competitive performance on this task. This showcases the potential of supervised models. </li>
  <li> Supervised models are better at robustness benchmarks, likely because these are ImageNet variants. </li>
  <li> CLIP models have a higher shape bias and make fewer classification mistakes relative to their ImageNet accuracy.</li>
</ol>

<h5 style="font-weight: bold;">Contact</h5>
<p>
  <a href="mailto:ki.vishniakov@gmail.com">ki [dot] vishniakov [at] gmail [dot] com</a>
</p>

<h5 style="font-weight: bold;">Citation</h5>

{% raw %}
```html
@article{vishniakov2023convnet,
      title={ConvNet vs Transformer, Supervised vs CLIP: Beyond ImageNet Accuracy}, 
      author={Kirill Vishniakov and Zhiqiang Shen and Zhuang Liu},
      year={2023},
      eprint={2311.09215},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```
{% endraw %}
