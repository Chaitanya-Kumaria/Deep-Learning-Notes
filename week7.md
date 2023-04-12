# Week 7 
![image](https://user-images.githubusercontent.com/64345863/231359719-814a8716-b75f-4d55-b7e4-505b2f0fb91c.png)

## Unsupervised Learning
Consider the Following Neural Network 
Notations which are used
- $x_i$ : inputs at Layer i
- $a_i$ : Preactivation Layer at Layer i
- $h_i$ : Activation Layer at Layer i
- $W_i$ : Weight Matrix at Layer i

![image](https://user-images.githubusercontent.com/64345863/231360610-52826d9d-06a7-41dc-a1f4-a000a7ea354a.png)


Consider the first two layers of this neural network
![image](https://user-images.githubusercontent.com/64345863/231360833-1444a197-29b5-4c29-9fd6-f8c6a025d6cd.png)
- We will train weights between $x ~and ~h1$ using an **unsupervised objective**
- That is we are trying to reconstruct input x from hidden representation, this is called unsupervised objective because we are not using output y 
- At the end of this step layer 1 gets trained such that $h_1$ captures an abstract representation of input x. Now the same procedure is repeated for subsequent layer
- After this layerwise pre-training, we add the output layer and train the whole network using the task specific objective
- Note that, in effect we have initialized the weights of the network using the greedy unsupervised objective and are now fine tuning these weights using the supervised objective

### Why does this help?

does it lead to better optimization?
- The error surface of the supervised objective of a Deep Neural Network is highly non-convex
- With many hills and plateaus and valleys
- Given that large capacity of DNNs it is still easy to land in one of these 0 error regions
- if last layer has large capacity then $L(\theta)->0$ even without pretraining
- - however if capacity is small pre training helps.

![image](https://user-images.githubusercontent.com/64345863/231396510-2b9b910c-d270-4468-a90e-09873e10efcf.png)
![image](https://user-images.githubusercontent.com/64345863/231396572-b70ae63b-9581-4bc2-a526-54d4af3aca29.png)

## Better Activation Function

[Activation Function Flowcharts](https://drive.google.com/file/d/1D8EiEfUb2V0wU7Zo7TcnjLVNovp8M-7o/view?usp=sharing)
![image](https://user-images.githubusercontent.com/64345863/231425128-1abbc20f-cd57-4c5b-8565-1ad18bae998b.png)



### All Activation Functions
![image](https://user-images.githubusercontent.com/64345863/231422551-74601dd2-11db-4231-ba32-a0b57e693e50.png)


### Model Averaging
![image](https://user-images.githubusercontent.com/64345863/231417392-072cd2f1-4fe5-4d31-95c3-7dbead0aea79.png)
![image](https://user-images.githubusercontent.com/64345863/231418627-2e10b173-19ac-4aed-b170-ec798098e0d7.png)
![image](https://user-images.githubusercontent.com/64345863/231418741-70c481ed-e04b-40f8-b7d2-65468dec731b.png)

## Better Initialization Strategies
**What happens if we initialize all the Weights to zero?**
$a_{ij} = \Sigma_{j=1}^{n}w_{ij}x_{j}$
$a_{ij} = 0 $
- implying that all neurons in layer one will get same activation function
- Even during Backpropogation they will get same updates and remain equal
- This is known as symmetry breaking problem

![image](https://user-images.githubusercontent.com/64345863/231428458-db694202-e707-498f-833d-593a8d3ce68e.png)
![image](https://user-images.githubusercontent.com/64345863/231428532-0dc756cc-a4e6-4062-8f8e-7b7ed346d477.png)

![image](https://user-images.githubusercontent.com/64345863/231428608-b755a87d-4766-4a2a-82bb-bdd870416e15.png)

## Batch Normalization 
- Batch normalization is a technique used to accelerate the training of deep learning neural networks. It standardizes the inputs to a layer for each mini-batch, stabilizing the learning process and dramatically reducing the number of training epochs required. Batch normalization accelerates training by halving epochs or better and provides some regularization, reducing generalization error.
- Batch normalization can be implemented during training by calculating the mean and standard deviation of each input variable to a layer per mini-batch and using these statistics to perform the standardization.
- Alternately, a running average of mean and standard deviation can be maintained across mini-batches, but may result in unstable training.
- ![image](https://user-images.githubusercontent.com/64345863/231429192-bf713290-08fb-4da1-9116-b3f288254f32.png)
- ![image](https://user-images.githubusercontent.com/64345863/231429302-0e1d4bf3-3e0c-473c-a7dd-0e773a25d3f9.png)

### Layer Normalization
The computation is simple. Take the average across outputs of hidden units in the layer. Therefore, the normalization is independent of samples in a batch.
This allows us to work with a batch size of 1 (if needed as in the case of RNN)
![image](https://user-images.githubusercontent.com/64345863/231429540-8c640e50-c44a-477c-82f3-080c1a3153f4.png)




