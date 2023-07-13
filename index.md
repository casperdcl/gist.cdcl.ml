---
title: Notes | Casper da Costa-Luis
description: Quick notes (too short to call a blog)
layout: default
---

{%- for item in site.html_pages -%}
{%- if item.title != page.title -%}
- [{{ item.title }}]({{ item.url }})
{% endif %}
{%- endfor -%}
