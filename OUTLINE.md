Shannon Gallagher 
4/27/20

Current outline of tasks between 4/27/20-4/29/20

Tasks:
- construct neural network to begin training moving into the weekend
- save percolation animations in mp4 or gif format for presentation
- get percolation_sim function to generate all frames of simulation

Structure of functions:

-percolation_sim
  -input: initial parameters
  -output: movie of water motion + arrays representing initial and final states of simualtion
  -check: If movie appears plausible the function works
 
 -neural network(made of different fucntions, but for this purpose a black box)
  -input: first frame of simulation as numpy array as first layer of neural-net
  -output: value of last layers 11 options (0-100% in increments of 10% submerged)
  -check: if the neural network accurately identifies the percolation thresholds,
  + correcly identifies final percentage based off of initial conditions.


Tasks from last week
-upload image of neural network structure to repository




4/22/20

Current outline for tasks between 4/22/20-4/27/20

-Establish the infrastructure of the repository for project
  -create file that will act as library of functions for project
  -create file for main project flow (point a to point b)
  -create file for visuals and figures for the project
  -create file for references in AIP format
  
 -Populate references file with at least 3 references of background
 
 -Begin writing code 2D lattice to convert to neural network
 -Diagram neural network on paper or whiteboard and add image to repository.
