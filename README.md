# Demonstration of the benefits of Physics-Informmed Neural Network

Physics Informed Neural Networks are deep learning frameworks that embed the knowledge of any physical system. This is often done through adding a residual of the partial differential equation describing the system into the loss function of the neural network. Since most physical laws that govern the dynamics of a system can be expressed as a partial differential equation (PDE), when the PDE residual is added into the loss function, it acts as a regularisation agent in the training of the network. 
Effectively, the PDE acts as a soft constraint on the space of admissible solutions and increases the accuracy of the function approximation.

Benefits:
1. Enhances the information content of the available data by embedding information
2. Ensures that prediction is physically possible
3. Reduces the amount of data required for training

In this repository, a simple kinematics problem is used to demonstrate the benefits of PINNs. 
To begin, we start with a one dimensional example of a ball being thrown upwards.

The physical law that the ball has to adhere to is the gravitational forces, as shown in the equation.
![alt text](http://url/to/img.png)

This equation is simple, non-linear and one dimensional. It assumes that a body in free-fall is subjected to a gravitational acceleration of 10m/s2.

The initial conditions that have bee arbitrarily set are at t=0 and t=10, the displacement would be zero, essentially meaning that the ball will drop back after 10 seconds. 
