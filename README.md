# JZKiller
Hey guys. Right now I am making a basic programmable car for a school assignment

#include <SoftwareSerial.h>
SoftwareSerial mySerial(0,1); // RX|TX
int command;

 
void setup() {
  Serial.begin(9600);
  mySerial.begin(9600);
  Serial.println("You're connected via bluetooth");
  pinMode(13,OUTPUT);  //left motors forward
  pinMode(12,OUTPUT);  //left motors reverse
  pinMode(11,OUTPUT);  //right motors forward
  pinMode(10,OUTPUT);  //right motors reverse
  // put your setup code here, to run once:
}
void loop() {
  if (mySerial.available())
  {
    command=(mySerial.read());
    if (command=="F")   //moves the car forward
    {
      Serial.println("Forward");
      digitalWrite(13,HIGH);
      digitalWrite(12,LOW);
      digitalWrite(11,HIGH);
      digitalWrite(10,LOW);
      }
    else if (command=="B")  //moves the car backwards
    {
      Serial.println("Backwards");
      digitalWrite(13,LOW);
      digitalWrite(12,HIGH);
      digitalWrite(11,LOW);
      digitalWrite(10,HIGH);
      }
    else if (command=="L") //the car turns left
    {
      Serial.println("Left");
      digitalWrite(13,LOW);
      digitalWrite(12,HIGH);
      digitalWrite(11,HIGH);
      digitalWrite(10,LOW);
      }
    else if (command=="R")  //the car turns right
    {
      Serial.println("Right");
      digitalWrite(13,HIGH);
      digitalWrite(12,LOW);
      digitalWrite(11,LOW);
      digitalWrite(10,HIGH);
      }
      else if (command=="S")  //the car stops
      {
        Serial.print("Stop");
      digitalWrite(13,LOW);
      digitalWrite(12,LOW);
      digitalWrite(11,LOW);
      digitalWrite(10,LOW);
        }
    }
}
