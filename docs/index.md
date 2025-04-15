---
Title: <div align="center">Overview</div>
---

<div align="center">
  <h1>Experimental Test Drop Setup Using OptiTrack and Force Gauge</h1>
  <h3>Updated 04/14/2025</h3>
</div>


## A. About  
<div align="center">  
<table>
  <tr>
    <td>Team Number</td>
    <td>04</td>
  </tr>
  <tr>
    <td>Team Members</td>
    <td>Vijaya Malhaar Gaddam, Harshavardhan Karancheti</td>
  </tr>
  <tr>
    <td>Semester, Year</td>
    <td>Spring, 2025</td>
  </tr>
  <tr>
    <td>Professor</td>
    <td>Dr. Daniel Aukes</td>
  </tr>
  <tr>
    <td>University</td>
    <td>Arizona State University</td>
  </tr>
</table>  
</div>

## B. The Project

<div style="text-align: justify;">

The objective of this experiment is to validate the stiffness and porjectile of the ankle of a pogo stick type model in a lab environment. This project will help investigate the impact of varying release heights, release angle, and object characteristics which will be used to establish parameters and compare to the simulations.

</div>

## C. Research Question

<p align="left">
  <b>"How do we get simulation parameters to measure the stiffness and projectile of an ankle design for stability in a quadruped?"</b>
</p>

<div align="center"></div>

<div style="text-align: justify;">

This study contributes to modeling research by evaluating robotic parts designs in various manufacturing and logistics applications.

</div>

## D. Concept

<div style="text-align: justify;">

The project involves using two setups:
<b>1.</b> OptiTrack via ROS2 to drop test objects at predetermined positions. A vision system, will record drop points and trajectories <br>
<b>2.</b> A force gauge is attached to the test object to measure the stiffness and deformation. The setup will fixate the test object to the ground and force will be measured at different displacements which forms data to find the best fit for the stiffness of the prototype<br><br>

The experiment analyzes how factors such as object weight and shape influence it and how it relates to the simulation readings. ROS2 software will use a node to publish the sensors to ensure repeatability in the experiment. The process flow chart of our project is shown in the chart below. <br>

</div>

<div align="center">

</div>

### OptiTrack setup

<div style="text-align: justify;">

- <b> Project Setup: </b> The setup contains an object which, for this project, an prototype of a ankle + leg of a quadruped similar to a pogostick model, with a OptiTrack continaing IR reflectors and vision system ready to record data. <br>
- <b> Define Experiment Parameters: </b> Points of placement of reflector sensors are selected along with angles and heights to drop from. <br><br>
- <b> ROS-Based Software Configuration: </b> The data of the movement from the OptiTrack are published and subscribed via ROS2 software to visualize the data. A GUI is also constructed using PyQT5 which will: <br><br>  
  1. Visualize the Data (2-D Plot of Position and Orientation with respect to time) <br>
  2. Contain a button to start and stop recording  <br>
  3. A recording system to save the data into a _bagfile_ or a _csv_ file <br><br>  
- <b> Conduct Experiment: </b> The prototype is physically dropped, with the sensors and vision system recording the drop locations and trajectories, and deformation values<br>  
- *Data Collection:* Vision system and sensor data are collected, such as trajectories <br>  
- *Analysis:* Data are visualized on a graph using PyQT <br>
- *Iterate (if necessary):* Conduct experiments with adjusted parameters if needed for confirmation <br>
- *Report Findings:* Findings are compiled, and conclusions are provided for simulations and future improvements <br>

</div>

## E. Sensor Intergration

<div style="text-align: justify;">

This project aims to develop a ROS 2-based robotic manipulation system that integrates *OptiTrack motion capture technology*, and force gauge for measuring simulation parameters. The goal is to drop them from a random height and angle and utilize the OptiTrack and find the projected trajectories. ROS2 will be used for processing and obtaining sensor information and real-time communication, ensuring seamless coordination between different sensor data. This experiment will help in supporting the simulation data of a similar model in MujoCo.<br>

The OptiTrack motion capture system will provide for improved tracking. By leveraging ROS 2’s distributed architecture, this project will enhance trajectory adaptation in real-time. The combination of motion capture (OptiTrack) will enable high-accuracy object handling. The findings from this experiment will have broader applications in industrial automation, assistive robotics, and testing.

</div>

## F. Interface

<div style="text-align: justify;">

The sensor data will be obtained using ROS2, leveraging MuJoCo for simulation comparision and custom ROS2 nodes for real-time interaction. The behavior of the robot will be influenced through:
<b> 1. </b> Vision-based Perception: OptiTrack motion capture data will be fused to provide high-accuracy object localization.<br> 
<b> 2. </b> Adaptive Motion Planning: ROS2 will handle trajectory updates dynamically, allowing the robot to adjust its movements based on real-time feedback.<br>

