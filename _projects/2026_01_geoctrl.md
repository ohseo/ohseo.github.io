---
title: GeoCtrl (2026)
description: Finger-Driven In-Hand Virtual Object Rotation for XR
# img: assets/img/geoctrl_teaser.jpg
excerpt: "<img src='/images/projects/geoctrl_teaser.png' width='500'>"
collection: projects
---

<div class="row">
    <div class="col-sm-12 text-center">
        <h2>GeoCtrl: Finger-based Geometric Mapping and Speed-Adaptive Gain for In-Hand Object Rotation in AR/VR</h2>
        <p>
            <b>Seo Young Oh</b>, Taejun Son, Juyoung Lee, Sang Ho Yoon, and Woontack Woo<br>
            <em>IEEE International Symposium on Mixed and Augmented Reality (ISMAR), 2026</em>
        </p>
    </div>
</div>

<div class="row justify-content-center">
    <div class="col-sm-12 text-center">
        <a href='http://ohseo.github.io/files/2026-10-05-ISMAR-Oh.pdf' class="btn btn-sm z-depth-0" role="button">Paper</a>
        <!-- <a href='http://ohseo.github.io/files/2026-10-05-ISMAR-Oh.mp4' class="btn btn-sm z-depth-0" role="button">Video</a> -->
    </div>
</div>

<br>

<div class="row justify-content-center">
    <div class="col-sm-12">
        <figure class="figure">
            <img src="/images/projects/geoctrl_teaser.png" class="img-fluid rounded z-depth-1" alt="GeoCtrl Teaser">
            <figcaption class="figure-caption text-center">
                GeoCtrl enables dexterous in-hand rotation of a virtual object through finger-level geometric mapping. (a) While the normal virtual hand is visible to the user, (b) an internal reference triangle is formed from the thumb, index, and middle fingertips. (c) When the user traces the desired motion of the object with the fingers, (d) the orientation and morphology changes of the reference triangle are directly applied to the object's rotation.
            </figcaption>
        </figure>
    </div>
</div>

---

## Abstract

We propose a geometry-based virtual object rotation technique that leverages triangular configuration of fingertips and a speed-responsive Control-Display (CD) gain. Rather than replicating real-world physics which often lead to unnatural mid-air behavior in the absence of physical feedback, we leverage finger-level geometry to enable low-effort object rotation. We map the orientation and morphology of a triangle formed around fingertips directly to the object's rotation, assuming that users tend to trace the object's intended motion when physical constraints are missing. To enhance the proposed interaction and accommodate natural motor limits, we implement an adaptive CD gain that scales geometric input according to the fingertip movement speed. In a user evaluation, our method yielded shorter task completion time than physics-based rotation, though longer than a commodity hand-interaction technique, while significantly reducing physical demand relative to both reference conditions without increasing overall workload. We demonstrate that geometry-driven mapping and dynamic gain adaptation enable low-effort, finger-level rotational control of virtual objects in immersive environments.

---

## System Overview

**GeoCtrl** is a bare-hand in-hand rotation technique built on Unity and Meta Quest 3. Instead of simulating physics, it reads the *geometry* of three fingertips and maps it to the object, so users can rotate virtual objects with coarse gestural approximations rather than the exact motor precision a physics engine demands.

### 1. Geometry-based Rotation

The system forms an imaginary **reference triangle** from the thumb, index, and middle fingertips, the minimal configuration affording stable grasp control. The triangle's orientation <em>Q<sub>orientation</sub></em> is built from a forward vector <em>d<sub>index</sub></em> and the normal <em>d<sub>index</sub></em> × <em>d<sub>middle</sub></em>, anchored at the thumb. Because this alone misses in-plane motion of the middle finger, an **offset** term <em>Q<sub>offset</sub></em> is derived from the angle <em>θ</em> between <em>d<sub>index</sub></em> and <em>d<sub>middle</sub></em>, capturing morphological change of the triangle.

The frame-to-frame change of the combined quaternion <em>Q<sub>curr</sub></em> = <em>Q<sub>orientation</sub></em> ∗ <em>Q<sub>offset</sub></em> is applied directly to the object. All computation runs in the local wrist coordinate frame, decoupling finger manipulation from wrist rotation, and a 1-Euro filter (<em>f<sub>c</sub></em> = 3.0, <em>β</em> = 0.66) on each fingertip suppresses tracking jitter.

<div class="row justify-content-center">
    <div class="col-sm-12">
        <figure class="figure">
            <img src="/images/projects/geoctrl_geometry.png" class="img-fluid rounded z-depth-1" alt="Geometry-based Rotation Mechanism">
            <figcaption class="figure-caption text-center">
                Geometry-based rotation mechanism: (a) a grab is initiated with three fingers, (b) the fingertips form a reference triangle, (c) its orientation is set by the forward vector and the normal, and (d) the offset by the angle between the index and middle directions.
            </figcaption>
        </figure>
    </div>
</div>

### 2. Speed-Adaptive Control-Display Gain

