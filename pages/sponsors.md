---
layout: page
title: Sponsors
permalink: /sponsors/
description: >
  Thank you to our community and institutional sponsors for supporting hpc.social! We are grateful for this support, which is financial only and does not provide any other rights to contribute or influence content. To become a sponsor and help to cover the costs of providing this site and the other hpc.social services, please use the "Sponsor" button below.
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
