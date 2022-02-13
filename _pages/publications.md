---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---


  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a></u> and on <u><a href="https://air.uniud.it/simple-search?query=Michele%5C+Libralato&location=&sort_by=score&order=desc&rpp=10&etal=0&filtername=author&filterquery=rp10686&filtertype=authority">IRIS</a>.</u>


{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
