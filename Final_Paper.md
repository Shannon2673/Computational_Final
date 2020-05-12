Shannon Gallagher 
PHY 325



Deep Learning and Deep Saturation
What Neural Networks Can Tell Us about Percolation

Introduction

Computational physics simulations are an efficient method for determining the emergent properties of a multibody system based off of individual interactions. Percolation is a model, in which the micro scale interactions are accurately modeled can be scaled up to a macro size without losing accuracy [1]. The way that water percolates through a real life or simulated sandbox can be extrapolated to applications in agriculture or civil engineering. As part of the hydrologic cycle water filters through sediment in the less dense zone of aeration to the zone of saturation [2]. However when soil is compacted to no longer have “pore space” between its components it is unable to absorb water and allow it to pass to the water table [3]. Soil with insufficient pore space can have negative consequences from crops receiving insufficient hydration to flooding.

My research question is:
Can a neural network determine if water percolates through a 2D lattice if trained with extreme data?


Model:

In my project I modeled groundwater percolation with a two dimensional lattice of interacting sites composed of either empty pore space or sediment. This lattice is an iterated 2D 50 by 50 numpy array in python3 jupyter notebooks. To analyze the results of these simulations I trained a neural network to identify if the water travels through the soil based off of initial conditions. The training and test data are composed of arrays containing the initial conditions of the simulation, combined with vectors that represent the correct label. The two possible labels are percolated and percolated. The training data was composed of only extreme data 10% 20% 80% and 90% rock, while the test data was composed of the intermediate fractions.

[(For more detail see 2D_Lattice_and_Data -> Data_Generation_and_Lattice.ipynb)](https://github.com/Shannon2673/Computational_Final/blob/master/2dLattice_and_Data/Data_Generation_and_Lattice.ipynb)



 A neural network is a machine learning tool, built of nodes which take data from samples and interact with each other before producing an output. A simple model for a node would be a gate in digital electronics, which produces a value based off input values. For example an OR gate will output true if at least one of its inputs is true. We can say that at least one input being true meets the threshold for a true output for that gate. This is a binary piecewise function, since if the inputs are greater than the threshold the output is one, and otherwise the output is zero.In a neural network this threshold is commonly called the bias. 

 Nodes do not treat their inputs equally. Each input is multiplied by a weight, which akin to the bias is initially randomized. To create a network that accurately labels its inputs(percolated or unpercolated,) the network must be trained. Training consists of a series of small improvements based off of small changes in the weights and biases. To make small changes in an output we need to move away from a step function, which can only be correct or incorrect.
This is accomplished by sending node outputs through a smooth sigmoid function. Since the function is continuous a small change in the input which is based on the weights and bias, makes a small change in the output. Additionally the sigmoid function is differentiable, which is crucial for our numerical training methods.
While it may seem arbitrary to choose the sigmoid function to describe our nodes’ behavior, it is a common choice for neural networks. The sigmoid function has behavior that is similar to a binary node with a threshold. If the weighted inputs are much less than the bias the result is very close to zero, and if the weighted inputs are much larger than the bias the result is very close to one.

To train the network I compared the initial outputs of the network generated from a training set to the actual desired value. From the application of the mean squared error function   a value representing how incorrect the network was in its prediction was produced. This value is known as the cost. To avoid rounding errors in python if values are within 10% of the desired label they are considered correct.

The ultimate goal was to minimize the cost in the network. The minimum cost is found by using a process called stochastic gradient descent. In this process the gradient with respect to the weights and biases is found and averaged across a batch, then the weights and biases are shifted in opposite direction of the gradient towards the minimum. The size of this shift is scaled by the value eta, also known as the learning step. 

The gradient is determined by a process called backpropagation which is an application of the chain rule. The cost derivative with respect to each weight and bias is calculated by finding the derivatives between nodes and multiplying them. This is done with matrix operations so a partial derivative is calculated for every weight and bias as a component of the cost gradient. 

[(For more detail see Figure_Creation -> Neural_Network_Training_and_Results.ipynb)](https://github.com/Shannon2673/Computational_Final/blob/master/Figure_Creation/Neural_Network_Training_and_Results.ipynb)

The first layer of this neural network will be made of 2500 nodes for each cell in the lattice. The hidden layer will have 100 nodes. And the last layer will have 2 nodes for each classification. The value contained in the last two nodes between 0 and 1 represents the confidence of the network of each respective label.

Results:
To determine the best method to train the neural network, I trained several randomized networks for 30 learning iterations with different learning steps between 0.1 and 5. Learning steps between 1 and 3 had the most promising results, in which there was a sustained increase in accuracy with more training.

[(For more detail see Figure_Creation ->Figure_maker.ipynb)](https://github.com/Shannon2673/Computational_Final/blob/master/Figure_Creation/Figure_Maker.ipynb)

Analysis:

The most optimal learning step size was 3. This was most likely due to the fact that step sizes below 1 did not reach their best accuracy before the end of training, and learning step sizes greater than 3 overcorrected and were overtrained to specific data points.

Ultimately the neural network failed to categorize the percolation data correctly. The best accuracy with the optimized learning step size was 48.3%. This is not sufficient, given there are only two labels for the system, which means the network was less accurate than a guess. This inaccuracy is likely due to simplifications made due to a lack of computational power. Repetition of training with more hidden layers and hidden layer nodes would likely produce more accurate results.

Summary:

I determined that a simple 3 layer neural network cannot accurately determine if water percolated through a 2D lattice when trained with extreme data. This is significant because in future applications of models for ground water percolation individuals should ensure that their analytic tools are of sufficient complexity prior to training and data analysis. Additionally I determined that step size is crucial in training a neural network to be accurate as possible, and for this specific network the best step size is 3. 

For my own personal goals I learned a lot from this project. I built a 2d lattice to model ground water percolation, animated it, and wrote functions to generate training and test data based off of its behavior. I built a neural network.  I learned about stochastic gradient descent, and how to apply it to neural network training. And lastly I leaned how to optimize the hyperparameters of the network training for the best possible result.




citations:
[1]Berkowitz, Brian & Balberg, Isaac. (1993)[Online]. Percolation theory and its application to groundwater hydrology. Water Resources Research

[2] Anderson W. Geology and Water [Online]. Geology and Water University of Northern Iowa. https://uni.edu/~andersow/geologyandwater.html [11 May 2020].

[3]Voyle G, Hudson H. What to do about compacted soil [Online]. MSU Extension: 2018. https://www.canr.msu.edu/news/what_to_do_about_compacted_soil [11 May 2020].

Forest Fire Model [Online]. The Forest-fire model. 
https://scipython.com/blog/the-forest-fire-model/ [10 May 2020].

Nielsen, A. M. Neural Networks and Deep Learning [Online]. Neural networks and deep learning Determination Press: 2019. http://neuralnetworksanddeeplearning.com/index.html [11 May 2020].
