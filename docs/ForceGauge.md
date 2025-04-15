<head>
  <meta charset="UTF-8">
  <title>Force Gauge</title>
</head>
<body>

<h1>Stiffness Measurement via Force Gauge and ROS2</h1>

<h2>About</h2>

<div style="text-align: justify;">
  The stiffness of the ankle in the pogo stick-type model is characterized through a separate controlled experiment using a force-displacement test setup. This setup is designed to find out loads to the ankle joint and measure the corresponding load, allowing the finding of accurate force-displacement points.
</div>

<br>

<head>
  <meta charset="UTF-8">
  <title>Centered Mermaid Flowchart</title>
  <script type="module">
    import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
    mermaid.initialize({ startOnLoad: true });
  </script>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      margin: 0;
    }
    .mermaid {
      text-align: center;
    }
  </style>
</head>
<body>

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

</body>

<br>

<h3>Force Gauge setup</h3>

<div style="text-align: justify;">
  - <b>Project Setup:</b> The setup contains an object which, for this project, a prototype of a ankle + leg of a quadruped similar to a pogostick model, with a Force Gauge ready to record data. <br><br>
  - <b>Define Experiment Parameters:</b> A setup in which the model is fixated to the ground and a string is used to attach the leg and a hook of the force gauge. A set of displacement points are marked and the force gauge readings are taken at those points. The values are graphed out and the best fit is made to find the stiffness. <br><br>
  - <b>ROS-Based Software Configuration:</b> The data of the Force readings are published and subscribed via ROS2 software to visualize the data. A GUI is also constructed using PyQT5 which will:<br>
    1. Visualize the Data (2-D Plot of Force data with respect to time).<br>
    2. Contain a button to start and stop recording<br>
    3. A recording system to save the data into a <b>bagfile</b> or a <b>csv</b> file. <br><br>
  4. <b>Conduct Experiment:</b> The prototype is physically dropped, with the force gauge recording the force values with respect to time.<br><br>
  5. <b>Data Collection:</b> Sensor data are collected, in this case Force and displacement.<br><br>
  6. <b>Analysis:</b> Data are visualized on a graph using PyQT.<br><br>
  7. <b>Iterate (if necessary):</b> Conduct experiments with adjusted parameters if needed for confirmation.<br><br>
  8. <b>Report Findings:</b> Findings are compiled, and conclusions are provided for simulations and future improvements.
</div>

<br>

<div align="center">
  <img src="force_setup.jpg" alt="Force Gauge Setup"><br>
  <b>Figure 2:</b> Setup for calculating. The displacements will be reached via human hand, preferably via an UR5 to reduce human error.
</div>

<div align="center">
  <img src="force_setup_wUR5.jpg" alt="Force Gauge Setup"><br>
  <b>Figure 3:</b> A variation of the setup for calculating. The displacements is reached with a UR5 with an attached gripper, which eliminates human error .
</div>

<br>

<h2>Hardware Configuration</h2>

<div style="text-align: justify;">
  The specimen or test object is fixated on the ground via supports and screws and via strings, the specimen is attached to the hook attachment of a Force Gauge which is placed horizontally and tensile forces are added onto the ankle component to get the reading. <br><br>

  The Force Gauge will pass through a few marked displacement points and the force readings are plotted to find a best fit. <br><br>

  The hardware involved are:<br>
  - <b>Force Gauge:</b> For this experiment, a high-precision digital force gauge is used, a <a href="https://mark-10.com/products/force-gauges/series-4/">Mark-10 M4-10 force gauge</a>.<br>
  - <b>Displacement Measurement:</b> Displacement are marked via a ruler and the force gauge is physically pulled to the displacement points.We also used UR5 which provides us help in studying the effect of displacement and velocity on the stiffness of the ankle attachment. <br>
  - <b>Mounting Fixture:</b> A custom test rig is built to hold the ankle in position which will isolate the axis along which the stiffness is being tested. It allows for controlled compression of the ankle ensuring consistent boundary conditions during each test. <br>
  - <b>Data Acquisition:</b> Force reading is continuously logged from the gauge via serial interface or USB using a custom ROS2 node.
</div>

<br>

<h2>Data Conditioning and Analysis</h2>

<div style="text-align: justify;">
  - <b>Repeatability Check:</b><br>
  Multiple trials are conducted under identical conditions to assess repeatability and account for any mechanical hysteresis or viscoelastic effects. <br><br>
  - <b>Units and Normalization:</b><br>
  Data is converted into consistent SI units and normalized (if necessary) based on geometry or mass to enable direct comparison with simulation models.
</div>

<br>

<h2>Software Configuration</h2>

<div style="text-align: justify;">
  The force gauge is connected to the system via serial communicator (USB provided by the manufacturer). <br><br>

  The goal of using ROS2 is to serve three purposes:<br>
  - To visualize graphically the force readings.<br>
  - Create a GUI and show the data, have a button to start and stop recording.<br>
  - Upon pressing the button, the GUI will automatically create a <b>csv</b> and <b>ros2bag</b> file, useful for post-processing. <br><br>

  Using ROS2 we created a publisher and subscriber nodes.<br>
  - The <b>publisher node</b> will access the data from the serial communicator and publish a topic <b>'\force_reading'</b> which continuously updates the force reading from the force gauge.<br>
  - The <b>subscriber node</b> subscribes the topic and performs the following:<br>
  1. Visualizes graphically the force readings.<br>
  2. Create a GUI and show the data, have a button to start and stop recording.<br>
  3. Upon pressing the button, the GUI will automatically create a <b>csv</b> and <b>ros2bag</b> file, useful for post-processing.
</div>

<div align="center">
  <img src="docs/rosgraph.jpg" alt="Force Gauge GUI"><br>
  <b>Figure 4:</b> GUI of the force gauge setup
</div>

<br>

<h2>Experimentation</h2>

<div style="text-align: justify;">
  Figure 3 below is the GUI interface used for the experiment. It graphs a live plot of the data as it is being collected, and there are buttons along the bottom that users can press to save specific data points. There is also a live demonstration video included, showing how the data is pulled out in real time as the experiment is being performed.
</div>

<br>

<div align="center">
  <img src="docs/fgGUI.jpg" alt="Force Gauge GUI"><br>
  <b>Figure 5:</b> GUI of the force gauge setup
</div>

<br>

<div align="center">
  <iframe width="560" height="315"
          src="https://youtube.com/shorts/WxmLll2VZsE?feature=share"
          frameborder="0"
          allowfullscreen></iframe>
  <br>
  <b>Video 2:</b> Video of experimentation using hand for studying on the stiffness characteristics.
</div>

<br>

<div align="center">
  <iframe width="560" height="315"
          src="https://youtu.be/wU4Gq8Kg_fg"
          frameborder="0"
          allowfullscreen></iframe>
  <br>
  <b>Video 2:</b> Video of experimentation using UR5 for studying on the stiffness characteristics.
</div>
</body>

<br>
<div style="text-align: justify;">
  <h2> Future plans </h2>
  We will be adding an OptiTrack to validate our displacement readings, attaching it to the IR markers, along with the UR5. We will also be adding those to the ROS2 interface and add filtering nodes as well.
</div>

