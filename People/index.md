---
title: People
nav:
  order: 3
---

<div class="pi-hero">
  <!-- 左侧大图：把 pi.jpg 换成你的文件名 -->
  <img src="{{ 'people/pi.png' | relative_url }}" alt="Principal Investigator" class="pi-photo">

  <!-- 右侧文字区 -->
  <div>
    <h1 class="pi-name">Prof. Baoping Zhang 張寶萍</h1>
    <div class="pi-title">Assistant Professor</div>

    <ul class="pi-meta">
      <li>Ph.D. in Fudan University</li>
    </ul>

    <p class="pi-links">
      <strong>Links:</strong>
      <a href="https://example.com">Group Page</a>
      <span class="sep">&bull;</span>  <!-- 在中间加字符：圆点，可以换成 | -->
      <a href="https://scholar.google.com/">Google Scholar</a>
      <span class="sep">&bull;</span>
      <a href="https://www.researchgate.net/">ResearchGate</a>
      <span class="sep">|</span>
      <strong>Email:</strong> <a href="mailto:you@your-domain">you@your-domain</a>
    </p>

    <p class="pi-office">
      <strong>Office:</strong> Room XXX, Your Building, Your University, City, ZIP
    </p>
    
  </div>
</div>

  <h2>Biography</h2>
  <ul>
    <li>Prof. Baoping Zhang received her Ph.D. degree in Materials Science from Fudan University in Jan 2019. Afterwards, she worked as a postdoctoral fellow at City University of Hong Kong and The Hong Kong Polytechnic University. She was promoted to Assistant Professor in the Department of Mechanical Engineering at The Hong Kong Polytechnic University in June 2024.</li>
    <li>Prof. Zhang's research interest has been broadly centered on nature-inspired materials and interfaces for sustainable water-energy nexus. Her research aims to explore nature's wisdoms and translate nature's principles into the development advanced materials and functional surfaces that can inspire innovative water-energy applications, ranging from water harvesting to energy harvesting and thermal management.</li>
    <li>Prof. Zhang has a track record with peer-reviewed publications in the field of Engineering/Materials/Energy, including Nature Reviews Electrical Engineering, Nature Communications, Science Advances, ACS Nano, Chemical Engineering Journal, ACS Applied Materials & Interfaces, etc.</li>
  </ul>
    
<!-- 下方两块浅底纹方框 -->
<div class="two-col">
  <div class="card">
    <h2>Research Interests</h2>
    <ul>
      <li>Heat and mass transfer</li>
      <li>Nanoengineered materials and devices</li>
      <li>Energy conversion, storage, and management</li>
      <li>Water harvesting, purification, and conservation</li>
    </ul>
  </div>

  <div class="card">
    <h2>Teaching</h2>
    <ul>
      <li>Thermal-Fluids Engineering I</li>
      <li>Thermal-Fluids Engineering II</li>
      <li>Intermediate Heat Transfer</li>
      <li>Advanced Heat Transfer</li>
    </ul>
  </div>
</div>



{% comment %}
1) 置顶的 PI 区块（单独拉取 role == "pi" 的第一位，放大显示）
{% endcomment %}
{% assign pi = site.members | where: "role", "pi" | first %}
{% if pi %}
  {% capture pi_block %}
  <div class="pi-block">
    <img src="{{ pi.image | relative_url }}" alt="{{ pi.name }}" class="pi-photo">
    <div class="pi-text">
      <h2 class="pi-name">{{ pi.name }}</h2>
      {% if pi.position %}<p class="pi-pos"><strong>{{ pi.position }}</strong></p>{% endif %}
      {{ pi.content }}
      <p class="pi-links">
        {% if pi.email %}<a href="mailto:{{ pi.email }}">Email</a>{% endif %}
        {% if pi.links.google-scholar %} · <a href="{{ pi.links.google-scholar }}">Google Scholar</a>{% endif %}
        {% if pi.links.orcid %} · <a href="https://orcid.org/{{ pi.links.orcid }}">ORCID</a>{% endif %}
        {% if pi.links.website %} · <a href="{{ pi.links.website }}">Website</a>{% endif %}
      </p>
    </div>
  </div>
  {% endcapture %}
  {% include section.html title="Principal Investigator" content=pi_block %}
{% endif %}

{% comment %}
2) Students 网格
{% endcomment %}
{% assign students = site.members | where: "role", "student" | sort: "weight" %}
{% if students and students.size > 0 %}
  {% capture students_grid %}
  <div class="people-grid">
    {% for m in students %}
      <div class="person-card">
        {% if m.image %}<img src="{{ m.image | relative_url }}" alt="{{ m.name }}">{% endif %}
        <div class="person-name">{{ m.name }}</div>
        {% if m.position %}<div class="person-pos">{{ m.position }}</div>{% endif %}
      </div>
    {% endfor %}
  </div>
  {% endcapture %}
  {% include section.html title="Group Members (Students)" content=students_grid %}
{% endif %}

{% comment %}
3) Staff 网格
{% endcomment %}
{% assign staff = site.members | where: "role", "staff" | sort: "weight" %}
{% if staff and staff.size > 0 %}
  {% capture staff_grid %}
  <div class="people-grid">
    {% for m in staff %}
      <div class="person-card">
        {% if m.image %}<img src="{{ m.image | relative_url }}" alt="{{ m.name }}">{% endif %}
        <div class="person-name">{{ m.name }}</div>
        {% if m.position %}<div class="person-pos">{{ m.position }}</div>{% endif %}
      </div>
    {% endfor %}
  </div>
  {% endcapture %}
  {% include section.html title="Research Staff" content=staff_grid %}
{% endif %}
