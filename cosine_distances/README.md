For this experiment, I used the CIFAR 10 dataset. The model setups are exactly
the same as the initial template, except that the input layer now has the
shape (32, 32, 3). In the graphs that I obtained, the line labeled 0 are
calculated using the weights of the first layer, 1 the biases of the first
layer, 2 the weights of the second layer, etc. When you read the graphs, make
sure to look at the scales, labels, and colours.
I will post the full template that I used for the experiment on githhub. The
seed that I used for all the experiments are 29876.
For the sake of simplifying the description of the graphs, I will go through
the process of federated learning, and name and label the weights here:
First we have the community model, with weights W1. We distribute it to all
the clients, and train them so that they have weights W2. Then we average
different clients' W2s and get the new community model weights W3. We train
further and get client weights W4.
In the experiments, I plotted the cosine distances between W1 and W3 to get
how much the community model is updated each time, W1 and W2 to get how much
each client is trained each round, W2 and W3 to see how the changes in client
weights differ from each other, and W2 and W4 to get how much the client model
changes in each round.
Some interpretations of the graph: actually in federated learning, the biases
are changed much more in each training round. This even holds true for the
case with IID data, which shouldn't be the case as the data come from the same
distribution. As for the weights, we also see that the weights in the first
layer are being trained the most.
And these lead to some potentialities for future experiments: first we can
examine how the models behave when we feed them with exactly the same data,
and we will separate the weights and biases, and focus on the weights with
more detail.
