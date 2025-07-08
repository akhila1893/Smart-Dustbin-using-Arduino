# Smart-Dustbin-using-Arduino
To design a Contactless smart dustbin that automatically opens its lid when a person approaches, using an ultrasonic sensor to detect proximity and a servo meter to control the lid

 Working Principle:
 
The ultrasonic sensor measures the distance of any object in front of it using sound waves.

When a person’s hand (or object) is detected within a set range (e.g., 10–30 cm), the Arduino receives the data.

Arduino sends a signal to the servo motor to rotate (usually 90°) to open the lid.

After a delay (e.g., 5 seconds), Arduino tells the servo to return to the original position, closing the lid.


CODE:

#include <Servo.h>

Servo myservo;  // create servo object to control a servo

const int trigPin = 9;    // Ultrasonic sensor trig pin
const int echoPin = 10;   // Ultrasonic sensor echo pin
const int servoPin = 6;   // Servo control pin

long duration;
int distance;

void setup() {
  pinMode(trigPin, OUTPUT);  // Sets the trigPin as an Output
  pinMode(echoPin, INPUT);   // Sets the echoPin as an Input
  myservo.attach(servoPin);  // attaches the servo on pin 6 to the servo object
  Serial.begin(9600);        // Starts the serial communication
}

void loop() {
  // Clear the trigPin
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  // Sets the trigPin on HIGH state for 10 micro seconds
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // Reads the echoPin, returns the sound wave travel time in microseconds
  duration = pulseIn(echoPin, HIGH);

  // Calculating the distance
  distance = duration * 0.034 / 2;

  // Prints the distance on the Serial Monitor
  Serial.print("Distance: ");
  Serial.println(distance);

  // Open the lid if an object is within the specified distance range (adjust as needed)
  if (distance < 15 && distance > 0) {
    openLid();
    delay(2000);  // Adjust delay time according to the servo and lid mechanism
    closeLid();
  }

  delay(1000);  // Delay before next reading
}

void openLid() {
  // Open the lid by rotating the servo motor
  myservo.write(0);   // Assuming 0 degrees is the open position, adjust as needed
}

void closeLid() {
  // Close the lid by rotating the servo motor back
  myservo.write(90);  // Assuming 90 degrees is the closed position, adjust as needed
}


