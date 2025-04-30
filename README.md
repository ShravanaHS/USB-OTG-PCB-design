# USB Type-C OTG Adapter Project


## 1. Introduction to USB Type-C

USB Type-C is a modern, future-proof interface that surpasses older USB connectors in terms of functionality, speed, and versatility. Its key advantages include:

Reversible Plug Orientation – No more flipping the connector.

Higher Pin Count – Supports more complex data and power operations.

Backward Compatibility – Supports legacy USB 2.0, 3.0, and 3.1 standards.

Higher Power Delivery (PD) – Standard 3A at 5V (15W), up to 5A at 20V (100W) with certified cables.

Higher Data Speeds – Supports USB 3.1 SuperSpeed (up to 10 Gbps).

Alternate Modes Support – Can carry HDMI, DisplayPort, MHL, and Thunderbolt signals.



##  2. What is USB OTG?

USB OTG allows devices like smartphones to act as hosts instead of just peripherals. Examples:

- 📁 Accessing files from a USB flash drive
- ⌨️ Connecting a keyboard or mouse
- 🎮 Plugging in game controllers
- 🌐 Using USB Ethernet dongles



##  3. USB Type-C Data and Power Capabilities

| Standard           | Data Rate | Power Delivery |
|--------------------|-----------|----------------|
| USB 2.0            | 480 Mbps  | 5V @ 500 mA    |
| USB 3.0            | 5 Gbps    | 5V @ 900 mA    |
| USB 3.1 Gen 2      | 10 Gbps   | 5V @ 3A (15W)  |
| USB PD (Certified) | Up to 40 Gbps | Up to 100W |



##  4. Alternate Modes

| Mode         | Use Case                        |
|--------------|----------------------------------|
| DisplayPort  | Video output to monitor/TV       |
| HDMI         | Video/audio output               |
| Thunderbolt 3/4 | High-speed + display + power |
| MHL          | Mobile video to TVs              |

Active cables have chips to manage these functions. Passive cables may support only basic modes.



##  5. OTG Supported Peripherals and Protocols

| Peripheral         | Protocol                    |
|--------------------|-----------------------------|
| Flash Drive        | Mass Storage Class (MSC)    |
| Keyboard/Mouse     | HID Class                   |
| Ethernet Adapter   | CDC-NCM or RNDIS            |
| Game Controller    | HID                         |
| MIDI Instruments   | USB Audio/MIDI Class        |
| USB Audio          | USB Audio Class             |
| Barcode Scanner    | Serial/HID                  |



##  6. USB Pin Configuration

### USB Type-C Connector

- 24 pins total
- Important lines:  
  - **VBUS / GND** for power  
  - **D+ / D-** for USB 2.0 data  
  - **TX/RX pairs** for SuperSpeed  
  - **CC1 / CC2** for orientation & role detection

### USB-A Female

- 4 pins: VBUS, D+, D-, GND

**OTG Configuration Tip:**  
Connect **5.1kΩ** resistor from **CC1 or CC2 to GND** to configure device as **host**.



##  7. Device Compatibility

| Device            | OTG Support        |
|-------------------|--------------------|
| Android Phones    | ✅ Yes (check settings) |
| Raspberry Pi      | ✅ Yes (USB-A)       |
| Laptops           | ✅ Yes (Type-C ports) |
| Smart TVs         | 🔄 Partial (file/media) |
| Microcontrollers  | ✅ With USB host       |



##  8. USB Versions – Quick Comparison

| USB Version | Speed      | Common Uses                          |
|-------------|------------|--------------------------------------|
| USB 2.0     | 480 Mbps   | Mouse, keyboard, flash drive         |
| USB 3.0     | 5 Gbps     | HDDs, SSDs, high-res peripherals     |
| USB 3.1     | 10 Gbps    | 4K video, advanced storage           |
| USB 3.2/4.0 | 20–40 Gbps | VR, video capture, external GPUs     |



##  9. Recommended Components

| Part Type              | Component Name                       |
|------------------------|--------------------------------------|
| Type-C Connector       | Amphenol 12401548E4#2A               |
| USB-A Female Socket    | TE 5787834-1                         |
| CC Resistors           | 5.1kΩ ±1% (e.g., Yageo RC0402FR-075K1L) |
| Capacitors             | 0.1 µF and 10 µF (Murata recommended) |
| ESD Protection Diodes  | PESD5V0S1UL (Nexperia)               |
| Optional PD Controller | STUSB4500 or FUSB302                 |


