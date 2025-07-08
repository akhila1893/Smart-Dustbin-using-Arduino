# Smart-Dustbin-using-Arduino
To design a Contactless smart dustbin that automatically opens its lid when a person approaches, using an ultrasonic sensor to detect proximity and a servo meter to control the lid

 Working Principle:
 
The ultrasonic sensor measures the distance of any object in front of it using sound waves.

When a person’s hand (or object) is detected within a set range (e.g., 10–30 cm), the Arduino receives the data.

Arduino sends a signal to the servo motor to rotate (usually 90°) to open the lid.

After a delay (e.g., 5 seconds), Arduino tells the servo to return to the original position, closing the lid.
