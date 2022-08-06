---
layout: post
title:  "Option Pricing Theory"
date:   2012-01-03 12:00:00 -0600
categories: jekyll Wolfram Post
permalink: /:categories #tells to put the url of the categories.
#can also be /:categories/:day/:year/:month/:title.html
author: "JV"
---

<!--this block make a for loop for the hyperlinks of the posts in the static site. Also added the if statment that highlights in color orange the link of the post you are on-->
### Post Navigation Pane
{% for post in site.posts %}
<li> <a style="{% if page.url == post.url %} color:#CE534D;{% endif%}" href="{{ post.url }}"> {{post.title}}</a> </li>
{% endfor %} 
---


<!--Code for MathJax which renders the latex code into math notation, but it is not necesarry if the plugin jekyll-spaceship is installed -->
<script type="text/javascript" async src="//cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>


# Option Pricing Theory <Repository Name>
### Contents are subject to copyright.
    
## About  <Synopsis>

* Theory notebook. <Abstract>
* In the next link you will find the whole Mathematica notebook of the work presented. [Gitlab Repo](https://gitlab.com/z37/Option-Pricing-Theory.git).

### Project status And Requirements
    
![Status](https://img.shields.io/badge/Status-Active-green) <Status>
![Version](https://img.shields.io/static/v1?message=Wolfram_L.V12&style=plastic&logo=wolfram&labelColor=ffffff&color=de1709&logoWidth=40&logoColor=red&label=%20) <Version>

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

<h1 style="color:rgb(232,0,0)" id="blue-h"> Option Pricing Notes</h1>

<h4 style="color:rgb(232,0,0)" id="blue-h">Stocks:</h4>
* Issued by firms to finance operations.
* Represent ownership of the firm.
* Price known today, but not in the future.
* May or may not pay dividends.


<h4 style="color:rgb(232,0,0)" id="blue-h">Bond:</h4>

* Price known today.
* Future pay offs known at fixed dates.
* Otherwise, the price movement is random.
* Final payoff at maturity: face vale/nominal value/principal.
* Intermediate payoffs: coupons.
* Exposed to default/credit risk.


<h4 style="color:rgb(232,0,0)" id="blue-h">Derivatives (Basic Securities):</h4>
* Sell for a price/value/premium today.
* Future value derived from the value of underlying securities.
* Tared at exchanges - standardized contract, no credit risk.
* or, over-the-counter(OTC)- a network of dealers and institutions, can be non-standard, some credit risk.

<h4 style="color:rgb(232,0,0)" id="blue-h">Forward Contract:</h4>
* An agreement to buy (long) or sell (short) a given underlying asset S: 
* At predetermined future date T  (maturity).
* At a predetermined price F (forward price).
* F is chosen so that the contract has zero value today.

---

<h3 style="color:rgb(232,0,0)" id="blue-h">Call and Put options</h3>

<h4 style="color:rgb(232,0,0)" id="blue-h">Vanilla options:</h4>
* Call option: a right to buy the underlying.
* Put option: a right to sell the underlying.
* European option: the right can be exercised only at maturity.
* American option: can be exercised at any time before maturity.


<h4 style="color:rgb(232,0,0)" id="blue-h">Exotic options: </h4>
* Asian options: the payoff depends of the average underlying asset price.
* Lookback options: the payoff depends on the maximum r minimum of the underlying asset price.
* Barrier option: the payoff depends on whether the underlying crossed a barrier or not
* Basket options: the payoff depends on the value of several underlying assets.

---

<h3 style="color:rgb(232,0,0)" id="blue-h">Brownian motion process</h3>

<h4 style="color:rgb(232,0,0)" id="blue-h">History:</h4>
* Brown, 1800's.
* Bachelier, 1900.
* Einstein, 1905, 1906.
* Wiener, Levy 1920\.b4s, 30\.b4s.
* Ito, 1940\.b4s.
* Samuelson, 1960\.b4s.
* Merton, Black, Scholes, 1970\.b4s.



<!-- CSS internal styling-->
<style>
  
.li {
  list-style-type:square;
  color:Red;
  }
.span   {
  color: black;
  }
.h4    {
  color: rgb(232,0,0);
  }
</style>

<h4 class="h4 ">Short introduction to the Merton-Black-Scholes  model: </h4>

<ul>
<li class="li">
    <span class="span">
    Risk-free asset : \(B(t)=e^{rt}\)
    </span>
</li>
  
<li class="li">
    <span class="span">
     Stock has a log normal distribution: \(log S(t)=log S(0)+ (\mu-\frac{1}{2} \sigma^2) t+\sigma \sqrt{t}\ z(t)\)
    </span>
</li>
<li class="li">
    <span class="span">
     Where z (t) is a standard normal random variable. Thus,    \(S(t) = S(0)  e^{(\mu-\frac{1}{2} \sigma^2)t+\sigma \sqrt{t}\ z(t)}\)
    </span>
  </li>
  <li class="li">
    <span class="span">
        
     And it can be shown that: \(ES(t) = S(0)*e^{(\mu t)}\)
        and \( \frac{1}{2} Var [log \frac{S(t)}{S(0)}]=\sigma^{2}\)
    </span>
  </li>
 </ul>
  
To see the whole Mathematica notebook click on the Gitlab project site. 
