###  DATE: 18/04/2024
###  NAME: RAJESHWARAN D
###  ROLL NO :212223040165
###  DEPARTMENT:CSE

# Experiment-no-6-DC-Motor-Speed-Control-Using-Arduino
### AIM : To control the speed and the direction of a DC motor using L293D driver ic( H- bridge)

### Components Required:
•	Arduino UNO board
•	L293D driver
•	12V DC motor
•	10K ohm potentiometer
•	Pushbutton
•	12V source
•	Breadboard
•	Jumper wires
### THEORY 
The L293D quadruple half-H drivers chip allows us to drive 2 motors in both directions, with two PWM outputs from the Arduino we can easily control the speed as well as the direction of rotation of one DC motor. (PWM: Pulse Width Modulation).
Arduino DC motor control circuit:
Project circuit schematic diagram is the one below.

![image](https://user-images.githubusercontent.com/36288975/167763051-b230c183-afc5-46f2-ba95-0f95e10dd6c9.png)
FIGURE-01 H BRIDGE CIRUCIT INTERFACE 

The speed of the DC motor (both directions) is controlled with the 10k potentiometer which is connected to analog channel 0 (A0) and the direction of rotation is controlled with the push button which is connected to pin 8 of the Arduino UNO board. If the button is pressed the motor will change its direction directly.
The L293D driver has 2 VCCs: VCC1 is +5V and VCC2 is +12V (same as motor nominal voltage). Pins IN1 and IN2 are the control pins where:
![image](https://user-images.githubusercontent.com/36288975/167763120-1421c2c5-8381-49eb-b376-03f6e1113b7a.png)
TABLE-01 EXITATION TABLE FOR H BRIDGE 

As shown in the circuit diagram we need only 3 Arduino terminal pins, pin 8 is for the push button which toggles the motor direction of rotation. Pins 9 and 10 are PWM signal outputs, at any time there is only 1 active PWM, this allows us to control the direction as well as the speed by varying the duty cycle of the PWM signal. The active PWM pin decides the motor direction of rotation (one at a time, the other output is logic 0).

### PROGRAM 
```
#include<Servo.h>

Servo sr1;

int pos=0;

int red=9;

int green=8;

void setup()

{

sr1.attach(6);

Serial.begin(9600);

pinMode(red, OUTPUT);

pinMode(green,OUTPUT);

}

void loop()

{

for(pos=0;pos<=180;pos+=5){

sr1.write(pos);

delay(200);

Serial.println(pos); }

for(pos=180;pos>=180;pos-=5){

sr1.write(pos);

delay(200);

Serial.println(pos); }

if(pos>120)

{

digitalWrite(red,HIGH);

delay(200);

digitalWrite(red,LOW);

delay(200); }

else{

digitalWrite(green, HIGH);

delay(200); // Wait for 1000 millisecond(s)

digitalWrite(green, LOW);

delay(200); }

}
```

### OUTPUT

### CIRCUIT DIAGRAM
![image](https://github.com/rajeshsmaha/EXPERIMENT-NO--05-INTERFACING-ANALOG-OUTPUT-SERVO-MOTOR-WITH-ARDUINO-/assets/147608800/cd4a7f5b-24c0-47e7-a99d-e01b9ec4ee65)

### SCHEMATIC VIEW
![WhatsApp Image 2024-04-29 at 2 57 25 PM](https://github.com/rajeshsmaha/EXPERIMENT-NO--05-INTERFACING-ANALOG-OUTPUT-SERVO-MOTOR-WITH-ARDUINO-/assets/147608800/41648a70-b3ae-43d2-92db-a4e01a1a24c3)

### GRAPH  

![image](https://github.com/rajeshsmaha/EXPERIMENT-NO--05-INTERFACING-ANALOG-OUTPUT-SERVO-MOTOR-WITH-ARDUINO-/assets/147608800/bec221f6-f56c-4fb3-817e-582a0de4ff39)


### RESULTS AND DISCUSSION 
Control of the speed and the direction of a DC motor using L293D driver ic( H- bridge) is successfully executed
