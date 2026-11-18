---
layout: default
lang: ru
permalink: /
---
{% capture manual %}{% include_relative README.md %}{% endcapture %}
{{ manual | replace: '(GUIDE.en.md)', '(en.html)' }}
