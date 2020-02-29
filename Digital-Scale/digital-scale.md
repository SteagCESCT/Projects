# Digital Scale

In this workhop we will learn how to how to make a digital scale to measure distance.


### Problem Statement 

In order to measure distance from some physical thing we can use scale or measuing tap, but what if we need to need to take continous measurement and analyize the differnce, or we need to make an action depends on the distance like water level, waste level, oil level etc. repetitive continous measurement cost too much human resource. 

### Idea

What if, we have a system that can be continually monitor the level and make actions. 

### Solution

Build a device that can be controled wcontinually monitor the level and make actions like getting notification when a waste bin is full or getting a notification that can be help to prevent flood by monitoring water level..etc

<hr>

### Prototype Building

* Build a device that Measure distace and displayed on LCD Screen

Here we are using an Arduino as controller and HCSR04 Ultrasonic Module to measure the distance and 16x2 LCD Display to Display the Distance. 

![digram](src/images/diagram.png) 

<hr>

### Things we need 

1. Arduino Uno
2. HCSR04 Ultrasonic sensor
3. 16x2 LCD Module
4. Jumper Wires
5. Breadboard

<hr>

### Step 1: Arduino Setup

#### 1.1: Install Arduino IDE 

Download the [Arduino IDE](https://www.arduino.cc/en/Main/Software) and install it on your computer.

![Arduino IDE Download](../docs/images/arduinoide01.JPG)

#### 1.2 walk-through the Arduino Introduction page to learn basics
If you are new to the arduino system, you can learn the [ Arduino basics from here](arduino-intro.md) , after reading then go to the next step. 

### Step 2: Coding

#### 2.1 Algorithm

![algorithm](src/images/algorithm.png)

