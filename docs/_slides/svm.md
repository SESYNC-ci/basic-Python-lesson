---
---

## Classification

The CBP dataset provides economic attributes of the three thousand and
some US counties. The employment numbers are continuous attributes, and
we expect those are somehow different between urban and rural counties.

We need a classifier suitable for:

1. many continuous "predictors"
1. a binary "response"

===

Continuous attributes paried with a binary class, which we hope to
predict given a model and a set of training data, could be a problem
for logistic regression. An alternative method, and a foundation of
machine learning, is the Support Vector Machine.

![]({{ site.baseurl }}/images/Kernel_Machine.svg){:width="60%"}  
*[Image][kernel_machine] by Alisneaky / [CC BY-SA]*
{:.captioned}

[kernel_machine]: https://commons.wikimedia.org/w/index.php?curid=47868867
[CC BY-SA]: https://creativecommons.org/licenses/by-sa/4.0

The name arises from the main optimization task: choosing a subset of
the training data attributes to be the "support vectors" (vector is
another way of referring to a point in attribute space). The support
vectors sit near ("support") a barrier that more or less divides
attribute space into regions dominated by a single class. The points
sitting on the dashed lines above are the support vectors.
{:.notes}

===

The USDA ERS classifies the counties of the US with a set of 9
[Rural-Urban Continuum Codes]. Joining these to the CBP attributes,
and creating a binary "Metropolitan" class based on the the codes for
urban-influenced areas, completes our dataset.


~~~python
rural_urban = pd.read_csv(
    'data/ruralurbancodes2013.csv',
    dtype={'FIPS':'str'},
    ).set_index('FIPS')
rural_urban['Metro'] = rural_urban['RUCC_2013'] < 4
~~~
{:.text-document title="{{ site.handouts[0] }}"}



[Rural-Urban Continuum Codes]: https://www.ers.usda.gov/data-products/rural-urban-continuum-codes/

===

By default, the join will take place on the index, which serves as a
primary key, for each table. It is a one-to-one join.


~~~python
income_rural_urban = income.join(
    rural_urban['Metro'],
    how='inner',
    )
~~~
{:.text-document title="{{ site.handouts[0] }}"}



Only the single variable "Metro" is taken from the `rural_urban` table for use
in the classification problem.
{:.notes}

===

Model evaluation for SVMs and other machine learning methods lacking a
probabilistic interpretion is based on subsetting data into "training"
and "validation" sets.


~~~python
import numpy as np

train = income_rural_urban.sample(
    frac=0.5,
    random_state = np.random.seed(345))
~~~
{:.text-document title="{{ site.handouts[0] }}"}



===

Import the learning machine from `sklearn`, and pass the training data
separately as the attributes (as `X` below) and class (as `y`).


~~~python
from sklearn import svm
ml = svm.LinearSVC()

X = train.drop('Metro', axis=1).values[:, :2]
X = np.log(1 + X)
y = train['Metro'].values.astype(int)

ml.fit(X, y)
~~~
{:.text-document title="{{ site.handouts[0] }}"}

~~~

LinearSVC(C=1.0, class_weight=None, dual=True, fit_intercept=True,
     intercept_scaling=1, loss='squared_hinge', max_iter=1000,
     multi_class='ovr', penalty='l2', random_state=None, tol=0.0001,
     verbose=0)
~~~
{:.output}



Why `np.log(1 + X)`? Remember, "whatever it takes" is the machine
learning mantra. In this case the high skew of the employment numbers
had attributes widely dispersed in attribute space, and the fit was
worse (and harder to visualize). The offset with a positive number is
necessary to keep counties with 0 employees in a sector.
{:.notes}

===

## Classifier Evaluation

The "confusion matrix" shows the largest numbers are on the
diagonal---that is the number of metro and Non-metro data points
correctly separated by the chosen support vectors.


~~~python
from sklearn import metrics

metrics.confusion_matrix(y, ml.predict(X), (True, False))
~~~
{:.text-document title="{{ site.handouts[0] }}"}

~~~

array([[355, 238],
       [109, 869]])
~~~
{:.output}



===

A quick visualization using the [mlxtend](){:.pylib} package
shows the challeng of separating this attribute space!


~~~python
from mlxtend.plotting import plot_decision_regions

plot_decision_regions(X, y, clf=ml, legend=2)
~~~
{:.text-document title="{{ site.handouts[0] }}"}

~~~
<matplotlib.axes._subplots.AxesSubplot at 0x7f11c31b7320>
~~~
{:.output}

![plot of ../images/svm_figure6_1.png]({{ site.baseurl }}/images/svm_figure6_1.png)

===

## Kernel Method

The `LinearSVM` is rarely used in practice despite its speed---rare is
the case when a hyperplane cleanly separates the attributes. The more
general `SVC` machine accepts multiple `kernel` options that provide
great flexibility in the shape of the barrier (no longer a hyperplane).


~~~python
ml = svm.SVC(kernel = 'rbf', C=1, gamma='auto')
ml.fit(X, y)
~~~
{:.text-document title="{{ site.handouts[0] }}"}

~~~

SVC(C=1, cache_size=200, class_weight=None, coef0=0.0,
  decision_function_shape='ovr', degree=3, gamma='auto', kernel='rbf',
  max_iter=-1, probability=False, random_state=None, shrinking=True,
  tol=0.001, verbose=False)
~~~
{:.output}



===

The improvement in the confusion matrix is slight---we have not tuned
the `gamma` value, which is automatically chosen based on the size of
the dataset.


~~~python
metrics.confusion_matrix(y, ml.predict(X), (True, False))
~~~
{:.text-document title="{{ site.handouts[0] }}"}

~~~

array([[322, 271],
       [ 35, 943]])
~~~
{:.output}



===

More important is to understand the nature of the separation, which
can "wrap around" the attribute space as necessary.


~~~python
plot_decision_regions(X, y, clf=ml, legend=2)
~~~
{:.text-document title="{{ site.handouts[0] }}"}

~~~
<matplotlib.axes._subplots.AxesSubplot at 0x7f11d0d30828>
~~~
{:.output}

![plot of ../images/svm_figure9_1.png]({{ site.baseurl }}/images/svm_figure9_1.png)

<!--
https://www.ers.usda.gov/data-products/rural-urban-continuum-codes/
FIPS over 3K
RUCC_2013 1,2,3 Metro / 4-9 Nonmetro
-->
