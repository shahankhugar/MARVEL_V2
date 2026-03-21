# How a Fixed-Wing RC Plane Works — From Build to Flight

**Author:** Shashank Hugar
**Program:** UVCE MARVEL AI/ML — Level 1

---

## Introduction

An RC (Radio Controlled) plane is a scaled-down aircraft that is controlled remotely using a transmitter. Unlike drones which use multiple rotors to stay airborne, a fixed-wing RC plane generates lift the same way a real aircraft does — through the shape of its wings and forward motion through the air.

I built a fixed-wing RC plane with a 100cm fuselage from scratch. It had no flight controller — every control input was handled manually through the transmitter. This article explains how the aircraft works, what each component does, and the physics behind flight.

---

## The Basic Principle — How a Wing Generates Lift

A wing is shaped so that the top surface is curved and the bottom is flatter. When the plane moves forward, air splits at the leading edge of the wing. The air going over the top has to travel a longer path, so it moves faster. Faster moving air has lower pressure (Bernoulli's principle). The difference in pressure between the top and bottom of the wing creates an upward force — **lift**.

For a fixed-wing plane to stay airborne, the lift generated must be greater than or equal to the weight of the aircraft. This is why forward speed is critical — without it, the wing stops generating lift and the plane stalls.

---

## Main Components

### 1. Fuselage
The fuselage is the main body of the aircraft. On my build it was 100cm long. It holds all the electronics, connects the wings and tail, and houses the receiver and battery. The length affects the stability of the aircraft — a longer fuselage gives more pitch and yaw stability.

### 2. Motor and Propeller
The motor spins the propeller to generate thrust — the forward force that pushes the plane through the air. The propeller converts rotational energy into linear thrust by pushing air backward. More throttle = more RPM = more thrust = more speed = more lift.

A brushless DC motor was used, which is standard for RC aircraft. They are lighter, more efficient, and more powerful than brushed motors.

### 3. ESC (Electronic Speed Controller)
The ESC sits between the battery and the motor. It controls how fast the motor spins based on the throttle signal from the receiver. Without an ESC, you cannot vary the speed of a brushless motor — it would only be on or off.

### 4. Battery (LiPo)
RC planes use LiPo (Lithium Polymer) batteries because they are lightweight and can discharge large amounts of current quickly. The voltage and capacity of the battery directly affects flight time and motor performance.

### 5. Receiver and Transmitter
The transmitter is the handheld remote you hold. The receiver is mounted inside the plane. When you move the sticks on the transmitter, it sends a radio signal to the receiver, which then sends the corresponding signal to the servos and ESC.

### 6. Servos
Servos are small motors that move the control surfaces. Each control surface (aileron, elevator, rudder) has its own servo connected to it by a thin rod called a pushrod. When the servo rotates, it pulls or pushes the control surface to deflect it.

---

## Control Surfaces — How the Plane Maneuvers

This is the most important part. A fixed-wing aircraft is controlled by three surfaces, each responsible for movement on a different axis. My plane had all three.

### Ailerons — Roll
Ailerons are located on the outer trailing edge of both wings. They move in opposite directions — when the left aileron goes up, the right goes down, and vice versa.

When one aileron goes up, it reduces lift on that wing. The other wing has more lift. This difference causes the plane to **roll** — tilt sideways. Banking left or right is how the plane turns.

### Elevator — Pitch
The elevator is on the horizontal tail (called the horizontal stabilizer). When it deflects upward, it pushes the tail down, which tilts the nose up — the plane climbs. When it deflects downward, the nose drops and the plane descends.

Pitch controls whether the plane goes up or down.

### Rudder — Yaw
The rudder is on the vertical tail (vertical stabilizer). It deflects left or right to swing the nose of the plane left or right. This is called yaw.

On a car or boat, the rudder would be your main steering. On a plane, steering is mostly done with ailerons (roll), while the rudder helps coordinate turns and keeps the nose aligned.

---

## No Flight Controller — Manual Flying

Most modern RC planes and drones use a flight controller — a small computer with gyroscopes and accelerometers that automatically stabilizes the aircraft and corrects for disturbances like wind.

My plane had none of this. Every correction had to be made manually by the pilot through the transmitter in real time. This means:

- If a gust of wind rolls the plane, you correct it with the ailerons yourself
- If the nose pitches up too much, you push the elevator down yourself
- There is no auto-leveling, no GPS hold, no stabilization assist

This makes manual flying significantly harder but gives a much deeper understanding of aircraft dynamics and control. It also means the aircraft is lighter since there is no additional electronics onboard.

---

## Four Forces of Flight

At any moment in flight, four forces are acting on the aircraft:

- **Lift** — upward force from the wings
- **Weight** — downward force due to gravity
- **Thrust** — forward force from the motor and propeller
- **Drag** — backward force due to air resistance

For level flight: Lift = Weight and Thrust = Drag.

To climb: increase throttle (more thrust, more speed, more lift).

To descend: reduce throttle and push elevator down slightly.

---

## Key Takeaways

- A fixed-wing RC plane generates lift through wing shape and forward motion, not rotors
- Three control surfaces — ailerons (roll), elevator (pitch), rudder (yaw) — give full control of the aircraft in 3D space
- Without a flight controller, the pilot handles all stabilization manually
- The ESC, motor, and propeller work together to convert battery power into thrust
- Building from scratch requires understanding aerodynamics, electronics, and structural design together

---

*Built and written by Shashank Hugar — UVCE MARVEL AI/ML Level 1*
