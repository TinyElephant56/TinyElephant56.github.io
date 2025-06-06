work in progress!

[:MORE INFO ABOUT THE BATTER](https://www.team5026.com/General_Electrical_Documentation#Battery)

## :What is this?
This is a guide for the full systems of the robot. Hopefully you'll learn something, no matter what subteam you're on! The expandable explanations are created using [:nutshell](https://ncase.me/nutshell/#WhatIsNutshell)

## :What controlls the robot during a match?

![](badroborio.png)

The robot is controlled by the RoboRIO, which acts as the central brain, processing inputs from drivers and sensors. During a match, it will execute our code to command subsystems like the drivetrain, intake, and shooter.

## :How is power distributed?

![](power_1.png)

A 12v lead-acid battery powers all components on the robot. It's important that we use a battery in [:good condition](#battery-beak) and secure the wiring, because any voltage drops can cause performace issues or even reboot the RoboRIO (very bad!)

The battery connects to the [:PDH/PDP](#pdh-and-pdp) with a breaker in between. The [:breaker](#breaker) is the on/off switch of the robot. Turn it on by pressing the lever in, off by pressing the red button.

![](breaker.gif)

The [:PDH/PDP](#pdh-and-pdp) distrubutes power throughout the robot. Each motor connects to one of a channels in the PDH/PDP with thick red and black [:wires](#wires-and-fuses). Each of those channels has a fuse, so if there is a surge of power the fuse will pop instead of it damaging a motor.

Some robot components require much less power than the [:motors](#krakens). The [:MPM](#mpm) provides channels for low power devices. One MPM channel can often power multiple devices. Devices that connect to the MPM include [:beam breaks](#beam-break), [:N100s](#n100), [:CANcoders](#cancoders), and the [:Pigeon](#pigeon). 

Note that things are slightly different for the PDP 2.0.

Also, the [:radio](#radio) is powered a little differently, utilizing [:POE](#poe)

## :What fuses and wire thickness do we use?

## :How do components communicate with the roboRIO?

![](power_2.png)

The roboRIO mainly has four ways of communication: CAN, PWM, DIO, and ethernet.

The most important one is the CAN bus. It's a two-wire comminication system that connects devices in a daisy chain. The [:Pigeon](#pigeon), [:CANdle](#candle), [:CANcoders](#cancoders), and [:motor controllers](#motor-controllers) are connected with cam. Each device has a unique ID, which we keep track of on a spreadsheet. [[:more info](#can-bus)]

[:DIO](#dio) ports are used to send simple on/off signals. DIO is great for small sensors like limit switches and [:beam breaks](#-bream-breaks).

[:PWM](https://en.wikipedia.org/wiki/Pulse-width_modulation) is used to control [:servos](servos) or older motor controllers. We would only use it when a device doesn't support CAN, since CAN is bi-directional and can send much more data.

We'll talk about ethernet in the next section!

## :What does the robot's network look like?

![](power_3.png)

The robot's network is built around the radio. It creates a private network for the robot under the team's [:IP](#ip) range and connects to the field management system (FMS) during matches. 

The radio connects to the RoboRIO and N100s via ethernet, allowing them to transmit data to each other. The cameras are connected and powered by the N100, which processes image data and sends it to the RoboRIO.

During a match, the radio connects to the [:driver station](#drive-station) over wifi, but in the pits the robot can be tethered directly with a ethernet cable ("radio" is a bit misleading lol).

[:heres how the match network works](#match-network)
## :What is the code actually doing during a match?
Our robots code is command-based. Its based around two core [:abstractions](#abstraction): Subsystems and Commands

![An example by [:FIRST](#how-does-the-vision-system-work)](command_based.svg)

Commands represent actions the robot can take

## :What is version control?


## :How does the vision system work?
camera camera camera


## :How do purchases work?
email to someone to create a [PO](#purchase-order)

## :How do we transport all our stuff to competition?

## :What is scouting for?

## :What is the district system?

## :Who made this?

---


### :Radio
radio radio radio

### :Drive Station
drivity drive drive drive

### :roboRIO 2.0
rio rio rio

### :PDH and PDP
Power Distrubution Hub / Power Distrubution Port

The PDP 1.0, PDH, and PDP 2.0 have the same purpose of distrubuting power, but they have significant differences!

![The PDP 1.0 by CTRE is the oldest of the three. It has ](pdp_1.jpeg)

![The PDH by REV. It has orange WAGO terminals](pdh.jpeg)

![The PDH by Electronics ](pdp_2.jpeg)

[:see more about the wiring](#)

### :Breaker
*video of someone turing the robot on and off 

## :What wires and fuses do you use?
This is complicated.

### :Bream breaks

![](beam_break.jpeg)

### :Pigeon
The gyroscope of the robot. This has to be in the very center of the robot!

### :CANdle
A device to control light strips. It revieves data through CAM 

![](candle.png)

### :CANcoders
CAN + encoder = cancoder

An encoder measures the rotation of a shaft. The CAN part means it transmits this data over the CAN bus

![For example, this CANcoder on the swerve uses magnets to measure the angle of the wheel.](cancoder_swerve.jpeg)

![This CANcoder could be used on a subsystem, lets say an arm, to measure its angle.](cancoder_shaft.jpeg)

### :N100
An intel computer. They are powered by a [:buck-boost converter](https://en.wikipedia.org/wiki/Buck%E2%80%93boost_converter)

### :CAN IDs
We have a spreadsheet to keep track of this

### :Can Bus
The CAN starts at the roboRIO and ends at the PDP because the CAN network is required to be terminated by 120 Ω resistors and these are built into these two devices.

[:video explanation](https://www.youtube.com/watch?v=YBrU_eZM110)

### :DIO
Digital Input Output.

There are three wires: red, white and black. The red wire is usually 5v, the black wire is 0v, and the white wire is in between that. The white wire measures the tou

### :Field Management System

### :PWM

### :MPM
Mini Power Module also known as a [:MPM](#mpm). it has a [:fuse](https://en.wikipedia.org/wiki/Fuse_(electrical))

### :IP
FRC has a pretty good explanation of how IP works [:here](https://docs.wpilib.org/en/stable/docs/networking/networking-introduction/networking-basics.html#networking-basics)

### :Motors
Motors used to be so much complicated lol. now we just krakens becasue they COOK

### :Motor controllers
Kraken and Falcon motors have build in motor controlers to the back, Talon FX. 

other teams might have external motor controlers, such as SPARK MAX

### :Coordinate System
nora can you write this? :)

### :Abstraction
Abstraction is the concept of hiding complex implementation details and exposing only the necessary parts of a system through a simplified interface. In FRC, abstraction lets you control a robot mechanism using simple commands without needing to directly manage motor speeds, sensor readings, or hardware configurations each time.

In our code you might see something like 

`superstructureIO.stop()`

The superstructure is an abstraction. (ok the class structure is actually [:so much more complicated](#class-structure))

### :Battery Break
We use a battery beak to measure the voltage of each battery. However, info it gives is not the most useful. [:This conference]() gives a bit of an explanation why. This system may be changed in the future.

### :Match Network
The 10.x.x.x is a private network, so it can't be found on the internet


### :x POE
Power Over Ethernet

<script src="https://cdn.jsdelivr.net/gh/ncase/nutshell/nutshell.js"></script>