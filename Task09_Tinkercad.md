# Task 09 — Tinkercad: Ultrasonic Sensor & Radar System

**Name:** Shashank Hugar
**Program:** UVCE MARVEL AI/ML — Level 1
**Status:** ✅ Completed

---

## What is Tinkercad?

Tinkercad is a free browser-based platform by Autodesk that lets you design and simulate electronic circuits without any physical hardware. You can place components like Arduino boards, sensors, motors, LEDs, and resistors on a virtual breadboard, write Arduino code, and run a full simulation — including the Serial Monitor output — all in the browser.

It is widely used for prototyping and learning electronics because it eliminates the need to purchase components just to test an idea.

---

## Part 1 — Ultrasonic Distance Sensor

### How an Ultrasonic Sensor Works

An ultrasonic sensor (HC-SR04) measures distance by emitting a high-frequency sound pulse and measuring how long it takes for the echo to return after bouncing off an obstacle.

The working principle is:

- A short HIGH pulse is sent to the **Trig** pin — this fires a sound burst
- The sensor emits 8 pulses of 40kHz ultrasonic sound
- The sound travels forward, hits an obstacle, and reflects back
- The **Echo** pin goes HIGH for exactly the duration the sound was travelling
- The microcontroller measures this duration using `pulseIn()`
- Distance is calculated using the formula:

```
distance = duration × 0.034 / 2
```

The `0.034` is the speed of sound in cm/microsecond. We divide by 2 because the sound travels to the obstacle and back — so the total distance is half the total travel time.

### Circuit Built

An HC-SR04 ultrasonic sensor was connected to an Arduino Uno R3 in Tinkercad:

- VCC → 5V
- GND → GND
- Trig → Digital Pin 9
- Echo → Digital Pin 10 (single pin mode used in simulation)

### Code

```cpp
int sensor = 10;
long duration;
float distance;

void setup() {
  Serial.begin(9600);
}

void loop() {
  // Send trigger pulse
  pinMode(sensor, OUTPUT);
  digitalWrite(sensor, LOW);
  delayMicroseconds(2);
  digitalWrite(sensor, HIGH);
  delayMicroseconds(10);
  digitalWrite(sensor, LOW);

  // Read echo
  pinMode(sensor, INPUT);
  duration = pulseIn(sensor, HIGH);

  // Calculate distance
  distance = duration * 0.034 / 2;

  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  delay(500);
}
```

### Result

The simulation ran successfully. The Serial Monitor displayed live distance readings updating every 500ms. The simulated obstacle was detected at approximately **78–81 cm**, which matched the visual position of the obstacle in the Tinkercad workspace.

---

## Part 2 — Radar System using Ultrasonic Sensor and Servo Motor

### Concept

A single ultrasonic sensor can only detect objects directly in front of it. By mounting it on a servo motor that sweeps back and forth, the sensor covers a wide arc — this is the basis of a simple radar system.

The servo rotates from 0° to 180° and back in small steps. At each angle, the ultrasonic sensor takes a distance reading. If the reading is below a threshold, an object has been detected within range at that angle.

### How a Servo Motor Works

A servo motor is a DC motor with a built-in gearbox and feedback mechanism that allows it to rotate to a precise angle. It receives a PWM (Pulse Width Modulation) signal and moves to the corresponding position. The standard range is 0° to 180°.

In the radar system, the Arduino sends angle commands to the servo one degree at a time, pausing at each step to take a sensor reading.

### What the Radar Does

- Servo sweeps from 0° to 180° then back to 0° continuously
- At every degree, the ultrasonic sensor fires and measures distance
- If an object is within range, it is detected and the angle + distance can be logged
- This creates a simple 180° field of detection — the core of radar technology

### Connection to Real Radar

Real radar systems work on the same principle — emit a signal, detect the reflection, and log both the angle and the return time to map objects in the surroundings. The difference is that real radar uses radio waves instead of sound waves, operates over much larger distances, and rotates 360°. The fundamental mechanism of emit → reflect → measure → map is identical.

---

## Physical Maze Solver Robot — Relevant Context

Alongside this Tinkercad task, a physical maze-solving robot was also built using an HC-SR04 ultrasonic sensor on an actual Arduino-based system. The sensor was used to detect walls and obstacles in real time while the robot navigated the maze using the Left Hand Rule algorithm. This gave hands-on experience with the same sensor used in this simulation — understanding how timing and distance calculations translate from simulation to real hardware.

---

## Key Takeaways

Tinkercad allows full circuit simulation without physical components, making it an excellent prototyping tool. The ultrasonic sensor works by measuring the round-trip time of a sound pulse to calculate distance. Mounting the sensor on a servo motor extends its detection range from a single point to a wide arc — which is the core concept behind radar systems. Building the same sensor into a physical robot reinforced how simulation-level understanding translates directly to real-world hardware.
