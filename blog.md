---
layout: page-small-header
title: Blog
permalink: /blog/
feature-img: "img/code-bg.jpg"
---
<!--Title + blog navigation-->
<div class="container">
    <div class="row">
        <div class="col">
            <h1 class="text-center mt-3">Blog</h1>
            <div class="divider-center mt-2 mb-2">
                <div class="divider-line-1"></div>
                <div class="divider-line-2"></div>
            </div>
            <!--Blog navigation-->
            <div class="mt-5">
            <div class="row" style="height: initial;margin-bottom: 30px;">
            {% for blog in site.data.blogs %}
            {% assign blog_topic = blog[1] %}     
                <div class="col col-12 col-md-2 mt-3" 
                    style="height: initial;text-align: center;font-weight: 800; cursor:pointer;">
                    <a onclick="showBlog('{{ blog_topic.topic_id }}')" 
                        style="color: #4b8d89;">{{blog_topic.topic}}</a>
                </div>
            {% endfor %} 
            </div>   
            </div>
        </div>
    </div>
</div>

<!--Blog boxes-->
<div class="projects-horizontal">
    <div class="container">
        <div class="row projects">
        {% for hash in site.data.blogs %}
        {% assign blog_sub = hash[1] %}
        {% for blog in blog_sub.blogs %}
            <div class="col-sm-6 item blog-container topic-{{blog_sub.topic_id}}">
                <div class="row">
                    <div class="col-md-12 col-lg-5">
                    <a href="#">{% if blog.image %} 
                        <img class="img-fluid" src={% if blog.image contains "://" %} 
                        "{{blog.image}}"
                        {% else %}
                        "{{ site.baseurl }}/{{blog.image}}" 
                        {% endif %}>
                        {% endif %}
                    </a>
                    </div>
                    <div class="col">
                        <h3 class="name" style="color: #4b8d89;"><a href="{{blog.url}}" style="color: #4b8d89;">{{blog.title}}</a></h3>
                        <p style="margin-top: 5px;margin-bottom: 5px;">{{blog.date}}</p>
                        <p style="margin-top: 5px;margin-bottom: 5px;">{{blog.author}}</p>
                    </div>
                    </div>
                </div>
        {% endfor %}
        {% endfor %}
        </div>
    </div>
</div>
<div></div>    

<script>
function showBlog(id) {
    hideBlogElemet();
    id = "topic-"+id;
    var element = document.getElementsByClassName(id);
    console.log(element);
    for (var i = 0; i<element.length; i++){
        element[i].style.display='block';
    }
}
function hideBlogElemet(){
    var elements = document.getElementsByClassName('blog-container');

    for (var i = 0; i<elements.length; i++){
        elements[i].style.display='none';
    }
}
</script>