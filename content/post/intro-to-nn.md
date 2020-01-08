---
title: "Non-linear Classification"
date: 2019-03-12T01:52:44-05:00
draft: false
tags: ["Neural Network", "Classification", "AI"]
categories: ["Projects"]
author: "Yizhou Mao"
comment: true
toc: false
# contentCopyright: '<a href="https://maoyizhou.com" rel="noopener" target="_blank">See origin</a>'
---

---

> Source Code: https://github.com/uohziyoam/Intro-to-NN

### Problem Definition

#### In this context, it requires us to generate a non-linear classification by utilizing neural network to fit in our model.

---

### Experiments

#### In my experiments, I followed the instruction about data method by using 5-fold round robin cross-validation. The data were didvided into five sets, and choose four of them as training set and rest of them as testing set. The program repeatedtly train the model five times with randomly choosed set from original 2000 data points.

#### The trainning model can successfully predict result with 99.2% accuracy. To evaluate the performance of the model, the program generate a confusion matrix to show how well the model predict positive while the ground truth is true, and conversly predict negative as the ground truth is false.

---

### Results

#### In this context, it requires us to generate a non-linear classification by utilizing neural network to fit in our model.

| Before                                                    |                           After                           |                                                 Before | After                                                  |
| :-------------------------------------------------------- | :-------------------------------------------------------: | -----------------------------------------------------: | :----------------------------------------------------- |
| ![Local Picture](/img/intro-to-nn/NonLinearResult/b1.png) | ![Local Picture](/img/intro-to-nn/NonLinearResult/a1.png) | ![Local Picture](/img/intro-to-nn/LinearResult/b1.png) | ![Local Picture](/img/intro-to-nn/LinearResult/a1.png) |
| ![Local Picture](/img/intro-to-nn/NonLinearResult/b2.png) | ![Local Picture](/img/intro-to-nn/NonLinearResult/a2.png) | ![Local Picture](/img/intro-to-nn/LinearResult/b2.png) | ![Local Picture](/img/intro-to-nn/LinearResult/a2.png) |
| ![Local Picture](/img/intro-to-nn/NonLinearResult/b3.png) | ![Local Picture](/img/intro-to-nn/NonLinearResult/a3.png) | ![Local Picture](/img/intro-to-nn/LinearResult/b3.png) | ![Local Picture](/img/intro-to-nn/LinearResult/a3.png) |
| ![Local Picture](/img/intro-to-nn/NonLinearResult/b4.png) | ![Local Picture](/img/intro-to-nn/NonLinearResult/a4.png) | ![Local Picture](/img/intro-to-nn/LinearResult/b4.png) | ![Local Picture](/img/intro-to-nn/LinearResult/a4.png) |

---

### Discussion

_**1. Why is 5-fold round robin cross-validation useful in machine learning?**_

#### Cross-validation is primarily used in applied machine learning to estimate the skill of a machine learning model on unseen data. That is, to use a limited sample in order to estimate how the model is expected to perform in general when used to make predictions on data not used during the training of the model.

_**2. What effect does the learning rate have on how your neural network is trained?**_

#### From the comparison among three choices of learning rates, the figures below clearly describe what happened to the predictions while training the model. The appropriate learning rate is essential to the training of model. A small leanring rate is very accurate because it slowly approaches the minimum of the derivative of loss to weight; however, it is not so efficient while choosing such small learning rate. On the other hand, a larger learning rate is more sufficient but it may always miss the minimum of the derivative of loss forever (e.g. the third figure below).

| Learning Rate: 0.001                                   |                  Learning Rate: 0.005                  |                                     Learning Rate: 1 |
| :----------------------------------------------------- | :----------------------------------------------------: | ---------------------------------------------------: |
| ![Local Picture](/img/intro-to-nn/LearningRate001.png) | ![Local Picture](/img/intro-to-nn/LearningRate005.png) | ![Local Picture](/img/intro-to-nn/LearningRate1.png) |

<!-- | Learning Rate: 0.001 | Learning Rate: 0.005 | Learning Rate: 1 |
| :------------------- | :------------------: | ---------------: |
|                      |                      |                  | -->

_**3. What is overfitting and why does it occur in practice? Name and briefly explain 3 ways to reduce overfitting.**_

#### Overfitting is the situation that a model seemly fit every data points, but it actually misses the most important information --- pattern in the reality. Three ways to reduce overfitting: 1. Regularization 2. Remove additional features 3. Stop training process earlier.

_**4. How does L2 regularization prevent overfitting? How differently does your model perform before and after implementing L2 regularization?**_

#### In the machine learning practice, we usually want to fit our model as accurately as possible. However, sometimes the model did fit all the data points but also the noise points in the dataset. L2 regularization can prevent overfitting by adding a penalty for an extreme parameter values in the system. L2 regularization reduces the magnitude of coefficients evenly.

#### From the figures show below, the slightly difference between them is the fit of the model. After L2 Regularization, the model looks more smoothly which means it avoid overfitting to certain extent. However, the figure of training without L2 Regularization looks more complex which fit every data points; It is very accurate for the datasets we have, but it is not optimal for our prediction in real world.

---

<!-- {{< youtube MqQb1aAtqdo >}} -->

<!-- $$ evidence\_{i}=\sum\_{j}W\_{ij}x\_{j}+b\_{i} $$ -->

```python
def sigmoid(z):
    ### sigmoid
    return 1 / (1 + np.exp(-z))

def sigmoidDerivative(a):
    ### sigmoid derivative
    return np.multiply(a, (1-a))

def hypertan(z):
    ### hypertan
    return np.tanh(z)

def hypertanDerivative(a):
    ### hypertan derivative
    return np.ones(np.shape(a)) - a**2
```

### Bibliography

#### 1. "Xiaojun Wu." PCA·Standford Machine Learning, 13 Jan.2019, https://yoyoyohamapi.gitbooks.io/, (accessed 03 Mar.2019).

#### 2. “Overfitting in Machine Learning: What It Is and How to Prevent It.” EliteDataScience, 25 Jan. 2019, https://elitedatascience.com/overfitting-in-machine-learning#how-to-prevent, (accessed 02 Mar.2019).

#### 3. Bronshtein, Adi. “Train/Test Split and Cross Validation in Python – Towards Data Science.” Towards Data Science, Towards Data Science, 17 May 2017, https://towardsdatascience.com/train-test-split-and-cross-validation-in-python-80b61beca4b6, (accessed 02 Mar.2019).
