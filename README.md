# SmartPresence-ESP8266
SmartPresence is an intelligent room automation system powered by ESP8266, PIR motion detection, manual switches, and Alexa voice control — enabling your appliances to respond automatically to human presence and your commands.
✅ Final README File (Ready for GitHub)
markdown
Copy
Edit
# 🔌 Smart Home Room Automation with ESP8266, PIR Sensor & Alexa

A complete smart home automation system using **NodeMCU ESP8266**, **PIR sensor**, **relay module**, **manual push buttons**, and **Alexa voice assistant** via SinricPro.

This project automatically turns appliances ON when motion is detected and OFF when the room is empty — while allowing manual or voice control anytime.

---

## 🧠 Features

- ✅ Alexa voice control (via SinricPro)
- ✅ Manual push-button control
- ✅ PIR-based motion detection for automation
- ✅ Saves and restores relay states based on presence
- ✅ Real-time sync between Alexa, buttons, and PIR

---

## 🧰 Hardware Required

| Component                | Quantity |
|--------------------------|----------|
| ESP8266 NodeMCU          | 1        |
| PIR Motion Sensor        | 1        |
| 2-Channel Relay Module   | 1        |
| Momentary Push Buttons   | 2        |
| Jumper Wires + Breadboard| As needed |
| USB Cable (Micro)        | 1        |
| 5V Power Source           | 1        |

---

## ⚙️ Wiring (Pin Mapping)

| Function           | ESP8266 Pin | GPIO |
|--------------------|-------------|------|
| Relay 1 (Light)     | D6          | 12   |
| Relay 2 (Fan)       | D2          | 4    |
| Button 1            | D7          | 13   |
| Button 2            | D3          | 0    |
| PIR Sensor OUT       | D5          | 14   |
| PIR VCC             | 3V3         | -    |
| PIR GND             | GND         | -    |
| Relay VCC           | VIN (5V)    | -    |
| Relay GND           | GND         | -    |

---

## 💻 Setup Instructions

### 🔧 1. Install Arduino IDE & Board
- Download [Arduino IDE](https://www.arduino.cc/en/software)
- Go to `File > Preferences` → Paste in board URL:  
http://arduino.esp8266.com/stable/package_esp8266com_index.json

markdown
Copy
Edit
- Go to `Tools > Board > Board Manager` → Search `ESP8266` → Install

### 📦 2. Install Required Libraries
In Arduino IDE:
- Go to `Sketch > Include Library > Manage Libraries`
- Install:
- `SinricPro`
- `ArduinoJson`
- `WebSockets`
- `ESP8266WiFi`

---

## 🔑 SinricPro Setup (Alexa Integration)

1. Go to [https://sinric.pro](https://sinric.pro)
2. Create 2 devices: `"Light"` and `"Fan"`
3. Copy:
 - Device IDs
 - App Key
 - Secret Key
4. Paste them into the code in place of:
 ```cpp
 const char* switch1_ID = "Your_Switch1_ID";
 const char* switch2_ID = "Your_Switch2_ID";
 const char* appKey = "Your_Sinric_AppKey";
 const char* secretKey = "Your_Sinric_SecretKey";
🔄 How It Works
Event	Result
Button 1 pressed	Toggle Relay 1 (Light)
Button 2 pressed	Toggle Relay 2 (Fan)
"Alexa, turn on light"	Relay 1 turns ON
PIR detects motion	Restores last known ON/OFF states
No motion for 30 seconds	Turns OFF both relays

🔍 Testing & Debugging
Open Serial Monitor at 9600 baud to see live feedback

Watch for messages like:

Motion detected: Previous relay states restored

No motion: Relays OFF (state saved)

📸 Sample Circuit (Optional)
You can attach a simple wiring diagram image here.

⚠️ Safety Note (AC Usage)
Use proper insulation if controlling 220V devices

Use relay modules with opto-isolation

Don’t touch live wires while testing

🙌 Credits
Made with ❤️ by INDRJEET.
Open-source, for learning and home innovation.

🪪 License
This project is open-source under the MIT License.
