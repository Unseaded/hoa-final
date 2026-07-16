---
layout: page
title: Board & Committees
---

Our Homeowners Association is entirely volunteer-run. The Board of Directors and various committees work diligently to maintain the quality of life in our community.

<div class="divider">{% include svg-fence.html %}</div>

## Board of Directors

{% assign board_members = site.committee | where: "group", "Board of Directors" | sort: "sort_order" %}
{% for member in board_members %}
### {{ member.title }} - {{ member.role }}
{{ member.content | markdownify }}
{% endfor %}

<div class="divider">{% include svg-fence.html %}</div>

## Architectural Review Committee

{% assign arc_members = site.committee | where: "group", "Architectural Review" | sort: "sort_order" %}
{% for member in arc_members %}
- **{{ member.title }}**, {{ member.role }}
{% endfor %}

## Social Committee

{% assign social_members = site.committee | where: "group", "Social" | sort: "sort_order" %}
{% for member in social_members %}
- **{{ member.title }}**, {{ member.role }}
{% endfor %}
