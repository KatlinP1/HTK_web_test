---
layout: page
title: Blog
permalink: /blog/
feature-img: "img/sample_feature_img_3.png"
---
<div class="blogs_nav projects_nav">
{% for blog in site.data.blogs %}
{% assign blog_topic = blog[1] %}
    <a onclick="showBlog('{{ blog_topic.topic_id }}')" style="cursor:pointer;">{{blog_topic.topic}}</a>
{% endfor %}
</div>

<div class="container">
  <div class="row">
    {% for hash in site.data.blogs %}
    {% assign blog_sub = hash[1] %}
    {% for blog in blog_sub.blogs %}
<div class="col-md-6 blog-container topic-{{blog_sub.topic_id}} project_info">
    <div class="row">
        <div class="col-md-6   project_short_desc">
            <h5> <a href="{{blog.url}}">{{blog.title}} </a></h5>
            <p>{{blog.date}}</p>
            <p>{{blog.author}}</p>
        </div>
        <div class="col-md-6">
        {% if blog.image %} 
            <img src= {% if blog.image contains "://" %} 
            "{{blog.image}}"
            {% else %}
            "{{ site.baseurl }}/{{blog.image}}" 
            {% endif %}>
        {% endif %}
        </div>
    </div>
</div>
    {% endfor %}
    {% endfor %}
</div>

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