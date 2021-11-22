<h1> Recurrent neural networks (RNN)</h1>

A recurrent neural network (RNN) processes sequences by iterating through the sequence elements and maintaining a state containing information relative
to what it has seen so far. An RNN is a type of neural network that has an internal loop

![RNN1](https://user-images.githubusercontent.com/86980802/142926674-0830ea17-a0df-4de8-a659-cf621fac915a.png)


What changes is that this data point is no longer processed in a single step; rather, the network internally loops over sequence elements.

RNN takes as input a sequence of vectors, which you’ll encode as a 2D tensor of size (*timesteps, input_features*). It loops over timesteps, and at each timestep, 
it considers its current state at *t* and the input at *t* (of shape (*input_ features*,), and combines them to obtain the output at *t*.

``` 
#Pseudocode RNN
state_t = 0
for input_t in input_sequence:
  output_t = f(input_t, state_t)
  state_t = output_t 
```
The transformation of the input and state into an output will be parameterized by two matrices, W and U, and a bias vector.

```
state_t = 0
for input_t in input_sequence:
output_t = activation(dot(W, input_t) + dot(U, state_t) + b)
state_t = output_t

```

RNN is a for loop that reuses quantities computed during the previous iteration of the loop. 

<h2> Different RNNs </h2>

<li> SimpleRNN
<li> Long Short-Term Memory (LSTM)
<li> Gated Recurrent Unit (GRU)

  
**SimpleRNN**
  

  
![gatesimple](https://user-images.githubusercontent.com/86980802/142936832-45fde359-d0e7-4bbf-b8ca-79b94b4557c6.png)

  The final output is a 2D tensor of shape (*timesteps, output_features*), where each timestep is the output of the loop at time *t*.
Each timestep *t* in the output tensor contains information about timesteps 0 to *t* in the input sequence—about the entire past. For this reason, in many
cases, you don’t need this full sequence of outputs; you just need the last output (*output_t* at the end of the loop), because it already contains information
about the entire sequence.

![gates1](https://user-images.githubusercontent.com/86980802/142935094-45af0476-93d8-48e7-a338-144179a02740.jpg) 

  
![gates2](https://user-images.githubusercontent.com/86980802/142936539-84bf2843-c588-44df-96b4-2ce7e7d20c4e.png)
Source: https://stanford.edu/~shervine/teaching/cs-230/cheatsheet-recurrent-neural-networks 
  
  
  

  
  

  
