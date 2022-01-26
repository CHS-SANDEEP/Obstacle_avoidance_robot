const int trig = 7;
const int echo = 6;
const int leftFrwrd = 5;
const int leftBack = 4;
const int rightFrwrd = 2;
const int rightBack = 3;
float duration = 0;
float distance = 0;

String voice;

#include<Servo.h>
#define IR A5
Servo myservo;
void setup() 
{
  pinMode(trig , OUTPUT);
  pinMode(echo , INPUT);
  pinMode(IR, INPUT);
  pinMode(leftFrwrd , OUTPUT);
  pinMode(leftBack , OUTPUT);
  pinMode(rightFrwrd , OUTPUT);
  pinMode(rightBack , OUTPUT);
  myservo.attach(8);
  myservo.write(90);
 
  Serial.begin(9600);

}
void loop()
{
while(Serial.available()) {
  voice = "";  
  voice = Serial.readString();
  
    Serial.print(voice);
}

  
  digitalWrite(trig,LOW);
  delay(100);
  digitalWrite(trig, HIGH);
  delay(1000);
  digitalWrite(trig, LOW);
  duration = pulseIn(echo, HIGH);
  distance = (duration*0.034/2);
  Serial.print("Distance: ");
  Serial.println(distance);
  if(distance > 40){  
   if(voice == "move forward"){
    forward();
  }else if(voice == "move backward"){
    backward();
  }else if(voice == "turn left"){
    left();
  }else if(voice == "turn right"){
    right();
  }else if(voice == "stop") {
    stop();
  }
  
    voice = "";
  }
  else{
    stop();}
}

void forward(){
    digitalWrite(leftFrwrd , HIGH);
    digitalWrite(leftBack , LOW);
    digitalWrite(rightFrwrd , HIGH);
    digitalWrite(rightBack ,LOW );
  }
 void backward(){
  int IR_Sensor = digitalRead(IR);
  if(IR_Sensor == 0) {
    digitalWrite(leftFrwrd , LOW);
    digitalWrite(leftBack , LOW);
    digitalWrite(rightFrwrd , LOW);
    digitalWrite(rightBack ,LOW );
    voice="";
  }
  else{
    digitalWrite(leftFrwrd , LOW);
    digitalWrite(leftBack , HIGH);
    digitalWrite(rightFrwrd , LOW);
    digitalWrite(rightBack ,HIGH );
  }
  }
 void right(){  
    myservo.write(0);
    delay(1000);
    myservo.write(90);
    delay(500);
    digitalWrite(leftFrwrd , LOW);
    digitalWrite(leftBack , HIGH);
    digitalWrite(rightFrwrd , HIGH);
    digitalWrite(rightBack ,LOW );
    delay(1000);
    digitalWrite(leftFrwrd , HIGH);
    digitalWrite(leftBack , LOW);
    digitalWrite(rightFrwrd , HIGH);
    digitalWrite(rightBack ,LOW );
   
  }
 void left(){
     myservo.write(180);
     delay(1000);
     myservo.write(90);
     delay(500);
    digitalWrite(leftFrwrd , HIGH);
    digitalWrite(leftBack , LOW);
    digitalWrite(rightFrwrd , LOW);
    digitalWrite(rightBack ,HIGH );
    delay(1000);
    digitalWrite(leftFrwrd , HIGH);
    digitalWrite(leftBack , LOW);
    digitalWrite(rightFrwrd , HIGH);
    digitalWrite(rightBack ,LOW );
   
  }
 void stop(){
    digitalWrite(leftFrwrd , LOW);
    digitalWrite(leftBack , LOW);
    digitalWrite(rightFrwrd , LOW);
    digitalWrite(rightBack ,LOW );
  }
