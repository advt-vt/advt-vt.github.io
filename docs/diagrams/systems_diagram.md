---
title: Systems Diagram
description: A diagram and explanation of all of the software we're using and how it interlinks
---

# <p style="text-align: center"> Systems Diagram </p>

---
<img src="./System_Diagram.drawio.svg" alt="A diagram showcasing how the full system works together." width=1000>

### NVIDIA Jetson
The NVIDIA Jetson chip runs all of the decision making calculations that are needed for the drone. The machine learning model we use will run on this chip. So if the cameras spot a bird, the Jetson chip will identify it as a bird and issue a command via MAVSDK to move out of the way.

### MAVSDK
MAVSDK is a high level API that allows several programing languages to interface with vehicles. This is what we will be using to issue commands to the drone, such as: land, take off, go up, ect.

### PX4
PX4 is an open source software that is able to run all of the calcluations for the movement of the drone. So if the drone needs to move up, PX4 will calculate what the drone hardware needs to do in order to make that happen.

### Microcontroller & Drone Hardware
The microcontroller is the actual peice of hardware that issues these commands to the drone from PX4. So if PX4 says 100% RPM on all rotors, the microcontoller is the thing that actually delivers this information to each of the rotors. The drone itself is equipped with several sensors and cameras which will send information back to the ground systems as well as to the Jetson chip for it's decision making.