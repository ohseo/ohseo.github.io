---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

[Download PDF](/files/CV_SYOh_2026Jan.pdf)

{% include base_path %}

Research Interests
------
Interaction Techniques, 3D User Interfaces, Augmented Reality, Ubiquitous Virtual Reality, Human-Computer Interaction


Education
------
* Ph.D. Candidate in <i>Culture Technology</i>, KAIST, 2026 (expected)
* M.S. in <i>Culture Technology</i>, KAIST, 2020
* B.S. in <i>Mechanical Engineering</i>, KAIST, 2014

Work experience
------
* **Naru EMS Inc.** as a Research Engineer, Apr 2016 - Feb 2019
  * Language porting, UI implementation, AR-based demo implementation
  
Skills
------
* **Programming**: C#, Python, C++
* **Development Tools**: Unity, OpenXR, Meta XR SDL, Mixed Reality Toolkit
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
* **Teaching Assistant** at KAIST
  * Undergraduate Research Participation Program (2015, 2022, 2025)
  * CTP445 Augmented Reality (2020, 2022)
  * GCT565 Augmented Humans (2021)
  * GCT700 Topics in Culture Techology Project Planning -- AR Project (2021)
  * ID216 Product Design Engineering (2013, 2014)
* **Graduate Mentor** at Korea Science Academy of KAIST
  * High School Research Participation Program (2015)
* **Volunteering**
  * **Reviewer**: CHI, CHI Late-Breaking Work, Korea Software Congress
  * **Academic Event Assistant**: ISMAR (2025 Best Student Volunteer), KAIST GSCT Post-Metaverse Forum

<div style="text-align: right"><i>Last Updated: Jan 2026</i></div>