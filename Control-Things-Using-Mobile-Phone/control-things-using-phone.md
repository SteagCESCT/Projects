# Control Things Using Mobile

In this workhop we will learn how to control things using a mobile app with arduino and bluetooth module .


### Problem Statement 

We need to get up and walk into the switch board everytime to turn on and off the light or fan etc. 

### Idea

What if, we have a system that can be contol the light and fan using our mobile phone.

### Solution

Build a device that can be controled with mobile app , so we can use the device to trigger the actions on home appliance .


<hr>

### Prototype Building

* Build a device that can be control with Android Application 

Using Arduino and Andoird App we can make the idea into a relaity, since the Arduino can turn on and off using programming also it can be attached with bluetooth module, so we can build a mobile app that can be communicate with arduino.

![Diagram](src/images/diagram.png)

<hr>


### Things we need

1. Arduino Uno
2. HC-05 Bluetooth Module
3. Led's
3. Jumber Wires
4. Breadboard

<hr>


### Step 1: Arduino Setup

#### 1.1: Install Arduino IDE 

Download the [Arduino IDE](https://www.arduino.cc/en/Main/Software) and install it on your computer.

![Arduino IDE Download](../docs/images/arduinoide01.JPG)

#### 1.2 walk-through the Arduino Introduction page to learn basics
If you are new to the arduino system, you can learn the [ Arduino basics from here](arduino-intro.md) , after reading then go to the next step. 

### Step 2: Coding

#### 2.1 Algorithm

![algorithm](src/images/Arduino_BT_Algoritham.png)


<hr>


#### 2.2 Open Arduino IDE and Start a new Sketch 

![Arduino IDE Sketch](../docs/images/arduinoide02.JPG)

#### 2.3 Copy and Paste the Code

````
char data = 0; //Variable for storing received data

void setup()
{
  Serial.begin(9600);         //Sets the data rate in bits per second (baud) for serial data transmission
  pinMode(13, OUTPUT);        //Sets digital pin 13 as output pin

}
void loop()
{
  if (Serial.available() > 0) // Send data only when you receive data:
  {
    data = Serial.read();      //Read the incoming data and store it into variable data
    if (data == 'A')           //Checks whether value of data is equal to "A"
      digitalWrite(13, HIGH);  //If value is "A" then LED turns ON
    else if (data == 'B')      //Checks whether value of data is equal to "B"
      digitalWrite(13, LOW);   //If value is "B" then LED turns OFF
  }
}
````
<hr>


#### 2.4 Code Overview


* `char data = 0;` :- **data** is **char** data type and it used to hold the incoming data from Android Application that receved vis bluetooth interface. 

* `void setup()` :- The **setup()** function is called when a sketch starts. Use it to initialize variables, pin modes, start using libraries, etc. The **setup()** function will only run once, after each powerup or reset of the Arduino board.

* `Serial.begin(9600);` :- Sets the data rate in bits per second (baud) for serial data transmission , 

Syntax `Serial.begin(speed);` here we used speed as 9600bps. 

* `pinMode(13,OUTPUT)` :- Configures the specified pin to behave either as an input or an output. See the Digital Pins page for details on the functionality of the pins.

**Syntax** `pinMode(pin, mode)` :-  **pin** : the Arduino pin number to set the mode of, **mode** :  INPUT, OUTPUT, or INPUT_PULLUP. 

* `void loop()` :- After creating a **setup()** function, which initializes and sets the initial values, the **loop()** function does precisely what its name suggests, and loops consecutively, allowing your program to change and respond. Use it to actively control the Arduino board.

* `Serial.available()` :-  Get the number of bytes (characters) available for reading from the serial port, it used to reply only when we receive data.

* `data = Serial.read();` :- Reads incoming serial data and store into the **data** varible that we declare in the first place. 

* `if` and `else` :- The if statement checks for a condition and executes the proceeding statement or set of statements if the condition is 'true'.

* The if…​else allows greater control over the flow of code than the basic if statement, by allowing multiple tests to be grouped. An else clause (if at all exists) will be executed if the condition in the if statement results in false. The else can proceed another if test, so that multiple, mutually exclusive tests can be run at the same time.

* `digitalWrite(13,HIGH);` :- Write a HIGH value to a digital pin. 

* `digitalWrite(13,LOW);` :- Write LOW value to a digital pin. 

**Syntax** `digitalWrite(pin, value)` , **Parameters** `pin` : the Arduino pin number. `value` : HIGH or LOW.

<hr>


#### 2.5 Compile the code 

You can Compile and verify your code by clicking the **Verify** button on Arduino IDE, this process will check syntax errors. 

![verify code](src/images/verifycode.png)

after successful compilation you can see **Done Compiling**

![done verify](src/images/doneverify.JPG)
<hr>

#### 2.5 Upload the code into Arduino uno 

After successful compilation we can upload the code into Arduino Uno Devlopment board. for that we need click ***Upload* button.

![uploadcode](src/images/uploadcode.png)

before upaloading we need to select the devlopment board from the from Arduino IDE **Tools -> Board**  and **Port** from Arduino IDE **Tools -> Port**. 

![selectport](src/images/selectport.png) 
<br><br>

![selectboard](src/images/selectboard.png)


here I selected **Arduino Uno** as board and **COM26** as **Port**. 

Then click **Upload**

![doneupload](src/images/doneupload.JPG)

<hr>

### Step 3: Testing

We can test the project from halfway without bluetooth module by using **Serial Monitor** . 

#### 3.1 Connect LED 

Connect the **LED Postive** pin on **Arduino Pin 13** and **Negative Pin** on **Arduino Grond (GND)**

![arduinoandled](src/images/ledandarduino.png)

After connecting the LED connect the USB cable and Open **Serial Monitor** .

![serial monitor](src/images/serialmonitor.png)

Open the **Serial Monitor**  and try enter **A** or **B** and press enter or click **send** button. 

![send char](src/images/sendchar.png)

You can see logic in action.


![test gif](src/images/testOne.gif)

<hr>

### Step 4: Building Android Application

To build Mobile application we are using **MIT APP INVENTOR**, MIT App Inventor for Android is an open-source web application originally provided by Google, and now maintained by the Massachusetts Institute of Technology (MIT).App Inventor lets you develop applications for Android phones using a web browser and either a connected phone or emulator.

![MIT App inventor](src/images/mitlogo.png)


#### Flow chart 

![MIT App inventor flowchart](src/images/mitflow.png)

App inventor have two part

1. The App Inventor Designer, where you select the components for your app.
2. The App Inventor Blocks Editor, where you assemble program blocks that specify how the components should behave. You assemble programs visually, fitting pieces together like pieces of a puzzle.

Here we are going to control LED light by using our phone , for this we need an Application so we are using MIT App inventor.


#### 4.1 UI Devlopment 

The App Inventor Components are located on the left hand side of the Designer Window under the title Palette. Components are the basic elements you use to make apps on the Android phone. They're like the ingredients in a recipe. Some components are very simple, like a Label component, which just shows text on the screen, or a Button component that you tap to initiate an action.

![app ui](src/images/appui.png)

We need add two Buttons For **Turn ON** and **Turn OFF** the LED , and One **Listpicker** for selecting the bluetooth device. also we need to add the Bluetooth Client it avilable under the Connectivity tab.

![app ui](src/images/appui2.png)

