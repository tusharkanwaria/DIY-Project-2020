# DIY-Project-2020
DIY project code for arduino at IIT KGP 

code : 

   #include <AFMotor.h>
 #define trigPin A0
#define echoPin A1
int Laser = A2;
int disco =  A4;
int laseron = 1;
float duration, distance;
char Incoming_value = 0;
AF_DCMotor motor4(4); 
AF_DCMotor motor2(2); 


void setup() {
  Serial.begin(9600);         
  pinMode(A2, OUTPUT);
  

}

void loop() {
 
     
 if(Serial.available() > 0)  
  {
    Incoming_value = Serial.read();      
           
    if(Incoming_value == '1') 
    { digitalWrite(trigPin, LOW);
        delayMicroseconds(2);
        digitalWrite(trigPin, HIGH);
       delayMicroseconds(10);
          digitalWrite(trigPin, LOW);
        duration = pulseIn(echoPin, HIGH);
          distance = (duration / 2) * 0.0343;
         Serial.print(distance);
         delay(400);
         if ( distance>20 && distance<75)
         {digitalWrite(Laser,HIGH);
         delay(200);
         digitalWrite(Laser,LOW);
         delay(200);
         digitalWrite(Laser,HIGH);
         delay(100);
         digitalWrite(Laser,LOW);
         delay(100);
         digitalWrite(Laser,HIGH);
         delay(50);
         digitalWrite(Laser,LOW);
         delay(50);
         digitalWrite(Laser,HIGH);
         delay(200);
         





         
         }
         }
        
    else if(Incoming_value == '2')       
    digitalWrite(Laser,HIGH);

    else if(Incoming_value == '0')       
    digitalWrite(Laser,LOW);

     else if(Incoming_value == '7'){ 
   motor4.run(FORWARD);
    motor4.setSpeed(255);  
    delay(100);
    motor4.setSpeed(0);;
  }
else if(Incoming_value == '5') 
   { motor2.setSpeed(255); 
  motor2.run(BACKWARD);
  delay(500);
    motor2.setSpeed(0);}
    
    else if(Incoming_value == '3') {
     motor4.run(BACKWARD);
    motor4.setSpeed(255);  
    delay(500);
    motor4.setSpeed(0);}

    else if(Incoming_value == '8') 
  {motor4.run(BACKWARD);
    motor4.setSpeed(255);  
    delay(100);
    motor4.setSpeed(0);}

  
    else if(Incoming_value == '9') 
  { motor2.setSpeed(255); 
  motor2.run(BACKWARD);
  delay(500);
    motor2.setSpeed(0);}

  
    else if(Incoming_value == '5') 
   { motor2.setSpeed(255); 
  motor2.run(BACKWARD);
  delay(500);
    motor2.setSpeed(0);}
}}
