---


---

<hr>
<h2 id="layout-defaulttitle-configurationnav_order-2">layout: default<br>
title: Configuration<br>
nav_order: 2</h2>
<h1 id="ardusub">ArduSub</h1>
<p>ArduSub is a fork of the popular Ardupilot suite designed to operate Blue Robotic’s BlueROV. Ardupilot includes the controller’s firmware sources, message declarations, and several tools for interacting or modifying Ardupilot controllers.</p>
<h2 id="packet-radio">Packet Radio</h2>
<p>Before we did anything relating to Ardupilot, we first designed a simple packet radio using Arduino MKRWAN 1300s and LoRa. It’s easy to use: bytes that are input into the Arduino’s USB serial interface will try to be sent over LoRa to the other radio and pushed out of the other radio’s USB serial interface. The radios are bidirectional, so any data sent into the other radio is also sent back to the original radio.</p>
<p>Due to the way LoRa is integrated into the MKRWAN’s, we had to design a simple locking protocol to avoid packet collisions. We designed a simple finite state machine with three states for each radio: <code>rest</code>, <code>sending</code>, and <code>receiving</code>.</p>
<h3 id="rest">Rest</h3>
<p>A radio initializes itself in the <code>rest</code> state. In this state, the radio polls the LoRa IC for incoming messages and any serial data queued on it’s USB interface. If there is an incoming message, the state is switched to <code>receiving</code> and if there is data on the serial port, the state is switched to <code>sending</code>.</p>
<h3 id="receiving">Receiving</h3>
<p>Before a radio locks itself into receiving, it first checks that the message is directed to itself. a</p>
<h3 id="sending">Sending</h3>

