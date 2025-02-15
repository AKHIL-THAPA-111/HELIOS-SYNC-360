##### code

#define TRIG_PIN PD2  
#define ECHO_PIN PD5  
#define SERVO_PIN PC0  // Servo PWM output

void setup() {
    pinMode(TRIG_PIN, OUTPUT);
    pinMode(ECHO_PIN, INPUT);
    pinMode(SERVO_PIN, OUTPUT);
}

void loop() {
    uint16_t duration;
    int distance;

    // Send trigger pulse
    digitalWrite(TRIG_PIN, LOW);
    delayMicroseconds(2);
    digitalWrite(TRIG_PIN, HIGH);
    delayMicroseconds(10);
    digitalWrite(TRIG_PIN, LOW);

    // Wait for Echo pin (with timeout)
    unsigned long startTime = millis();
    while (digitalRead(ECHO_PIN) == LOW) {
        if (millis() - startTime > 100) return;  // Exit if timeout
    }

    // Measure Echo duration
    duration = 0;
    while (digitalRead(ECHO_PIN) == HIGH) {
        duration++;
        delayMicroseconds(1);
    }

    // Convert to distance (integer math)
    distance = (duration * 34) / 2000;

    // Servo control logic using if-else
    if (distance > 0 && distance <= 10) {
        // Move to 90° and stay there
        digitalWrite(SERVO_PIN, HIGH);
        delayMicroseconds(1500);
        digitalWrite(SERVO_PIN, LOW);
        
    } else {
        // Move back to 0°
        digitalWrite(SERVO_PIN, HIGH);
        delayMicroseconds(500);
        digitalWrite(SERVO_PIN, LOW);
    }
    }
    








###### => video demonstration



https://github.com/user-attachments/assets/04ceeaf0-ac6b-4794-822e-9f4fdf024ff1




