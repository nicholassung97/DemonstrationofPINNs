# Demonstration of the benefits of Physics-Informmed Neural Network

Physics Informed Neural Networks are deep learning frameworks that embed the knowledge of any physical system. This is often done through adding a residual of the partial differential equation describing the system into the loss function of the neural network. Since most physical laws that govern the dynamics of a system can be expressed as a partial differential equation (PDE), when the PDE residual is added into the loss function, it acts as a regularisation agent in the training of the network. 
Effectively, the PDE acts as a soft constraint on the space of admissible solutions and increases the accuracy of the function approximation.

Benefits:
1. Enhances the information content of the available data by embedding information
2. Ensures that prediction is physically possible
3. Reduces the amount of data required for training
