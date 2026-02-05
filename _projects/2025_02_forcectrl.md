---
title: ForceCtrl (2025)
description: Hand-Raycasting with User-Defined Pinch Force for Control-Display Gain Application
img: assets/img/forcectrl_teaser.jpg
collection: projects
---

<div class="row">
    <div class="col-sm-12 text-center">
        <h2>ForceCtrl: Hand-Raycasting with User-Defined Pinch Force for Control-Display Gain Application</h2>
        <p>
            <b>Seo Young Oh</b>, Junghoon Seo, Juyoung Lee, Boram Yoon, Sang Ho Yoon, and Woontack Woo<br>
            <em>IEEE Transactions on Visualization and Computer Graphics (TVCG), 2024</em>
        </p>
    </div>
</div>

<div class="row justify-content-center">
    <div class="col-sm-12 text-center">
        <a href="URL_TO_PDF" class="btn btn-sm z-depth-0" role="button">Paper</a>
        <a href="URL_TO_VIDEO" class="btn btn-sm z-depth-0" role="button">Video</a>
        </div>
</div>

<br>

<div class="row justify-content-center">
    <div class="col-sm-10">
        <figure class="figure">
            <img src="/assets/img/forcectrl_fig1.jpg" class="img-fluid rounded z-depth-1" alt="ForceCtrl Teaser">
            <figcaption class="figure-caption text-center">
                Overview of ForceCtrl. (a) Users control pointing precision via pinch force detected by an sEMG armband. (b) Comparison of three CD gain strategies activated by force.
            </figcaption>
        </figure>
    </div>
</div>

---

### Abstract

We present **ForceCtrl**, a novel 3D hand raycasting technique that enhances pointing precision based on control-display (CD) gain controlled with user-defined pinch force. We introduce a target-agnostic approach for refining raycasting precision, overcoming limitations in human motor accuracy. User-defined pinch force, detected with surface electromyography (sEMG), enables users to easily activate or deactivate CD gain during interaction. We propose three CD gain strategies and compare them through target selection and placement tasks. Our system reduces selection errors, placement jitters, and user workload, especially for distant targets in high-difficulty tasks. These results highlight the effectiveness of applying CD gain to hand raycasting and demonstrate the potential of user-defined pinch force as a robust input modality for precise hand interaction in AR/VR.

---

### System Overview

ForceCtrl leverages user-defined pinch force to adjust the Control-Display (CD) ratio of the ray, allowing for high-precision interaction without requiring handheld devices.

#### 1. Force Classification via sEMG
The system uses a forearm-worn sEMG armband to detect pinch force levels. Unlike traditional methods that rely on fixed thresholds or MVC (Maximum Voluntary Contraction), our model classifies **user-defined subjective force levels** (None, Moderate, Very Strong). A CNN-based model ensures robust classification across different users and sessions.

<div class="row justify-content-center">
    <div class="col-sm-10">
        <figure class="figure">
            <img src="/assets/img/forcectrl_system.jpg" class="img-fluid rounded z-depth-1" alt="System Architecture">
            <figcaption class="figure-caption text-center">
                System architecture: (a) CNN-based Force Classifier, (b) Force Accumulator for stability, (c) Interaction State Machine.
            </figcaption>
        </figure>
    </div>
</div>

#### 2. Ray Shifting Strategies (CD Gain)
To apply CD gain to 3D raycasting, we proposed and evaluated three ray shifting strategies:

* **CDHandPos:** Scales the virtual hand's position based on physical hand movement.
* **CDRayDir:** Scales the change in ray direction, maintaining the hand position.
* **CDRayRev (Best Performing):** Reverses and scales the directional change, causing the ray to converge. This method was found to be most effective for high-precision tasks at a distance.

<div class="row justify-content-center">
    <div class="col-sm-8">
        <figure class="figure">
            <img src="/assets/img/forcectrl_strategies.jpg" class="img-fluid rounded z-depth-1" alt="Ray Shifting Strategies">
            <figcaption class="figure-caption text-center">
                Visual comparison of CDHandPos, CDRayDir, and CDRayRev strategies.
            </figcaption>
        </figure>
    </div>
</div>

---

### Key Results

We conducted a user study (n=16) comparing ForceCtrl techniques against standard raycasting in target selection and placement tasks.

* [cite_start]**Improved Precision:** All ForceCtrl techniques significantly reduced selection errors and jitter compared to the baseline[cite: 1042].
* [cite_start]**Reduced Jitter:** **CDRayRev** showed the most stable performance for distant targets[cite: 1149].
* [cite_start]**User Preference:** Participants preferred **CDRayRev** for high-precision tasks due to its intuitive converging behavior, despite it deviating from physical hand pointing[cite: 1321].

---

### Citation

```bibtex
@article{oh2024forcectrl,
  title={ForceCtrl: Hand-Raycasting with User-Defined Pinch Force for Control-Display Gain Application},
  author={Oh, Seo Young and Seo, Junghoon and Lee, Juyoung and Yoon, Boram and Yoon, Sang Ho and Woo, Woontack},
  journal={IEEE Transactions on Visualization and Computer Graphics},
  year={2024},
  publisher={IEEE}
}