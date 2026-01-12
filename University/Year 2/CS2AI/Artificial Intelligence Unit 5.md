### Lecture 5 "Neural Networks and Deep Learning"
In previous units like [[Artificial Intelligence Unit 4]] and [[Artificial Intelligence Unit 2]] we've talked about the dilemma of identifying classes amongst a group of data. We've discussed ML models like Decision Trees and K-Nearest Neighbour.
Now we will discuss Artificial Neural Networks.

The Neuron involves dendrites, the point of receiving input from other cells, the cell body or "Soma" where information is processed, the axon or output structure of the Neuron and the synapses where two nerve cells can connect.
![[{65CFA6EB-8161-4A39-9E50-6A7C8E700CB2}.png]]
Now we can construct an artificial Neuron:
![[{7DE82232-BADF-4CED-92A5-CCDF67D48DB9}.png]]
![[{E8559E39-C1D8-433D-A927-41593C119390}.png]]
Dendrites are the inputs of an artificial Neuron.
Synapses are the weights in an artificial Neuron.
Soma is the processing unit of the artificial Neuron.
Axon is the output of a cell in the artificial Neuron.

We also have activation functions to consider:
The perceptron computes a weighted sum $(w^T x + b)$ and passes it through an activation function to get the final output. This determines what kind of output the artificial Neuron will produce.
Different problems also require different activation functions, 
"Step Functions" or Binary Classifications give us an output of either 0 or 1 (this would be a hard decision, like is X email spam?).
![[Pasted image 20260112213838.png]]
"Sigmoid Functions" or Probabilistic Binary Classifications give us an output that follows a smooth curve between 0 and 1, a soft decision or a probability, e.g., "What's the probability that this is spam?"
![[Pasted image 20260112214004.png]]
With a regression problem, or ReLU, the activation function will produce positive values or 0 (which also can represent negative values). This is useful for predicting something that can't be negative, like an amount of items that can sell in a market.
![[Pasted image 20260112214015.png]]
With a regression problem that involves both positive and negative values, known as Tanh, the activation function will produce outputs between -1 and 1. This is useful for scenarios like "How much is the temperature changing?" which could be +5 or -5 degrees.
![[Pasted image 20260112214204.png]]
The choice of activation function matters because it determines our output (binary, probability, continuous), what problems we can solve and how the perceptron learns.

![[Pasted image 20260112215140.png]]
We have to also get rid of the "bias" or the flexibility of the model. Bias allows the decision boundary to shift position, which we need for solving real problems. It's comparable to the y-intercept in a graph equation.
![[{A652241B-4F82-4785-B817-ABAF7578031E}.png]]

"Computation by Perceptron"
Let's say we have a perceptron with two binary inputs, $x_1, x_2 \in$ {0,1} and one dummy input $x_0$ = 1 that uses the unit step activation function:
$$\varphi(z) = \begin{cases} 0, & \text{if } z < 0 \\ 1, & \text{if } z \geq 0 \end{cases}$$
The weights corresponding to the inputs have the following values:
$$w_0 = 1, w_1 = 1, w_2 = -2$$
We also have the dummy input of $x_0$ = 1.
So to figure out the different input patterns that the perceptron can output we have to do the following (in this scenario using $x_1 = 0, x_2 = 0$)
"Write out the formula"
weighted sum = $w_0 \times x_0 + w_1 \times x_1 + w_2 \times x_2$
"Plug in the numbers"
weighted sum = 1 x 1 + 1 x 0 + (-2) x 0
*There's a 0 in place of $x_1$ as we have no value there.*
"Do the multiplication"
weighted sum = 1 + 0 + 0
"Add them up"
weighted sum = 1

Then we apply the unit step activation function:
Is 1 < 0? NO!
Is 1 $\geq$ 0? YES!
So output y = 1

Now let's try with $x_1 = 0, x_2 = 1$:
"Write out the formula"
weighted sum = $w_0 \times x_0 + w_1 \times x_1 + w_2 \times x_2$
"Plug in the numbers"
weighted sum = 1 x 1 + 1 x 0 + (-2) x 1
*There's a 0 in place of $x_1$ as we have no value there.*
"Do the multiplication"
weighted sum = 1 + 0 + (-2)
"Add them up"
weighted sum = -1

Then we apply the unit step activation function:
Is -1 < 0? YES!
So output y = 0

Now let's try with $x_1 = 1, x_2 = 0$:
"Write out the formula"
weighted sum = $w_0 \times x_0 + w_1 \times x_1 + w_2 \times x_2$
"Plug in the numbers"
weighted sum = 1 x 1 + 1 x 1 + (-2) x 0
*There's a 0 in place of $x_1$ as we have no value there.*
"Do the multiplication"
weighted sum = 1 + 1 + 0
"Add them up"
weighted sum = 2

Then we apply the unit step activation function:
Is 2 $\geq$ 0? YES!
So output y = 1

Now let's try with $x_1 = 1, x_2 = 1$:
"Write out the formula"
weighted sum = $w_0 \times x_0 + w_1 \times x_1 + w_2 \times x_2$
"Plug in the numbers"
weighted sum = 1 x 1 + 1 x 1 + (-2) x 1
*There's a 0 in place of $x_1$ as we have no value there.*
"Do the multiplication"
weighted sum = 1 + 1 + (-2)
"Add them up"
weighted sum = 0

Then we apply the unit step activation function:
Is 0 $\geq$ 0? YES! It's EQUAL TO 0!
So output y = 1

We have now set the values of $x_1$ and $x_2$ four times, setting two different values (0 and 1) for each x. This means we have 4 patterns, but we represent it in binary inputs i.e., 4 input patterns = 2$^2$.
These input patterns can be mapped out as:
- $x_1$ = 0, 0, 1, 1
- $x_2$ = 0, 1, 0, 1

