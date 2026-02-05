---
title: ForceCtrl (2025)
description: Hand-Raycasting with User-Defined Pinch Force for Control-Display Gain Application
# img: assets/img/forcectrl_teaser.jpg
excerpt: "<img src='/images/projects/forcectrl_teaser.png' width='500'>"
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
        <a href= 'http://ohseo.github.io/files/2025-12-23-TVCG-Oh.pdf' class="btn btn-sm z-depth-0" role="button">Paper (Early Access)</a>
        <!-- <a href='http://ohseo.github.io/files/2025-12-23-TVCG-Oh.mp4' class="btn btn-sm z-depth-0" role="button">Video</a> -->
        </div>
</div>

<br>

<div class="row justify-content-center">
    <div class="col-sm-10">
        <figure class="figure">
            <img src="/images/projects/forcectrl_main.png" class="img-fluid rounded z-depth-1" alt="ForceCtrl Teaser">
            <figcaption class="figure-caption text-center">
                Overview of ForceCtrl. (a) Users control pointing precision via pinch force detected by an sEMG armband. (b) Comparison of the proposed three CD gain strategies activated by force.
            </figcaption>
        </figure>
    </div>
</div>

---

## Abstract

We present **ForceCtrl**, a novel 3D hand raycasting technique that enhances pointing precision by adjusting control-display (CD) gain based on user-defined pinch force. We introduce a target-agnostic approach for refining raycasting precision, overcoming limitations in human motor abilities. User-defined pinch force, detected with surface electromyography (sEMG), enables users to easily activate or deactivate CD gain during interaction. We propose three CD gain strategies and compare them through target selection and placement tasks. Our system reduces selection errors, placement jitters, and user workload, especially for distant targets in high-difficulty tasks. These results highlight the effectiveness of applying CD gain to hand raycasting and demonstrate the potential of user-defined pinch force as a robust input modality for precise hand interaction in AR/VR.

---

## Demo Video

<div class="row justify-content-center">
    <div class="col-sm-10">
        <video width="100%" height="auto" controls muted class="rounded z-depth-1">
            <source src="/files/2025-12-23-TVCG-Oh.mp4" type="video/mp4">
            Your browser does not support the video tag.
        </video>
    </div>
</div>
<br>

---

## System Overview

**ForceCtrl** leverages user-defined pinch force to adjust the Control-Display (CD) ratio of the ray, allowing for high-precision interaction without requiring handheld devices.

### 1. Force Classification via sEMG
The system uses a forearm-worn sEMG armband to detect pinch force levels. Unlike traditional methods that rely on fixed thresholds or MVC (Maximum Voluntary Contraction), our model classifies **user-defined subjective force levels** based on the Borg Scale (None, Moderate, Very Strong). A CNN-based model ensures robust classification across different users and sessions. This personalized approach accommodates individual physical differences and ensures consistent performance across various users. 

<div class="row justify-content-center">
    <div class="col-sm-10">
        <figure class="figure">
            <img src="/images/projects/forcectrl_system_diagram.png" class="img-fluid rounded z-depth-1" alt="System Architecture">
            <figcaption class="figure-caption text-center">
                System architecture: (a) CNN-based Force Classifier, (b) Force Accumulator for stability, (c) Interaction State Machine.
            </figcaption>
        </figure>
    </div>
</div>

### 2. Interaction States and Transitions
A dedicated **interaction state machine** manages the workflow: it transitions from standard raycasting to a high-precision mode when force is detected. This seamless integration of force sensing and raycasting logic allows for stabilized pointing without the need for additional buttons or complex gestures.

<div class="row justify-content-center">
    <div class="col-sm-10">
        <figure class="figure">
            <img src="/images/projects/forcectrl_interaction_state.png" class="img-fluid rounded z-depth-1" alt="Interaction State Machine">
            <figcaption class="figure-caption text-center">
                Interaction state transitions: (a) Coarse Pointing, (b) Coarse Dragging, (c) Precise Pointing, and (d) Precise Dragging.
            </figcaption>
        </figure>
    </div>
</div>

### 3. Ray Shifting Strategies for CD Gain Application
To apply CD gain to 3D raycasting, we proposed and evaluated three ray shifting strategies:

* **CDHandPos:** Scales the virtual hand's position based on physical hand movement.
* **CDRayDir:** Scales the change in ray direction, maintaining the hand position.
* **CDRayRev (Best Performing):** Reverses and scales the directional change, causing the ray to converge. This method was found to be most effective for high-precision tasks at a distance.

<div class="row justify-content-center">
    <div class="col-sm-5">
        <figure class="figure">
            <img src="/images/projects/forcectrl_ray.png" class="img-fluid rounded z-depth-1" 
            style="width:100%"
            alt="Ray Shifting Strategies">
            <figcaption class="figure-caption text-center">
                Visual comparison of CDHandPos, CDRayDir, and CDRayRev strategies.
            </figcaption>
        </figure>
    </div>
</div>

---

## Key Results

We conducted a user study (n=16) comparing **ForceCtrl** techniques against standard raycasting in target selection and placement tasks.

* **Improved Precision:** All **ForceCtrl** techniques significantly reduced selection errors and jitter compared to the baseline.
* **Reduced Jitter:** **CDRayRev** showed the most stable performance for distant targets.
* **User Preference:** Participants preferred **CDRayRev** for high-precision tasks due to its intuitive converging behavior, despite it deviating from physical hand pointing.

---

## Citation

```bibtex
@article{oh2025forcectrl,
  title={ForceCtrl: Hand-Raycasting with User-Defined Pinch Force for Control-Display Gain Application},
  author={Oh, Seo Young and Seo, Junghoon and Lee, Juyoung and Yoon, Boram and Yoon, Sang Ho and Woo, Woontack},
  journal={IEEE Transactions on Visualization and Computer Graphics},
  year={2025},
  publisher={IEEE}
}
```

<!-- <p>
<b>Publications</b>
    <ul>
        <li>
            <b>Seo Young Oh</b>, Junghoon Seo, Juyoung Lee, Boram Yoon, Sang Ho Yoon, and Woontack Woo. (2025). &quot;ForceCtrl: Precision Control of Hand-Raycasting with User-Adaptive Force Input.&quot; <i>IEEE Transactions on Visualization and Computer Graphics</i>
            <a href="/publication/2025-12-23-TVCG-Oh">Link</a>
        </li>
    </ul>
</p> -->