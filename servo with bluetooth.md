#include<Servo.h>

Servo servo2;
const int angle=0;

int ledPin=13;
int state=0;
int flag=0;

void setup() {
  pinMode(ledPin, OUTPUT);
  servo2.attach(7);
  servo2.write(angle);
  digitalWrite(ledPin, LOW);
  Serial.begin(9600);
  delay(1000);
  
}

void loop(){
  if(Serial.available()>0) {
    state=Serial.read();
    flag=0;
  }
if (state=='0') {
  //Serial.println(state);
  servo2.write(0);
  if(flag==0) {
    Serial.println("servo0");
    flag=1;
  }
}
else if (state== '1') {
  servo2.write(90);
  //Serial.println(state);
  if(flag==0) {
    Serial.println("servo90");
    flag=1;
  }
}
}
