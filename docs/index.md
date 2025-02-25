# Experimental Test Drop Setup Using UR5e Robot
## A. About
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

## B. The Project

The objective of this experiment is to validate the drop accuracy and consistency of a UR5 robot arm in a lab environment. This project will help investigate the impact of varying release heights, grip configurations, and object characteristics on drop accuracy.

## C. Research Question
 
***"How accurately and consistently can a UR5 robotic system drop objects from predefined positions, and what factors influence its precision?".***  

This study contributes to automation research by evaluating robotic handling performance in various manufacturing and logistics applications.

## D. Concept
The project involves configuring the UR5 robotic arm to drop test objects at predetermined positions. A vision system, in addition to sensors, will record drop points and trajectories. The analysis will be on the deviation from target points and how factors such as object weight, shape, and grip pressure influence it. ROS2 software will program the movements of the robot to ensure repeatability in the experiment. The process flow chart of our project is shown in the chart below.



``` mermaid
graph TD
    A[Project Setup] --> B[Define Experiment Parameters]
    B --> C[ROS-Based Software Configuration]
    C --> D[Conduct Experiment]
    D --> E[Data Collection]
    E --> F[Analysis]
    F --> G{Iterate?}
    G -->|Yes| D
    G -->|No| H[Report Findings]
```
>**Figure 1:** Process flow chart for the experiment.

a. *Project Setup:* The UR5 robot arm is installed, with sensors and vision system ready to record data.
b. *Define Experiment Parameters:* Reference points of drop locations and test objects with varying characteristics are selected.
c. *ROS-Based Software Configuration:* The robot movements are configured using ROS2 software to ensure repeatability.
d. *Conduct Experiment:* Robotic arm drops test objects, with the sensors and vision system recording the drop locations and trajectories.
e. *Data Collection:* Vision system and sensor data are collected, such as target point deviations.
f. *Analysis:* Data are processed to determine how specified variables influence deviations.
g. *Iterate (if necessary):* Conduct experiments with adjusted parameters if needed for confirmation
h. *Report Findings:* Findings are compiled, and conclusions are provided for future improvements.

## E. Sensor Intergration
This project aims to develop a ROS 2-based robotic manipulation system that integrates a UR5 robotic arm, OptiTrack motion capture technology, and ArUco markers for precise object tracking and manipulation. The goal is to enable the UR5 to autonomously pick up various test objects, identify them using ArUco marker detection, and drop them from a predefined height. ROS 2 will be used for motion planning, perception, and real-time communication, ensuring seamless coordination between different subsystems. This experiment will contribute to research in robotic grasping, object manipulation, and vision-based control.
The system will employ ArUco markers affixed to the test objects, allowing a camera-based ROS 2 node to detect, identify, and estimate their 6DoF pose. The OptiTrack motion capture system will provide additional high-precision localization feedback, which will be fused with the ArUco marker-based pose estimation for improved tracking accuracy. The robotic arm will adjust its approach dynamically based on real-time feedback from both ArUco marker tracking and OptiTrack data, ensuring robustness against positional variations and environmental disturbances.
By leveraging ROS 2’s distributed architecture, this project will enhance robotic perception, closed-loop manipulation, and trajectory adaptation in real-time. The combination of vision-based tracking (ArUco) and motion capture (OptiTrack) will enable high-accuracy object handling, automated sorting, and advanced grasping strategies. The findings from this experiment will have broader applications in industrial automation, assistive robotics, and autonomous material handling systems.

## F. Interface
The UR5 robotic arm will be controlled using ROS 2, leveraging MoveIt 2 for motion planning and custom ROS 2 nodes for real-time interaction. The behavior of the robot will be influenced through:
•	Vision-based Perception: ArUco marker tracking and OptiTrack motion capture data will be fused to provide high-accuracy object localization and ensure precise grasping.
•	Adaptive Motion Planning: ROS 2 will handle trajectory updates dynamically, allowing the robot to adjust its movements based on real-time feedback.
•	Closed-loop Control: Sensor feedback, including force-torque sensing (if applicable), will enable the UR5 to refine its grasping and dropping strategy iteratively.

# Interfaces for Interaction, Visualization, and Data Storage
To facilitate monitoring and user interaction, the following interfaces will be developed:
1.	*Simulation:* Used for real-time visualization of the robot’s workspace under control environment, including object positions, planned trajectories, and motion execution.
2.	*Web-Based Dashboard:* A user-friendly interface displaying object tracking data, robot status, and logs of executed actions.
3.	*Data Logging System:* All relevant data (object positions, timestamps, drop locations, and trajectory corrections) will be stored in a ROS 2-based database for post-experiment analysis.


## G. Control and Autonomy
A *low-latency feedback loop* will be established to provide real-time feedback to the UR5 controller where sensor data is processed and transmitted. 
This enables the UR5 inverse kinematics and control algorithms to dynamically adjust grip strength and drop execution in real-time. 
A *High-Level decision-making module* will also read long-term trends from sensor feedback to make higher-level decisions. When systematic errors in drop accuracy occur, the system will adjust its release strategies, i.e., altering grip pressure or release angles, to improve performance.

## H. Preparation Setup

# Resources needed from IDEALab
1. *UR5 Robotic Arm* – Primary manipulator for pick-and-drop operations.
2. *OptiTrack Motion Capture System* – Infrared cameras for real-time tracking.
3. *ArUco Markers* – Printed fiducial markers for object identification and pose estimation.
4. *Camera for ArUco Detection* – e.g., Intel RealSense or Logitech C920 for vision-based tracking.
5. *Computer with GPU Support* – High-performance system for ROS 2, computer vision, and motion planning.
6. *Network Infrastructure* – Ethernet and/or Wi-Fi for seamless communication.

## I. Final Demonstration

# Changes in environmental conditions:
To handle variability in the environment, the robot will leverage sensor fusion by combining OptiTrack motion capture for global positioning and ArUco marker detection for precise local object tracking, ensuring robust localization even under occlusion. Closed-loop control mechanisms, including force-torque sensing (if available) or visual feedback, will refine grasping by adjusting grip strength based on object weight and slippage. In case of misalignment, the system will implement error recovery strategies, such as reattempting detection and adjusting the pick position. Additionally, ROS 2-based dynamic reconfiguration will allow real-time parameter tuning and trajectory modifications, supported by a web-based interface for manual overrides. This integrated approach ensures the system remains resilient and adaptable in dynamic environments, maintaining precise and reliable object manipulation.

## J. Impact

Our team has no prior experience with ROS2, sensor fusion, or object detection, making this a valuable challenge for us to advance in robotic experimentation. We are focused on developing a robust and standalone test procedure for dropping test materials from a height. This process can be applied to material testing, orientation-based drop tests, impact conditioning, and assessing real-world behavior under critical conditions. Such a testing framework could significantly enhance rescue operations by evaluating the impact on a robot when deployed from higher floors, such as the 4th or 5th, ensuring better reliability in high-stakes scenarios.

## K. Advising
