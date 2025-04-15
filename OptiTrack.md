---
Title: <div align="center">OptiTrack</div>
---

<div align="center">
  <h1>OptiTrack for documenting Positioning and Trajectory</h1>
  <h3>Updated 04/14/2025</h3>
</div>

## About

<div style="text-align: justify;">
The stability of the ankle in the pogo stick-type model is characterized through a separate controlled experiment using a Motion Capture setup. This setup is designed to find out the trajectory and stability of our designed ankle design using OptiTrack.
</div>

<br>

## Flowchart

<div align="center">
<div class="mermaid">
graph TD
    A[Project Setup] --> B[Define Experiment Parameters]
    B --> C[ROS2-Based Software Configuration]
    C --> D[Conduct Experiment]
    D --> E[Data Collection]
    E --> F[Analysis]
    F --> G{Iterate?}
    G -->|Yes| D
    G -->|No| H[Report Findings-find trajectory]
</div>
</div>

<br>

## OptiTrack Setup

<div style="text-align: justify;">
- <b>Project Setup:</b> The setup contains an object which, for this project, is a prototype of an ankle + leg of a quadruped similar to a pogostick model, with reflective markers to facilitate OptiTrack in capturing the data.<br><br>
- <b>Define Experiment Parameters:</b> The parameters involve setting up the placement of the reflective sensors, and defining the ground frame and the rigid body in the MOTIVE GUI.<br><br>
- <b>ROS-Based Software Configuration:</b> The OptiTrack sends its data to a software named MOTIVE which can be accessed on the Virtual Machine via Ethernet. ROS2 is used to visualize the published data. A GUI can also be constructed using PyQT5 which will:<br>
  1. Visualize the Data (serially showing the Cartesian coordinates and quaternions with timestamps).<br>
  2. Contain a button to start and stop recording.<br>
  3. A recording system to save the data into a <b>bagfile</b> or a <b>csv</b> file.<br><br>
- <b>Conduct Experiment:</b> The prototype is physically dropped, and trajectories are tracked by the motion capture system.<br><br>
- <b>Data Collection:</b> Coordinates and quaternions are collected.<br><br>
- <b>Analysis:</b> Data is visualized via GUI using PyQT.<br><br>
- <b>Iterate (if necessary):</b> Adjust parameters and repeat if needed.<br><br>
- <b>Report Findings:</b> Findings are compiled for simulation and future enhancements.
</div>

<br>

<p align="center">
  <img src="force_setup.jpg" alt="OptiTrack Setup" width="500"><br>
  <b>Figure 2:</b> Setup for calculating. The displacements will be reached via human hand, preferably via an UR5 to reduce human error.
</p>

## Hardware Configuration

<div style="text-align: justify;">
The specimen is dropped from a fixed height and angle. Reflective markers measure its movement and stability. This provides insight into the effectiveness of the ankle attachment.<br><br>
<b>Hardware involved:</b><br>
- <b>OptiTrack:</b> Uses reflective IR markers and IR camera setup for accurate tracking.<br>
- <b>Mounting Fixture:</b> The specimen is free-fallen by hand.<br>
- <b>Data Acquisition:</b> MOTIVE software streams the data to the user machine via Ethernet.
</div>

<br>

## Data Conditioning and Analysis

<div style="text-align: justify;">
- <b>Conditioning:</b> The rigid body is configured in Motive with proper marker layout and labeling. Data is streamed into ROS2 via a dedicated bridge.<br><br>
- <b>Filtering:</b> A Savitzky-Golay or Butterworth filter can be applied to position data. Differentiation is used for velocity and acceleration. Filtering is handled by a ROS2 node.<br><br>
- <b>Repeatability Check:</b> Conducted to ensure consistent results.<br><br>
- <b>Units and Normalization:</b> Data is standardized to SI units and normalized for simulation comparisons.
</div>

<br>

## Software Configuration

### OptiTrack Node

<div style="text-align: justify;">
- Publishes 6-DOF pose data from MOTIVE to ROS2.<br>
- Topic published: <b>/ankle/pose</b>.<br>
- Rigid body configurations are passed via a YAML parameter file.
</div>

<br>

### Filtering Node

<div style="text-align: justify;">
- Applies real-time filtering to smooth noisy measurements.<br>
- Filters: Butterworth or Savitzky-Golay.<br>
- Outputs:<br>
  - <b>/ankle/pose_filtered</b><br>
  - <b>/ankle/velocity</b><br>
  - <b>/ankle/acceleration</b>
</div>

<br>

## Node Communication

<div align="center">
<div class="mermaid">
graph LR
  OPTI[/optitrack_node/] --> POSE[/ankle/pose/]
  POSE --> FILTER[/filter_node/]
  FILTER --> POSEF[/ankle/pose_filtered/]
  FILTER --> VEL[/ankle/velocity/]
  FILTER --> ACC[/ankle/acceleration/]
</div>
</div>

<br>

## Experimentation

<div style="text-align: justify;">
OptiTrack was calibrated for a controlled environment. The videos below show our team working at IDEALab to calibrate and capture pose data using Python. Future work includes applying ROS2 filters to clean and refine data in real-time.
</div>

<br>

<div align="center">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/dQw4w9WgXcQ" frameborder="0" allowfullscreen></iframe><br><br>
  <iframe width="560" height="315" src="https://www.youtube.com/embed/dQw4w9WgXcQ" frameborder="0" allowfullscreen></iframe>
</div>
