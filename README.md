# Kalam 🖊️

**Kalam** is an open-source, low-cost assistive communication device designed for blind and visually impaired users. By translating simple analog joystick movements into Morse code, Kalam enables users to type text efficiently without relying on a visual interface, leveraging tactile interaction and muscle memory.

The word **"Kalam"** means *pen*, *expression*, *writing*, or *communication*. This project embodies the vision of making digital writing accessible to everyone.

---

## 💡 Inspiration & Vision

Many modern assistive technologies are expensive, complex, or steep to learn. Morse code offers a lightweight, highly efficient alternative that can be mastered purely through touch and muscle repetition.

Kalam is built on the belief that communication should be:

* **Independent:** Removing the absolute necessity for high-cost visual interfaces.
* **Affordable:** Utilizing widely available, budget-friendly microcontrollers and components.
* **Accessible:** Adapting technology to fit the unique ways people interact with the digital world.

---

## ✨ Features

* **Tactile Text Entry:** Seamless Morse code typing using standard joystick directions.
* **Real-Time Decoding:** Instant translation from Morse symbols to alphanumeric characters.
* **Lightweight Architecture:** Optimized embedded C++ code that runs perfectly on low-spec microcontrollers.
* **Minimal Hardware Footprint:** Requires only an Arduino and a basic joystick module to get started.
* **Highly Expandable:** Designed to easily integrate displays, haptics, or wireless modules.

---

## 🕹️ Control Scheme

Kalam maps the standard 2-axis movement of a joystick into the building blocks of Morse code:

| Direction | Action | Symbol / Output |
| --- | --- | --- |
| **Up** | Input Dot | `.` |
| **Down** | Input Dash | `_` |
| **Right** | Confirm Character / Add Space | Decodes current sequence / ` ` |
| **Left** | Backspace | Deletes last symbol/character |

### 📋 Example Input (Typing "HELLO")

1. **H** $\rightarrow$ `.` `.` `.` `.` $\rightarrow$ Move **Right** (Confirms 'H')
2. **E** $\rightarrow$ `.` $\rightarrow$ Move **Right** (Confirms 'E')
3. **L** $\rightarrow$ `.`, `_`, `.`, `.` $\rightarrow$ Move **Right** (Confirms 'L')
4. **L** $\rightarrow$ `.`, `_`, `.`, `.` $\rightarrow$ Move **Right** (Confirms 'L')
5. **O** $\rightarrow$ `_`, `_`, `_` $\rightarrow$ Move **Right** (Confirms 'O')

---

## 🛠️ Hardware Requirements

### Core Components

* **Microcontroller:** Arduino UNO, Nano, or compatible board.
* **Input Device:** Standard Analog 2-Axis Joystick Module (e.g., KY-023).
* **Connectivity:** USB Cable (for power and Serial interfacing).

### Optional Upgrades

* **Haptics:** Vibration motor or piezo buzzer for tactile/audio feedback.
* **Display:** 0.96" OLED Display (SSD1306) for visual debugging.
* **Wireless:** HC-05 Bluetooth module or an ESP32 upgrade for standalone wireless keyboard capabilities.

---

## 🔌 Circuit Diagram

Connect your joystick module to the Arduino using the following pinout configuration:

| Joystick Pin | Arduino Pin | Notes |
| --- | --- | --- |
| **VCC** | 5V | Power supply |
| **GND** | GND | Ground |
| **VRx** | A0 | Analog X-axis (Left/Right) |
| **VRy** | A1 | Analog Y-axis (Up/Down) |
| **SW** | D2 | Joystick Switch Click *(Optional)* |

---

## ⚙️ How It Works

1. **Read Analog Inputs:** The Arduino constantly monitors the analog voltage levels from the `VRx` and `VRy` pins.
2. **Threshold Detection:** Movement thresholds are established to prevent accidental triggers due to joystick drift:
```cpp
if (y > 800) currentMorse += ".";   // Joystick pushed Up
if (y < 200) currentMorse += "_";   // Joystick pushed Down

```


3. **Sequence Buffering:** Dot and dash symbols append to a dynamic string buffer.
4. **Decoding Matrix:** When the joystick is pushed **Right**, the buffered Morse sequence matches against a lookup library to output the exact alphanumeric character.
5. **Output Generation:** The final decoded text is printed out straight to the system's Serial connection.

### 🖥️ Expected Serial Monitor Output

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

1. **Clone the Repository:**

```bash
   git clone https://github.com/pranitdhanade-sys/Kalam.git

```

2. **Open the Project:** Launch the Arduino IDE and open the main sketch file (`.ino`) from the cloned directory.
3. **Upload Code:** Connect your Arduino via USB, select your board/port configuration, and hit **Upload**.
4. **Launch Monitor:** Open the Serial Monitor (`Ctrl + Shift + M`), and change the baud rate setting to **115200**.

---

## 🗺️ Roadmap & Future Improvements

We intend to evolve Kalam across multiple fronts to maximize its accessibility potential:

### 🔊 Accessibility Extensions

* **Vibration & Audio Feedback:** Distinct haptic rhythms and audio tones for dots, dashes, and letters.
* **Speech Synthesis:** Text-to-speech integration to speak aloud full sentences.
* **Braille Output:** Integration with small physical Braille refreshable pins.

### 📶 Connectivity & UI

* **USB/Bluetooth HID Keyboard:** Allow the device to act as an actual native keyboard for PCs and smartphones.
* **Mobile App Integration:** Companion app for easier device calibration and text logs.

### 🧠 Smart Features

* **Predictive Text:** T9-style or AI-powered predictive text suggestions to speed up typing rates.
* **Adaptive Learning:** Software that automatically calibrates thresholds based on individual muscle response profiles.

### 🏗️ Hardware Re-designs

* **Wearable Glove/Wristband:** Moving the inputs away from joysticks to wearable finger-taps.
* **Ergonomic Enclosures:** 3D-printable cases optimized for handheld comfort.

---

## 🤝 Contributing

Contributions make the open-source community an amazing place to learn, inspire, and create. Any contributions you make toward improving accessibility, code optimization, or documentation are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

Distributed under the **MIT License**. See `LICENSE` for more information.

```

```
