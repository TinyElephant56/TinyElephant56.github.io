work in progress!

## :What is this?
I hope to make an overview of the full systems within the robot! dont judge yet. it uses [:nutshell](https://ncase.me/nutshell/#WhatIsNutshell) to make expandable explanations

## :What controlls the robot during a match?

![](roborio2.jpg)

This, the [:roboRIO](#roborio), is the “brains” of the robot. We upload code to it before a match, and during a match it will revieve inputs from the driver through the [:radio](#radio). The roboRIO knows its position on the field and whether it has a game piece or not. It will process the inputs and control the motors. 

## :How is power distributed?

Here's a diagram on how the battery powers the robot! We'll start with

![](power_1.png)

A 12v battery powers the robot. Its important that we [:take care of our batteries](#battery-care)

The battery connects to the PDH/PDP with a breaker in between. The [:breaker](#breaker) is the on switch of the robot. Turn it on by pressing 

The [:PDH/PDP](#pdh-and-pdp) splits the power into many channels. Each motor connects to one of these channels with thick red and black [:wires](#wires-and-fuses). Each of those channels has a fuse, so if there is a surge of power the fuse will pop instead of it damaging a motor.

Some robot components require much less power than the motors. The [:MPM](#mpm) has channels similar to the PDH, but provides channels for small power. Devices that connect to the CAM are [:beam breaks](#beam-break), [:N100s](#n100), [:CANcoders](#cancoders), and the [:pigeon](#pigeon). One MPM channel can often power multiple devices. 

*note that things are slightly different for the PDP 2.0

## :How do components communicate with the roboRIO?
We also need wires to transmit data! Lets revise our diagram to include it:

![](power_2.png)

*diagram involving CAN
The roboRIO mainly uses three communication protocols: CAN, PWM, and DIO.

The most important one is the [:CAN bus](#can-bus). It's a two-wire comminication system that connects devices like [Pigeons](#pigeon), [:CANdles](#candle), [:CANcoders](#cancoders), and [:motor controllers]() in a daisy chain. Each device has a unique [:ID](#can-ids).

[:DIO]

[:PWM]

To communicate to the roboRIO, components either [:PWM](https://en.wikipedia.org/wiki/Pulse-width_modulation), [:DIO](#dio), or [:CAN](https://www.youtube.com/watch?v=YBrU_eZM110).

## :What does the robot's network look like?
*diagram of radio, roborio, laptop, and n100

ethernet

## :What is the code actually doing during a match?
adsd


## :How does the vision system work?
camera camera camera


## :Who made this?


---


### : Radio
radio radio radio

### : Drive Station
drivity drive drive drive

### : roboRIO
rio rio rio

### : PDH-and-PDP
PDH: Power Distrubution Hub
PDP: Power Distribution Power

### : Breaker
*video of someone turing the robot on and off 

## :What wires and fuses do you use?
This is complicated.

### : Bream breaks

![](beam_break.jpeg)

### : Pigeon
The gyroscope of the robot. This has to be in the very center of the robot!

### : CANdle
A device to control light strips. It revieves data through CAM 

![](candle.png)

### : CANcoders
CAN + encoder = cancoder

An encoder measures the rotation of a shaft. The CAN part means it transmits this data over the CAN bus

![For example, this CANcoder on the swerve uses magnets to measure the angle of the wheel.](cancoder_swerve.jpeg)

![This CANcoder could be used on a subsystem, lets say an arm, to measure its angle.](cancoder_shaft.jpeg)

### : N100
An intel computer. They are powered by a [:buck-boost converter](https://en.wikipedia.org/wiki/Buck%E2%80%93boost_converter)

### : CAN IDs
We have a spreadsheet to keep track of this

### : Can Bus

### : DIO
digital input output.

the thing provides resistance or something

### : MPM
Mini Power Module also known as a [:MPM](#mpm). it has a [:fuse](https://en.wikipedia.org/wiki/Fuse_(electrical))


<script src="https://cdn.jsdelivr.net/gh/ncase/nutshell/nutshell.js"></script>