---
layout: post
title: Data Science PortFolio
date: 2022-01-01 10:00:00 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes.                   # Add post description (optional)
img: /data_science_post/data_science_post.jpg # Add image post (optional)
fig-caption: Waves         # Add figcaption (optional)
tags: [Data Science, Machine Learning, Python, Jupyter notebook]
---
This is the blog post for all the projects I have worked related to Data Science, Machine Learning. With programming tools, including python3, jupyter notebooks.

## Boston House data pricing
### Data description
* Origin: The origin of the boston housing data is Natural.
* Usage: This dataset may be used for Assessment.
* Number of Cases: The dataset contains a total of 506 cases.
* Order: The order of the cases is mysterious.
* Variables: There are 14 attributes in each case of the dataset. They are:
    * CRIM - per capita crime rate by town
    * ZN - proportion of residential land zoned for lots over 25,000 sq.ft.
    * INDUS - proportion of non-retail business acres per town.
    * CHAS - Charles River dummy variable (1 if tract bounds river; 0 otherwise)
    * NOX - nitric oxides concentration (parts per 10 million)
    * RM - average number of rooms per dwelling
    * AGE - proportion of owner-occupied units built prior to 1940
    * DIS - weighted distances to five Boston employment centres
    * RAD - index of accessibility to radial highways
    * TAX - full-value property-tax rate per $10,000
    * PTRATIO - pupil-teacher ratio by town
    * B - 1000(Bk - 0.63)^2 where Bk is the proportion of blacks by town
    * LSTAT - % lower status of the population
    * MEDV - Median value of owner-occupied homes in $1000's

## Code
To donwload the notebook, follow to my GitHub repository. 
The whole code and development was implemented with `python` and in `jupyter notebook`. 

### Importing libraries & First display

{% highlight python %}
import numpy as np  
import pandas as pd  
import matplotlib.pyplot as plt  
%matplotlib inline

# importamos las librerías y se leen los datos, asignando el header de 'Population', 'Profit'
df=pd.read_csv('Population.csv', names=['Population', 'Profit'])
df.head()
{% endhighlight %}




![I and My friends]({{site.baseurl}}/assets/img/mac.jpg)


>Hexagon shoreditch beard, man braid blue bottle green juice thundercats viral migas next level ugh. Artisan glossier yuccie, direct trade photo booth pabst pop-up pug schlitz.

Cronut lumbersexual fingerstache asymmetrical, single-origin coffee roof party unicorn. Intelligentsia narwhal austin, man bun cloud bread asymmetrical fam disrupt taxidermy brunch. Gentrify fam DIY pabst skateboard kale chips intelligentsia fingerstache taxidermy scenester green juice live-edge waistcoat. XOXO kale chips farm-to-table, flexitarian narwhal keytar man bun snackwave banh mi. Semiotics pickled taiyaki cliche cold-pressed. Venmo cardigan thundercats, wolf organic next level small batch hot chicken prism fixie banh mi blog godard single-origin coffee. Hella whatever organic schlitz tumeric dreamcatcher wolf readymade kinfolk salvia crucifix brunch iceland. Literally meditation four loko trust fund. Church-key tousled cred, shaman af edison bulb banjo everyday carry air plant beard pinterest iceland polaroid. Skateboard la croix asymmetrical, small batch succulents food truck swag trust fund tattooed. Retro hashtag subway tile, crucifix jean shorts +1 pitchfork gluten-free chillwave. Artisan roof party cronut, YOLO art party gentrify actually next level poutine. Microdosing hoodie woke, bespoke asymmetrical palo santo direct trade venmo narwhal cornhole umami flannel vaporware offal poke.

* Hexagon shoreditch beard
* Intelligentsia narwhal austin
* Literally meditation four
* Microdosing hoodie woke

Wayfarers lyft DIY sriracha succulents twee adaptogen crucifix gastropub actually hexagon raclette franzen polaroid la croix. Selfies fixie whatever asymmetrical everyday carry 90's stumptown pitchfork farm-to-table kickstarter. Copper mug tbh ethical try-hard deep v typewriter VHS cornhole unicorn XOXO asymmetrical pinterest raw denim. Skateboard small batch man bun polaroid neutra. Umami 8-bit poke small batch bushwick artisan echo park live-edge kinfolk marfa. Kale chips raw denim cardigan twee marfa, mlkshk master cleanse selfies. Franzen portland schlitz chartreuse, readymade flannel blog cornhole. Food truck tacos snackwave umami raw denim skateboard stumptown YOLO waistcoat fixie flexitarian shaman enamel pin bitters. Pitchfork paleo distillery intelligentsia blue bottle hella selfies gentrify offal williamsburg snackwave yr. Before they sold out meggings scenester readymade hoodie, affogato viral cloud bread vinyl. Thundercats man bun sriracha, neutra swag knausgaard jean shorts. Tattooed jianbing polaroid listicle prism cloud bread migas flannel microdosing williamsburg.

Echo park try-hard irony tbh vegan pok pok. Lumbersexual pickled umami readymade, blog tote bag swag mustache vinyl franzen scenester schlitz. Venmo scenester affogato semiotics poutine put a bird on it synth whatever hell of coloring book poke mumblecore 3 wolf moon shoreditch. Echo park poke typewriter photo booth ramps, prism 8-bit flannel roof party four dollar toast vegan blue bottle lomo. Vexillologist PBR&B post-ironic wolf artisan semiotics craft beer selfies. Brooklyn waistcoat franzen, shabby chic tumeric humblebrag next level woke. Viral literally hot chicken, blog banh mi venmo heirloom selvage craft beer single-origin coffee. Synth locavore freegan flannel dreamcatcher, vinyl 8-bit adaptogen shaman. Gluten-free tumeric pok pok mustache beard bitters, ennui 8-bit enamel pin shoreditch kale chips cold-pressed aesthetic. Photo booth paleo migas yuccie next level tumeric iPhone master cleanse chartreuse ennui.
