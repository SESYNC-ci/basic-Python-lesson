---
---

## Lesson Objectives

- Earn your Python "learner's permit"
- Work with Pandas, the `DataFrame` package
- Recognize differences between R and Python
- Hit the *autubahn* with [Scikit-learn](){:.pylib}

===

## Specific Achievements

- Differentiate between data types and structures
- Learn to use indentation as syntax
- Import data and try a simple "split-apply-combine"
- Implement a SVM for binary classification

Why learn Python? While much of the academic research community has
dived into R for an open source toolbox for data science, there are
plenty of reasons to learn Python too. Some find they can learn to
write scripts more quickly in Python, others find its object
orientation a real boon. This lesson works towards a simple "machine
learning" problem, which has long been a speciality of Python's
[Scikit-learn](){:.pylib} package.
{:.notes}

===

## Machine Learning

Machine Learning is another take on regression (for continuous
response) and classification (for categorical response).

- Emphasis on prediction over parameter inference
- Equal emphasis on probabilistic and non-probabilistic methods: whatever works
- Not necessarilly "supervised" (e.g. clustering)

This lesson will step through a non-probabilistic classifier, because
it's at far end of the spectrum relative to generalized linear
regression. Some classification methods have probabilistic
interpretations: logistic regression is actually a classifier, whether
or not you follow through to choosing the most likely outcome or are
satisfied with estimating its probability. Others optimize the
classifier based on other abstract quantities: SVMs maximize the
distance between the "support vectors".
{:.notes}

===

## Jupyter

Sign into JupyterHub and open up `{{ site.handouts[0] }}`. This
worksheet is an Jupyter Notebook document: it is divided into "cells"
that are run independently but access the same Python interpreter. Use
the Notebook to write and annotate code.
{:.notes}

After opening `{{ site.handouts[0] }}`, right click anywhere in your
notebook and choose "Create Console for Notebook". Drag-and-drop the
tabs into whatever arrangement you like.
