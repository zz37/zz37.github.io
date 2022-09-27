---
layout: post
title:  "Web Development Theory"
date:   2022-03-03 10:00:00 -0600
categories: jekyll Web Development Theory Post
img: /p_Html_css/intro.png # Add image post (optional)
permalink: /:categories #tells to put the url of the categories.
# can also be /:categories/:day/:year/:month/:title.html
author: "JV"
---

# Web Development Theory

<!--this block make a for loop for the hyperlinks of the posts in the static site. Also added the if statment that highlights in color orange the link of the post you are on-->
### Post Navigation Pane
{% for post in site.posts %}
<li> <a style="{% if page.url == post.url %} color:#CE534D;{% endif%}" href="{{ post.url }}"> {{post.title}}</a> </li>
{% endfor %}  
---

# HTML & Css Web Introduction 
* Contents are subject to copyright.

## About  
* Introduction Theory.

![Status](https://img.shields.io/badge/Status-Active-green) 
![HTML5](https://img.shields.io/static/v1?label=&message=HTML5&color=orange&style=flat&logo=HTML5&logoColor=orange&logoWidth=30&labelColor=black)
![CSS3](https://img.shields.io/static/v1?label=&message=CSS3&color=blue&style=flat&logo=CSS3&logoColor=blue&logoWidth=30&labelColor=white)


## Table of contents
1. Basic securities,
2. Call an Put options.
3. Brownian Motion Process. 
4. Stochastic Differential Equation.


## Contributing  <Reporting issues>
  <!--- If your README is long or you have some specific process or steps you want contributors to follow, consider creating a separate CONTRIBUTING.md file--->
Contribution is welcomed on component (or project if there is no component for that project).
To contribute to <project_name>, follow these steps:

1. Fork this repository.
2. Create a branch: `git checkout -b <branch_name>`.
3. Make your changes and commit them: `git commit -m '<commit_message>'`
4. Push to the original branch: `git push origin <project_name>/<location>`
5. Create the pull request.

## License
![Apache License, Version 2.0](https://img.shields.io/hexpm/l/plug?color=orange&label=License&style=flat-square)

---

### HTML & CSS

* HTML.- hypertext markup language.
* Represent the technology that boosts the web.
* HTML5 -> Core structure -> components and infrastructure.
* CSS3 -> Colors, styles.
* JavaScript JS -> Behavior, for dynamic content.
* Annotation contents.
* Definition of document structure.
* 3 Core languages for the web technologies.


### HTML tag
* Opening and closing tag, not always. <p> --- --- </p> “paragraph”.
* <p id= “my_id”> --- --- </p>
*  is ->  attribute name;  “ my_id” -> attribute value.
* No space between opening and closing brackets.
* Spaces are allowed before attribute.
* no content opening and cloning before attribute.

### HTML5 Basic Document Layout.
* <! doctype html> -> document type.
* <html> </html> -> tag.
* Is the html version declaration.
* Sequential from top to bottom rendering.

### HTML5 Content Model Layout.
* Elements to be nested and not.
* 2 categories 1) Block level elements. 2) Inline elements.
* Render to begin one a new line by default.
* May involve other inline elements.

---

### CSS3 Anatomy
* Associating rules with HTML elements.
* Selector -> p -> property
	            -> color: blue (value)
		  |-> declaration.
* Zero or more delcarations.

{% highlight css %}
p ->{ 1.- -.-.- 
  2.-
  3.- 
}
{% endhighlight %}

* Combine rules for stylesheet.
* Class selector

{% highlight css %}
 .blue {color:blue}  -> class blue
<p class: “blue”>  -> affected 
<p > … </p> -> unaffected
{% endhighlight %}

* id Selector, #name {color:blue}

{% highlight html %}
<div id: “name”>--- </div>
{% endhighlight %}

* Syntax selectors with commas.
* Syntax simple css selectors.
* Class (define with a . ).
* id (define with #).
* Class selector 

{% highlight css %}
p.big -> selector of class "big"
{% endhighlight %}

* Child selector, Descent selector, no limits on selectors.

{% highlight css %}
.colored p -> every p that is inside (any level) an element with class "colored"
{% endhighlight %}

* Combining Selectors.
* Element with class selecetor.
* Child (direct) selector.
* Descendent selector.

## Web Development Course Theory
* Web Development fundamentals.
* HTML5.
* CSS3.
* BootStrap 5.
* JavaScritp ES6(EcmaScript 6).
* DOM (Document Object Model).
* jQuery Framework.
* Unix Command Line.
* Git, GitHub, and version control.
* Node.JS, MVC(Model-View-Controller) Framework.
* Back-development.
* Express.js.
* Application Program Interface (APIs).
* EJS (Embedded JavaScript).
* Database Fundamentals.
* SQL Databases.
* NoSQL DB, with MongoDB and Mongoose.
* CRUD(create, read, update, delete).
* Deployment (GitHub, Heroku, Mongo Atlas).
* RERSTful APIs(GET, POST, PUT, PATCH, DELETE).



 
 
