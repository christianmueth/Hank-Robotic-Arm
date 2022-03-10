# Hank-Robotic-Arm
Very small-scale arduino project. Still being upgraded/updated. This was a first attempt at a robotic arm, to grip things

Most recent image:
![20220120_232342 (1)](https://user-images.githubusercontent.com/59476460/157579713-48997e9d-8c48-4233-8b8f-87327c6e65e6.jpg)





#include<Servo.h> // include server library

#include <Stepper.h>

Servo ser1; // create servo object to control a servo 1

Servo ser2;// create servo object to control a servo 2

Servo ser3;// create servo object to control a servo 3

const int stepsPerRevolution = 200; //Define number of steps for the stepper motor, in its rotation

Stepper myStepper(stepsPerRevolution, 10, 11, 12, 13);// Define pins of stepper motor, and assign step definition


int poser = 0; // initial position of servo

int val; // define value of control input

void setup() {

myStepper.setSpeed(40);

Serial.begin(9600); // Serial comm begin at 9600bps

ser1.attach(5);// servo is connected at pin 5

ser2.attach(3); // servo is connected at pin 3

ser3.attach(2);// servo is connected at pin 2
}

void loop() {

if (Serial.available()) // if serial value is available

{

val = Serial.read();// then read the serial value

if (val == 'd') //if value input is equals to d

{

poser += 1; //then position of servo motor increases by 1 ( anti clockwise)

ser1.write(poser);// the servo will move according to position

delay(150);//delay for the servo to get to the position

}

if (val == 'a') //if value input is equals to a

{

poser -= 1; //than position of servo motor decreases by 1 (clockwise)

ser1.write(poser);// the servo will move according to position

delay(150);//delay for the servo to get to the position

}

{

if (val == 'e') //if value input is equals to d

{

poser += 1; //then position of servo motor increases by 1 ( anti clockwise)

ser2.write(poser);// the servo will move according to position

delay(15);//delay for the servo to get to the position

}

if (val == 'q') //if value input is equals to a

{

poser -= 1; //then position of servo motor decreases by 1 (clockwise)

ser2.write(poser);// the servo will move according to position

delay(15);//delay for the servo to get to the position

}

{

if (val == 'c') //if value input is equals to d

{

poser += 1; //then position of servo motor increases by 1 ( anti clockwise)

ser3.write(poser);// the servo will move according to position

delay(15);//delay for the servo to get to the position

}

if (val == 'z') //if value input is equals to d

{

poser -= 1; //then position of servo motor increases by 1 ( anti clockwise)

ser3.write(poser);// the servo will move according to position

delay(15);//delay for the servo to get to the position

}

}
if (val == 'n') //if value input is equals to a

{

Serial.println("clockwise");

myStepper.step(stepsPerRevolution);

delay(15);//delay for the stepper to get to the position

}
{

if (val == 'm') //if value input is equals to d

{

Serial.println("counterclockwise");

myStepper.step(-stepsPerRevolution);

delay(15);//delay for the stepper to get to the position

}


}}}}
