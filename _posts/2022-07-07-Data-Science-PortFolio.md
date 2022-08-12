---
layout: post
title: Data Science PortFolio
date: 2022-07-07 10:00:00 -0600
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes.                   # Add post description (optional)
img: /DataS_post/Post_title.jpg # Add image post (optional)
fig-caption: Waves         # Add figcaption (optional)
tags: [Data Science, Machine Learning, Python, Jupyter notebook]
---
This is the blog post for all the projects I have worked related to Data Science, Machine Learning. With programming tools, including python3, jupyter notebooks.

# Boston House data pricing
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

### Code
To donwload the notebook, follow to my GitHub repository. 
The whole code and development was implemented with `python` and in `jupyter notebook`. 

### Importing libraries & First display

{% highlight python %}
# imposrt libraries and data reading
import numpy as np  
import pandas as pd  
import matplotlib.pyplot as plt  
%matplotlib inline

# asign headers to 'Population', 'Profit'
df=pd.read_csv('Population.csv', names=['Population', 'Profit'])
df.head()
{% endhighlight %}

<p align="center">
    <img src="{{site.baseurl}}/assets/img/DataS_post/BostonHouse/fig1.png" alt="drawing" style="width:500px;"/>
</p>

### Plotting Data (Exploratory data analysis)
Now we proceed to view the data, by doing a exploratory data analysis. By defining a function, for the scatter plot between the Population and Profit in units of $10,000s.

{% highlight python %}
def PlotData(x, y):  

    ''' This function makes the scatter plot from x,y data.
    @param : x and y data.
    With options of the size of figure, color, marker, plot and axes legends.
    Args:
        x: x data (Population of City in 10,000s)
        y: y data (Profit in $10,000s)
    Return: 
        scatter plot of y vs x '''
    plt.figure(figsize=(5, 4), dpi=78)
    plt.scatter(x,y,c='red',marker='x',alpha=0.5,label='training data')
    plt.xlabel('Population of City in 10,000s')
    plt.ylabel('Profit in $10,000s')
    plt.legend(loc='lower right')
    plt.grid()
    plt.show()

## ========== Part 2: Plotting =======================
# sending the columns 'Population', 'Profit', as x and y, from the data frame
PlotData(df.Population,df.Profit)
{% endhighlight %}

As a result of the code above, we can see that there is a tendency of the data towards a positive slope.

<p align="center">
    <img src="{{site.baseurl}}/assets/img/DataS_post/BostonHouse/fig2.png" alt="drawing" style="width:500px;"/>
</p>

### Cost Computation And Hypothesis
For the cost, the use of the correct cost function needs to be appropriate for correct interpetration of cost computation. In here the cost function used is the mean squared error.
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

<style>
    .li {list-style-type:square;
         color:Red; }
    .span{color: black; }
    .h4{color: rgb(232,0,0);}
</style>

<li class="li">
    <span class="span">
    Cost Function: \(J(\theta_{0},\theta_{1}) = \frac{1}{2n} \sum^{n}_{i=1} (h_{\theta (x^{i})} - y^{i})^{2}\)
    </span>
</li>

Which in other words we can stablish a hypothesis, the parameters that are goint to be used, the cost function and the goal of the minimization.

<h4 class="h4 ">Model attributes </h4>
<li class="li">
    <span class="span">
    Hypothesis Fit(linear function): \( f_{\theta} = \theta_{0} + \theta_{1} \cdot x \)
    </span>
</li>
<li class="li">
    <span class="span">
    Parameters used: \( theta_{0}, \theta_{1} \)
    </span>
</li>
<li class="li">
    <span class="span">
    Cost Function: \( J(\theta_{0},\theta_{1}) = \frac{1}{2n} \sum^{n}_{i=1} (h_{\theta (x^{i})} - y^{i})^{2} \)
    </span>
</li>
<li class="li">
    <span class="span">
    Goal:\(  \underset{\theta_{0}, \theta_{1}}{min} \ J(\theta_{0},\theta_{1}) \)
    </span>
</li>

But first we need to prepare data for the data ingestion to the model.

{% highlight python %}
# obtaining the number of features, which is 1, 'Population of City in 10,000s'
n = len(df.columns)-1 # subtract the target column

# Create a function to pepare the data.
def Prepare_Data(df, n):
    
    """
    Add 1s column, convert to matrices,
    initialize theta.
    Args:
        df: read the data file
        n: int
    Return:
        x: a m by n+1 matrix
        y: a m by 1 vector
        theta: a n+1 by 1 vector
    """
    # Adding one column of ones (1's) to the dataset, at start of the dataframe
    # Ones|Population|Profit
    #  1  |  ...     | ...
    df.insert(0, 'Ones', 1)

    # defining x y y, separating the dataset with iloc by its index
    # x selects all rows and cols from 0 to 2 (n+1) ->  Ones|Population
    # y selects all rwos and cols from 2 (n+1) to 3 (n+2) ->  Profit
    x = df.iloc[:, 0:n+1]
    y = df.iloc[:, n+1:n+2]
    
    # converts the matrices and initialize de parameters theta to 0s (zeros)
    # theta is a vector 2*1 (n+1*1) and its transpose is a vector of 1*2 (1*n+1)
    # where n is the number of freatures 
    x = np.asmatrix(x.values)
    y = np.asmatrix(y.values)
    theta = np.asmatrix(np.zeros((n+1, 1)))
    return x, y, theta

x,y,theta=Prepare_Data(df, n)
{% endhighlight %}

