# 🌙 Automatic Night Lamp using Arduino and Photoresistor

This project demonstrates an automatic night lamp using Arduino and a photoresistor (LDR).
The LED turns ON automatically in dark conditions and turns OFF when sufficient light is present.
This project introduces sensor-based automation using Arduino.

---

## 🧰 Components Used
- Arduino Uno / Nano
- Photoresistor (LDR)
- 1 × 10kΩ resistor
- 1 × LED
- 1 × 220Ω resistor
- Breadboard
- Jumper wires

---

## 🔌 Circuit Connections

### Photoresistor (LDR) Voltage Divider
| Connection | Arduino |
|----------|---------|
| One end of LDR | 5V |
| Other end of LDR | A0 |
| 10kΩ resistor | A0 → GND |

### LED Connection
| Component | Arduino Pin |
|---------|-------------|
| LED (+) | D9 |
| LED (–) | GND |

⚠️ The LED is connected with a 220Ω resistor to protect the Arduino pin.

---

## ⚙️ Working Principle
- The photoresistor changes resistance based on light intensity
- Arduino reads the sensor value using `analogRead()`
- When the environment is dark, the LED turns ON
- When sufficient light is detected, the LED turns OFF
- This process repeats continuously

---

## 💻 Arduino Code
```cpp
int ldrPin = A0;
int ledPin = 9;
int ldrValue = 0;

void setup() {
  pinMode(ledPin, OUTPUT);
}

void loop() {
  ldrValue = analogRead(ldrPin);

  if (ldrValue < 500) {   // Dark condition
    digitalWrite(ledPin, HIGH);
  } else {               // Bright condition
    digitalWrite(ledPin, LOW);
  }
}