##  10. Key Design Considerations

-  Use **certified Type-C cables** for 3A+ power
-  Add **ESD protection** to avoid voltage spikes
-  Follow **trace impedance matching** for high-speed data
-  Design with **thermal relief** if using PD
-  Ensure proper **mechanical enclosure & strain relief**
- Many phones require **manual OTG toggle in settings**
  


# 2. Project 

In this project, I have designed a USB Type-C to USB Type-A OTG (On-The-Go) adapter capable of data transfer speeds of up to 480 Mbps, compliant with the USB 2.0 standard. The schematic and PCB layout were created using [EasyEDA](https://easyeda.com), an intuitive and powerful online electronics design tool. Additionally, the custom enclosure for the adapter was modeled using [Tinkercad](https://www.tinkercad.com), a beginner-friendly 3D design and modeling platform. This project emphasizes simplicity and accessibility while delivering full OTG functionality for use with smartphones, tablets, laptops, and embedded systems.

## 1. Circuit Diagram / Schematic

The schematic was designed using [EasyEDA](https://easyeda.com). It shows the connection between the USB Type-C connector, ESD protection diodes, decoupling capacitors, pull-down resistors, and the USB Type-A output.

**Insert schematic image here**
![Schematic](images/schematic.png)

---

## 2. Bill of Materials (BOM) / Components Used

| No. | Quantity | Designator(s) | Value               | Footprint                          | Manufacturer Part        | Manufacturer         | Supplier Part | Supplier |
|-----|----------|----------------|----------------------|------------------------------------|---------------------------|------------------------|----------------|----------|
| 1   | 2        | C3, C4         | 100nF               | C0805                              | CC0805KRX7R9BB104         | YAGEO (国巨)           | C49678         | LCSC     |
| 2   | 2        | D1, D2         | KPESD5V0S1UL        | X1-DFN1006-2_L1.0-W0.6-RD          | KPESD5V0S1UL              | KUU                    | C2891661       | LCSC     |
| 3   | 2        | R4, R5         | 5.1kΩ               | R0805                              | 0805W8F5101T5E            | UNI-ROYAL (厚声)       | C27834         | LCSC     |
| 4   | 1        | USB1           | TYPE-C 16PIN 2MD(073) | USB-C-SMD_TYPE-C-6PIN-2MD-073     | TYPE-C 16PIN 2MD(073)     | SHOU HAN (首韩)        | C2765186       | LCSC     |
| 5   | 1        | USB2           | USB-301WD-ARY       | USB-TH_XUNPU_USB-301WD-ARY        | USB-301WD-ARY             | XUNPU (讯普)           | C2895025       | LCSC     |

---

## 3. PCB Layout

The PCB was designed. here i have made layer 2 as a ground plane and layer 1 is designed ensuring short traces, minimal EMI, and proper CC resistor placement for OTG functionality. The layout features USB Type-C input and USB-A output with ESD and power filtering.

**Insert PCB layout image here**
![PCB Layout](images/pcb-layout.png)

---

## 4. 3D View

This is the 3D view of the PCB generated using EasyEDA's built-in 3D viewer.

**Insert 3D PCB image here**
![3D View](images/3d-view.png)

---

## 5. Enclosure Design

The enclosure was designed using [Tinkercad](https://www.tinkercad.com), a browser-based 3D modeling tool. It provides a compact housing with cutouts for USB Type-C and USB-A connectors and snap-fit features for easy assembly.

**Insert enclosure design render or photo here**
![Enclosure Design](images/enclosure.png)

---
## 6. Project files
All the essential files required for this USB Type-C OTG adapter project are available in the repository. The schematic and PCB layout were designed using EasyEDA, and the enclosure was created using Tinkercad. You can find the schematic file (schematic.json) and the PCB layout file (pcb_layout.json) in the files/ directory. For PCB manufacturing, the Gerber files are available as a .zip archive (gerber.zip). The complete list of components used in the project is provided as a CSV file (bom.csv). The 3D printable enclosure model is available as an STL file (enclosure.stl), and if you wish to modify the design, the source file is also included (enclosure.scad). Additionally, a 3D view image (3d-view.png) of the assembled board can be found in the images/ folder. All files are organized under the files/ and images/ directories within this repository for easy access.