### Interfaces for Interaction, Visualization, and Data Storage
To facilitate monitoring and user interaction, the following interfaces will be developed: <br><br>
<b> 1. </b> *Simulation:* Used for real-time visualization of the robot’s workspace under control environment, including object positions, planned trajectories, and motion execution. <br>  
<b> 2. </b> *Web-Based Dashboard:* A user-friendly interface displaying object tracking data, and force gauge readings.  <br>
<b> 3. </b> *Data Logging System:* All relevant data (object positions, timestamps, drop locations, and trajectory corrections) will be stored in a ROS 2-based database for post-experiment analysis. <br>

</div>

## G. Control and Autonomy

<div style="text-align: justify;">

<b> A low-latency feedback loop </b> will be established to provide real-time feedback to the UR5 controller where sensor data is processed and transmitted.<br>  
This enables the UR5 inverse kinematics and control algorithms to dynamically adjust grip strength and drop execution in real-time.  <br>
<b> A High-Level decision-making module </b> will also read long-term trends from sensor feedback to make higher-level decisions. When systematic errors in drop accuracy occur, the system will adjust its release strategies, i.e., altering grip pressure or release angles, to improve performance.

</div>

## H. Resources needed

<div style="text-align: justify;">

Since we heavily require camera sensing and sensor fusion, we would be needing knowledge about Control Systems and Autonomous Algorithms, Computer Vision, Object tracking and Sensor Fusion and Filtering Techniques. To run simulations for data comparisions, we would also need knowledge of Mujoco. Furthemore, self study and expert advice will go a long way in covering the gaps.

</div>

## I. Final Demonstration

### Resources needed from IDEALab

<div style="text-align: justify;">

1. <b> OptiTrack Motion Capture System – </b> Infrared cameras for real-time tracking <br>
2. <b> Force Gauge - </b> For studying stiffness  <br>
3. <b> Computer with GPU Support – </b> High-performance system for ROS2 and computer vision <br>
4. <b> Network Infrastructure – </b> Ethernet and/or Wi-Fi for seamless communication <br>
5. <b> Test Object - </b> Quadruped Robot or a prototype <br>

</div>

<p align="center">
  <img src="DemoSetup.jpg" width="500"/>
</p>

### Changes in environmental conditions:

<div style="text-align: justify;">

<b> 1. </b> To handle variability in the environment, the robot will leverage sensor fusion by combining OptiTrack motion capture for global positioning and force gauge for precise local object tracking, ensuring robust localization and more research data. <br>  
<b> 2. </b> In case of misalignment, the system will implement error recovery strategies, such as reattempting detection and adjusting the pick position. Additionally, ROS 2-based dynamic reconfiguration will allow real-time parameter tuning and trajectory modifications, supported by a web-based interface for manual overrides. This integrated approach ensures the system remains resilient and adaptable in dynamic environments, maintaining precise and reliable object manipulation.<br>

</div>

## J. Impact

<div style="text-align: justify;">

Our team has no prior experience with ROS2, sensor fusion, or object detection, making this a valuable challenge for us to advance in robotic experimentation. We are focused on developing a robust and standalone test procedure for dropping test materials from a height. <br>  
This process can be applied to material testing, orientation-based drop tests, impact conditioning, and assessing real-world behavior under critical conditions. Such a testing framework could significantly enhance rescue operations by evaluating the impact on a robot when deployed from higher floors, such as the 4th or 5th, ensuring better reliability in high-stakes scenarios.

</div>

## K. Advising

<div style="text-align: justify;">

We will be mentored by Dr. Daniel M. Aukes, who has expressed his interest in providing mentoring and access to state-of-the-art hardware facilities. Dr. Aukes' guidance will be a key factor in ensuring the technical aspects of the project are addressed effectively. His demands involve regular progress tracking, strict adherence to project milestones, and active participation in troubleshooting sessions. Other facilities, such as laboratory access and state-of-the-art simulation tools, have been guaranteed to aid in our experimental setup.

</div>

### Timeline

<p align="center">
  <img src="your-image.jpg" width="300"/>
</p>

## Update #1 - 04/13/2025

### Changes in goal statement

<div style="text-align: justify;">

Previously, we were of the idea of using a UR5 to test the repeatability and drop test our quadruped with an added ankle attachment for stability. But considering timeline and limitation constraints, we changed our goal statement to analyzing the position, orientation(drop trajectory) via OptiTrack and stiffness via force gauge. We will be physically dropping testing a part of the quadruped (the ankle attachment) for the study. Sensor data which is filtered will be further analyzed and added as a simulation parameter for a MujoCo simulation adding on to research done by Prof. Aukes.

</div>
