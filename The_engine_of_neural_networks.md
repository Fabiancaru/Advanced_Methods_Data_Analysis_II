<h1> Gradient-based optimization. Intuitive idea </h1>

**Introduction**

https://user-images.githubusercontent.com/86980802/131268721-148d065c-f193-408c-9abf-d286c5f1aedf.mp4


Loss function (objective function)—The quantity that will be minimized during training. It represents a measure of success for the task at hand.

 ![entrenamiento_del_2](https://user-images.githubusercontent.com/86980802/132169795-a94be650-5433-43e4-bc4b-e2859fc60849.png)
 
  What comes next is to gradually adjust these weights, based on a feedback signal

<ol>
		<li>Draw a batch of training samples *x* and corresponding targets *y*.</li>
		<li>Run the network on *x* (a step called the forward pass) to obtain predictions *y_pred*.</li>
		<li>Compute the loss of the network on the batch, a measure of the mismatch *between y_pred* and *y*.</li>
		<li>Update all weights of the network in a way that slightly reduces the loss on this batch.</li>
	</ol>



![entrenamiento_2_2](https://user-images.githubusercontent.com/86980802/132169999-9073c04d-d839-453c-8d3e-9953b047788d.png)

Let us consider a single item

Network transforms its input data as follows:

*output = relu(dot(W, input) + b</font>*

 In this expression, W and b are tensors that are attributes of the layer. They’re called the weights or trainable parameters of the layer (the kernel and bias attributes, respectively).


*Neurons that fire together wire together*

**Increasing or decreasing weights and biases**

![entrenamiento_del2_3](https://user-images.githubusercontent.com/86980802/132179043-750c97b3-4c14-4583-9263-b1336654a4ce.png)

The process is performed for each of the neurons in the output layer.


![Entrenamiento_reprop](https://user-images.githubusercontent.com/86980802/132180445-b372408d-6d73-45dc-abf7-3eff3b76fe6d.png)


All desired movements are obtained for all neurons in the last layer. (for the image of number two)

![Agrega_retrop](https://user-images.githubusercontent.com/86980802/132180718-af9e4ac5-e549-4992-ae2a-7c050f13a006.png)

The same process is performed for all images

![Entrenamiento_reprop2](https://user-images.githubusercontent.com/86980802/132180475-2bddf3d2-a20a-4283-a071-475fcb741778.png)

The averages of each weight are calculated for all images.

![agrega_retrop_2](https://user-images.githubusercontent.com/86980802/132180973-259d4965-f181-4335-9bbe-a5bae3dae660.png)
 
 This is the negative gradient of the cost function!!!! 

![agrega_gradiente](https://user-images.githubusercontent.com/86980802/132180997-c96cbb72-78c5-49d7-b393-b170c2595b7c.png)

  



