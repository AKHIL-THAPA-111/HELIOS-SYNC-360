# PROJECT HelioSync360 [Smart Dual Axis Solar Tracker]
  
  - by Akhil, Vardan , Pridhvi , Visnudev and Kabiraj
  
![Screenshot 2025-02-14 022425](https://github.com/user-attachments/assets/9a655418-36ca-4368-b4d8-b3b4906c941d)


###### ABSTRACT : This project implements a dual-axis solar tracker using a servo motor controlled by the CH32V003F4U6 microcontroller with a 32-bit RISC-V core. The system adjusts solar panel orientation to maximize energy absorption, ensuring efficiency through servo control enhancing sustainability .
***
### OVERVIEW OF THE PROJECT

![image](https://github.com/user-attachments/assets/b48da5e9-179e-49c7-ac9a-aae386d8257e)
***
###### => video presentation
https://github.com/vardanchettri/Hackathon_2025/blob/main/presentation.mp4
***
### Key Features 
* Automatic Dual-Axis Tracking: Constantly adjusts solar panel orientation (azimuth and elevation) for maximum sunlight exposure.
* Smart Microcontroller: Built on the 32-bit RISC-V core  for low power consumption and high computational performance.
* Efficient Servo Motor Control: Utilizes real-time feedback for precise, low-power motor movements.
* Energy Optimization: Increases solar panel efficiency by up to 30%, lowering operational costs in the long term.
# Why This Matters 
#### Scalable and Cost-Effective
###### => "SCALABLE" , Perfect for small to medium-sized solar installations, easily scalable to meet growing energy needs.
#### Low Maintenance
###### => This design "minimizes manual intervention", saving time and labor costs.
***
# How It Works
*  Sensors detect sunlight intensity
* Servo motors adjust the solar panel's position
* Microcontroller processes feedback and ensures alignment
***
# Requirements 
###### HARDWARE
* VSD SQUADRON MINI
* SOLAR PANEL
* SERVO MOTORS
* DIODES,TRANSISTER
* POTENTIOMETER 
###### SOFTWARE
* PLATFORM.IO
* VISUAL STUDIO CODE
* FRAMEWORK : ARDUINO
* LANGUAGE : C++
***
# SCHEMATIC DIAGRAM
![image](https://github.com/user-attachments/assets/bf3c1d5e-9929-4610-903f-394a5858a67a)

***

## WORKING OF THE CODE(LOGIC)

###### FLOW CHART :

![Screenshot 2025-02-14 013436](https://github.com/user-attachments/assets/a65cb03b-d131-4e22-8294-4467ddf35eb1)


##### code
```

#define SERVO_PIN PD0
#define SERVO2_PIN PD6
#define ldr1_PIN PD4 
#define ldr2_PIN PD5 
#define ldr3_PIN PD3 
#define ldr4_PIN PD2 

int moveServoo = 750;
int moveServoo2 = 650;
int stepsize1 = 200;
int stepsize2 = 200;
bool forward = 1;
bool reverse = 0;
bool forward2 = 1;
bool reverse2 = 0;


void setup() {
  pinMode(SERVO_PIN, OUTPUT);
  pinMode(SERVO2_PIN, OUTPUT);
  pinMode(ldr1_PIN, INPUT);
  pinMode(ldr2_PIN, INPUT);
  pinMode(ldr3_PIN, INPUT);
  pinMode(ldr4_PIN, INPUT);
}

void loop() {
  /
  if ((digitalRead(ldr1_PIN) == HIGH) && (digitalRead(ldr2_PIN) == HIGH) && (digitalRead(ldr3_PIN) == HIGH) && (digitalRead(ldr4_PIN) == HIGH)) { //1
    ;
  } 
  else if ((digitalRead(ldr1_PIN) == LOW) && (digitalRead(ldr2_PIN) == HIGH) && (digitalRead(ldr3_PIN) == HIGH) && (digitalRead(ldr4_PIN) == HIGH)) { //2
      ;
  } 
  else if ((digitalRead(ldr1_PIN) == HIGH) && (digitalRead(ldr2_PIN) == LOW) && (digitalRead(ldr3_PIN) == HIGH) && (digitalRead(ldr4_PIN) == HIGH)) { //3
      ;
  } 
  else if ((digitalRead(ldr1_PIN) == LOW) && (digitalRead(ldr2_PIN) == LOW) && (digitalRead(ldr3_PIN) == HIGH) && (digitalRead(ldr4_PIN) == HIGH)) { //4
      if (forward2 == 1){
      moveServoo2 = moveServoo2 + stepsize2;
    }
      else if (reverse2 == 1){
      moveServoo2 = moveServoo2 - stepsize2;
    }
  }
  else if ((digitalRead(ldr1_PIN) == HIGH) && (digitalRead(ldr2_PIN) == HIGH) && (digitalRead(ldr3_PIN) == LOW) && (digitalRead(ldr4_PIN) == HIGH)) { //5
      ;
  } 
  else if ((digitalRead(ldr1_PIN) == LOW) && (digitalRead(ldr2_PIN) == HIGH) && (digitalRead(ldr3_PIN) == LOW ) && (digitalRead(ldr4_PIN) == HIGH)) { //6
      if (forward2 == 1){
      moveServoo2 = moveServoo2 + stepsize2;
    }
      else if (reverse2 == 1){
      moveServoo2 = moveServoo2 - stepsize2;
    }
  } 
  else if ((digitalRead(ldr1_PIN) == HIGH) && (digitalRead(ldr2_PIN) == LOW) && (digitalRead(ldr3_PIN) == LOW) && (digitalRead(ldr4_PIN) == HIGH)) { //7
      if (forward2 == 1){
      moveServoo2 = moveServoo2 + stepsize2;
    }
      else if (reverse2 == 1){
      moveServoo2 = moveServoo2 - stepsize2;
    }
  } 
  else if ((digitalRead(ldr1_PIN) == LOW) && (digitalRead(ldr2_PIN) == LOW) && (digitalRead(ldr3_PIN) == LOW) && (digitalRead(ldr4_PIN) == HIGH)) { //8
      if (forward == 1){
      moveServoo = moveServoo + stepsize1;
    }
      else if (reverse == 1){
      moveServoo = moveServoo - stepsize1;
    }
  } 
  else if ((digitalRead(ldr1_PIN) == HIGH) && (digitalRead(ldr2_PIN) == HIGH) && (digitalRead(ldr3_PIN) == LOW) && (digitalRead(ldr4_PIN) == LOW)) { //9
      if (forward2 == 1){
      moveServoo2 = moveServoo2 + stepsize2;
    }
      else if (reverse2 == 1){
      moveServoo2 = moveServoo2 - stepsize2;
    }
  } 
  else if ((digitalRead(ldr1_PIN) == LOW) && (digitalRead(ldr2_PIN) == HIGH) && (digitalRead(ldr3_PIN) == LOW) && (digitalRead(ldr4_PIN) == LOW)) { //10
      if (forward == 1){
      moveServoo = moveServoo + stepsize1;
    }
      else if (reverse == 1){
      moveServoo = moveServoo - stepsize1;
    }
  } 
  else if ((digitalRead(ldr1_PIN) == HIGH) && (digitalRead(ldr2_PIN) == LOW) && (digitalRead(ldr3_PIN) == LOW) && (digitalRead(ldr4_PIN) == LOW)) { //11
      if (forward == 1){
      moveServoo = moveServoo + stepsize1;
    }
      else if (reverse == 1){
      moveServoo = moveServoo - stepsize1;
    }
  } 
  else if ((digitalRead(ldr1_PIN) == LOW) && (digitalRead(ldr2_PIN) == LOW) && (digitalRead(ldr3_PIN) == LOW) && (digitalRead(ldr4_PIN) == LOW)) { //12
    ;
  } 
  else if ((digitalRead(ldr1_PIN) == HIGH) && (digitalRead(ldr2_PIN) == HIGH) && (digitalRead(ldr3_PIN) == HIGH) && (digitalRead(ldr4_PIN) == LOW)) { //13
      ;
  }
  else if ((digitalRead(ldr1_PIN) == LOW) && (digitalRead(ldr2_PIN) == HIGH) && (digitalRead(ldr3_PIN) == HIGH) && (digitalRead(ldr4_PIN) == LOW)) { //14
      if (forward2 == 1){
      moveServoo2 = moveServoo2 + stepsize2;
    }
      else if (reverse2 == 1){
      moveServoo2 = moveServoo2 - stepsize2;
    }
  } 
  else if ((digitalRead(ldr1_PIN) == HIGH) && (digitalRead(ldr2_PIN) == LOW) && (digitalRead(ldr3_PIN) == HIGH) && (digitalRead(ldr4_PIN) == LOW)) { //15
      if (forward2 == 1){
      moveServoo2 = moveServoo2 + stepsize2;
    }
      else if (reverse2 == 1){
      moveServoo2 = moveServoo2 - stepsize2;
    }
  }
  else if ((digitalRead(ldr1_PIN) == LOW) && (digitalRead(ldr2_PIN) == LOW) && (digitalRead(ldr3_PIN) == HIGH) && (digitalRead(ldr4_PIN) == LOW)) { //16
      if (forward == 1){
      moveServoo = moveServoo + stepsize1;
    }
      else if (reverse == 1){
      moveServoo = moveServoo - stepsize1;
    }
  }  
  
  if (moveServoo > 2500) {
    forward = 0;
    reverse=1;
  }
  if (moveServoo < 750) {
    forward = 1;
    reverse=0;
  }
  if (moveServoo2 > 1600) {
    forward2 = 0;
    reverse2=1;
  }
  if (moveServoo2 < 650) {
    forward2 = 1;
    reverse2=0;
  }

  
  moveBothServos(moveServoo, moveServoo2);

  

  delay(1);





void moveBothServos(int pulseWidth1, int pulseWidth2) {
  for (int i = 0; i < 50; i++) { 
    digitalWrite(SERVO_PIN, HIGH);
    digitalWrite(SERVO2_PIN, HIGH);
    
    delayMicroseconds(min(pulseWidth1, pulseWidth2)); 
    digitalWrite(SERVO_PIN, (pulseWidth1 < pulseWidth2) ? LOW : HIGH);
    digitalWrite(SERVO2_PIN, (pulseWidth2 < pulseWidth1) ? LOW : HIGH);
    
    delayMicroseconds(abs(pulseWidth1 - pulseWidth2));
    digitalWrite(SERVO2_PIN, LOW);

    delay(20 - (max(pulseWidth1, pulseWidth2) / 1000)); 
}




```

***



# Demonstration 

![image](https://github.com/user-attachments/assets/c87c1dbc-0abb-451d-9568-972ffaf68489)
***
###### => video demonstration
https://github.com/vardanchettri/Hackathon_2025/blob/main/helioSync360sssihl.mp4






***


 
