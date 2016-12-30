Shift your thinking here to the edges between layers.

Shift your thinking here to the edges between layers.

Linear algebra nicely reflects the idea of transforming values between layers in a graph. In fact, the concept of a transform does exactly what a layer should do - it converts inputs to outputs in many dimensions.

Let's go back to Equation (1).
Equation (1)

Equation (1)

In the old paradigm of neurons, a single output, o, is the result of summing n weighted inputs (x * w) with a bias, b. In the new paradigm of layers with multiple inputs and multiple outputs, Equation (1) needs revision with vectors and matrices.

For the rest of this section we'll denote x as X and w as W since they are now matrices, b is a vector so it will still be lowercase b.

Consider a Linear layer with 1 input and k outputs (mapping 1 input to k outputs). In this context an input/output is synonymous with a feature.

In this case X is a 1 by 1 matrix.
1 by 1 matrix, 1 element.

1 by 1 matrix, 1 element.

W becomes a 1 by k matrix (looks like a row).
A 1 by k weights row matrix.

A 1 by k weights row matrix.

The result of the matrix multiplication of X and W is a 1 by k matrix. Since b is also a 1 by k row matrix (1 bias per output), b is added to the output of the X and W matrix multiplication.

What if we are mapping n inputs to k outputs?

Then X is now a 1 by n matrix and W is a n by k matrix. The result of the matrix multiplication is still a 1 by k matrix so the use of the biases remain the same.
X is now a 1 by n matrix, n inputs/features.

X is now a 1 by n matrix, n inputs/features.
W is now a n by k matrix.

W is now a n by k matrix.
Row matrix of biases, one for each output.

Row matrix of biases, one for each output.

Let's take a look at an example of n inputs. Consider an 28px by 28px greyscale image, as is in the case of images in the MNIST dataset. We can reshape the image such that it's a 1 by 784 matrix, n = 784. Each pixel is an input/feature. Here's an animated example emphasizing a pixel is a feature.
Your browser does not support the video tag.

In practice, it's common to feed in multiple data examples in each forward pass rather than just 1. The reasoning for this is the examples can be processed in parallel, resulting in big performance gains. The number of examples is called the batch size. Common numbers for the batch size are 32, 64, 128, 256, 512. Generally, it's the most we can comfortably fit in memory.

What does this mean for X, W and b?

X becomes a m by n matrix and W and b remain the same. The result of the matrix multiplication is now m by k, so the addition of b is broadcast over each row.
X is now an m by n matrix. Each row has n inputs/features.

X is now an m by n matrix. Each row has n inputs/features.

In the context of MNIST each row of X is an image reshaped from 28 by 28 to 1 by 784.

Equation (1) turns into:
Equation (2).

Equation (2).

Equation (2) can also be viewed as Z = XW + B where B is the biases vector, b, stacked m times as a row. Due to broadcasting it's abbreviated to Z = XW + b.

I want you to rebuild Linear as a Layer, rather than a Neuron. To do so, you'll use the venerable Python math package numpy to make your life easier. numpy is often abbreviated as np, so we'll refer to it as np when referring to code.

I used np.array (documentation) to create the matrices and vectors. You'll want to use np.dot, which functions as matrix multiplication for 2D arrays (documentation), to multiply the input and weights matrices from Equation (2). It's also worth noting that numpy actually overloads the __add__ operator so you can use it directly with np.array (eg. np.array() + np.array()).
Instructions

    Open nn.py. See how the neural network implements the Linear layer.
    Open miniflow.py. Implement Equation (2) within the forward pass for the Linear layer.
    Test your work!

