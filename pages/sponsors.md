---
layout: page
title: Sponsors
permalink: /sponsors/
description: >
  Thank you to our community and institutional sponsors for supporting hpc.social!
no_groups: true
---

<style>
.gray {
    filter: none;
    -webkit-filter: grayscale(0);
    border-radius: 5px;
}

.gray:hover {
    filter: grayscale(100%);
    -webkit-filter: grayscale(100%);
}
</style>

{% for sponsor in site.data.sponsors.sponsors %}
<div class="card">
<h2>{{ sponsor.name }}</h2>
<a href="{{ sponsor.url }}" target="_blank"><img class="gray" src="{{ site.baseurl }}/{{ sponsor.image }}"></a>
</div>
{% endfor %}

<div style="padding-top:100px">
<a type="button" class="btn btn-primary" target="_blank" href="https://github.com/sponsors/hpc-social?o=esb">Sponsor 💗️ hpc.social</a>
</div>