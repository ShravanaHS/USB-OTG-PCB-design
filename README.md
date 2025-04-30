# USB Type-C OTG Adapter Project



In this project, I have designed a USB Type-C to USB Type-A OTG (On-The-Go) adapter capable of data transfer speeds of up to 480 Mbps, compliant with the USB 2.0 standard. The schematic and PCB layout were created using [EasyEDA](https://easyeda.com), an intuitive and powerful online electronics design tool. Additionally, the custom enclosure for the adapter was modeled using [Tinkercad](https://www.tinkercad.com), a beginner-friendly 3D design and modeling platform. This project emphasizes simplicity and accessibility while delivering full OTG functionality for use with smartphones, tablets, laptops, and embedded systems.



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

---

##  10. Key Design Considerations

-  Use **certified Type-C cables** for 3A+ power
-  Add **ESD protection** to avoid voltage spikes
-  Follow **trace impedance matching** for high-speed data
-  Design with **thermal relief** if using PD
-  Ensure proper **mechanical enclosure & strain relief**
- Many phones require **manual OTG toggle in settings**
  


## 11. Project Specification Summary

| Parameter                  | Value                                |
|---------------------------|--------------------------------------|
| Adapter Type              | USB Type-C Male ↔ USB-A Female OTG   |
| USB Standard              | USB 2.0 / 3.0 / 3.1 Gen 2             |
| Power                     | Default 5V @ 3A, PD up to 100W        |
| Data Speed                | Up to 10 Gbps                         |
| CC Configuration          | 5.1kΩ resistor to GND (host mode)     |
| Enclosure                 | Custom 3D-printed (STL provided)      |
| Protection                | ESD diodes,
