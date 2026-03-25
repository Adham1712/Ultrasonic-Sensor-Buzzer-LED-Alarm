# Project 2 : Ultrasonic-Sensor-Buzzer-LED-Alarm
Description:
This is an Ultrasonic sensor project that, when detecting an object within its range, would make the buzzer beep and LED light up until the object blocking the view is removed. 

Tools used:
- Elegoo UNO R3
- LED
- Resistor
- Breadboard
- buzzer
- Ultrasonic sensor (HC-SO4 model)

Process:
- Planned the circuit layout
- Built the physical circuit on a breadboard
- Wrote and uploaded all of my code
- Tested and debugged LED, buzzer and ultrasonic sensor

Results:
- Project worked flawlessly
- Learned how to use buzzer and Ultrasonic sensor and timing them correctly and using them in unison with one another, as well as with the LED

Photos: 
- https://drive.google.com/file/d/1xX3g6LX0MPM41Q3aEOUiN556IWUqSb_t/view?usp=sharing
- https://drive.google.com/file/d/1hYNfpYBWadJlIahnQP4hd-u-t3u7ekr9/view?usp=sharing
- https://drive.google.com/file/d/10ADolyS-4dd7NygyEkawEt9g1wtpEjWn/view?usp=sharing
- https://drive.google.com/file/d/1Teb9dx51l5XJB7KkFO8bPmwdltvaTTkJ/view?usp=sharing
- https://drive.google.com/file/d/1JVOmB320HZRUNMsFrwtEmFgOAquPnkOE/view?usp=sharing

Videos:
- https://drive.google.com/file/d/1PU7-79AD20gU43bOa2tCLl8fZyx2WyYK/view?usp=sharing
- https://drive.google.com/file/d/1sfgGHlgI0wpXI33sdDkt941PVoVP7nFs/view?usp=sharing
- https://drive.google.com/file/d/1sfgGHlgI0wpXI33sdDkt941PVoVP7nFs/view?usp=sharing
- https://drive.google.com/file/d/1umDe1SePo0zbWSWySqktdMC3yHmo5oz5/view?usp=sharing
- https://drive.google.com/file/d/1umDe1SePo0zbWSWySqktdMC3yHmo5oz5/view?usp=sharing

Code:

const int trigPin = 9;
const int echoPin = 10;
const int buzzer = 11;
const int ledPin = 13;

long duration;
int distance;
int safetyDistance;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(buzzer, OUTPUT);
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);
  distance = duration * 0.034 / 2;

  safetyDistance = distance;
  if (safetyDistance <= 5) {
    digitalWrite(buzzer, HIGH);
    digitalWrite(ledPin, HIGH);
  } else {
    digitalWrite(buzzer, LOW);
    digitalWrite(ledPin, LOW);
  }

  Serial.print("Distance: ");
  Serial.println(distance);
}
