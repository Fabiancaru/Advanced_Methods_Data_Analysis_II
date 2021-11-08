<h1> Convolutional Neural Network (ConvNet/CNN) </h1>

A Convolutional Neural Network (ConvNet/CNN) is a Deep Learning algorithm which can take in an input image, assign importance (learnable weights and biases) to 
various aspects/objects in the image and be able to differentiate one from the other.




![brain_conv](https://user-images.githubusercontent.com/86980802/140668994-844894fe-f655-431e-b2fb-36a954199778.jpg)


<h2> The convolution operation </h2>

The fundamental difference between a densely connected layer and a convolution layer is this: Dense layers learn global patterns in their input feature space (for example,
for a MNIST digit, patterns involving all pixels), whereas convolution layers learn local patterns, in the case of images, patterns found in small 2D windows
of the inputs.

![image](https://user-images.githubusercontent.com/86980802/140677767-ad7e7df1-c37d-4511-92af-3e3bbbfebc33.png)

<li> The patterns they learn are translation invariant. After learning a certain pattern in the lower-right corner of a picture, a convnet can recognize it anywhere: for
example, in the upper-left corner. A densely connected network would have to learn the pattern anew if it appeared at a new location. This makes convnets data efficient when 
processing images  they need fewer training samples to learn representations that have generalization power.
  
  <li> They can learn spatial hierarchies of patterns. A first convolution layer will learn small local patterns such as edges, a second convolution layer will
learn larger patterns made of the features of the first layers, and so on. This allows convnets to efficiently learn increasingly complex and abstract visual concepts
 
    
*Convolutions operate over 3D tensors, called feature maps*
   
![image](https://user-images.githubusercontent.com/86980802/140685652-47774831-dd1c-4d8d-a8ce-469a802301f4.png)
    
    
    
```
(28, 28, 1) two spatial axes (height and width) as well as a depth axis (also called the channels axis).
```

    


![image](https://user-images.githubusercontent.com/86980802/140691391-e1ec1217-8829-4842-b4ca-0084ba8da74b.png)

*Response map* of the filter over the input, indicating the response of that filter pattern at
different locations in the input.

The convolution operation extracts patches from its input feature map and applies the same transformation to all of these patches, producing an output
*feature map*.

<img src="https://forum.huawei.com/enterprise/en/data/attachment/forum/202108/24/103820cexymqo330bn4ye3.png?1.png" data-src="https://forum.huawei.com/enterprise/en/data/attachment/forum/202108/24/103820cexymqo330bn4ye3.png?1.png" data-is-lazy="1" alt="Weight sharing" data-is-loaded="1">

    
    
<li> Size of the patches extracted from the inputs—These are typically 3 × 3 or 5 × 5. 
<li> Depth of the output feature map—The number of filters computed by the convolution.

  
```
Conv2D(output_depth, (window_height, window_width)).
model.add(layers.Conv2D(32, (3, 3), activation='relu', input_shape=(28, 28, 1))) **32 filters**
```

Note that the output width and height may differ from the input width and height.
They may differ for two reasons:
<li> Border effects, which can be countered by padding the input feature map
<li> The use of strides

**Padding**
  
  If you want to get an output feature map with the same spatial dimensions as the
input, you can use padding. Padding consists of adding an appropriate number of rows
and columns on each side of the input feature map so as to make it possible to fit center
convolution windows around every input tile.
  
  ![Tex2Img_1636353471](https://user-images.githubusercontent.com/86980802/140695343-c4dfa081-937e-4cf6-8f3a-ee952f0275d7.jpg)

Where K is the filter size.
  
  
For instance, For a 3 × 3 window, you add one column
on the right, one column on the left, one row at the top, and one row at the
bottom. For a 5 × 5 window, you add two rows. 

In Conv2D layers, padding is configurable via the padding argument, which takes two
values: "valid", which means no padding (only valid window locations will be used);
and "same", which means “pad in such a way as to have an output with the same width
and height as the input.” The padding argument defaults to "valid".
  

**Convolution Strides** 
The other factor that can influence output size is the notion of strides. The description
of convolution so far has assumed that the center tiles of the convolution windows are
all contiguous. But the distance between two successive windows is a parameter of the
convolution, called its stride, which defaults to 1. It’s possible to have strided convolutions:
convolutions with a stride higher than 1.

  For instance, 3x3 convolution with 2x2 strides:
  
  ![image](https://user-images.githubusercontent.com/86980802/140695974-1b7f6896-49c9-4ed6-bf94-b065c30e3a9b.png)

  
Convolutional layers are not only applied to input data, e.g. raw pixel values, but they can also be applied to the output of other layers.
The stacking of convolutional layers allows a hierarchical decomposition of the input.
Consider that the filters that operate directly on the raw pixel values will learn to extract low-level features, such as lines.
The filters that operate on the output of the first line layers may extract features that are combinations of lower-level features, such as features that comprise multiple lines to express shapes.
This process continues until very deep layers are extracting faces, animals, houses, and so on.
  
  <h2> The max-pooling operation </h2>
  
The role of max pooling: to aggressively downsample feature maps, much like
strided convolutions.
Max pooling consists of extracting windows from the input feature maps and outputting
the max value of each channel. It’s conceptually similar to convolution, except
that instead of transforming local patches via a learned linear transformation (the convolution
kernel), they’re transformed via a hardcoded max tensor operation
  
  ![CVN](https://user-images.githubusercontent.com/86980802/140704067-97414094-cb16-45af-ab23-e4080879ee87.jpg)

  
