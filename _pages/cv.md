---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

[Download PDF](/files/CV_SYOh_2026Sep.pdf)

{% include base_path %}

Research Interests
------
3D Hand Interaction, Virtual Object Manipulation, XR Interfaces, and Human-Computer Interaction


Education
------
* Ph.D. in <i>Culture Technology</i>, KAIST, 2026
  * "Finger-Driven Semi-Isomorphic Hand Interaction for Fine-Grained 3D Manipulation"
  * Co-advised by Woontack Woo and Sang Ho Yoon
* M.S. in <i>Culture Technology</i>, KAIST, 2020
  * "Finger Contact in 3D Gesture Interaction to Improve Temporal Input Accuracy in HMD-based Augmented Reality"
* B.S. in <i>Mechanical Engineering</i>, KAIST, 2014

Work experience
------
* **SpaceTop Research Center, KAIST** as a Postdoctoral Researcher, Sep 2026 - Present
  * Managing a national human resource development project on <i>Spatial Computing HCI Technology</i>, spanning cross-lab XR research. (IITP, 2026 - Present)
* **Ubiquitous Virtual Reality Lab, KAIST** as a Graduate Researcher, Mar 2019 - Aug 2026
  * Led two research projects on virtual object interaction techniques for <i>Real-time XR Interface Technology</i>. (IITP, 2024 - 2026)
  * Developed cross-device interfaces spanning XR headsets and handhelds for <i>WISE AR UI/UX Platform for Smartglasses</i>. (IITP, 2022 - 2023)
  * Implemented hand and avatar interaction components for remote collaboration systems under <i>Human Reconstruction for Telepresent Interaction</i>. (NRF, 2019 - 2020)
* **Naru EMS Inc. / SQAnd Inc.** as a Research Engineer, Sep 2016 - Feb 2019
  * Designed and demonstrated a HoloLens-based real-time AR visualization of mid-air sound sources rendered by the company's spatial audio technology. (SQAnd, 2018 - 2019)
  * Ported engineering simulation algorithms to C and implemented the simulator user interfaces. (Naru EMS, 2016 - 2019)

  
Skills
------
* **Programming**: C#, Python, C++
* **XR Development**: Unity, OpenXR, Meta XR SDK, Mixed Reality Toolkit
* **Devices**: Meta Quest 3/Pro/2, Microsoft HoloLens, Magic Leap, Android
* **Methods**: 3D interaction design, XR prototyping, controlled user studies, statistical analysis
* **Design & Graphhics**: Illustrator, Photoshop, Premiere Pro
* **Languages**: Korean (Native), English (Proficient)

Publications
------
  <ul>
    {% if site.publication_category %}
      {% for category in site.publication_category  %}
        {% assign title_shown = false %}
        {% for post in site.publications reversed %}
          {% if post.category != category[0] %}
            {% continue %}
          {% endif %}
          {% unless title_shown %}
            <h3>{{ category[1].title }}</h3><hr />
            {% assign title_shown = true %}
          {% endunless %}
          {% include archive-single-cv.html %}
        {% endfor %}
      {% endfor %}
    {% else %}
      {% for post in site.publications reversed %}
        {% include archive-single-cv.html %}
      {% endfor %}
    {% endif %}
  </ul>
  
Honors and Awards
------
* **Best Implementation Award - Student Design Competition**, Oct 2022
  * <i>ACM International Conference on Human-Computer Interaction with Mobile Devices and Services (MobileHCI)</i>
* **Best Student Volunteer**, Oct 2025
  * <i>IEEE International Symposium on Mixed and Augmented Reality (ISMAR)</i>

Academic Services
------
* **Teaching Assistant** at KAIST: CTP445 Augmented Reality, GCT565 Augmented Humans, GCT700 Culture Technology AR Project, Undergraduate Research Participation Program
* **Reviewer**: ACM CHI, ACM UIST, ACM CHI Late-Breaking Work, Korea Software Congress
* **Event Assistant**: IEEE ISMAR 2025, KAIST GSCT Post-Metaverse Forum

<div style="text-align: right"><i>Last Updated: Sep 2026</i></div>