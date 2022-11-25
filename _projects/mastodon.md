---
layout: project
title: 'hpc.social on Mastodon'
date: 20 Nov 2022
image: 
  path: /assets/img/projects/mastodon.png
screenshot: /assets/img/projects/mastodon.png
links:
  - title: hpc.social on Mastodon
    url: https://mast.hpc.social
caption: Meet your colleagues in a new environment!
description: >
  If you are looking for a new community to migrate to, come join us on the Mastodon instance of
  <a class="link" href="https://mast.hpc.social" target="_blank">mast.hpc.social</a>! 
  It's an open community for HPC practitioners and friends alike!
  <br>
accent_color: '#4fb1ba'
accent_image:
  background: 'linear-gradient(to bottom,rgb(100, 102, 201) 0%,#27a1fc 100%)'
  overlay:    true
---

### hpc.social on Mastodon

<img src="https://img.shields.io/badge/dynamic/json?label=Accounts&query=stats.user_count&url=https%3A%2F%2Fmast.hpc.social%2Fapi%2Fv1%2Finstance"/>

We are proud to provide the HPC community with a Mastodon instance at
<a class="link" href="https://mast.hpc.social" target="_blank">mast.hpc.social</a>! 
You can check out <a href="https://mast.hpc.social/directory" target="_blank">community profiles here</a>,
and find important contacts, policy, and <a href="https://mast.hpc.social/about" target="_blank">details here</a>

The policy documents linked here are served from <a href="https://github.com/hpc-social/mastodon-policies" target="_blank">hpc-social/mastodon-policies</a> on GitHub. You can ask questions, or make contributions or suggestions for changes there.

<div id="server-policy" style="display:none"></div>

<br><br>

<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.4/jquery.min.js"></script>
<script src="{{ site.baseurl }}/assets/js/showdown.min.js"></script>

<script>
function getImages(string) {
  const imgRex = /<img.*?src="(.*?)"[^>]+>/g;
  const images = [];
    let img;
    while ((img = imgRex.exec(string))) {
     	images.push(img[1]);
    }
  return images;
}

function getLinks(string) {
  const imgRex = /href="(.*?)"/g;
  const links = [];
    let img;
    while ((img = imgRex.exec(string))) {
     	links.push(img[1]);
    }
  return links;
}

function basename(str) {
   var base = new String(str).substring(str.lastIndexOf('/') + 1); 
    if(base.lastIndexOf(".") != -1)       
        base = base.substring(0, base.lastIndexOf("."));
   return base;
}

$(document).ready(function(){

    url = "https://raw.githubusercontent.com/hpc-social/mastodon-policies/main/README.md"
    $.get(url, function(data) {
        var converter = new showdown.Converter({tables: true}),
                 html = converter.makeHtml(data);

        // Convert top level headings to next level for site
        html = html.replace("<h1 ", "<h2 ")

        // Find all relative markdown links and replace with pages
        var links = getLinks(html)        
        for (var i = 0; i < links.length; i++) {
            link = links[i];

            // Relative directory or markdown path (link to page)
            if (!link.startsWith("http") && !link.startsWith('mailto:')) {
                html = html.replace(link, "https://github.com/hpc-social/mastodon-policies/tree/main/" + link)
            }
        }

        // Relative images need to be replaced by a raw GitHub url
        // We will need to do this for other relative paths too
        var images = getImages(html)
        for (var i = 0; i < images.length; i++) {
            image = images[i];
            if (!image.startsWith("http")) {
                html = html.replace(image, "https://raw.githubusercontent.com/hpc-social/mastodon-policies/main/" + image);
            }            
        }
                
        $('#server-policy').html(html)
        $('#server-policy').show();
    });

});
</script>
