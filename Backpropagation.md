<h1> Backpropagation</h1>

Algorithm for training feedforward neural networks. Backpropagation computes the gradient of the loss function with respect to the weights of the network for a single input–output example.

*The term backpropagation strictly refers only to the algorithm for computing the gradient, not how the gradient is used*.


Consider a neural network with a single input neuron, an output neuron, and two hidden layers with a single neuron respectively.

![red1](https://user-images.githubusercontent.com/86980802/132998336-416ae049-c687-462b-8181-4cd5953d9287.png)

<img src="http://www.sciweavers.org/tex2img.php?eq=C%28w_%7B1%7Db_%7B1%7D%2C%20w_%7B2%7Db_%7B2%7D%2C%20w_%7B3%7Db_%7B3%7D%29&bc=White&fc=Black&im=jpg&fs=24&ff=mathdesign&edit=0" align="center" border="0" alt="C(w_{1}b_{1}, w_{2}b_{2}, w_{3}b_{3})" width="275" height="39" />

and only consider the last two neurons


![red2neu](https://user-images.githubusercontent.com/86980802/132999570-40e731f7-c4f4-4120-8588-f7b2c9b16dac.png)

In this case we have:

<img src=
"http://www.sciweavers.org/tex2img.php?eq=a%5E%7B%28L%29%7D%3D%5Csigma%28w%5E%7B%28L%29%7D%20a%5E%7B%28L-1%29%7D%2Bb%5E%7B%28L%29%7D%29%20%20&bc=White&fc=Black&im=jpg&fs=24&ff=mathdesign&edit=0" align="center" border="0" alt="a^{(L)}=\sigma(w^{(L)} a^{(L-1)}+b^{(L)})  " width="378" height="44" /> 
 
and     

<img src="https://bit.ly/3CaUcdH" align="center" border="0" alt="C_{0}=(a^{(L)}-y)^{2}" width="233" height="44" />


Where *y* is the expected target and for simplicity we use MSE.


Let us denote by

<img src="http://www.sciweavers.org/tex2img.php?eq=Z%5E%7B%28L%29%7D%3Dw%5E%7B%28L%29%7D%20a%5E%7B%28L-1%29%7D%2Bb%5E%7B%28L%29%7D&bc=White&fc=Black&im=jpg&fs=24&ff=mathdesign&edit=0" align="center" border="0" alt="Z^{(L)}=w^{(L)} a^{(L-1)}+b^{(L)}" width="339" height="39" />

Therefore, we have 

<img src="https://bit.ly/3C7czzU" align="center" border="0" alt="a^{(L)}=\sigma (Z^{(L)})" width="206" height="44" />


🏁 **The objective is to understand the sensitivity of the cost function to weights and biases. Once this is understood, we can determine how to make very small changes in these variables to reduce the cost function.** 

Compute the gradient of the loss with regard to the network’s parameters (a backward pass).

![retro_graf](https://user-images.githubusercontent.com/86980802/133028750-2ba6a180-c923-4013-8203-3cbc1f2add45.png)


According to the above, by the chain rule, we have:  

<img src="http://www.sciweavers.org/tex2img.php?eq=%20%5Cfrac%7B%5Cpartial%20C_%7B0%7D%7D%7B%5Cpartial%20w%5E%7B%28L%29%7D%7D%3D%5Cfrac%7B%5Cpartial%20z%5E%7B%28L%29%7D%7D%7B%5Cpartial%20w%5E%7B%28L%29%7D%7D%20%5Cfrac%7B%5Cpartial%20a%5E%7B%28L%29%7D%7D%7B%5Cpartial%20Z%5E%7B%28L%29%7D%7D%20%5Cfrac%7B%5Cpartial%20C_%7B0%7D%7D%7B%5Cpartial%20a%5E%7B%28L%29%7D%7D&bc=White&fc=Black&im=jpg&fs=24&ff=mathdesign&edit=0" align="center" border="0" alt=" \frac{\partial C_{0}}{\partial w^{(L)}}=\frac{\partial z^{(L)}}{\partial w^{(L)}} \frac{\partial a^{(L)}}{\partial Z^{(L)}} \frac{\partial C_{0}}{\partial a^{(L)}}" width="378" height="78" />

And thus, 


  1️⃣<img src="http://www.sciweavers.org/tex2img.php?eq=%5Cfrac%7B%5Cpartial%20C_%7B0%7D%7D%7B%5Cpartial%20a%5E%7B%28L%29%7D%7D%3D2%28a%5E%7B%28L%29%7D-y%29&bc=White&fc=Black&im=jpg&fs=18&ff=mathdesign&edit=0" align="center" border="0" alt="\frac{\partial C_{0}}{\partial a^{(L)}}=2(a^{(L)}-y)" width="206" height="54" />  </li>
  
  2️⃣<img src="http://www.sciweavers.org/tex2img.php?eq=%5Cfrac%7B%5Cpartial%20a%5E%7B%28L%29%7D%7D%7B%5Cpartial%20Z%5E%7B%28L%29%7D%7D%20%3D%20%5Csigma%5E%7B%5Cprime%7D%28Z%5E%7B%28L%29%7D%29&bc=White&fc=Black&im=jpg&fs=18&ff=mathdesign&edit=0" align="center" border="0" alt="\frac{\partial a^{(L)}}{\partial Z^{(L)}} = \sigma^{\prime}(Z^{(L)})" width="183" height="58" />
  
  3️⃣<img src="http://www.sciweavers.org/tex2img.php?eq=%5Cfrac%7B%5Cpartial%20z%5E%7B%28L%29%7D%7D%7B%5Cpartial%20w%5E%7B%28L%29%7D%7D%3Da%5E%7B%28L-1%29%7D&bc=White&fc=Black&im=jpg&fs=18&ff=mathdesign&edit=0" align="center" border="0" alt="\frac{\partial z^{(L)}}{\partial w^{(L)}}=a^{(L-1)}" width="160" height="58" />


This corresponds only to the first training example, i.e.,

<img src="http://www.sciweavers.org/tex2img.php?eq=%5Cfrac%7B%5Cpartial%20C_%7B0%7D%7D%7B%5Cpartial%20w%5E%7B%28L%29%7D%7D%3Da%5E%7B%28L-1%29%7D%5Csigma%5E%7B%5Cprime%7D%28Z%5E%7B%28L%29%7D%292%28a%5E%7B%28L%29%7D-y%29%0A%0A%0A%0A&bc=White&fc=Black&im=jpg&fs=18&ff=mathdesign&edit=0" align="center" border="0" alt="\frac{\partial C_{0}}{\partial w^{(L)}}=a^{(L-1)}\sigma^{\prime}(Z^{(L)})2(a^{(L)}-y)" width="358" height="54" />

Now, our total cost function would be:


<img src="http://www.sciweavers.org/tex2img.php?eq=%5Cfrac%7B%5Cpartial%20C%7D%7B%5Cpartial%20w%5E%7B%28L%29%7D%7D%3D%20%5Cfrac%7B1%7D%7Bn%7D%20%5Csum_%7Bk%3D0%7D%5E%7Bn-1%7D%20%5Cfrac%7B%20%5Cpartial%20C_%7Bk%7D%7D%7B%5Cpartial%20w%5E%7B%28L%29%7D%7D%0A%0A&bc=White&fc=Black&im=jpg&fs=24&ff=mathdesign&edit=0" align="center" border="0" alt="\frac{\partial C}{\partial w^{(L)}}= \frac{1}{n} \sum_{k=0}^{n-1} \frac{ \partial C_{k}}{\partial w^{(L)}}" width="297" height="100" />

And therefore, you have a part of the gradient

<img src="http://www.sciweavers.org/tex2img.php?eq=%20%20%5CDelta%20C%20%3D%20%5Cbegin%7Bbmatrix%7D%5Cfrac%7B%5Cpartial%20C%7D%7B%5Cpartial%20w%5E%7B%281%29%7D%7D%20%20%5C%5C%20%5Cfrac%7B%5Cpartial%20C%7D%7B%5Cpartial%20b%5E%7B%281%29%7D%7D%20%5C%5C%20%5Cvdots%20%5C%5C%20%5Cfrac%7B%5Cpartial%20C%7D%7B%5Cpartial%20w%5E%7B%28L%29%7D%7D%20%5C%5C%20%5Cfrac%7B%5Cpartial%20C%7D%7B%5Cpartial%20b%5E%7B%28L%29%7D%7D%20%20%5Cend%7Bbmatrix%7D%20%0A%0A&bc=White&fc=Black&im=jpg&fs=24&ff=mathdesign&edit=0" align="center" border="0" alt="  \Delta C = \begin{bmatrix}\frac{\partial C}{\partial w^{(1)}}  \\ \frac{\partial C}{\partial b^{(1)}} \\ \vdots \\ \frac{\partial C}{\partial w^{(L)}} \\ \frac{\partial C}{\partial b^{(L)}}  \end{bmatrix} " width="214" height="225" />

The other part of the gradient corresponds to the derivatives with respect to the bias, i.e., 

<img src="http://www.sciweavers.org/tex2img.php?eq=%5Cfrac%7B%5Cpartial%20C_%7B0%7D%7D%7B%5Cpartial%20b%5E%7B%28L%29%7D%7D%3D%5Cfrac%7B%5Cpartial%20z%5E%7B%28L%29%7D%7D%7B%5Cpartial%20b%5E%7B%28L%29%7D%7D%20%5Cfrac%7B%5Cpartial%20a%5E%7B%28L%29%7D%7D%7B%5Cpartial%20Z%5E%7B%28L%29%7D%7D%20%5Cfrac%7B%5Cpartial%20C_%7B0%7D%7D%7B%5Cpartial%20a%5E%7B%28L%29%7D%7D%3D%5Csigma%5E%7B%5Cprime%7D%28Z%5E%7B%28L%29%7D%292%28a%5E%7B%28L%29%7D-y%29&bc=White&fc=Black&im=jpg&fs=18&ff=mathdesign&edit=0" align="center" border="0" alt="\frac{\partial C_{0}}{\partial b^{(L)}}=\frac{\partial z^{(L)}}{\partial b^{(L)}} \frac{\partial a^{(L)}}{\partial Z^{(L)}} \frac{\partial C_{0}}{\partial a^{(L)}}=\sigma^{\prime}(Z^{(L)})2(a^{(L)}-y)" width="504" height="58" />

And so, we have the gradient for a network with a single neuron in each layer.  But the process is the same, if you increase the number of layers and neurons. 

![retro_red_dos](https://user-images.githubusercontent.com/86980802/133036128-2e1b72b4-6d9f-4527-801a-b5684787adaa.png)

Therefore, the cost function of the last layer will be: 

<img src="http://www.sciweavers.org/tex2img.php?eq=%5Cfrac%7B%5Cpartial%20C_%7B0%7D%7D%7B%5Cpartial%20w_%7Bjk%7D%5E%7B%28L%29%7D%7D%3D%5Cfrac%7B%5Cpartial%20z_%7Bj%7D%5E%7B%28L%29%7D%7D%7B%5Cpartial%20w_%7Bjk%7D%5E%7B%28L%29%7D%7D%20%5Cfrac%7B%5Cpartial%20a_%7Bj%7D%5E%7B%28L%29%7D%7D%7B%5Cpartial%20Z_%7Bj%7D%5E%7B%28L%29%7D%7D%20%5Cfrac%7B%5Cpartial%20C_%7B0%7D%7D%7B%5Cpartial%20a_%7Bj%7D%5E%7B%28L%29%7D%7D&bc=White&fc=Black&im=jpg&fs=18&ff=mathdesign&edit=0" align="center" border="0" alt="\frac{\partial C_{0}}{\partial w_{jk}^{(L)}}=\frac{\partial z_{j}^{(L)}}{\partial w_{jk}^{(L)}} \frac{\partial a_{j}^{(L)}}{\partial Z_{j}^{(L)}} \frac{\partial C_{0}}{\partial a_{j}^{(L)}}" width="283" height="81" />

However, considering the previous layer, we have:

![Tex2Img_1631517689](https://user-images.githubusercontent.com/86980802/133041122-7839bc64-ab7f-4b52-84a4-e512c035de5b.jpg)


