# Morse Code Tutor System

A layered Morse code learning system that combines an ESP8266 (NodeMCU) for real-time signal processing with a Raspberry Pi 4 for supervision, logging, and web hosting.

This project allows users to practice Morse code through audio playback and physical key input, with real-time feedback delivered through a web interface.

---

## Features

* Real-time Morse code playback (audio output via ESP8266)
* Telegraph key input with timing-based decoding
* Dot/Dash classification with tolerance for human input
* Adjustable WPM (Words Per Minute)
* Adjustable tone frequency (Hz)
* Web-based control interface
* Session tracking and performance logging (Raspberry Pi)
* Local hosting (no external server required)

---

## System Architecture

This system is divided into two main layers:

### ESP8266 (Device Layer)

Handles all real-time interaction and signal processing:

* Telegraph key detection (D6)
* Morse timing logic
* Dot/Dash classification
* Audio generation (D5)
* Input grading logic

### Raspberry Pi 4 (Supervisor Layer)

Handles system coordination and data management:

* Logs user attempts
* Stores word lists
* Manages session data
* Tracks performance over time
* Hosts the web interface

---

## Hardware Setup

* ESP8266 NodeMCU
* Raspberry Pi 4
* Piezo speaker or buzzer connected to D5
* Telegraph key or push button connected to D6 (INPUT_PULLUP to GND)
* Breadboard and jumper wires

---

## Web Interface

The system includes a browser-based interface that allows users to:

* Start and stop Morse playback
* Adjust WPM and tone frequency
* View real-time feedback
* Interact with the tutor without refreshing the page

---

## API Overview

The ESP8266 exposes REST-style endpoints:

* GET /api/status → returns system status
* POST /api/start → starts Morse playback
* POST /api/stop → stops playback
* POST /api/config → updates settings

Example configuration request:

```json
{
  "wpm": 18,
  "hz": 700
}
```

---

## How It Works

1. User selects a word or input through the web interface
2. Raspberry Pi sends instructions to the ESP8266
3. ESP8266 converts the word into Morse code
4. Audio is played through the speaker
5. User inputs Morse using the telegraph key
6. ESP8266 evaluates timing and classifies dots and dashes
7. The system compares input with expected output
8. Raspberry Pi logs results and tracks performance

---

## Project Structure

```
morse-code-tutor-system/
│
├── esp8266/            # Firmware (NodeMCU)
├── raspberry-pi/       # Server, logging, data
├── web/                # Frontend interface
├── docs/               # Diagrams and documentation
├── images/             # Demo and setup images
├── README.md
└── LICENSE
```


---

## Open Source

This project is open-source and intended for learning and experimentation in Computer networks, Embedded Systems, IoT architecture, and real-time device interaction.

---

## License

MIT License

---

## Author

Josiah Horn
Victor Adeoye
Ajayi Ifeloluwa
