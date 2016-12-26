If you want to practice on your own, check out my initial commit from master.
The latest commit contains my solution.
Learning and Loss

Like MiniFlow in its current state, neural networks take inputs and produce outputs. But unlike MiniFlow in its current state, neural networks can improve the accuracy of their outputs over time (it's hard to imagine improving the accuracy of Add over time!). To explore why accuracy matters, I want you to first implement a trickier (and more useful!) node than Add: the Linear node.
The Linear Function
As described by Charles and Michael, a Neuron calculates the weighted sum of its inputs.

As described by Charles and Michael, a Neuron calculates the weighted sum of its inputs.

Think back to Neural Networks lesson with Charles and Michael. A simple artificial neuron depends on three components:

    input, x
    weight, w
    bias, b

The output, o, is just the weighted sum of the inputs plus the bias:
Equation (1)

Equation (1)

Remember, by varying the weights, you can vary the amount of influence any given input has on the output. The learning aspect of neural networks takes place during a process known as backpropagation. In backpropogation, the network modifies the weights to improve the network's output accuracy. You'll be applying all of this shortly.

In this next quiz, you'll try to build a linear neuron that generates an output by applying a simplified version of Equation (1). Linear should take an list of inbound neurons of length n, a list of weights of length n, and a bias.
Instructions

    Open nn.py below. Read through the neural network to see the expected output of Linear.
    Open miniflow.py below. Modify Linear, which is a subclass of Neuron, to generate an output with Equation (1).

(Hint: you could use numpy to solve this quiz if you'd like, but it's possible to solve this with vanilla Python.)
