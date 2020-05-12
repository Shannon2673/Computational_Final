This data was compiled for Shannon Gallagher's Computational Physics Final (S20).

In this same folder is a jupyter notebook for data creation.
Files need to be moved to main folder to be implemented in training.

The files currently in this folder include:

training_data.npy: (for 100 x100 lattice)
A numpy array of 1000 tuples of initial conditions and final percolation states. This set of training data contains the [.1,.2,.8,.9] rock fraction cases of extreme values.

test_data.npy:(for 100 x100 lattice)
A numpy array of 1000 tuples of initial conditions and final percolation states. This set of test data contains the [.3,.4,.5,.6] rock fractions near the critical point.

training_data.npy: (for 50 x50 lattice)
A numpy array of 100 tuples of initial conditions and final percolation states. This set of training data contains the [.1,.2,.8,.9] rock fraction cases of extreme values.

test_data_small.npy:(for 50 x50 lattice)
A numpy array of 100 tuples of initial conditions and final percolation states. This set of test data contains the [.3,.4,.5,.6] rock fractions near the critical point.


training_extreme.npy:(for 50 x50 lattice)
A numpy array of 10000 tuples of initial conditions and final percolation states. This set of training data contains the [.1,.2,.8,.9] rock fraction cases of extreme values.

training_plural.npy:(for 50 x50 lattice)
A numpy array of 10000 tuples of initial conditions and final percolation states. This set of training data contains the [.1,.2,.3,.4,.5,.6,.7,.8,.9] rock fraction cases of extreme values.

