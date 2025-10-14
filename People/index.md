---
title: People
nav:
  order: 3
---

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
