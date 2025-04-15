---
Title: <div align="center">Force Gauge</div>
---

<div align="center">
  <h1>Stiffness Measurement via Force Gauge and ROS2</h1>
  <h3>Updated 04/14/2025</h3>
</div>

## About

<div style="text-align: justify;">
The stiffness of the ankle in the pogo stick-type model is characterized through a separate controlled experiment using a force-displacement test setup. This setup is designed to find out loads to the ankle joint and measure the corresponding load, allowing the finding of accurate force-displacement points.
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
    G -->|No| H[Report Findings - find stiffness]
</div>
</div>

<br>

## Force Gauge Setup

<div style="text-align: justify;">
- <b>Project Setup:</b> The setup contains an object which, for this project, a prototype of a ankle + leg of a quadruped similar to a pogostick model, with a Force Gauge ready to record data. <br><br>
- <b>Define Experiment Parameters:</b> A setup in which the model is fixated to the ground and a string is used to attach the leg and a hook of the force gauge. A set of displacement points are marked and the force gauge readings are taken at those points. The values are graphed out and the best fit is made to find the stiffness. <br><br>
- <b>ROS-Based Software Configuration:</b> The data of the Force readings are published and subscribed via ROS2 software to visualize the data. A GUI is also constructed using PyQT5 which will:<br>
  1. Visualize the Data (2-D Plot of Force data with respect to time).<br>
  2. Contain a button to start and stop recording<br>
  3. A recording system to save the data into a <b>bagfile</b> or a <b>csv</b> file.<br><br>
- <b>Conduct Experiment:</b> The prototype is physically dropped, with the force gauge recording the force values with respect to time.<br><br>
- <b>Data Collection:</b> Sensor data are collected, in this case Force and displacement.<br><br>
- <b>Analysis:</b> Data are visualized on a graph using PyQT.<br><br>
- <b>Iterate (if necessary):</b> Conduct experiments with adjusted parameters if needed for confirmation.<br><br>
- <b>Report Findings:</b> Findings are compiled, and conclusions are provided for simulations and future improvements.
</div>

<br>

<p align="center">
  <img src="force_setup.jpg" alt="Force Gauge Setup" width="500"><br>
  <b>Figure 2:</b> Setup for calculating. The displacements will be reached via human hand, preferably via an UR5 to reduce human error.
</p>

## Hardware Configuration

<div style="text-align: justify;">
The specimen or test object is fixated on the ground via supports and screws and via strings, the specimen is attached to the hook attachment of a Force Gauge which is placed horizontally and tensile forces are added onto the ankle component to get the reading. <br><br>
The Force Gauge will pass through a few marked displacement points and the force readings are plotted to find a best fit. <br><br>
The hardware involved are:<br>
- <b>Force Gauge:</b> For this experiment, a high-precision digital force gauge is used, a <a href="https://mark-10.com/products/force-gauges/series-4/">Mark-10 M4-10 force gauge</a>.<br>
- <b>Displacement Measurement:</b> Displacements are marked via a ruler and the force gauge is physically pulled to the displacement points.<br>
- <b>Mounting Fixture:</b> A custom test rig is built to hold the ankle in position which will isolate the axis along which the stiffness is being tested.<br>
- <b>Data Acquisition:</b> Force reading is continuously logged from the gauge via serial interface or USB using a custom ROS2 node.
</div>

<br>

## Data Conditioning and Analysis

<div style="text-align: justify;">
- <b>Repeatability Check:</b><br>
Multiple trials are conducted under identical conditions to assess repeatability and account for any mechanical hysteresis or viscoelastic effects. <br><br>
- <b>Units and Normalization:</b><br>
Data is converted into consistent SI units and normalized (if necessary) based on geometry or mass to enable direct comparison with simulation models.
</div>

<br>

## Software Configuration

<div style="text-align: justify;">
The force gauge is connected to the system via serial communicator (USB provided by the manufacturer). <br><br>
The goal of using ROS2 is to serve three purposes:<br>
- To visualize graphically the force readings.<br>
- Create a GUI and show the data, have a button to start and stop recording.<br>
- Upon pressing the button, the GUI will automatically create a <b>csv</b> and <b>ros2bag</b> file.<br><br>
Using ROS2 we created publisher and subscriber nodes:<br>
- <b>Publisher node:</b> accesses the data from the serial communicator and publishes a topic <b>'\force_reading'</b>.<br>
- <b>Subscriber node:</b> subscribes the topic and:<br>
  1. Visualizes the force readings.<br>
  2. Manages the GUI with recording controls.<br>
  3. Saves output to both CSV and ros2bag formats.
</div>

<br>

## Experimentation

<div style="text-align: justify;">
Figure 3 below is the GUI interface used for the experiment. It graphs a live plot of the data as it is being collected, and there are buttons along the bottom that users can press to save specific data points. There is also a live demonstration video included, showing how the data is pulled out in real time as the experiment is being performed.
</div>

<br>

<p align="center">
  <img src="fgGUI.png" alt="Force Gauge GUI" width="500"><br>
  <b>Figure 3:</b> GUI of the force gauge setup
</p>

<br>

<div align="center">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/dQw4w9WgXcQ" frameborder="0" allowfullscreen></iframe>
</div>
