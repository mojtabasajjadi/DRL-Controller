# DRL-Controller
Deep reinforcement learning for traffic light control in transportation networks

<h2>Introduction </h2><br>
In this repository, a deep reinforcement learning model for traffic light control is provided. The main task of this model is to improve the performance of traffic lights with reinforcement learning methods and the use of deep learning networks. If the traffic light is ineffective, it causes problems such as travel delays, energy loss, air pollution, vehicle accidents, etc.
The existing traffic lights have a fixed schedule and do not take into account momentary traffic. Others use sensors on the ground to determine how many cars are waiting in front of the light. This model of lights has low efficiency. For example, during a football match or peak traffic hours, most of these systems are paralyzed. In these cases, the police control the traffic manually. Observing the police and this manual operator gives this motivation to design a system like that. This system requires an eye to observe the momentary intersection traffic and a brain to process it.
The eye can recognize the number of cars, as well as where and when they are waiting. Reinforcement learning is used for the brain part of the system. This section also has three parts: states, actions, and rewards that we must model for use in the deep network. 
<br>

<img src="https://github.com/mojtabasajjadi/DRL-Controller/blob/main/1.png?raw=true" alt="Italian Trulli">
<br>
<h2>Deep learning model</h1><br>
At first, state, action, and rewards must be determined so that we can model them. <br><br>
<b>State:</b> We define the state based on the speed and location of the vehicle at the intersection. The traffic light takes a picture of the intersection and divides it into small equal squares. If there is a vehicle in the square, the value is 1, and if there is no vehicle in the square, the null value is considered for small squares.<br>
<img src="https://github.com/mojtabasajjadi/DRL-Controller/blob/main/2.png?raw=true" alt="Italian Trulli"><br>
<img src="https://github.com/mojtabasajjadi/DRL-Controller/blob/main/3.png?raw=true" alt="Italian Trulli"><br>

<b>Action:</b> The action is defined in such a way that the phase time is selected in the next loop. Each ring in the figure below represents the time of 4 phases in one cycle of the traffic light. We considered the time of each cycle as 5 seconds and showed it as an addition and subtraction of 5 seconds from each phase.<br>
<img src="https://github.com/mojtabasajjadi/DRL-Controller/blob/main/4.png?raw=true" alt="Italian Trulli"><br>
<b>Reward:</b> Our goal is to increase efficiency at the intersection. One way to measure the efficiency is the waiting time of vehicles. So the waiting time between two neighboring rings is the reward of this system. which can be seen in the following relationships:<br>

<img src="https://github.com/mojtabasajjadi/DRL-Controller/blob/main/5.png?raw=true" alt="Italian Trulli"><br><br>
<h2>Overall system architecture</h2>
According to the figure below, the current state and the predicted action are given to the primitive neural network, so that the action with the highest reward is selected. The current state the predicted action the next state resulting from this action and the reward received from this action are stored in quadruple tuples <s, a, r, sp> in the memory. These data are selected in the memory by the prioritization system and to produce categories that update and optimize the parameters of the neural network.<br><br>
<img src="https://github.com/mojtabasajjadi/DRL-Controller/blob/main/6.png?raw=true" alt="Italian Trulli"><br><br>



