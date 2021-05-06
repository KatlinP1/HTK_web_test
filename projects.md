---
layout: page-small-header
title: Projects
permalink: /research/projects/
feature-img: "img/banner/new_projects.jpg"
---
<!-- feature-img: "img/banner/banner_projects.jpg" -->
<!-- feature-img: "img/Kaanefoto4.jpg" enne oli see -->
<!--Title + Project navigation -->
<div class="row">
  <div class="col">
    <h1 class="text-center mt-3">Projects</h1>
      <div class="divider-center mt-2 mb-2">
            <div class="divider-line-1"></div>
            <div class="divider-line-2"></div>
      </div>
      <div class="mt-5">
          <div class="row" style="height: initial;margin-bottom: 30px;">
          {% assign sorted = site.data.projects | sort: topic_id %}
          {% for project in sorted %}
          {% assign project_topic = project[1] %}
            <div class="col col-12 col-md-2 mt-3" style="height: initial;text-align: center;font-weight: 800">
            <a onclick="showProject('{{ project_topic.topic_id }}')" id="topic-a-{{ project_topic.topic_id }}" class="project-link" style="color: #4b8d89; cursor:pointer;">{{project_topic.topic}}</a>
            </div>
          {% endfor %}  
          </div>
      </div>
  </div>
</div>
    
<!--Projects content-->
<div class="projects-horizontal">
  <div class="container">
    <div class="row projects">
      {% for hash in site.data.projects %}
      {% assign project_sub = hash[1] %}
      {% for project in project_sub.projects %}
          <div class="col-sm-6 item project-container topic-{{project_sub.topic_id}}">
            <div class="row">
                <div class="col-md-12 col-lg-5">
                {% if project.url %}
                    <a href="{{project.url}}">{% if project.image %} 
                      <img class="img-fluid" src={% if project.image contains "://" %} 
                      "{{project.image}}"
                      {% else %}
                      "{{ site.baseurl }}/{{project.image}}" 
                      {% endif %}>
                      {% endif %}
                    </a> 
                {% else %}
                  {% if project.image %} 
                    <img class="img-fluid" src={% if project.image contains "://" %} 
                      "{{project.image}}"
                      {% else %}
                      "{{ site.baseurl }}/{{project.image}}" 
                      {% endif %}>
                {% endif %}
                {% endif %}
                </div>
                <div class="col">
                  <h3 class="name" style="color: #4b8d89; margin-top: -2px;">
                  {% if project.url %} 
                    <a href="{{project.url}}" style="color: #4b8d89;">{{project.title}}</a>
                  {% else %}
                    {{project.title}}
                  {% endif %}  
                  </h3>
                  <p style="margin-top: 5px;margin-bottom: 5px;">{{project.period}}</p>
                  <p style="margin-top: 5px;margin-bottom: 5px;">{{project.program}}</p>
                  <p style="margin-top: 5px;margin-bottom: 5px;">{{project.members}}</p>
                </div>
            </div>
          </div>
      {% endfor %}
      {% endfor %}
    </div>
  </div>
</div>

<!--Function to show projects-->
<script>
  function showProject(topic_id){
    hideProjectElements();
    makeLinkActive(topic_id); 
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

//title color
  function makeLinkActive(topicId){ 

    var elems = document.getElementsByClassName('project-link active');
    for (var i = 0; i < elems.length; i ++) {
        elems[i].classList.remove("active");
    }

    var elem = document.getElementById("topic-a-"+topicId);
    elem.classList.add("active");
  }

</script>
