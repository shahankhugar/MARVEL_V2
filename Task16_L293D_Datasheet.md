# Task 16 — Datasheet Report: L293D Motor Driver

**Name:** Shashank Hugar
**Program:** UVCE MARVEL AI/ML — Level 1
**Status:** ✅ Completed

---

## What is the L293D?

The L293D is a quadruple half-H-bridge motor driver IC manufactured by Texas Instruments and ST Microelectronics. It is designed to drive DC motors, stepper motors, and other inductive loads that require higher current than a microcontroller can supply directly.

The "D" in L293D indicates it has built-in protection diodes (flyback diodes) that protect the IC from voltage spikes generated when a motor suddenly stops — something the base L293 does not have.

---

## Why a Motor Driver IC is Needed

A microcontroller like Arduino or ESP32 can only supply around 20–40mA from its output pins. A DC motor typically requires 500mA to several amperes to run. Connecting a motor directly to a microcontroller pin would damage the microcontroller instantly.

The L293D solves this by acting as a power switch — it takes low-current control signals from the microcontroller and uses them to switch a higher-current power supply to the motor. The microcontroller controls direction and speed; the L293D handles the actual power.

---

## IC Specifications (from Datasheet)

- Supply voltage (Vcc1 — logic): 5V
- Supply voltage (Vcc2 — motor): 4.5V to 36V
- Output current per channel: 600mA continuous, 1.2A peak
- Total channels: 4 half-bridge outputs (can drive 2 DC motors or 1 stepper motor)
- Built-in flyback diodes: Yes (the "D" suffix)
- Operating temperature: 0°C to 70°C
- Package: 16-pin DIP

---

## Pin Configuration

The L293D has 16 pins arranged as follows:

- **Pin 1 (EN1,2)** — Enable pin for channels 1 and 2. PWM signal here controls motor speed.
- **Pin 2 (IN1)** — Input 1 for channel 1 — direction control
- **Pin 3 (OUT1)** — Output 1 — connects to motor terminal A
- **Pin 4, 5 (GND)** — Ground pins (also act as heat dissipation)
- **Pin 6 (OUT2)** — Output 2 — connects to motor terminal B
- **Pin 7 (IN2)** — Input 2 for channel 1 — direction control
- **Pin 8 (Vcc2)** — Motor power supply (up to 36V)
- **Pins 9–15** — Mirror of pins 1–7 for the second motor channel
- **Pin 16 (Vcc1)** — Logic supply voltage (5V from microcontroller)

---

## H-Bridge — How Direction Control Works

The H-Bridge is the core circuit inside the L293D. It gets its name from its shape — four switches arranged like the letter H with the motor in the middle crossbar.

By opening and closing different combinations of switches, current can be made to flow through the motor in either direction:

**Forward:** IN1 = HIGH, IN2 = LOW → current flows from OUT1 to OUT2 → motor spins forward

**Reverse:** IN1 = LOW, IN2 = HIGH → current flows from OUT2 to OUT1 → motor spins in reverse

**Stop (brake):** IN1 = HIGH, IN2 = HIGH → both outputs at same potential → no current flows → motor stops

**Coast (free spin):** IN1 = LOW, IN2 = LOW → outputs floating → motor coasts to stop

This is the fundamental mechanism behind bidirectional motor control. Without an H-bridge, a motor can only be turned on or off — not reversed.

---

## PWM — Speed Control

PWM (Pulse Width Modulation) is applied to the Enable pin (EN) to control motor speed. The Enable pin does not switch the motor on and off directly — it controls how much power reaches the motor on average.

PWM rapidly switches the enable signal between HIGH and LOW. The ratio of ON time to total cycle time is the duty cycle:

- 100% duty cycle → full power → maximum speed
- 50% duty cycle → half power → half speed
- 0% duty cycle → no power → motor stopped

A microcontroller's `analogWrite()` function generates PWM with values from 0 (0% duty cycle) to 255 (100% duty cycle). This value is sent to the EN pin of the L293D, and the motor speed changes proportionally.

---

## Flyback Diodes

When a motor is suddenly switched off, the collapsing magnetic field in the motor coil generates a large reverse voltage spike — sometimes hundreds of volts. Without protection this spike would destroy the IC.

The L293D has eight built-in flyback diodes (clamp diodes) — one across each output transistor — that safely redirect these voltage spikes to the supply rail, protecting the IC from damage. This is why the L293D is preferred over the base L293 for motor control applications.

---

## Difference Between L293D and L298N

Both are H-bridge motor drivers but with key differences:

The L293D can supply 600mA per channel — suitable for small BO motors and light loads. The L298N can supply up to 2A per channel — suitable for larger motors.

The L293D has built-in flyback diodes. The L298N does not — external diodes must be added.

The L293D is available in a compact 16-pin DIP package. The L298N is a larger module.

For light robotics and small motor projects, L293D is preferred. For heavier loads, L298N is the better choice — which is why L298N was used in Task 10.

---

## Applications

- DC motor speed and direction control in robots
- Stepper motor control for CNC machines and 3D printers
- Conveyor belt drives
- Robotic arm joint control
- Any application requiring bidirectional control of an inductive load

---

## Key Takeaways

The L293D is a complete H-bridge driver in a single 16-pin IC. It solves the fundamental problem of microcontrollers not being able to drive motors directly. The H-bridge enables bidirectional control, PWM on the enable pin enables speed control, and the built-in flyback diodes protect the IC from motor-generated voltage spikes. Understanding this IC is essential for any robotics or automation project involving DC or stepper motors.

---

## Reference

L293D Datasheet — Texas Instruments
https://www.ti.com/lit/ds/symlink/l293d.pdf
