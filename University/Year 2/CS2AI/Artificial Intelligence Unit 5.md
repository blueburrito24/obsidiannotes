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
If we include the dummy input $x_0$ = 1,
- $x_0$ = 1, 1, 1, 1
- $x_1$ = 0, 0, 1, 1
- $x_2$ = 0, 1, 0, 1
This is because we need to multiply the bias weight w$_0$.

To get the weighted sum for each input pattern, we take the weights $w_0 = 1, w_1 = 1, w_2 = -2$ and the different values of each row from above.
So we take these weights alongside the input patterns and create the following formula:
$$w^T x = (w_0 \times x_0) + (w_1 \times x_1) + (w_2 \times x_2)$$
We substitute the weight values in:
$$w^T x = (1\times x_0) + (1 \times x_1) + (-2 \times x_2)$$
$$w^T x = x_0 + x_1 -2x_2$$
Then we plug in the numbers from the rows of input patterns and we get:
$$w^T x = 1 + 0 - 2(0)$$
We multiply:
$$w^T x = 1 + 0 - 0$$
and add:
$$w^T x = 1$$
So our weighted sum is 1!
![[{524E15AB-7833-43E2-9ADE-D054D1FCC7CF}.png]]

### "Training a Perceptron for Logical OR & AND"
"Logical OR arguments"
We want to train a perceptron to behave like a logical OR gate. This is a gate that outputs a true output if atleast one input is true.
![[{A6006C4D-68A1-46D5-8703-14839DA670FF}.png]]
If both inputs are 0, then the output is 0 (as seen in the target table).
In the "structure" we have the inputs, the weights, the sum/activation and the output (from left to right).
The activation function, seen on the left, says that if the weighted sum value is negative then it outputs 0, if its 0 or positive then it outputs 1.
So we get the present input formula.

Now, we have a perceptron with unknown weight values, $w_0, w_1, w_2$. We want to find the values of these weights so the perceptron outputs the correct answer for "OR" arguments.
The way we do this is we look at the above "OR" table (featuring $x_1, x_2$ and $y_{target}$) and its rows of inputs and target outputs, and figure out the weights needed to achieve these target outputs.

For example, if we want $x_1 = 0, x_2 = 0$ to output $y=0$,
we have the inputs, (dummy) $x_0 = 1, x_1 = 0, x_2 = 0$.
The perceptron takes the weighted sum = $w_0 \times x_0 + w_1 \times x_1 + w_2 \times x_2$ 
and plugs in our inputs:
$$= w_0 \times 1 + w_1 \times 0 + w_2 \times 0$$
$$= w_0 + 0 + 0$$
$$= w_0$$
So when both inputs are 0, the weighted sum equals $w_0$.
We want y to equal 0, so let's compare the weighted sum with our parameters:
if weighted sum, or $w_0$ < 0 -> output 0
if $w_0$ $\geq$ 0 -> output 1
So if we want our target output, y, to be 0, $w_0$ (the bias) needs to be less than 0.

Now let's look at our second pattern, $x_1 = 0, x_2 = 1$ and output y=1.
We plug our inputs into the weighted sum = $w_0 \times x_0 + w_1 \times x_1 + w_2 \times x_2$
$$= w_0 \times 1 + w_1 \times 0 + w_2 \times 1$$
$$= w_0 + 0 + w_2$$
$$= w_0 + w_2$$
So the weighted sum equals $w_0 + w_2$.
We want our target output, y, to equal 1.
if $w_0 + w_2$ < 0 -> output 0
if $w_0 + w_2$ $\geq$ 0 -> output 1
So for y to = 1, we need $w_0$ to be more than or equal to 0.
We need $w_0 + w_2 \geq 0$.
We can say this as "when $x_2=1$, the weight $w_2$ must be positive enough to overcome the negative bias $w_0$ and make the sum non-negative."
$$w_0 + w_2 \geq 0$$
$$\rightarrow w_2 \geq -w_0$$
Since $w_0$ here is negative, $-w_0$ is positive, so $w_2$ needs to be atleast equal to that positive value.

Now our third pattern, $x_1 = 1, x_2 = 0$ with a target output of y=1.
We plug our inputs into the weighted sum = $w_0 \times x_0 + w_1 \times x_1 + w_2 \times x_2$
$$= w_0 \times 1 + w_1 \times 1 + w_2 \times 0$$
$$= w_0 + w_1 + 0$$
$$= w_0 + w_1$$
We want our target output, y, to equal 1.
if $w_0 + w_1$ < 0 -> output 0
if $w_0 + w_1$ $\geq$ 0 -> output 1
So we need the weighted sum to be equal to or greater than 0.
$w_0 + w_1 \geq 0$.

Now our fourth pattern, $x_1 = 1, x_2 = 1$ with a target output of y=1.
We plug our inputs into the weighted sum = $w_0 \times x_0 + w_1 \times x_1 + w_2 \times x_2$
$$= w_0 \times 1 + w_1 \times 1 + w_2 \times 1$$
$$= w_0 + w_1 + w_2$$
We want our target output, y, to equal 1.
if $w_0 + w_1 + w_2$ < 0 -> output 0
if $w_0 + w_1 + w_2$ $\geq$ 0 -> output 1
So we need the weighted sum to be equal to or greater than 0.
$w_0 + w_1 + w_2\geq 0$.
"When both inputs are 1, the combined effect of $w_1, w_2$ must overcome the negative bias of $w_0.$"
![[{ACAC2894-DCF5-4C0D-B040-DA537F073168}.png]]Remember, the bias matters because it gives us a range to operate in.
Without a bias, let's say as a graph, our line could only go through the origin point (0,0).
With a bias, we can move around the line anywhere we want, creating a decision boundary.

"Logical AND arguments"
Similar to the process for "OR" arguments, we now will look at decision arguments for an "AND" gate.
"AND" only outputs true (1) when both inputs are true (1).
![[{34DDD5AE-F02E-43B4-B53D-91A6583F90F4}.png]]
Here is a truth table of what values we would get from an AND gate.
If both inputs are 0, y=0, if both are 1, y=0. Unlike OR, one input being 1 and the other being 0 gives us y=0.
![[{927BA588-E58A-4A5A-8565-3D7B5D3FCCA0}.png]]
We use the same structure and activation function
$$\varphi(z) = \begin{cases} 0, & \text{if } z < 0 \\ 1, & \text{if } z \geq 0 \end{cases}$$
, and the same output formula.
$$y = \begin{cases} 0, & \text{if } w_0 + w_1x_1 + w_2x_2 < 0 \\ 1, & \text{if } w_0 + w_1x_1 + w_2x_2 \geq 0 \end{cases}$$
