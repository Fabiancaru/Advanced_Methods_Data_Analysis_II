<h1> Gradient-based optimization </h1>

https://user-images.githubusercontent.com/86980802/131268721-148d065c-f193-408c-9abf-d286c5f1aedf.mp4

Network transforms its input data as follows:

*output = relu(dot(W, input) + b</font>*

  In this expression, W and b are tensors that are attributes of the layer. They’re called the weights or trainable parameters of the layer (the kernel and bias attributes, respectively).
  
  ![activation-functions](https://user-images.githubusercontent.com/86980802/131270369-bcefa4e1-8d52-425c-b11b-dacce5c13a8d.png)

  
  What comes next is to gradually adjust these weights, based on a feedback signal

<ol>
		<li>Draw a batch of training samples *x* and corresponding targets *y*.</li>
		<li>Run the network on *x* (a step called the forward pass) to obtain predictions *y_pred*.</li>
		<li>Compute the loss of the network on the batch, a measure of the mismatch *between y_pred* and *y*.</li>
		<li>Update all weights of the network in a way that slightly reduces the loss on this batch.</li>
	</ol>

<h2> Derivate <h2>

<a href="https://www.codecogs.com/eqnedit.php?latex=a=\frac{f(x&plus;\Delta&space;x)&space;-&space;f(x)}{\Delta&space;x}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?a=\frac{f(x&plus;\Delta&space;x)&space;-&space;f(x)}{\Delta&space;x}" title="a=\frac{f(x+\Delta x) - f(x)}{\Delta x}" /></a></center>
  
  <center><a href="https://www.codecogs.com/eqnedit.php?latex=f(x)&plus;\Delta&space;x=y&space;&plus;&space;\Delta&space;y" target="_blank"><img src="https://latex.codecogs.com/gif.latex?f(x)&plus;\Delta&space;x=y&space;&plus;&space;\Delta&space;y" title="f(x)+\Delta x=y + \Delta y" /></center></a>


