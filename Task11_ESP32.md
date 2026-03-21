# Task 11 — LED Toggle Using ESP32 Web Server

**Name:** Shashank Hugar
**Program:** UVCE MARVEL AI/ML — Level 1
**Status:** ✅ Completed

---

## What is the ESP32?

The ESP32 is a microcontroller similar to the Arduino Uno but with one critical addition — built-in WiFi and Bluetooth. This means it can connect to a local network and communicate wirelessly, something the Arduino Uno cannot do without external modules.

This makes the ESP32 ideal for IoT (Internet of Things) projects — devices that can be controlled or monitored over a network. In this task, the ESP32 acts as a standalone web server, hosting a webpage that controls a physical LED connected to one of its GPIO pins.

---

## What is a Web Server?

A web server is a program that listens for requests from a browser and sends back responses — usually HTML pages. Normally web servers run on large computers in data centres. The ESP32 is powerful enough to run a lightweight web server locally on the chip itself.

When connected to the same WiFi network, any device — phone, laptop, tablet — can open the ESP32's IP address in a browser, see the control page, and send commands to toggle the LED.

---

## How it Works

**Step 1 — ESP32 connects to WiFi**

The code is given your WiFi network name (SSID) and password. On startup, the ESP32 connects to that network and is assigned a local IP address (like `192.168.1.105`).

**Step 2 — Web server starts**

The ESP32 starts listening on port 80 — the standard HTTP port. Any browser request to that IP address is handled by the ESP32.

**Step 3 — Browser loads the control page**

When you open the IP address in your browser, the ESP32 sends back an HTML page with two buttons — LED ON and LED OFF.

**Step 4 — Button press sends a request**

Clicking ON sends a GET request to `/on`. Clicking OFF sends a request to `/off`. The ESP32 reads the URL path and acts accordingly.

**Step 5 — GPIO pin is toggled**

The LED is connected to a GPIO pin. When `/on` is received, the pin is set HIGH — current flows and the LED turns on. When `/off` is received, the pin is set LOW — LED turns off.

---

## GPIO Pins

GPIO stands for General Purpose Input Output. These are the pins on the ESP32 that can be configured as either inputs (reading sensors, buttons) or outputs (controlling LEDs, motors). In this task, one GPIO pin was configured as an output to control the LED.

---

## Configuring Arduino IDE for ESP32

By default Arduino IDE only supports Arduino boards. To upload code to an ESP32 you need to add the ESP32 board package:

Go to **File → Preferences** → paste the ESP32 board manager URL into "Additional Board Manager URLs":
```
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
```

Then go to **Tools → Board → Board Manager** → search ESP32 → install.

After installation, select the correct ESP32 board from **Tools → Board**, set the correct COM port, and upload as normal.

---

## Code Overview

```cpp
#include <WiFi.h>
#include <WebServer.h>

const char* ssid = "Your_WiFi_Name";
const char* password = "Your_WiFi_Password";

WebServer server(80);
int ledPin = 2;

void handleOn() {
  digitalWrite(ledPin, HIGH);
  server.send(200, "text/plain", "LED is ON");
}

void handleOff() {
  digitalWrite(ledPin, LOW);
  server.send(200, "text/plain", "LED is OFF");
}

void setup() {
  pinMode(ledPin, OUTPUT);
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) delay(500);

  server.on("/on", handleOn);
  server.on("/off", handleOff);
  server.begin();
}

void loop() {
  server.handleClient();
}
```

The `WiFi.h` library handles network connection. `WebServer.h` handles incoming browser requests. `server.on()` maps URL paths to functions. `server.handleClient()` in the loop continuously listens for incoming requests.

---

## Result

The ESP32 successfully connected to the WiFi network and hosted a web server. The LED connected to the GPIO pin was toggled on and off in real time by clicking buttons on the browser page — accessed from a phone on the same network. No physical button or switch was needed — the control was entirely wireless through the browser.

---

## Key Takeaways

The ESP32's built-in WiFi makes it a powerful tool for IoT applications — any physical component (LED, motor, relay) can be controlled wirelessly through a browser. GPIO pins are the bridge between software and hardware. Arduino IDE with the ESP32 board package provides a familiar environment to program the chip. This is the foundation for home automation, smart devices, and remote monitoring systems.

---

## Video Demo

https://www.youtube.com/watch?v=z45kebAVEvY
