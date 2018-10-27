# Agenda for 01 Meetup on 10/20
Slides: [Meetup 01 Presentation](https://docs.google.com/presentation/d/1VvWQjbIapmasHWp6tJeHh1bqGxmYtDLev97K2T8i7Ho/edit?usp=sharing)
* Introduction to School of AI - Angel
* Challenges of ML - Angel
* Regression VS Decision Tree - Rishov (Python) / Jamel (R) 
* Regularization/ Post analysis - Romand 
* Akaike information criterion (AIC)
* Stepwise Regression - Rishov
* Logistical Regression - Jamel (R) / Rishov (Python) 
* Sampling - Angel
* Principal Components Analysis
* AB Testing, Baysien Testing
* Data Scrapping

## Introduction to School of AI
[School of AI](https://www.youtube.com/watch?v=8yu8rtXThy8&t=6s)

## Challenges of ML
Source: “Hands-On Machine Learning with Scikit-Learn and TensorFlow by Aurélien Géron (O’Reilly). Copyright 2017 Aurélien Géron, 978-1-491-96229-9.

 In Machine Learning, the main task is to **select a learning algorithm and train it on some data**, the two things that can go wrong are **bad algorithm** and **bad data**.

## Bad Data
### Insufficient Quantity of Training Data
For a toddler to learn what an apple is, all it takes is for you to point to an apple and say “apple” (possibly repeating this procedure a few times). Now the child is able to recognize apples in all sorts of colors and shapes.

Machine Learning is not quite there yet. **It takes a lot of data for most Machine Learning algorithms to work properly**. Even for very simple problems you typically need thousands of examples, and for complex problems such as image or speech recognition you may need millions. 

> There is a trade off between spending money on algorithms vs getting extra training data*

### Non Representative Training Data
In order to generalize well, it is crucial that your training data be representative of the new cases you want to generalize to.

Adding **missing data significantly alters a model** and using a non-representative training set is **unlikely to make accurate prediction**. It is crucial to use a training set that is representative of the cases you want to generalize to. 

> This is often harder than it sounds: if the sample is too small, you will have *sampling noise* (i.e., nonrepresentative data as a result of chance), but even very large samples can be nonrepresentative if the sampling method is flawed. This is called *sampling bias*.

### Poor-Quality Data
Obviously, if your training data is full of **errors, outliers, and noise** (e.g., due to poor quality measurements), it will **make it harder for the system to detect the underlying patterns**, so your system is less likely to perform well.

> It is often well worth the effort to spend time cleaning up your training data. The truth is, most data scientists spend a significant part of their time doing just that. 

Solution:

* Discard or fix instances that are clearly outliers
* If some instances are missing a few features (e.g., 5% of your customers did not specify their age), you must decide whether you want to ignore this attribute altogether, ignore these instances, fill in the missing values (e.g., with the median age), or train one model with the feature and one model without it, and so on.

### Irrelevant Features
As the saying goes: **garbage in, garbage out**. Your system will only be capable of learning if the training data contains enough relevant features and not too many irrelevant ones. A critical part of the success of a Machine Learning project is coming up with a good set of features to train on. 

This process, called feature engineering, involves:

* *Feature selection*: **selecting the most useful features** to train on among existing features.

* *Feature extraction*: **combining existing features to produce a more useful one** (as we saw earlier, dimensionality reduction algorithms can help).
* Creating new features by gathering new data.

## Bad Algorithms
### Overfitting

Say you are visiting a foreign country and the taxi driver rips you off. You might be tempted to say that all taxi drivers in that country are thieves. Overgeneralizing is something that we humans do all too often, and unfortunately machines can fall into the same trap if we are not careful. In Machine Learning this is called **overfitting**.

> Overfitting means that the model performs well on the training data, but it does not generalize well.

Overfitting happens when the model is too complex relative to the amount and noisiness of the training data. The possible solutions are:

1. Simplify the model 

> This can me done by selecting a model with fewer parameters, by reducing the number of attributes in the training data or by constraining the model

2. To gather more training data
3. To reduce the noise in the training data (e.g., fix data errors and remove outliers)

Constraining a model to make it simpler and reduce the risk of overfitting is called **regularization**

### Underfitting
As you might guess, underfitting is the opposite of overfitting: it occurs when your model is too simple to learn the underlying structure of the data. 

The main options to fix this problem are:

* Selecting a more powerful model, with more parameters
* Feeding better features to the learning algorithm (feature engineering)
* Reducing the constraints on the model (e.g., reducing the regularization hyper-parameter)

# Testing and Validating
The only way to know how well a model will generalize to new cases is to actually try it out on new cases. 

One way to do this is to split your data into two sets: **the training set and the test set**. 

The error rate on new cases is called the **generalization error** (or out-of-sample error), and by evaluating your model on the test set, you get an estimation of this error. 

This value tells you how well your model will perform on instances it has never seen before.

> If the training error is low (i.e., your model makes few mistakes on the training set) but the generalization error is high, it means that your model is overfitting the training data. It is common to use 80% of the data for training and hold out 20% for testing.

So evaluating a model is simple enough: just use a test set. Now suppose you are hesitating between two models (say a linear model and a polynomial model): how can you decide? One option is to train both and compare how well they generalize using the test set.

## For the More Curious

Suppose that the linear model generalizes better, but you want to apply some regularization to avoid overfitting. The question is: how do you choose the value of the regularization hyperparameter? One option is to train 100 different models using 100 different values for this hyperparameter. Suppose you find the best hyperparameter value that produces a model with the lowest generalization error, say just 5% error.
So you launch this model into production, but unfortunately it does not perform as well as expected and produces 15% errors. What just happened?
The problem is that you measured the generalization error multiple times on the test set, and you adapted the model and hyperparameters to produce the best model for that set. This means that the model is unlikely to perform as well on new data.
A common solution to this problem is to have a second holdout set called the validation set. You train multiple models with various hyperparameters using the training set, you select the model and hyperparameters that perform best on the validation set, and when you’re happy with your model you run a single final test against the test set to get an estimate of the generalization error.
To avoid “wasting” too much training data in validation sets, a common technique is to use cross-validation: the training set is split into complementary subsets, and each model is trained against a different combination of these subsets and validated against the remaining parts. Once the model type and hyperparameters have been selected, a final model is trained using these hyperparameters on the full training set, and the generalized error is measured on the test set.

## Regression VS Decision Tree
[Decision Tree Classifier Pt. 1](https://youtu.be/nSKOeH9vKHo)

[Decision Tree Classifier Pt. 2](https://youtu.be/ezXGC_47C6s)

## Regularization/ Post analysis 
## Akaike information criterion (AIC)
## Stepwise Regression
## Logistical Regression
[Logistic Regression Pt. 1](https://youtu.be/-vPg0OfLa3M)

[Logistic Regression Pt. 2](https://youtu.be/rjbkEsWSf_w)

## Sampling
## Principal Components Analysis
## AB Testing, Baysien Testing
## Data Scrapping

