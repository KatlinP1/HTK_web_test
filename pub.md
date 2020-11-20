---
layout: page
title: Publications
permalink: /research/publications2/
feature-img: "img/sample_feature_img_3.png"
---
<p>
{% for year in site.data.publications_conf.publication_years %}
    <a onclick="showYear({{ year.year }})" style="cursor:pointer;">{{year.year}}</a>
  <script>var lastYear="{{ year.year }}"</script>
{% endfor %}
</p>
 
{% for hash in site.data.publications %}
{% assign pub = hash[1] %}
<div id="publications-{{pub.year}}" class="year-container" style="display:none;">
  <h2>{{pub.year}}</h2>

{% for publication in pub.publications %}
<div class="publication">

<h4>{{publication.authors}}</h4>
<p>{{publication.title}}</p>
</div>
{% endfor %}
</div>
{% endfor %}

<script>
  function showYear(year){
    hideYearElements();
    var id = "publications-"+year;
    var elem = document.getElementById(id);
    if(elem!==null){7
      elem.style.display = 'block';
    }
  }
  function hideYearElements(){
    var elems = document.getElementsByClassName('year-container');

    for (var i = 0; i < elems.length; i ++) {
        elems[i].style.display = 'none';
    }
  }
  
  (function() {
  
  if(typeof lastYear!==undefined && isNaN(lastYear)===false){
    showYear(lastYear);
  }

  })();
</script>
