---
layout: page-small-header
title: Publications
permalink: /research/publications/
feature-img: "img/banner/banner_publications.jpg"
---
<!--feature-img: "img/publications4.jpg" oli enne selline pilt-->
<!-- permalink: /research/publications2/ -->

<!--Title-->
<div class="row">
  <div class="col col-md-10 offset-md-1">
    <h1 class="text-center mt-3">Publications</h1>
      <div class="divider-center mt-2 mb-2">
        <div class="divider-line-1"></div>
        <div class="divider-line-2"></div>
  </div>

<!--Navigation for years-->
<div class="row mt-4" style="height: initial;margin-bottom: 30px;">
{% for year in site.data.publications_conf.publication_years %}
<div class="col col-12 col-md-1 mt-3" style="height: initial;text-align: center;font-weight: 800;">
    <a onclick="showYear({{ year.year }})" style="cursor:pointer; color: #4b8d89;" class="pub pub-link-{{ year.year}}" >{{year.year}}</a>
  <script>var lastYear="{{ year.year }}"</script>
</div>  
{% endfor %}
</div> 
 
<!--Container for publications + year heading --> 
{% for hash in site.data.publications %}
{% assign pub = hash[1] %}
<div id="publications-{{pub.year}}" class="year-container" style="display:none;">
  <h2 class="mt-5 mb-4">{{pub.year}}</h2>
{% for publication in pub.publications %}
<div class="publication" class="mb-3 text-justify">
<!-- esialgne variant, autori nimest
<h4 class="d-inline" style="font-size: 16px;">{{publication.authors}}</h4>
-->
<p class="d-inline" style="font-size: 16px;"><strong>{{publication.authors}}</strong></p>
<p class="d-inline pl-1">{{publication.title}}</p>
</div>
{% endfor %}
</div>
{% endfor %}

<!--Show year function-->
<script>
  function showYear(year){
    hideYearElements();
    var id = "publications-"+year;
    var elem = document.getElementById(id);
    if(elem!==null){
      elem.style.display = 'block';
    }
     makeLinkActive(year);
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
 
    function makeLinkActive(year){ 

    var elems = document.getElementsByClassName('pub active');
    for (var i = 0; i < elems.length; i ++) {
        elems[i].classList.remove("active");
    }

    elems = document.getElementsByClassName('pub-link-' + year); 
    for (var i = 0; i < elems.length; i ++) {
        elems[i].classList.add("active");
    }
  }
</script>