The geometric mapping does not require a 1:1 ratio, so a **speed-responsive CD gain** is layered on top to improve efficiency and controllability. Following the two-phase model of motor control, fast fingertip motion (ballistic) is amplified and slow motion (corrective) is attenuated via a sigmoid of the maximum fingertip speed <em>v</em>:

<div class="row justify-content-center">
    <div class="col-sm-12 text-center">
        <p><em>g</em>(<em>v</em>) = (<em>g<sub>max</sub></em> &minus; <em>g<sub>min</sub></em>) / (1 + <em>e</em><sup><em>k</em>(<em>v<sub>inf</sub></em> &minus; <em>v</em>)</sup>) + <em>g<sub>min</sub></em></p>
    </div>
</div>

The rotational increment is converted to angle-axis form and its angle scaled by <em>g</em>(<em>v</em>). The inflection point <em>v<sub>inf</sub></em> = 0.074 m/s was derived from prior finger-based Fitts' Law work, and four candidate curves were implemented and compared in a controlled study. The **Low** curve (0.3–1.3) performed best and ships as the system default.

<div class="row justify-content-center">
    <div class="col-sm-7">
        <figure class="figure">
            <img src="/images/projects/geoctrl_gain_curve.png" class="img-fluid rounded z-depth-1" alt="CD Gain Curves">
            <figcaption class="figure-caption text-center">
                The four CD gain curves implemented and compared. All sigmoid curves share the same inflection point and minimum gain, but differ in maximum gain.
            </figcaption>
        </figure>
    </div>
</div>

### 3. Grab, Clutching, and Stability Handling

Supporting mechanisms keep the interaction stable without any physics-based contact handling:

* **Grab and release.** A grab triggers when all three fingertips contact the object, establishing the initial reference triangle; release occurs when contact is lost for two or more fingertips.
* **Grip-anchored positioning.** The object snaps to the *angle-weighted centroid* of the triangle. Because the thumb vertex subtends the sharpest interior angle in a precision grip, inverse-angle weighting gives it the greatest influence, keeping the anchor at the center of the grip rather than drifting toward the two close fingers.
* **Dwell-based clutching.** Reaching a kinematic limit naturally induces a pause, so a fingertip pause over 0.15 s decouples input from output, letting users reset their hand pose without moving the object. It exits automatically on release.
* **Triangle-area thresholding.** Rotation is deactivated when the triangle area falls below an empirically set threshold (5th percentile of observed areas), suppressing the unwanted rotation that occurs when fingertips are too close together.

### 4. Evaluation Testbed

A docking task testbed was built to evaluate the technique: two 4 cm semi-transparent dice, threshold-based dock-and-hold completion (2 cm / 10°, held 1 s), with grab, clutching, and docked states surfaced through outline feedback. Two reference conditions were deployed in the same environment for comparison — **HPTK+**, a state-of-the-art physics-based hand simulation, and **HandLevel**, the Touch Hand Grab feature of the Meta XR Interaction SDK.

<div class="row justify-content-center">
    <div class="col-sm-9">
        <figure class="figure">
            <img src="/images/projects/geoctrl_task.png" class="img-fluid rounded z-depth-1" alt="Docking Task Testbed">
            <figcaption class="figure-caption text-center">
                The docking task testbed. (a) The object die is to be matched to a target die rotated 135° around a random axis. (b) A green outline indicates successful docking within the completion threshold.
            </figcaption>
        </figure>
    </div>
</div>

---

## Key Results

We ran two within-subject user studies: a gain-curve exploration (n=16) and a system evaluation (n=24) comparing **GeoCtrl** against the physics-based and commodity references.

* **Gain curve:** The **Low** curve outperformed all alternatives on completion time and total rotation (*p* < .001). Steeper curves hurt usability, as users briefly exceed <em>v<sub>inf</sub></em> even during fine adjustment.
* **Faster than physics simulation:** **GeoCtrl** significantly reduced task completion time and time-on-target against the physics-based reference, confirming more effective rotational control without haptic feedback.
* **Lowest physical demand:** Rated significantly below both references on NASA-TLX physical demand, with no difference from the commodity technique on any other subscale — the added finger-level DOF cost no extra workload.
* **Finger-level, not arm-level:** **GeoCtrl** produced the greatest object rotation with far less wrist movement, confining manipulation to a significantly smaller workspace than both references.
* **User preference:** Preferred by 67% of participants, and rated more realistic and more physically comfortable than the physics-based reference, at the cost of a longer completion time than the commodity technique.

---

## Citation

```bibtex
@inproceedings{oh2026geoctrl,
  title={GeoCtrl: Finger-based Geometric Mapping and Speed-Adaptive Gain for In-Hand Object Rotation in AR/VR},
  author={Oh, Seo Young and Son, Taejun and Lee, Juyoung and Yoon, Sang Ho and Woo, Woontack},
  booktitle={2026 IEEE International Symposium on Mixed and Augmented Reality (ISMAR)},
  year={2026},
  publisher={IEEE}
}
```
