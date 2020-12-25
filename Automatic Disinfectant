#include <LiquidCrystal_I2C.h>
#include <Wire.h>

LiquidCrystal_I2C lcd(0x27,16,2);

const int trigPin = 7;
const int echoPin = 6;
const int buzzer = 8;
const int ledPin = 13;
const int rolePin = 2;
// defines variables
long duration;
int distance;
int safetyDistance;
int counter = 0;
int currentState = 0;
int previousState = 0;
int counter2;
int result;

void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(buzzer, OUTPUT);
pinMode(ledPin, OUTPUT);
pinMode(rolePin, OUTPUT);
Serial.begin(9600); // Starts the serial communication
lcd.backlight();
lcd.begin(16, 2);
lcd.setCursor(0, 0);
lcd.print("Senseless People");
 }



void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
counter2=0;


if (30<=safetyDistance&&safetyDistance <=171+){ //Enter the Distance 
  digitalWrite(buzzer, HIGH);
  delay(500);
  currentState = 1;
  digitalWrite(ledPin, HIGH);
  digitalWrite(rolePin, LOW);
}
else if(safetyDistance<10){
digitalWrite(rolePin,HIGH);
currentState = 0;
}

else{
  digitalWrite(buzzer,LOW);
  digitalWrite(ledPin, LOW);
  digitalWrite(rolePin,LOW);
 
  currentState = 0;

}

delay(200);
 if(currentState != previousState){
 if(currentState == 1){
 counter = counter + 1;
 result=counter;
 lcd.print(result);
 lcd.setCursor(0,1);
 delay(1000);
 }
 }

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
}
