# Demonstration of the benefits of Physics-Informmed Neural Network

Physics Informed Neural Networks are deep learning frameworks that embed the knowledge of any physical system. This is often done through adding a residual of the partial differential equation describing the system into the loss function of the neural network. Since most physical laws that govern the dynamics of a system can be expressed as a partial differential equation (PDE), when the PDE residual is added into the loss function, it acts as a regularisation agent in the training of the network. 
Effectively, the PDE acts as a soft constraint on the space of admissible solutions and increases the accuracy of the function approximation.

Benefits:
1. Enhances the information content of the available data by embedding information
2. Ensures that prediction is physically possible
3. Reduces the amount of data required for training

# Kinematics Example

In this repository, a simple kinematics problem is used to demonstrate the benefits of PINNs. 
To begin, we start with a one dimensional example of a ball being thrown upwards.

The physical law that the ball has to adhere to is the gravitational forces, as shown in the equation.

<img src="https://github.com/nicholassung97/DemonstrationofPINNs/blob/main/image/Screenshot%202022-09-22%20at%202.10.46%20PM.png" width="100" height="60" />

This equation is simple, non-linear and one dimensional. It assumes that a body in free-fall is subjected to a gravitational acceleration of 10m/s2.

The initial conditions that have bee arbitrarily set are at t=0 and t=10, the displacement would be zero, essentially meaning that the ball will drop back after 10 seconds. 

Based on knowledge of the partial differential equation the system has to adhere to, and the initial conditions of the system, the loss function can be defined to be:

<img src="https://github.com/nicholassung97/DemonstrationofPINNs/blob/main/image/Screenshot%202022-09-22%20at%202.20.15%20PM.png" width="500" height="300" />

Given an input (denoted t), the physics-based machine learning model can be used to predict an output(denotedas 𝑥̂), as shown in the figure below.To train the model, the loss function includes the 2 datasets at the initial condition and 50 random unlabelled training data (between t=0 and t=10) that will serve as collocation points to run through the PDE. 


<img src="https://github.com/nicholassung97/DemonstrationofPINNs/blob/main/image/Screenshot%202022-09-22%20at%202.20.32%20PM.png" width="600" height="300" />

The aim is to infer the value of the entire displacement solution between t=0 and t=10 using the kinematicsequation. A shallow neural network with only one hidden layer that has20 neurons,and a hyperbolic tangent activation function was used. The shallow neural network was chosen due to the anticipated simplicity of the problem.Since the total training data is relatively small, the loss function is optimised using L-BFGS optimiser. It is a quasi-Newton, full-batch gradient-based optimisation algorithm. This means that in each iteration, all the data is used for training. 

# Results
When training the physics-based machine learning model, we used two labelled data sets and one PDE for training as previously shown.​

Next, we used 250 test data to run through the network and obtain the error highlighted on the screen. ​

To compared how effective physics-based machine learning is compared a normal neural network, we constructed a neural network with the same number of neurons in the hidden layer, and we used the same weights and bias initialisation, same activation function and optimiser. ​

In this neural network, we varied the number of labelled training data to see how it affects the test error. We found that to achieve the same test error as the physics-based machine learning model, we had to run 150 training data sets through the normal neural network. In terms of predictions, we can observe their similarity.​

<img src="https://github.com/nicholassung97/DemonstrationofPINNs/blob/main/image/Screenshot%202022-09-22%20at%202.37.55%20PM.png" width="500" height="300" />


<img src="https://github.com/nicholassung97/DemonstrationofPINNs/blob/main/image/Screenshot%202022-09-22%20at%202.21.01%20PM.png" width="400" height="300" />

Essentially, this shows is that unlike the normal neural network, physics based machine learning requires much less training data​


To take things further, we took 50 test data from 10 seconds to 15 seconds which is out of the range of the training, and this data was input into both models.​

What we observed is that the physics-based machine learning model was able to capture the physical trends of beyond the training data so that the predictions were physically consistent​

<img src="https://github.com/nicholassung97/DemonstrationofPINNs/blob/main/image/Screenshot%202022-09-22%20at%202.38.41%20PM.png" width="500" height="300" />

To sum up the advantages of physics-based machine learning are​

- It requires less training data​

- It captures the trend beyond the range of the training and such that the predictions made are physically consistent​
