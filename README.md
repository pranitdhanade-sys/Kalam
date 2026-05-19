

# Kalam 🖊️

**Kalam** is an open-source, low-cost assistive communication device designed to empower blind, visually impaired, and deafblind users. By translating standard analog joystick movements into Morse code, Kalam enables individuals to type and communicate efficiently entirely through tactile interaction, muscle memory, and haptic feedback.

The word **"Kalam"** translates to *pen*, *expression*, or *writing*. This project aims to lower the barrier to digital expression by replacing expensive, specialized assistive technology with an affordable, customizable, open-source alternative.

---

## 📺 Demo Video & Audio Walkthrough

> [!NOTE]
> **To our visually impaired contributors and users:** The video linked below includes a full spoken-audio description detailing the hardware layout, joystick movements, and corresponding serial text output.

* **Video Link:** [Click here to watch the Kalam demonstration video](https://github.com/pranitdhanade-sys/Kalam/blob/main/demo.mp4) *(Replace this link and the image source above once your video is ready)*
* **Visual Description of the Demo:** The video shows a compact breadboard containing an Arduino Nano connected to a standard thumb-stick joystick. A hand pushes the joystick up multiple times to buffer dots, then down to buffer dashes. Pushing the joystick to the right triggers the immediate conversion of the Morse string into text on a nearby laptop screen running a serial monitor.

---

## 🕹️ Accessible Control Scheme

Kalam uses the physical limits of a 2-axis joystick to map out the characters of the alphabet. The control mapping is structured as follows:

* **Joystick Up:** Input Dot (`.`)
* **Joystick Down:** Input Dash (`_`)
* **Joystick Right:** Confirm letter / Insert a text space
* **Joystick Left:** Backspace (Deletes the last inputted symbol or letter)

### Text Entry Example (Typing the word "HELLO")

1. **Letter H:** Push **Up** four times (`....`), then push **Right** to confirm 'H'.
2. **Letter E:** Push **Up** once (`.`), then push **Right** to confirm 'E'.
3. **Letter L:** Push **Up**, **Down**, **Up**, **Up** (`._..`), then push **Right** to confirm 'L'.
4. **Letter L:** Push **Up**, **Down**, **Up**, **Up** (`._..`), then push **Right** to confirm 'L'.
5. **Letter O:** Push **Down** three times (`___`), then push **Right** to confirm 'O'.

---

## 💡 Accessibility and Design Goals

* **Low Cognitive Load:** Morse code relies on spatial and rhythmic muscle memory, making it ideal for non-visual operation.
* **Affordable Fabrication:** Built using common, budget-friendly electronics components rather than proprietary, high-cost assistive tech.
* **Tactile Autonomy:** Designed to be operated entirely through physical sensation without relying on screens, text-heavy menus, or complex gestures.

---

## 🛠️ Hardware Specifications

### Standard Components

* **Microcontroller:** Arduino UNO, Nano, or any equivalent 5V board.
* **Input Interface:** Analog 2-Axis Joystick Module (e.g., KY-023 or similar).
* **Interface Cable:** USB Cable for power and serial data transmission.

### Recommended Accessibility Add-ons

* **Haptic Interface:** 5V Vibration Motor to give physical confirmation patterns for dots and dashes.
* **Audio Interface:** Piezo Buzzer to output matching audio tones.

---

## 🔌 Circuit Wiring Map

| Joystick Module Pin | Arduino Connection Pin | Purpose |
| --- | --- | --- |
| **VCC** | 5V | Logic Power |
| **GND** | GND | Ground Reference |
| **VRx** | A0 | X-axis Position (Left/Right controls) |
| **VRy** | A1 | Y-axis Position (Up/Down controls) |
| **SW** | D2 | Built-in push-button toggle *(Optional)* |

---

## ⚙️ Software Logic & Operation

The firmware monitors the analog voltages output by the joystick potentiometers. Threshold limits are coded to trigger inputs smoothly:

```cpp
// Coordinate detection rules
if (y > 800) currentMorse += ".";   // Joystick pushed completely Up
if (y < 200) currentMorse += "_";   // Joystick pushed completely Down

```

When the joystick is deflected to the **Right**, the string buffer containing the dots and dashes is run through an internal lookup array. The translated character is sent directly to the device interface.

### Example Serial Output Log

```text
DOT
.

DASH
._

LETTER: A

TEXT: HELLO

```

---

## 🚀 Installation & Setup

1. **Clone the Source Code:**
```bash
git clone [https://github.com/pranitdhanade-sys/Kalam.git](https://github.com/pranitdhanade-sys/Kalam.git)

```


2. **Flash the Code:** Load the main `.ino` sketch file using your preferred IDE (such as Arduino IDE) and upload it to your board.
3. **Configure the Interface:** Launch your serial terminal utility and set the communication speed to **115200 baud**.

---

## 🗺️ Future Accessibility Enhancements

* **Native HID Support:** Upgrading to microcontrollers like the ATmega32U4 (Arduino Leonardo/Micro) or ESP32-S3 to let Kalam function natively as a USB or Bluetooth wireless keyboard.
* **Integrated Speech Synthesis:** Attaching a text-to-speech breakout board to read back fully typed words without needing a computer screen.
* **Smart Autocorrect:** Implementing a localized dictionary or lightweight predictive engine to compensate for accidental joystick movements.

---

## 🤝 Contributing & Community

We warmly welcome pull requests, hardware revisions, and feedback—especially from users within the blind and visually impaired community.

1. Fork this project repository.
2. Create your working branch (`git checkout -b feature/Optimization`).
3. Commit your modifications (`git commit -m 'Add haptic patterns'`).
4. Push your changes (`git push origin feature/Optimization`).
5. Open a Pull Request for review.

---

## 📄 License

This repository is distributed and licensed under the open-source **MIT License**.

```

```
