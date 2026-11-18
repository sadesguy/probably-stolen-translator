---
layout: default
lang: en
permalink: /en.html
---
{% capture manual %}{% include_relative GUIDE.en.md %}{% endcapture %}
{{ manual | replace: '(README.md)', '(./)' }}