Initialize parameters for iterations and learning rate α.

{% highlight python %}
# alpha init
iterations = 1500
alpha = 0.01

# Check the dimensions of the matrices.
x.shape, y.shape, theta.shape
{% endhighlight %}

Which gives the next result. Meaning that the shape of the matrix x, y and theta.

{% highlight python %}
Out:= ((97, 2), (97, 1), (2, 1))
{% endhighlight %}

Let us now create the cost computation, implementation

{% highlight python %}
# Create a function to compute cost.
def ComputeCost(x, y, theta):
    """
    Compute the cost function.
    Args:
        x: a m by n+1 matrix
        y: a m by 1 vector
        theta: a n+1 by 1 vector
    Returns:
        cost: float
    """
    m = len(x) # cuantos datos hay
    J_cost =1/(2*m) *(np.sum(np.square((x * theta) - y))) 
    # here is the operation, with numpy matrix, making all the operations in one iteration
    # print(f"For theta {theta[0,0]:.2f} and {theta[1,0]:.2f}, the cost (J) is {J_cost:.2f}") # for more info uncomment
    return J_cost
ComputeCost(x, y, theta)
{% endhighlight %}

Having a return value of the whole value of J, for the base case.

{% highlight python %}
Out:= 32.072733877455676
{% endhighlight %}

Now we are ready to implement the gradient descent in order to iterate and get better fits every time the model learns.

{% highlight python %}
# Create a function to implement gradient descent.
def gradientDescent(x, theta, iterations):
    """
    Implement gradient descent.
    Args:
        x: a m by n+1 matrix
        theta: a n+1 by 1 vector
    Return:
        theta: a n+1 by 1 vector
        J_vals: a #iterations by 1 vector
    """
    m = len(x) # tamaño de los ejemplos de entrenamiento
    J_vals = [] # inicializar J como una lista
    
    for i in range(iterations):
        error = (x * theta) - y
        for j in range(len(theta)):
            theta.T[0, j] = theta.T[0, j] - (alpha/m) * np.sum(np.multiply(error, x[:, j]))
        J_vals.append(ComputeCost(x, y, theta))
    return (theta, J_vals)

theta, J_vals = gradientDescent(x, theta, iterations)
{% endhighlight %}

### Plotting Data and Fit
We are now ready how the model implementation worked and plot the fitted hypothesis in the scatter data. 

{% highlight python %}
theta_f = list(theta.flat)
xs = np.arange(5, 23)
ys = theta_f[0] + theta_f[1] * xs

plt.figure(figsize=(8, 5))
plt.xlabel('Population of City in 10,000s')
plt.ylabel('Profit in $10,000s')
plt.grid()
plt.plot(df.Population, df.Profit, 'rx', label=' Training Data')
plt.plot(xs, ys, 'b-', label='Linear Regression: h(x) = %0.2f + %0.2fx'%(theta[0], theta[1]))
plt.legend(loc=4)
{% endhighlight %}

Which can be seen in the figure below.

<p align="center">
    <img src="{{site.baseurl}}/assets/img/DataS_post/BostonHouse/fig3.png" alt="drawing" style="width:500px;"/>
</p>

### Obtaining Predicted Values
Testing the model and output predictions for an estimate of some test cases population.

{% highlight python %}
# Predict the profit for population of 35000 and 70000.
print((theta_f[0] + theta_f[1] * 3.5) * 10000)
print((theta_f[0] + theta_f[1] * 7) * 10000)
{% endhighlight %}

As can be seen the return output gives us an estimate of how much the price can increase in terms of the population fitted model.

{% highlight python %}
Out:= 4519.767867701772
      45342.45012944714
{% endhighlight %}

For more visualization on the how the cost function is minimized, and the plot of the estimate of the cost function J, for all of the iterations. 

{% highlight python %}
from mpl_toolkits.mplot3d import axes3d

# Create meshgrid.
xs = np.linspace(-10,10,100)
ys = np.linspace(4,-1,100)
xx, yy = np.meshgrid(xs, ys)

# Initialize J values to a matrix of 0's.
J_vals = np.zeros((xs.size, ys.size))

# Fill out J values.
for index, v in np.ndenumerate(J_vals):
    J_vals[index] = ComputeCost(x, y, [[xx[index]], [yy[index]]])

# Create a set of subplots.
fig = plt.figure(figsize=(16, 6))
ax1 = fig.add_subplot(121,projection='3d')
ax2 = fig.add_subplot(122)

# Create surface plot.
hh=ax1.plot_surface(xx,yy, J_vals, alpha=0.5, cmap='jet')
ax1.set_zlabel('Cost', fontsize=12,rotation=90)
ax1.set_title('Surface plot of cost function')
cbar = fig.colorbar(hh)

# Create contour plot.
ax2.contour(xx,yy, J_vals, np.logspace(-2, 3, 20), cmap='jet')
ax2.plot(theta_f[0], theta_f[1], 'rx')
ax2.set_title('Contour plot of cost function, showing minimum')

# Create labels for both plots.
for ax in fig.axes:
    ax.set_xlabel(r'$\theta_0$', fontsize=14)
    ax.set_ylabel(r'$\theta_1$', fontsize=14)

ax1.view_init( 20,-135)
{% endhighlight %}

Plotting the 3D cost funcition J and the contour plot of the vest minimization value of the fitted model.

<p align="center">
    <img src="{{site.baseurl}}/assets/img/DataS_post/BostonHouse/fig4.png" alt="drawing" style="width:500px;"/>
</p>
