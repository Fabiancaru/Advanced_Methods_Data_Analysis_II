<h1> Backpropagation</h1>

Algorithm for training feedforward neural networks. Backpropagation computes the gradient of the loss function with respect to the weights of the network for a single input–output example.

*The term backpropagation strictly refers only to the algorithm for computing the gradient, not how the gradient is used*.


Consider a neural network with a single input neuron, an output neuron, and two hidden layers with a single neuron respectively.

![red1](https://user-images.githubusercontent.com/86980802/132998336-416ae049-c687-462b-8181-4cd5953d9287.png)

![Tex2Img_1631553615](https://user-images.githubusercontent.com/86980802/133128603-643f112a-cc83-4308-bd25-45a2693c110a.jpg)


and only consider the last two neurons


![red2neu](https://user-images.githubusercontent.com/86980802/132999570-40e731f7-c4f4-4120-8588-f7b2c9b16dac.png)

In this case we have:

![Tex2Img_1631553712](https://user-images.githubusercontent.com/86980802/133128766-85fef6a7-f2ff-443d-85a3-e34602080b7b.jpg)

 
and     

![Tex2Img_1631553800](https://user-images.githubusercontent.com/86980802/133128938-dea28868-0348-4e0f-b752-401d8251f00f.jpg)



Where *y* is the expected target and for simplicity we use MSE.


Let us denote by

![Tex2Img_1631553849](https://user-images.githubusercontent.com/86980802/133129041-59b5d646-5c65-42db-b1ff-171557647876.jpg)


Therefore, we have 

![Tex2Img_1631553893](https://user-images.githubusercontent.com/86980802/133129150-3eabfb01-90a9-4bf5-a118-314af9481f34.jpg)



🏁 **The objective is to understand the sensitivity of the cost function to weights and biases. Once this is understood, we can determine how to make very small changes in these variables to reduce the cost function.** 

Compute the gradient of the loss with regard to the network’s parameters (a backward pass).

![retro_graf](https://user-images.githubusercontent.com/86980802/133028750-2ba6a180-c923-4013-8203-3cbc1f2add45.png)


According to the above, by the chain rule, we have:  


![Tex2Img_1631561974](https://user-images.githubusercontent.com/86980802/133146105-b07c36c1-58e3-41b5-a0b7-e7896ebb89e8.jpg)


And thus, 


  1️⃣![Tex2Img_1631562035](https://user-images.githubusercontent.com/86980802/133146215-466791f6-0764-49e4-bf65-aad4618af54a.jpg)
  
  2️⃣![Tex2Img_1631562092](https://user-images.githubusercontent.com/86980802/133146314-092e93c0-eddf-4ea4-bbcf-670e1247f46e.jpg)
  
  3️⃣![Tex2Img_1631562143](https://user-images.githubusercontent.com/86980802/133146412-70a40918-3b1c-443e-898b-cb7bef1108e8.jpg)



This corresponds only to the first training example, i.e.,

![Tex2Img_1631562190](https://user-images.githubusercontent.com/86980802/133146535-71d347cf-f52f-4a50-b00e-ad91f200eaba.jpg)


Now, our total cost function would be:

![Tex2Img_1631562283](https://user-images.githubusercontent.com/86980802/133146713-6904dcce-9304-48b6-a94b-1d8514a8f371.jpg)


And therefore, you have a part of the gradient

![Tex2Img_1631562321](https://user-images.githubusercontent.com/86980802/133146822-5770bb7e-c729-4299-bb63-672042f5ebca.jpg)


The other part of the gradient corresponds to the derivatives with respect to the bias, i.e., 

![Tex2Img_1631562379](https://user-images.githubusercontent.com/86980802/133146926-f588c432-3d1c-48df-977f-24fb63b01d95.jpg)


And so, we have the gradient for a network with a single neuron in each layer.  But the process is the same, if you increase the number of layers and neurons. 

![retro_red_dos](https://user-images.githubusercontent.com/86980802/133036128-2e1b72b4-6d9f-4527-801a-b5684787adaa.png)

Therefore, the cost function of the last layer will be: 

![Tex2Img_1631562444](https://user-images.githubusercontent.com/86980802/133147065-54a154b2-2d8d-4a71-8b72-0ebbd095e1bf.jpg)


However, considering the previous layer, we have:

![Tex2Img_1631517689](https://user-images.githubusercontent.com/86980802/133041122-7839bc64-ab7f-4b52-84a4-e512c035de5b.jpg)


