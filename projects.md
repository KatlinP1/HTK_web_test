---
layout: page
title: Projects
permalink: /research/projects/
feature-img: "img/sample_feature_img_3.png"
---
<div class="projects_nav">
{% for project in site.data.projects %}
{% assign project_topic = project[1] %}
    <a onclick="showProject('{{ project_topic.topic_id }}')" style="cursor:pointer;">{{project_topic.topic}}</a>
{% endfor %}
</div>

<div class="container">
  <div class="row">
    {% for hash in site.data.projects %}
    {% assign project_sub = hash[1] %}
    {% for project in project_sub.projects %}
<div class="col-md-6 project-container topic-{{project_sub.topic_id}} , project_info">
    <div class="row">
        <div class="col-md-6 project_short_desc" >
        <h5 href="">{{project.title}}</h5>
        <p>{{project.period}}</p>
        <p>{{project.program}}</p> 
        <p>{{project.members}}</p>
        </div>
        <div class="col-md-6">
            <img src="{{project.image}}">
        </div>
    </div>
</div>
    {% endfor %}
    {% endfor %}
</div>

<script>
  function showProject(topic_id){
    hideProjectElements();
    var classElem = "topic-"+topic_id;

    var elems = document.getElementsByClassName(classElem);

    for (var i = 0; i < elems.length; i ++) {
        elems[i].style.display = 'block';
    }
  }
  function hideProjectElements(){
    var elems = document.getElementsByClassName('project-container');

    for (var i = 0; i < elems.length; i ++) {
        elems[i].style.display = 'none';
    }
  }
  
</script>