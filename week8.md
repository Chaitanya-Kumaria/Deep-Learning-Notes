# Convulation Neural Network
A Convolutional Neural Network, also known as CNN or ConvNet, is a class of neural networks that specializes in processing data that has a grid-like topology, such as an image. 
A digital image is a binary representation of visual data. It contains a series of pixels arranged in a 
grid-like fashion that contains pixel values to denote how bright and what color each pixel should be.

The human brain processes a huge amount of information the second we see an image. Each neuron works in its own receptive field and is connected to other neurons in a way that they cover the entire visual field. Just as each neuron responds to stimuli only in the restricted region of the visual field called the receptive field in the biological vision system, each neuron in a CNN processes data only in its receptive field as well. The layers are arranged in such a way so that they detect simpler patterns first (lines, curves, etc.) and more complex patterns (faces, objects, etc.) further along. By using a CNN, one can enable sight to computers.

# Convolution Neural Networks Architecture
![image](https://user-images.githubusercontent.com/64345863/231998484-9d8e045f-2023-4cfc-8948-e3c3e5f36ee3.png)
# Convulation Layer
The convolution layer is the core building block of the CNN. It carries the main portion of the network’s computational load.

This layer performs a dot product between two matrices,  
During the forward pass, the kernel slides across the height

$W_{out} = \frac{W-S+2P}{S}+1$
![image](https://user-images.githubusercontent.com/64345863/232001264-07517322-20a2-4f58-a9f1-544ef24f1156.png)

## Motivation behind Convolution
Convolution leverages three important ideas that motivated computer vision researchers: sparse interaction, parameter sharing, and equivariant representation. Let’s describe each one of them in detail.

Trivial neural network layers use matrix multiplication by a matrix of parameters describing the interaction between the input and output unit. This means that every output unit interacts with every input unit. However, convolution neural networks have sparse interaction. This is achieved by making kernel smaller than the input e.g., an image can have millions or thousands of pixels, but while processing it using kernel we can detect meaningful information that is of tens or hundreds of pixels. This means that we need to store fewer parameters that not only reduces the memory requirement of the model but also improves the statistical efficiency of the model.

If computing one feature at a spatial point (x1, y1) is useful then it should also be useful at some other spatial point say (x2, y2). It means that for a single two-dimensional slice i.e., for creating one activation map, neurons are constrained to use the same set of weights. In a traditional neural network, each element of the weight matrix is used once and then never revisited, while convolution network has shared parameters i.e., for getting output, weights applied to one input are the same as the weight applied elsewhere.

Due to parameter sharing, the layers of convolution neural network will have a property of equivariance to translation. It says that if we changed the input in a way, the output will also get changed in the same way.

# Pooling Layer

The pooling layer replaces the output of the network at certain locations by deriving a summary statistic of the nearby outputs. This helps in reducing the spatial size of the representation, which decreases the required amount of computation and weights. The pooling operation is processed on every slice of the representation individually.

There are several pooling functions such as the average of the rectangular neighborhood, L2 norm of the rectangular neighborhood, and a weighted average based on the distance from the central pixel. However, the most popular process is max pooling, which reports the maximum output from the neighborhood.

![image](https://user-images.githubusercontent.com/64345863/232002272-5d91b8d9-b1a7-47da-b16c-428fa59e1a7b.png)

If we have an activation map of size W x W x D, a pooling kernel of spatial size F, and stride S, then the size of output volume can be determined by the following formula:

$W = \frac{W-F}{S}+1$

This will yield an output volume of size Wout x Wout x D.

In all cases, pooling provides some translation invariance which means that an object would be recognizable regardless of where it appears on the frame.

# Fully Connected 

Neurons in this layer have full connectivity with all neurons in the preceding and succeeding layer as seen in regular FCNN. This is why it can be computed as usual by a matrix multiplication followed by a bias effect.

The FC layer helps to map the representation between the input and the output.

# Non-Linearity Layers
Since convolution is a linear operation and images are far from linear, non-linearity layers are often placed directly after the convolutional layer to introduce non-linearity to the activation map.

# Designing CNN
![image](https://user-images.githubusercontent.com/64345863/232003311-882d6c29-224f-44ec-9fd4-ca30f0caffe0.png)

![image](https://user-images.githubusercontent.com/64345863/232003353-dd03772d-a9e6-4251-9e78-6296b235ca25.png)

![image](https://user-images.githubusercontent.com/64345863/232003393-d9331e6a-7b23-445c-9799-5bdc40ee559e.png)

![image](https://user-images.githubusercontent.com/64345863/232003425-3d1d2837-db9d-4401-8161-2772deac695e.png)

![image](https://user-images.githubusercontent.com/64345863/232003508-35f9046c-7693-493a-92b8-4be41cfbf273.png)



