# Movie-Rating-AI
## Introduction

Our goal was to create a machine learning model that is able to predict the success of a movie. By using the important pre-production details of a movie such as budget, duration, genre and plot description as input, we wanted to create a model that accurately predicted the final viewer ratings of the movie. This is a great use case for machine learning, as we have access to historical movie data that we can use to train our model in making accurate predictions for brand new films. Furthermore, Hollywood has shown interest in doing something similar, by using AI to try to figure out who the best cast is for a given movie script to have the highest projected box office revenue. In essence, our goal is to provide movie producers with a useful tool for predicting the success of a film during the pre-production phase so that they will be able to invest their money in movies that have a high chance of success.

## Illustration

![Capture](https://user-images.githubusercontent.com/65812536/127953686-8785bde6-ea79-49da-b232-57835027138b.PNG)

## Model Architecture

We used an autoencoder model since we had redefined our initial problem as a data imputation problem. Essentially, we needed to generate the ratings for movies based on other details regarding the film, which is a great use case for an autoencoder.

The auto encoder consists of two parts, the encoder and the decoder. The encoder converts information regarding the films into an internal representation while the decoder attempts to accurately reconstruct the original information. The internal representation is found in the embedding space of the autoencoder, which is created through the use of a bottleneck.

We achieved optimal  results by using a stacked autoencoder with linear layers. A single hidden layer each was added to the encoder and the decoder. We applied ReLu activations functions between the input layer and the first hidden layer as well as the second hidden layer and the output layer to prevent vanishing gradients. We also applied a sigmoid function on the final outputs so that it would be scaled from 0 to 1. A full breakdown of the sizes of each layer is shown below.

![Capture](https://user-images.githubusercontent.com/65812536/127953868-dc0e6370-8284-4e4d-85f9-14967b406ee0.PNG)

## Results

The measure of our model’s success was based on how well it was able to predict the average rating a movie would receive. This measurement is one that investors would care the most about. An investor is more likely to invest in a movie that is going to perform well and receive praise from the public, i.e. get a high rating. Thus, the best measurement to use is the average rating as it is able to represent the publics’ opinion on a movie. If a model was able to predict the true rating of a movie within 10% to either side, it would count as correct. Our baseline, an SGD Regression model, was only able to obtain an accuracy of 48.13% on the test set. This further shows the necessity of a neural network model in order to get better results for this problem. When we used our primary model, an Autoencoder, the test accuracy improved drastically and we received a test accuracy of 62.88%. The graph in figure 10 shows the effect that training for more and more epochs had on our training and validation accuracy. This was done with a batch size of 32, a learning rate of 0.00001, and it was run for 10 epochs. As shown below, as the epochs increased, a steady rise in training and validation accuracy is shown. However, the validation accuracy had started to flatline so it was important to not train for too many epochs otherwise we would end up overfitting the model to the training data. The final validation accuracy was 62.15% and the final training accuracy was 65.28%.

![Capture](https://user-images.githubusercontent.com/65812536/127954004-33aa14fe-b5a5-46ef-9a86-269686e7b4aa.PNG)




