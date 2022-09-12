<h1> Back to network architecture </h1>

Training a neural network revolves around the following objects:


<li> Layers, which are combined into a network (or model)
<li> The input data and corresponding targets
<li> The loss function, which defines the feedback signal used for learning
<li> The optimizer, which determines how learning proceeds
  
<a href="https://www.asimovinstitute.org/neural-network-zoo/">Asimovinstitute</a>
  
![Neural-Networks-Chart](https://user-images.githubusercontent.com/86980802/133149783-8f6cc505-1501-4866-b4f2-198a435f310c.png)

  
  <h2> Activation function </h2>

An activation function in a neural network defines how the weighted sum of the input is transformed into an output from a node or nodes in a layer of the network.
Sometimes the activation function is called a “transfer function.” If the output range of the activation function is limited, then it may be called a “squashing function.” Many activation functions are nonlinear and may be referred to as the “nonlinearity” in the layer or the network design.

**Hidden layers**
  
There are perhaps three activation functions you may want to consider for use in hidden layers; they are:

<li>Rectified Linear Activation (ReLU)
<li>Logistic (Sigmoid)
<li>Hyperbolic Tangent (Tanh)
  
![activation-functions](https://user-images.githubusercontent.com/86980802/133154629-d3d9ac3e-8797-4cb7-be86-31ebf1baf181.png)

A general problem with both the sigmoid and tanh functions is that they saturate. This means that large values snap to 1.0 and small values snap to -1 or 0 for tanh and sigmoid respectively. Further, the functions are only really sensitive to changes around their mid-point of their input, such as 0.5 for sigmoid and 0.0 for tanh.

  
  
  ![sigmoide](https://user-images.githubusercontent.com/86980802/189765390-638f10cf-7867-4d0f-b2c3-1b4575559d2c.png)

  ![tanh](https://user-images.githubusercontent.com/86980802/189765404-2dc26c7c-cba9-4bf3-80e0-739c974b8c7b.png)

Layers deep in large networks using these nonlinear activation functions fail to receive useful gradient information. Error is back propagated through the network and used to 
update the weights. The amount of error decreases dramatically with each additional layer through which it is propagated, given the derivative of the chosen activation function. 
 **This is called the vanishing gradient problem.**

  **How to Choose a Hidden Layer Activation Function**  
Recurrent networks still commonly use Tanh or sigmoid activation functions, or even both. For example, the LSTM commonly uses the Sigmoid activation for recurrent connections and the Tanh activation for output.

<li>Multilayer Perceptron (MLP): ReLU activation function.
<li>Convolutional Neural Network (CNN): ReLU activation function.
<li>Recurrent Neural Network: Tanh and/or Sigmoid activation function.

**Activation for Output Layers**

 The output layer is the layer in a neural network model that directly outputs a prediction.

There are perhaps three activation functions you may want to consider for use in the output layer; they are:

<li>Linear
<li>Logistic (Sigmoid)
<li>Softmax
  
  ![Tex2Img_1631569524](https://user-images.githubusercontent.com/86980802/133160677-06373298-be7e-449f-90d6-53409d300f3e.jpg)
