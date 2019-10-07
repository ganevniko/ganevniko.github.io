---
layout: post
title:      "Monitoring Toxic and Hate Speech in Online Comments"
date:       2019-06-04 23:42:33 -0400
permalink:  monitoring_toxic_and_hate_speech_in_online_comments
---


This dataset is from the [Toxic Comment Classification competition on Kaggle](https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge#description), where participants were challenged to build a model that’s capable of detecting different types of toxicity in online comments such as threats, obscenity, insults, and identity-based hate. The Dataset is a collection of labeled comments from Wikipedia’s talk page edits. I have not yet participated in a real Kaggle competition but it is on my to do list and this was a great opportunity to practice. 

The training data has one hundred and sixty thousand rows and I will be using various types of neural networks to sort out the all kind of toxic ones from the lot. As we can see below the toxic category is the one that is represented the most while threat and identity hate are seen less often but I probably the ones we want to classify the most accurately. 

![](img/46.png)

The first step was to label the non-toxic comments. In order to train the models properly I created an additional column titled “neutral” and label it with a one for every row where all the toxic categories had a zero. 

The next step was to tokenize the data using Keras tokenizer. Tokenizing means that we are breaking the sequences of strings from each comment into words and then assign a number (token) to these words. I passed two hundred thousand as a parameter in the tokenizer meaning that our tokenizer will have a vocabulary of a maximum of two hundred thousand words. The next step is to make sure that all the comments tokenized are the same length and I chose an average length of two hundred words by cutting the longer ones to the first two hundred words and padding the shorter ones with zeros to bring them up to two hundred tokens. After tokenizing the data make sure to save the tokenizer. If you are going to put the model into production later on and need to process new comments the same tokenizer has to be used in order for the model to work. The reason for that is that the tokenizer has needs to have the same two hundred thousand words vocabulary and the same number needs to be assigned to each word. I used the pickle library to save the tokenizer as “tokenizer.pickle”. 

I am now ready to move into the modeling part of the project. Three types of neural network models will be tested here. First I start with a baseline model and then add a convolutional neural network and finally a recurrent neural network. Convolutional neural networks are known for being most efficient on classifying images because they break them into major graphic patterns. We will still give convolutional networks a try here to see how they do. What is expected to perform the best is the long short term memory (LSTM) recurrent neural network model.  These types of model keep in memory the previous data encountered which is very much needed when you are analyzing text: it is better to remember what was said at the beginning all the way through the end. They also have what is called a “forget gate”. The forget gate tells the model how long to keep data in memory and helps it assign more weight to recently encountered values and less to the one further behind. 

Because we are performing a classification task the ReLu activation function that is currently the most commonly used with neural networks would not be appropriate for the output layer and the activation function I will use in all the neural networks is the sigmoid function and associate it with binary cross-entropy as a loss function. I also apply a dropout layer between each layer to avoid overfitting of the model. My output layer has a dimension of seven for each one of the six toxic comments classes plus the neutral, non-toxic class. 

The table below shows a summary of results for the three models:

![](img/47.png)

<u><b>Conclusion:</b></u>

All three models have performed very well but as expected the recurrent model has the smaller loss and the highest accuracy. In the last notebook of the model I wrote code that allows you to test the model on any string of your choice. These types of models can be very useful especially if they are able to spot threats, insults…They can contribute to improving online communication and encourage people to express themselves if they know that the environment is safe as well as spot individuals that need to be monitored for various reasons.


