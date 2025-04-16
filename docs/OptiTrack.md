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


## OptiTrack Setup

<div style="text-align: justify;">
- <b>Project Setup:</b> The setup contains an object which, for this project, is a prototype of an ankle + leg of a quadruped similar to a pogostick model, with reflective markers to facilitate OptiTrack in capturing the data. <br><br>
- <b>Define Experiment Parameters:</b> The parameters involve setting up the placement of the reflective sensors, and defining the ground frame and the rigid body in the MOTIVE GUI. <br><br>
- <b>ROS-Based Software Configuration:</b> The OptiTrack sends its data to a software named MOTIVE which can be accessed on the Virtual Machine via Ethernet. ROS2 is used to access and visualize the data. A GUI can also be constructed using PyQT5 which will:<br>
  1. Visualize the Data (serially showing the Cartesian coordinates and quaternions with timestamps).<br>
  2. Contain a button to start and stop recording.<br>
  3. A recording system to save the data into a <b>bagfile</b> or a <b>csv</b> file.<br><br>
- <b>Conduct Experiment:</b> The prototype is physically dropped, and trajectories are tracked by the motion capture system. <br><br>
- <b>Data Collection:</b> Sensor data are collected, in this case, coordinates and quaternions. <br><br>
- <b>Analysis:</b> Data are visualized via GUI using PyQT. <br><br>
- <b>Iterate (if necessary):</b> Conduct experiments with adjusted parameters if needed for confirmation. <br><br>
- <b>Report Findings:</b> Findings are compiled, and conclusions are provided for simulations and future improvements.
</div>

<br>

<p align="center">
  <img src="force_setup.jpg" alt="OptiTrack Setup" width="500"><br>
  <b>Figure 2:</b> Setup for calculating. The displacements will be reached via human hand, preferably via an UR5 to reduce human error.
</p>

<br>

## Hardware Configuration

<div style="text-align: justify;">
The specimen or test object is physically dropped at a fixed height and angle, and the reflective markers on the specimen measure its movement in the controlled space and its contact with the ground. This helps study the stability of the ankle attachment. <br><br>
<b>Hardware involved:</b><br>
- <b>OptiTrack:</b> Reflective IR markers and a specialized IR camera setup to accurately track the markers.<br>
- <b>Mounting Fixture:</b> The specimen is held by hand and is free-fallen onto the ground.<br>
- <b>Data Acquisition:</b> Data is acquired from the MOTIVE software and transmitted via Ethernet.
</div>

<br>

## Data Conditioning and Analysis

<div style="text-align: justify;">
- <b>Conditioning:</b> A rigid body is configured in MOTIVE with appropriate marker layout and labeling to ensure robust tracking even during rapid motion. Data is streamed into ROS2 via a dedicated bridge.<br><br>
- <b>Filtering:</b> A Savitzky-Golay or low-pass Butterworth filter can be applied to the position data to smooth high-frequency noise. Numerical differentiation is used for computing velocity and acceleration in a dedicated ROS2 node.<br><br>
- <b>Repeatability Check:</b> Multiple trials are conducted under identical conditions to assess repeatability.<br><br>
- <b>Units and Normalization:</b> Data is converted into consistent SI units and normalized (if necessary) for direct comparison with simulation models.
</div>

<br>

## Software Configuration

### OptiTrack Node

<div style="text-align: justify;">
- A dedicated bridge node is used to stream 6-DOF pose data from MOTIVE into ROS2.<br>
- It publishes a topic: <b>/ankle/pose</b>.<br>
- Rigid body configurations are provided via a YAML parameter file.
</div>

<br>

### Filtering Node

<div style="text-align: justify;">
- Applies real-time filtering to remove measurement noise.<br>
- Suitable filters include Butterworth or Savitzky-Golay to smooth the position signal.<br>
- Outputs include:<br>
  - <b>/ankle/pose_filtered</b><br>
  - <b>/ankle/velocity</b><br>
  - <b>/ankle/acceleration</b>
</div>

<br>

## Node Communication
<head>
  <meta charset="UTF-8">
  <title>Mermaid Flowchart Example</title>
  <script type="module">
    import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
    mermaid.initialize({ startOnLoad: true });
  </script>
  <style>
    /* Optional: center the flowchart container */
    .chart-container {
      text-align: center;
    }
  </style>
</head>
<body>
  <div class="chart-container">
    <div class="mermaid">
graph LR
  OPTI[/optitrack_node/] --> POSE[/ankle/pose/]
  POSE --> FILTER[/filter_node/]
  FILTER --> POSEF[/ankle/pose_filtered/]
  FILTER --> VEL[/ankle/velocity/]
  FILTER --> ACC[/ankle/acceleration/]
    </div>
  </div>
</body>

<br>

## Experimentation

<div style="text-align: justify;">
OptiTrack was calibrated for our controlled environment. The video below shows our team working at IDEALab to calibrate and obtain pose data via Python on Windows. Future work involves implementing ROS2 filters to smooth the data in real time.
</div>

<br>

<div align="center">
  <iframe width="560" height="315"
          src="https://youtu.be/embed/vSl41NQOHbg"
          frameborder="0"
          allowfullscreen></iframe><br>
  <b>Video 1:</b> Video of Optitrack Calibration.
</div>

<br>

<div align="center">
  <iframe width="560" height="315"
          src="https://youtu.be/embed/JNOpxTxRALE"
          frameborder="0"
          allowfullscreen></iframe><br>
  <b>Video 1:</b> Video of Optitrack Calibration.
</div>