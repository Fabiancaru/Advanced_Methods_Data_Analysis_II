<h1> Back to network architecture_2 </h1>

<h2> Gradient Descent </h2>

*Gradient descent is an iterative machine learning optimization algorithm to reduce the cost function*

<li> Weights are initialized randomly with values close to zero, but not zero.
<li> The gradient is calculated, ∂c/∂ω which is a partial derivative of cost with respect to weight.
<li> α is learning rate, helps adjust the weights with respect to gradient descent.

![Tex2Img_1632101894](https://user-images.githubusercontent.com/86980802/133950331-7338bc10-8946-4087-a9e8-468264a557dc.jpg)
  
  
![Tex2Img_1632101970](https://user-images.githubusercontent.com/86980802/133950338-62c1db45-8cc4-4b71-94c0-f8f7abf5be3e.jpg)

  
https://user-images.githubusercontent.com/86980802/133947220-c95225a8-7229-4ef2-b407-f458f0a51af8.mp4

  
  <h3> Learning rate </h3>
  
  Learning rate controls how much we should adjust the weights with respect to the loss gradient. Learning rates are randomly initialized.

  
  ![learning_rate](https://user-images.githubusercontent.com/86980802/133947484-fba2e076-3eee-4bb0-8cfa-8d66028d06e8.jpg)

<li> Lower the value of the learning rate, slower will be the convergence to global minima.
<li> A higher value for learning rate will not allow the gradient descent to converge
 
  
  
  ![local_global_minimun](https://user-images.githubusercontent.com/86980802/133947702-4eb435e0-4755-49af-9dd4-cdc3dc43eb44.png)

  
**How can we avoid local minima and always try and get the optimized weights based on global minima?**
  
1️⃣ **Batch Gradient Descent**: use the entire dataset to compute the gradient of the cost function for each iteration of the gradient descent and then update the weights. 
  
  
2️⃣ **Stochastic Gradient Descent**: use a single datapoint or example to calculate the gradient and update the weights with every iteration.
  
  
3️⃣ **Mini batch Gradient Descent**: is a variation of stochastic gradient descent where instead of single training example, mini-batch of samples is used.
  

https://user-images.githubusercontent.com/86980802/133948045-e47d5605-81ef-42e1-906d-d7f94539aa23.mp4

  <h2> Types of Optimizers </h2>

  <h3> SGD with momemtum </h3>
   
  <li> Momentum helps accelerate Gradient Descent when we have surfaces that curve more steeply in one direction than in another direction. </li>
  
    
 ![momentum](https://user-images.githubusercontent.com/86980802/133949888-da3e38db-68bf-4670-9100-6a7d05c5b1ca.png)


 
 
 <li> For updating the weights it takes the gradient of the current step as well as the gradient of the previous time steps. </li>


<p align="center">
            
  ![Tex2Img_1632112845](https://user-images.githubusercontent.com/86980802/133957839-a4f6b5e3-644b-426d-ab6a-106b5668416e.jpg) 
  
</p>
Where,

<p align="center">
            
  ![Tex2Img_1632113699](https://user-images.githubusercontent.com/86980802/133958410-2c80cf6a-be46-48c2-ab34-74d54dfae566.jpg)

  
</p>
<p align="center">


  ![momentum1](https://user-images.githubusercontent.com/86980802/133958574-0559f018-eb9e-4e9b-9a29-81655df6ab7e.jpeg)

  </p>

<h3> Nesterov accelerated gradient (NAG) </h3>


Calculate the gradient not with respect to the current step but with respect to the future step
 <p align="center"> 
  
 ![Tex2Img_1632114443](https://user-images.githubusercontent.com/86980802/133959104-2b3278a4-775f-4db1-a4c9-de609cd1bbaf.jpg)
  
  ![Tex2Img_1632114725](https://user-images.githubusercontent.com/86980802/133959285-ec1bf956-db54-4afe-abb3-249d7058a9a1.jpg)


 </p> 
 
 ![nesterov1](https://user-images.githubusercontent.com/86980802/133959379-c27a54a6-a629-45fd-a257-c4d7a1277254.jpeg)

<h3> Adagrad — Adaptive Gradient Algorithm </h3>

Adagrad is an adaptive learning rate method. 

In Adagrad we adopt the learning rate to the parameters. We perform larger updates for infrequent parameters and smaller updates for frequent parameters.

For SGD, Momentum, and NAG we use the same learning rate **α**. In Adagrad we use different learning rate for every parameter **W** for every time step *n*.


![Tex2Img_1632117237](https://user-images.githubusercontent.com/86980802/133961631-5bdb16d9-25f4-407a-8c37-d4dc57874916.jpg)


where *G* is sum of the squares of the past gradients


 
 
<body style="margin: 0px; background: #0e0e0e; height: 100%"><img style="-webkit-user-select: none;margin: auto;background-color: hsl(0, 0%, 90%);transition: background-color 300ms;" src="https://miro.medium.com/max/724/1*SjtKOauOXFVjWRR7iCtHiA.gif">
