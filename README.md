# Hank-Robotic-Arm
Robotic arduino project. Actively being upgraded/updated. This was a first attempt at a robotic arm, to grip things

Most recent image:
![20220403_141257](https://user-images.githubusercontent.com/59476460/161455879-e43a642f-c852-40cb-adf2-b1adbc0e4d9b.jpg)





//All code communicates off of serial data from "Tera Term". Tera term connects to the board, and outputs a user's letter input

//

//

#include<Servo.h> // include server library

#include <Stepper.h> //include stepper library

//

//

Servo ser1; // Micro servo, for claw actuation

Servo ser2; //Large servo, kept at the center of the arm for angling

Servo ser3; // Large servo, kept at the base of the arm for angling

Servo ser4; // Micro servo, for claw rotation

Servo ser5; // Large servo, kept at the top of the arm for angling

//

const int stepsPerRevolution = 200; //number of steps for each letter input into the stepper

Stepper myStepper(stepsPerRevolution, 10, 11, 12, 13); //Stepper motor, kept within base of the arm for rotation. Attach to pins 10, 11, 12, and 13


int poser = 0; // initial position of each servo

int val; //name the serial input value

void setup() {

myStepper.setSpeed(40); //set the speed of the stepper motor to 40

Serial.begin(9600); // Serial comm begin at 9600bps

ser1.attach(5);//attach claw actuation micro-servo to pin 5

ser2.attach(3);//attach mid-angling servo to pin 3

ser3.attach(2);//attach base-angling servo to pin 2

ser4.attach(4);//attach claw rotation micro-servo to pin 4

ser5.attach(6);//attach top-angling servo to pin 6

}

void loop() {

if (Serial.available()) // if serial value is available (from Tera Term)

{

val = Serial.read();// then read the serial value, equate the value to the "val"

if (val == 'k') //if value input is equals to k

{

poser += 1; //then position of servo motor increases by 1 ( anti clockwise)

ser1.write(poser);//the new position is inserted into a servo positioning function -- the servo will move according to the new "poser" value

delay(15);//delay, for the servo to get to the position

}

if (val == 'l') //if value input is equals to l

{

poser -= 1; //then position of servo motor decreases by 1 (clockwise)

ser1.write(poser);// the servo will move according to position

delay(15);//delay for the servo to get to the position

}
{

if (val == 'a') //if value input is equals to a

{

poser += 1; //then position of servo motor increases by 1 ( anti clockwise)

ser2.write(poser);// the servo will move according to position

delay(15);//delay for the servo to get to the position

}

if (val == 's') //if value input is equals to s

{

poser -= 1; //then position of servo motor decreases by 1 (clockwise)

ser2.write(poser);// the servo will move according to position

delay(15);//delay for the servo to get to the position

}
{

if (val == 'z') //if value input is equals to z

{

poser += 1; //then position of servo motor increases by 1 ( anti clockwise)

ser3.write(poser);// the servo will move according to position

delay(15);//delay for the servo to get to the position

}
if (val == 'x') //if value input is equals to x

{

poser -= 1; //then position of servo motor increases by 1 ( anti clockwise)

ser3.write(poser);// the servo will move according to position

delay(15);//delay for the servo to get to the position

}
if (val == 'q') //if value input is equals to q

{

poser += 1; //then position of servo motor increases by 1 ( anti clockwise)

ser4.write(poser);// the servo will move according to position

delay(15);//delay for the servo to get to the position

}
if (val == 'w') //if value input is equals to w

{

poser -= 1; //then position of servo motor increases by 1 ( anti clockwise)

ser4.write(poser);// the servo will move according to position

delay(15);//delay for the servo to get to the position

}
if (val == 'o') //if value input is equals to o

{

poser += 1; //then position of servo motor increases by 1 ( anti clockwise)

ser5.write(poser);// the servo will move according to position

delay(15);//delay for the servo to get to the position

}
if (val == 'p') //if value input is equals to p

{

poser -= 1; //then position of servo motor increases by 1 ( anti clockwise)

ser5.write(poser);// the servo will move according to position

delay(15);//delay for the servo to get to the position

}
}
if (val == 'n') //if value input is equals to n

{

Serial.println("clockwise");
myStepper.step(stepsPerRevolution);

delay(15);//delay for the stepper to get to the position

}
{

if (val == 'm') //if value input is equals to m

{

Serial.println("counterclockwise");
myStepper.step(-stepsPerRevolution);
delay(15);//delay for the stepper to get to the position

}


}}}}
