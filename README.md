# twopiece: Two Piece Distributions

- **Homepage:** https://github.com/quantgirluk/twopiece
- **Free software:** MIT license

### Overview

The **twopiece** library provides a Python implementation of the family of Two Piece distributions.

The family of univariate two–piece distributions is a family of univariate three-parameter location-scale models, where skewness is introduced by differing scale parameters either side of the location.


**Definition.** Let <img src="/tex/4ca7071da574c80015a95feaaac0db88.svg?invert_in_darkmode&sanitize=true" align=middle width=82.9221657pt height=22.831056599999986pt/> be a unimodal symmetric (about 0) probability density function (pdf) from the [location-scale family](https://en.wikipedia.org/wiki/Location%E2%80%93scale_family), possibly including a shape parameter <img src="/tex/38f1e2a089e53d5c990a82f284948953.svg?invert_in_darkmode&sanitize=true" align=middle width=7.928075099999989pt height=22.831056599999986pt/>. Then, the pdf of a member of the two-piece family of distributions is given by

<p align="center"><img src="/tex/9ca96c940649a631c3b13f49eea29620.svg?invert_in_darkmode&sanitize=true" align=middle width=373.54424249999994pt height=78.90491235pt/></p>

**Example** If <img src="/tex/190083ef7a1625fbc75f243cffb9c96d.svg?invert_in_darkmode&sanitize=true" align=middle width=9.81741584999999pt height=22.831056599999986pt/> corresponds to the normal pdf, then <img src="/tex/6f9bad7347b91ceebebd3ad7e6f6f2d1.svg?invert_in_darkmode&sanitize=true" align=middle width=7.7054801999999905pt height=14.15524440000002pt/> corresponds to the pdf of the Two-Piece Normal distribution as proposed by [Gustav Fechner](https://en.wikipedia.org/wiki/Gustav_Fechner).

For details on this family of distributions we refer to
[Inference in Two-Piece Location-Scale Models with Jeffreys Priors](https://projecteuclid.org/euclid.ba/1393251764)
published in Bayesian Anal.
Volume 9, Number 1 (2014), 1-22 and the references therein.


### Supported Distributions
Implementation is provided for the following distributions

#### Three Parameters

- two-piece normal [[+ info]](https://en.wikipedia.org/wiki/Split_normal_distribution)
- two-piece Laplace
- two-piece Cauchy
- two-piece logistic

#### Four Parameters

- two-piece t
- two-piece exponential power


### Main Features
We provide the following functionality:

- probability density function ***pdf***
- cumulative distribution function ***cdf***
- quantile function ***ppf***
- random generation ***random_sample***

for all the supported distributions.


### Quick Start

To illustrate usage of the features for the 3 and 4 parameters distributions we will use
the two-piece normal, and two-piece t, respectively. The behaviour is analogous for the rest of the supported distributions.

``` python
from twopiece.single import *
```


#### 1. Create a twopiece instance
To create an instance we need to specify either 3 or 4 parameters:

For the **two-piece normal** we require:

- *loc*: which is the location parameter
- *sigma1*, *sigma2* : which are both scale parameters

```python
loc=0.0
sigma1=1.0
sigma2=1.0
dist = tpnorm(loc=loc, sigma1=sigma1, sigma2=sigma2)
```

For the **two-piece t** we require:

- *loc*: which is the location parameter
- *sigma1*, *sigma2* : which are both scale parameters
- *shape* : which defines the degrees of freedom for the t-Student distribution

```python
loc=0.0
sigma1=1.0
sigma2=1.0
shape=3.0
dist = tpstudent(loc=loc, sigma1=sigma1, sigma2=sigma2, shape=shape)
```

Hereafter we assume that there is a twopiece instance called *dist*.

#### 2. Evaluate and visualise the probability density function (pdf)
We can evaluate the pdf on a single point or an array type object

```python
dist.pdf(0)
```

```python
dist.pdf([0.0,0.25,0.5])
```

To visualise the pdf use
```python
x = arange(-12, 12, 0.1)
y = dist.pdf(x)
plt.plot(x, y)
plt.show()
```

#### 3. Evaluate the cumulative distribution function (cdf)
We can evaluate the cdf on a single point or an array type object
```python
dist.cdf(0)
```

```python
dist.cdf([0.0,0.25,0.5])
```

To visualise the cdf use

```python
x = arange(-12, 12, 0.1)
y = dist.cdf(x)
plt.plot(x, y)
plt.show()
```

#### 4. Evaluate the quantile function (ppf)
We can evaluate the ppf on a single point or an array type object. Note that the ppf has support on [0,1].
```python
dist.ppf(0.95)
```

```python
dist.ppf([0.5, 0.9, 0.95])
```

To visualise the ppf use
```python
x = arange(0.001, 0.999, 0.01)
y = dist.ppf(x)
plt.plot(x, y)
plt.show()
```

#### 5. Generate a random sample

To generate a random sample we require:
- *size*: which is simply the size of the sample

```python
sample = dist.random_sample(size = 100)
```

### Install

#### Requirements

**twopiece** has been developed and tested on [Python 3.6, and 3.7](https://www.python.org/downloads/)
