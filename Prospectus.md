Shannon Gallagher 
PHY 325


Deep Learning and Deep Saturation
What Neural Networks Can Tell Us about Percolation


	Computational physics simulations are an efficient method for determining the 
emergent properties based off a multibody system based off of individual interactions. Percolation is one model which once the micro scale interactions are accurately modeled can be scaled up to a macro size without losing accuracy [citation 1]. The way that water percolates through a real life or simulated sandbox can be extrapolated to applications in agriculture or civil engineering. As part of the hydrologic cycle water filters through sediment in the less dense zone of aeration to the zone of saturation [citation 2]. However when soil is compacted to no longer have “pore space” between its components it is unable to absorb water and allow it to pass to the water table [citation 3]. Soil with insufficient pore space can have negative consequences from crops receiving insufficient hydration to flooding.

	In my project I will model groundwater percolation with a two dimensional lattice of interacting sites composed of either empty pore space or sediment. This lattice will be an iterated 2D 50 by 50 numpy array in python jupyter notebooks. To analyze the results of these simulations I will train a neural network to identify the final ground saturation based off of initial conditions.

 A neural network is a machine learning tool, built of nodes which take data from samples and interact with each other before producing an output. A simple model for a node would be a gate in digital electronics, which produces a value based off input values. For example an OR gate will output true if at least one of its inputs is true. We can say that at least one input being true meets the threshold for a true output for that gate. One difference with . nodes is that their inputs are not considered equally. Each input has a weight, which akin to the threshold is initially randomized. To make these weights and threshold accurate the neural network must be trained. To train the network we compare the initial outputs of the network generated from a training set to the actual desired value. Even when randomized some nodes will contribute to correct guesses of the desired output. The nodes that contribute to correct answers will have their weights increased, while nodes that contribute to inaccurate answers will be decreased.

 Some nodes contribute more than others, decided by weights that are initially randomized. Nodes with greater weights add to the output more, much like how values with larger weights make a bigger difference in weighted averages. In order to make the neural network successful it must be trained on a data set, much like other machine learning methods. Nodes which contribute to desired outputs will have their weights increased. Eventually through iterations of training the neural network will accurately produce the desired values.

The first layer of this neural network will be made of 250 nodes for each cell in the lattice. The last layer will have 11 nodes of percentages saturated from 0% to 100% in increments of 10%. The neural network will have two to three hidden layers between the input and output layers. 

This will answer the question:

Can a neural network determine the end state of a porous medium based off of initial conditions of a 2d grid model? 




citations:
1. https://www.researchgate.net/publication/241060386_Percolation_theory_and_its_application_to_groundwater_hydrology

2.
https://uni.edu/~andersow/geologyandwater.html

3.
https://www.canr.msu.edu/news/what_to_do_about_compacted_soil
