# Task 11 — LED Toggle Using ESP32 Web Server

**Name:** Shashank Hugar
**Program:** UVCE MARVEL AI/ML — Level 1
**Status:** ✅ Completed

---

## What is the ESP32?

I've worked with Arduino before but the ESP32 is a step up. It's a microcontroller like Arduino but it has built-in WiFi and Bluetooth — which means it can connect to a network on its own without any extra modules. That one difference opens up a completely different category of projects.

In this task I used that WiFi capability to turn the ESP32 into a web server — basically a tiny website hosted on the chip itself that lets you control an LED from your phone's browser.

---

## How the Web Server Works

The idea is simple once you understand it. The ESP32 connects to your WiFi and gets an IP address — something like `192.168.1.105`. You open that IP in your browser, the ESP32 sends back an HTML page with ON and OFF buttons. You click a button, your browser sends a request to the ESP32, and the ESP32 turns the LED on or off.

No cloud, no internet needed. Just the ESP32 and your phone on the same WiFi.

Step by step:
- ESP32 connects to WiFi using the SSID and password in the code
- It starts a web server listening on port 80 (standard HTTP)
- You open the IP in your browser — ESP32 sends back the control page
- Click ON → browser hits `/on` → ESP32 sets GPIO pin HIGH → LED turns on
- Click OFF → browser hits `/off` → ESP32 sets GPIO pin LOW → LED turns off

---

## GPIO Pins

GPIO stands for General Purpose Input Output. These are the pins you connect components to. Each pin can be set as either an input (reading a sensor or button) or an output (controlling an LED or motor). Here I configured one GPIO pin as output and connected the LED to it.

---

## Setting Up Arduino IDE for ESP32

This part took a bit of setup. By default Arduino IDE doesn't support ESP32 — you have to manually add the board package.

Go to **File → Preferences** → paste this URL in "Additional Board Manager URLs":
```
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
```

Then **Tools → Board → Board Manager** → search ESP32 → install. After that you can select the ESP32 board and upload like normal.

---

## The Code

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

`WiFi.h` handles connecting to the network. `WebServer.h` handles the incoming requests. `server.on()` maps a URL path to a function — so when `/on` is hit it calls `handleOn()` which sets the pin HIGH. The `loop()` just keeps listening for new requests continuously.

---

## What Happened

Connected to WiFi, opened the IP on my phone browser, clicked ON — LED turned on. Clicked OFF — LED turned off. Worked cleanly with no lag. The whole thing felt like controlling real hardware from a webpage which is pretty cool when you see it working for the first time.

---

## Video Demo

[![Watch](https://img.youtube.com/vi/z45kebAVEvY/0.jpg)](https://www.youtube.com/watch?v=z45kebAVEvY)
