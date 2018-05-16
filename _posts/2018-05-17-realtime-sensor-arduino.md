---
layout: post
title: Realtime Arduino Sensor Data Monitoring using NodeJS
date:       2018-05-17 02:49:15
author:     Utkarsh Gupta
description:    Project for plotting realtime sensor data plot using Arduino Uno.
keywords:	"nodejs, arduino, realtime, pubnub, mongodb, database, plot, graph, visualization"
categories: blog
thumbnail:  code
comments: true
tags:
---

The aim of this project was to monitor the Arduino sensor data values , view those sensor values on any device connected to the internet and store the values for predictive maintenance analysis purposes.

## Collection of Sensor Data
For the sake of practical purpose, a single phase transformer connected with variable lamp load on secondary was used and the following values were monitored

 1. AC Current in secondary (using ACS712 current sensor)
 2. AC Voltage of primary 
 3. Temperature of field winding of the transformer (using LM35)

For measuring AC voltage, a voltage divider arrangement(using necessary resistances) was used along with a diode so as to scale the value down to 0-5 V which could be directly read by Arduino Uno.

![Basic Connection Scheme](https://i.imgur.com/Bjg1rHw.jpg "Basic Connection Scheme")
<center><small><i>Basic Connection Scheme</i></small></center>

You can find the connection scheme of various sensors to Arduino on the internet according to the sensors being employed.

To transmit this collected data to the server on the internet, a SIM900A GSM Module was used which was powered by another 12V DC adapter separately.

## Server Side Implementation
A NodeJS server was deployed on Heroku which accpets GET requests made from the Arduino at periodic intervals. On each and every request, the data was stored into Mongo database and the data was pushed to a [PubNub](http://pubnub.com/) server under a pre-defined channel name - which would in turn publish the data to all the subscribed devices in real-time. For plotting purposes, [EON.js](https://www.pubnub.com/developers/eon/) was used which is another project of PubNub team. The entire server side source code can be found in this [Github](https://github.com/UtkarshGpta/realtime-arduino-sensor-data) repository. 

## Arduino Code
Head over to the following [Gist](https://gist.github.com/UtkarshGpta/cbc7a899d3c6e1072db4b5f55e87b5a6) for Arduino Code.

### Source
[Github](https://github.com/UtkarshGpta/realtime-arduino-sensor-data)