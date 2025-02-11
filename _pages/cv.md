---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Research Interests
------
Interaction Techniques, 3D User Interfaces, Augmented Reality, Ubiquitous Virtual Reality, Human-Computer Interaction


Education
------
* Ph.D. Candidate in Culture Technology, KAIST, 2026 (expected)
* M.S. in Culture Technology, KAIST, 2020
* B.S. in Mechanical Engineering, KAIST, 2014

Work experience
------
* **Naru EMS Inc.** as a Research Engineer, Apr 2016 - Feb 2019
  * Language porting, UI implementation, AR-based demo implementation
  
Skills
------
* **Programming**: C#, Python, C++, C, Java
* **Development Tools**: Unity, ARCore, ARKit, OpenXR, Mixed Reality Toolkit
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
* **Best Implementation Award - Student Design Competition**, Oct 2022 <br />
  * <i>The International Conference on Human-Computer Interaction with Mobile Devices and Services (MobileHCI)</i>

Academic Services and Experiences
------
* **Reviewer**
  * Proceedings of the CHI Conference on Human Factors in Computing Systems (CHI), 2024
  * Korea Software Congress (KSC), 2024
  * Extended Abstracts of the CHI Conference on Human Factors in Computing Systems (CHI Late-Breaking Work), 2022
* **Teaching Assistant**
  * Undergraduate Research Participation Program: 2015, 2022, 2025
  * CTP445 Augmented Reality: 2020, 2022
  * GCT565 Augmented Humans: 2021
  * GCT700 Topics in Culture Techology Project Planning: AR Project: 2021
  * ID216 Product Design Engineering: 2013, 2014
* **Academic Event Assistant**
  * KAIST GSCT Post-Metaverse Forum: 2021


<!-- Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html  %}
  {% endfor %}</ul>
  
Teaching
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Service and leadership
======
* Currently signed in to 43 different slack teams -->
