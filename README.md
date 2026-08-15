# ESP32-C3 Custom Development Board

A custom two-layer development board based on the **ESP32-C3-WROOM-02**, designed using **KiCad** as a hands-on project to develop practical skills in embedded hardware and PCB design.

> **Project Status:** PCB design completed
> **Design Tool:** KiCad
> **MCU Module:** ESP32-C3-WROOM-02
> **PCB:** 2-layer

---

## 📌 Project Overview

The objective of this project was to design a compact custom development board around the ESP32-C3-WROOM-02 rather than relying entirely on a commercially available development board.

The design incorporates the essential circuitry required for powering, programming, resetting, and interfacing with the ESP32-C3.

The project also served as a practical exercise in understanding the relationship between **schematic design, component selection, PCB layout, signal routing, power distribution, RF considerations, and design-rule checking**.

---

## ✨ Key Features

* ESP32-C3-WROOM-02 module
* USB-C connector
* USB 2.0 Full-Speed interface
* 3.3 V regulated power supply
* BOOT control
* RESET control
* GPIO breakout
* Decoupling capacitors
* Power filtering
* Ground copper zones
* Two-layer PCB
* ESP32 antenna keep-out region
* Through-hole mounting holes
* Front and back silkscreen labeling

---

## 🧠 ESP32-C3

The core of the board is the **ESP32-C3-WROOM-02** module.

The ESP32-C3 provides:

* 32-bit RISC-V processing
* Wi-Fi connectivity
* Bluetooth Low Energy
* GPIO interfaces
* UART
* SPI
* I²C
* ADC
* USB Serial/JTAG functionality

The module integrates the ESP32-C3 SoC and supporting RF components, allowing the custom PCB to focus on the required power, USB, control, and breakout circuitry.

---

## 🔌 USB-C Interface

A USB-C connector is provided for power and USB communication.

The USB data interface uses:

* **D+ → ESP32-C3 USB D+**
* **D− → ESP32-C3 USB D−**
* **VBUS → 5 V input**
* **GND → Ground**

The ESP32-C3 supports **USB 2.0 Full-Speed**, so this board is designed around the USB 2.0 Full-Speed interface rather than USB 3.x.

The D+ and D− signals are routed as a differential pair, with attention given to keeping the traces together and maintaining a suitable return path.

---

## ⚡ Power Architecture

The USB-C connector provides the board's primary 5 V input.

The power architecture can be summarized as:

```text
USB-C
  │
  │ 5 V VBUS
  ▼
3.3 V Voltage Regulator
  │
  │ 3.3 V
  ▼
ESP32-C3-WROOM-02
```

Decoupling and filtering capacitors are placed around the power circuitry to help reduce supply noise and provide local transient current.

---

## 🔄 BOOT and RESET

### RESET / EN

The ESP32-C3's EN/CHIP_EN control is used to reset and enable the module.

The RESET button provides a convenient way to restart the ESP32-C3.

### BOOT

The BOOT control is associated with the ESP32-C3 boot/strapping configuration and is used when entering the appropriate programming/download mode.

---

## 📡 Antenna Layout

The ESP32-C3-WROOM-02 includes an integrated PCB antenna.

Special attention was given to the antenna region during PCB layout.

The antenna area is kept clear of unnecessary:

* Copper
* Traces
* Vias
* Components

The PCB outline was also positioned with consideration for the antenna region.

> **Note:** Antenna performance depends heavily on the final PCB geometry, enclosure, surrounding materials, and manufacturing stack-up. This project has not been presented as a certified RF design.

---

## 🟢 PCB Design

The PCB was designed as a **2-layer board**.

### Layer usage

**F.Cu**

* Main component-side routing
* USB routing
* Signal routing
* Copper zones where appropriate

**B.Cu**

* Ground and power routing
* Supporting signal routing
* Copper zones

### PCB Design Considerations

During layout, attention was given to:

