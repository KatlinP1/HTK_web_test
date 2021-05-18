---
layout: page-small-header
title: People
permalink: /people/
feature-img: "img/posts/jtel2016.png"
---
<!--Heading + navigation-->
<div class="row">
    <div class="col">
        <h1 class="text-center mt-3">People</h1>
        <div class="divider-center mt-2 mb-2">
        <div class="divider-line-1"></div>
        <div class="divider-line-2"></div>
    </div>
<!--Nav. menu for people-->    
    <div class="mt-5">
        <div class="row" style="height: initial;margin-bottom: 30px;">
            <div class="col col-12 col-md-3 mt-1" style="height: initial;text-align: center;font-weight: 800;"><a href="#admin" style="color: #4b8d89;">Administrative</a></div>
            <div class="col col-12 col-md-3 mt-1" style="height: initial;text-align: center;font-weight: 800;"><a href="#research" style="color: #4b8d89;">Research</a></div>
            <div class="col col-12 col-md-3 mt-1" style="height: initial;text-align: center;font-weight: 800;"><a href="#support" style="color: #4b8d89;">Research support and dev staff</a></div>
        </div>
    </div>
</div>
</div>

<!-- People information box-->  
<!-- Title row -->     
<div class="row">
      {% for hash in site.data.peoples %}
      {% assign people_sub = hash[1] %} 
      <div class="col-12 mt-3 pb-3">
        <h2 id="{{people_sub.topic_id}}">{{people_sub.topic}}</h2>
    </div>
      {% for people in people_sub.peoples %}
<!--People info box   class inimeste kastil class="col-md-4 mt-4"-->
    <div class="col-6 offset-3 offset-sm-1 offset-md-0 col-md-4 mt-4" style="height: 395px;"> 
    <a {% if people.etis %}  href="{{people.etis}}" target="_blank" {% endif %}>
    <div class="rounded mt-3 mb-3 picture-style" style="background-image: url({{people.image}})"></div>
    </a>
        <h5><strong>{{people.name}}</strong></h5>
        <p class="title pt-1 pb-1" style="margin: 0px;">{{people.worktitle}}</p>
        <p class="pt-0 pb-1" style="margin: 0px;">{{people.email}}</p>
        {% if people.phone %} 
        <p class="pt-0 pb-1" style="margin: 0px;">{{people.phone}}</p>
        {% endif %}
        {% if people.etis %} 
        <a class="pt-0 pb-2 mb-3" href="{{people.etis}}" target="_blank">Link ETIS<br></a>
        {% else %}
        <p class="pt-0 pb-2 mb-4"> </p>
        {% endif %}
    </div>
    {% endfor %}
    {% endfor %}
    
<!-- esialgne pildi lahendus 
<a {% if people.etis %}  href="{{people.etis}}" target="_blank" {% endif %}>
    <img class="rounded mt-3 mb-3" src="{{people.image}}" width="150px" height="150px">
</a>
-->

<!-- UUS PILDI LAHENDUS
<div class="rounded mt-3 mb-3" style="picture-style background-image: url({{people.image}})"></div>

stiili kirjeldus 
width: 150px;
    height: 150px;
    background-image: url(/img/people/Triinu_Jesmin.jpeg);
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;

-->