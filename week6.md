# Week 6
![image](https://user-images.githubusercontent.com/64345863/231137975-de081b98-0f58-40cc-9f45-f0f185e7b19f.png)


## Bias Variance Tradeoff 
| Model | Bias | Variance | Type of error|
| ----- | ----- | -------- |------------- |
| Complex| Low | High | Over Fitting |
| Simple | High | Low | Under Fitting | 

![image](https://user-images.githubusercontent.com/64345863/231139017-c9f377a7-019a-4fc5-a6a8-a12b3c9f538e.png)

### Why do we care about Bias variance Trade off
- Deep Neural networks are highly complex models.
- Many parameters, many non-linearities. 
- It is easy for them to overfit and drive training error to 0. 
- Hence we need some form of regularization. 

## Different Forms of Regularization
### l2 Regularization
For l2 regularization we have
$\tilde{L(w)} = L(w) + \frac{\alpha}{2}||w||^2$

For SGD and its variants we have
$\nabla \tilde(L(w) = \nabla L(w)+ \alpha w$
updated rule:
$w_{t+1}  = w_t-\eta \nabla L(w_t)- \eta \alpha w_t$

![image](https://user-images.githubusercontent.com/64345863/231141713-fc9fd6ef-6ec7-4691-ab63-7120e519a442.png)
![image](https://user-images.githubusercontent.com/64345863/231141754-2ec6b5a4-e8c2-4442-9b22-f9b0ed266325.png)
![image](https://user-images.githubusercontent.com/64345863/231141977-d2a435c9-191c-4fab-88e1-cbe8f430055d.png)
![image](https://user-images.githubusercontent.com/64345863/231142086-5be43eb9-fd22-4a1f-97f1-205727b13cca.png)

![image](https://user-images.githubusercontent.com/64345863/231142134-45775c41-5ce8-400c-a634-b9f1748353f2.png)


### Dataset Augmentation
- Data augmentation is a technique of artificially increasing the training set by creating modified copies of a dataset using existing data. It includes making minor changes to the dataset or using deep learning to generate new data points.  
- For example if we are doing Image classification of say Mango, we can add its rotated  or blurred images 
- We exploit the fact that certain transformations to the image do not change the label of the image.
- Typically, More data  = better learning
- Works well for image classification / object recognition tasks
- Also shown to work well for speech
- For some tasks it may not be clear how to generate such data

### Parameter Sharing and Tying
- Typically used in CNN where same Kernel Filters throughout the dataset
- Tying is typically used in auto encoders


### Adding Noise to Input and Output
![image](https://user-images.githubusercontent.com/64345863/231143322-d04dff49-2a81-4510-abf0-ae5ca833aeb0.png)
![image](https://user-images.githubusercontent.com/64345863/231143577-c2d40908-1306-4bb0-9cb5-6085bf1ddd65.png)

### Early Stopping
- Track the validation error
- Have a patience parameter 
$
p$ If you are at step $k$ and there was no improvement in validation error in the previous  p steps then stop training and return the model stored at step $k−p$
- Basically, stop the training early before it drives the training error to 0 and blows up the validation error
- Very effective and the mostly widely used form of regularization
![image](https://user-images.githubusercontent.com/64345863/231144375-d94ace2f-0e95-4ad6-8bb5-a3ff6e541498.png)

![image](https://user-images.githubusercontent.com/64345863/231144573-417a02a1-c0a3-4192-81c3-d3ea897ff9d3.png)

### Ensemble Method
- Combine the output of different models to reduce generalization error
- The models can correspond to different classifiers
- It could be different instances of the same classifier trained with:
  - different hyperparameters
  - different features 
  - different samples of the training data
- Bagging and Boosting are major types of Ensemble methods used

### Dropouts
- An analogy to understand is use of CNNs with filters
- Effectively it allows training several neural networks without any significant computational overhead.
Also gives an efficient approximate way of combining exponentially many different neural networks.
![image](https://user-images.githubusercontent.com/64345863/231146595-ea7c337e-b23e-45e2-b8d2-11df181d76b1.png)

- Dropout refers to dropping out units
- Temporarily remove a node and all its incoming/outgoing connections resulting in a thinned network
- Each node is retained with a fixed probability say 0.5
- Only active parameters get updated
- Weight Sharing is generally used along with it
- Dropout essentially applies a masking noise to the hidden units 
- Prevents hidden units from coadapting 
- Essentially a hidden unit cannot rely too much on other units as they may get dropped out any time
- Each hidden unit has to learn to be more robust to these random dropouts

![image](https://user-images.githubusercontent.com/64345863/231147462-c2565f55-1898-4981-9561-bec5e9ad7b20.png)

![image](https://user-images.githubusercontent.com/64345863/231147525-bb87a623-1512-4727-a858-b00161861833.png)

****