* Component placement
* Trace clearance
* Via placement
* Grounding
* Power distribution
* USB routing
* Antenna keep-out
* Board-edge clearances
* Silkscreen readability
* Component accessibility

---

## 🔧 Design Workflow

The board was developed through the following workflow:

```text
Requirements
     ↓
Schematic Design
     ↓
Component Selection
     ↓
Footprint Assignment
     ↓
PCB Placement
     ↓
Power & Ground Routing
     ↓
Signal Routing
     ↓
USB D+/D− Routing
     ↓
Antenna / Keep-out Review
     ↓
DRC
     ↓
Design Refinement
     ↓
Manufacturing Files
```

---

## 🛠️ Tools Used

| Tool                 | Purpose                         |
| -------------------- | ------------------------------- |
| **KiCad**            | Schematic and PCB design        |
| **KiCad PCB Editor** | Component placement and routing |
| **KiCad 3D Viewer**  | PCB visualization               |
| **Bitmap2Component** | Silkscreen/logo generation      |

---

## 📚 What I Learned

This project significantly improved my practical understanding of PCB design.

### PCB Design

* Schematic-to-PCB workflow
* Footprint selection
* Component placement
* PCB routing
* Copper zones
* Via placement
* DRC debugging
* Silkscreen design

### Hardware Design

* ESP32-C3 power requirements
* USB-C connectivity
* USB D+/D− routing
* Decoupling
* Reset and boot circuitry
* Grounding and return paths
* RF antenna keep-out considerations

### Design Thinking

One of the biggest lessons from this project was that **electrical connectivity alone does not make a good PCB**.

A functional PCB also requires consideration of:

* Signal integrity
* Power integrity
* Thermal behavior
* RF performance
* Manufacturing constraints
* Component availability
* Mechanical requirements

---

## 📁 Repository Structure

```text
ESP32-C3-Development-Board/
│
├── README.md
│
├── KiCad/
│   ├── Schematic/
│   ├── PCB/
│   ├── Footprints/
│   └── Libraries/
│
├── Manufacturing/
│   ├── Gerbers/
│   └── Drill/
│
├── Documentation/
│   ├── Schematic.pdf
│   ├── PCB_Layout.pdf
│   └── BOM.xlsx
│
├── Images/
│   ├── PCB_2D.png
│   ├── PCB_3D_Front.png
│   └── PCB_3D_Back.png
│
└── LICENSE
```

---

## 📸 Project Images

### PCB Layout

*Add your KiCad PCB Editor screenshot here.*

### 3D Front View

*Add your front 3D render here.*

### 3D Back View

*Add your back 3D render here.*

### Schematic

*Add your schematic image here.*

---

## ⚠️ Design Limitations

This board was developed primarily as a **learning and hardware-design project**.

Before using the design in a production product, the following should be independently verified:

* Power regulator thermal performance
* USB signal integrity
* Controlled impedance requirements
* Antenna/RF performance
* EMI/EMC performance
* Manufacturing tolerances
* Component availability
* ESD protection
* USB compliance
* Electrical safety requirements

These areas were not treated as formal certification/compliance testing in this project.

---

## 🚀 Future Improvements

Possible improvements for a future revision include:

* Dedicated ESD protection for USB
* More robust USB power protection
* Improved USB controlled-impedance routing
* Additional power-status indicators
* More GPIO accessibility
* Improved mounting/mechanical design
* Optimized antenna implementation
* Additional test points
* Power/current monitoring
* Improved manufacturing optimization
* Complete prototype testing and validation

---

## 📌 Project Status

**Design:** Completed
**Schematic:** Completed
**PCB Layout:** Completed
**DRC:** Reviewed
**Hardware Validation:** To be documented

---

## 👨‍💻 Author

**Jishin Bijumon George**

Electronics Engineering | PCB Design | Embedded Systems | Hardware Development

---

## 📜 License

Add an appropriate license depending on whether you want the hardware design files to be freely reused, modified, or commercially used.
