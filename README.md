# TIME-STAMPED-SENSOR-DATA-LOGGER
# 📌 Time-Stamped Sensor Logger System  
## LPC21xx (ARM7) Based Embedded Project

---

## 📖 Project Overview

The **Time-Stamped Sensor Logger System** is an embedded system developed using the **LPC21xx (ARM7)** microcontroller.

It measures temperature using an **LM35 sensor**, logs it with real-time timestamps using the internal **RTC**, displays data on an **LCD**, allows user interaction via a **4x4 keypad**, and sends data through **UART**.

The system also supports:

- Adjustable temperature threshold (Set Point)
- Alert system (Buzzer/LED)
- Serial monitoring via UART
- Edit mode for configuration

---

## 🚀 Features

- 🌡 Temperature sensing using LM35  
- 🕒 Real-Time Clock (RTC) timestamping  
- 📟 16x2 LCD display output  
- ⌨ 4x4 Matrix Keypad input  
- 🔔 Alert system with LED/Buzzer  
- 🔁 ADC-based analog reading  
- 📡 UART serial communication  
- ⚙ Edit mode for setpoint adjustment  

---

## 🧰 Hardware Requirements

- LPC21xx (ARM7) Microcontroller (e.g., LPC2148)
- LM35 Temperature Sensor
- 16x2 LCD Display
- 4x4 Matrix Keypad
- LED
- Buzzer (Optional)
- Push Button Switch
- 12 MHz Crystal
- Power Supply (3.3V / 5V as required)
- USB-to-UART converter (for serial output)

---

# 🔌 Pin Connections

---

## 🧠 Microcontroller: LPC21xx

---

## 🌡 LM35 Temperature Sensor

| LM35 Pin | Connection |
|----------|------------|
| VCC      | +5V |
| GND      | GND |
| VOUT     | P0.28 (AIN1 / ADC Channel 1) |

### ADC Channel Used:
CH1 → P0.28 (AIN1)

---

## 📟 16x2 LCD (8-bit Mode)

### Data Pins (Connected to Port 1)

| LCD Pin | LPC21xx Pin |
|----------|------------|
| D0–D7 | P1.16 – P1.23 |

### Control Pins

| LCD Pin | LPC21xx Pin |
|----------|------------|
| RS | P0.11 |
| RW | P0.12 |
| EN | P0.13 |

---

## ⌨ 4x4 Matrix Keypad

### Row Connections

| Row | LPC Pin |
|------|---------|
| R0 | P1.24 |
| R1 | P1.25 |
| R2 | P1.26 |
| R3 | P1.27 |

### Column Connections

| Column | LPC Pin |
|----------|---------|
| C0 | P1.28 |
| C1 | P1.29 |
| C2 | P1.30 |
| C3 | P1.31 |

### Keypad Layout
C0 C1 C2 C3
R0 1 2 3 A
R1 4 5 6 B
R2 7 8 9 C
R3 * 0 # D

---

## 🔘 Switch Input

| Component | LPC Pin |
|------------|----------|
| Switch | P0.16 |

---

## 🚨 Alert System

| Component | LPC Pin |
|------------|----------|
| Buzzer / Alert Output | P0.15 |
| LED Indicator | P0.17 |

---

# 🧩 Software Architecture

The project is modular and divided into functional layers:

- Main Control  
- ADC Driver  
- RTC Module  
- LCD Driver  
- Keypad Interface  
- UART Driver  
- LM35 Driver  
- Display Formatting  
- Edit Mode  
- Alert System  

---

# 📁 Proper GitHub File Structure
TIME-STAMPED-SENSOR-LOGGER/
│
├── README.md
│
├── MAINPROJECT/
│ │
│ ├── mainproject.c
│ │
│ ├── adc/
│ │ ├── adc.c
│ │ ├── adc.h
│ │ └── adc_defines.h
│ │
│ ├── rtc/
│ │ ├── rtc.c
│ │ ├── rtc.h
│ │ └── rtc_defines.h
│ │
│ ├── lcd/
│ │ ├── lcd.c
│ │ └── lcd.h
│ │
│ ├── keypad/
│ │ ├── keypad.c
│ │ ├── keypad.h
│ │ └── KeyPdDefines.h
│ │
│ ├── lm35/
│ │ ├── lm35.c
│ │ └── lm35.h
│ │
│ ├── uart/
│ │ ├── uart.c
│ │ └── uart.h
│ │
│ ├── display/
│ │ ├── display.c
│ │ └── display.h
│ │
│ ├── editmode/
│ │ ├── editmode.c
│ │ └── editmode.h
│ │
│ ├── alert_sys/
│ │ ├── alert_sys.c
│ │ └── alert_sys.h
│ │
│ ├── defines/
│ │ └── defines.h
│ │
│ └── types/
│ └── types.h

---

# ⚙️ How It Works

1. System initializes:
   - UART
   - LCD
   - RTC
   - ADC
   - Keypad

2. LM35 reads temperature via ADC (CH1).

3. RTC provides current date and time.

4. LCD displays:
   - Temperature
   - Time
   - Status

5. If temperature exceeds set point:
   - Alert output activates
   - LED turns ON

6. User can:
   - Enter edit mode
   - Change temperature set point

7. Data can be monitored via UART.

---

# 🖥 Build Instructions

### Recommended IDE:
- Keil µVision (ARM7)
- Flash Magic (for programming)

### Steps:

1. Create new LPC21xx project.
2. Add all `.c` and `.h` files.
3. Set crystal frequency to 12 MHz.
4. Compile the project.
5. Flash the HEX file to LPC2148.
6. Connect serial terminal (9600 baud recommended).

---

# 🔧 Default Configuration

| Parameter | Value |
|------------|--------|
| Crystal Frequency | 12 MHz |
| CCLK | 60 MHz |
| PCLK | 15 MHz |
| ADC Channel | CH1 |
| Default Set Point | 45°C |

---

# 📸 System Operation Flow
Initialize System
↓
Read Temperature (ADC)
↓
Read Time (RTC)
↓
Display on LCD
↓
Compare with Setpoint
↓
Trigger Alert (if needed)
↓
Repeat
# 📌 Applications

- Industrial Temperature Monitoring  
- Data Logging Systems  
- Environmental Monitoring  
- Laboratory Monitoring  
- Embedded System Learning Project  

---
# 👩‍💻 Developed By

## Rutuja Anandrao More  
**Embedded Systems | IoT | ARM Microcontrollers**
## 📸 Hardware & Simulation Outputs  

The following results were captured during testing:

### 🔹 LCD Startup & Initial Logging  
<img width="1600" height="847" alt=" startup Screen" src="C:\Users\ASUS\Downloads\WhatsApp Image 2026-03-04 at 12.05.47 PM.jpeg"/>

### 🔹 Menu Interface Screen  
<img width="1600" height="832" alt="Menu Interface" src=""C:\Users\ASUS\Downloads\WhatsApp Image 2026-03-04 at 12.05.47 PM.jpeg"/>

---
### 🔹 RTC Update Screen  
<img width="1600" height="828" alt="RTC Update Screen" src=""C:\Users\ASUS\Downloads\RTC UPDATE.jpeg"" />

### 🔹 Alert Message on UART and LED ON 
<img width="1600" height="836" alt="Temperature Logging" src=" />


---








# 🚀 Future Enhancements

The current system provides reliable real-time temperature monitoring and logging.  
The following enhancements can be implemented to extend its capabilities:

## 🔹 1. SD Card Data Logging
- Store temperature logs in `.csv` format  
- Maintain historical records  
- Enable offline data analysis  

## 🔹 2. IoT Integration
- Interface with ESP8266 / ESP32 module  
- Upload real-time data to cloud platforms such as:
  - ThingSpeak  
  - Firebase  
  - Blynk  
- Enable remote monitoring from anywhere  

## 🔹 3. GSM-Based Alert System
- Send SMS alerts when temperature exceeds threshold  
- Suitable for industrial and remote monitoring systems
  ## 🔹 4. Mobile Application Integration
- Develop Android/iOS application  
- Real-time dashboard monitoring  
- Push notifications for alerts  

## 🔹 5. Cloud Dashboard & Web Interface
- Web-based monitoring portal  
- Data visualization using charts  
- Historical data analytics  

## 🔹 6. Multi-Sensor Integration
Expand system to include:
- Humidity Sensor (DHT11/DHT22)  
- Gas Sensor  
- Pressure Sensor  
- Light Sensor  
## 🔹 7. Data Encryption & Security
- Secure UART communication  
- Add authentication for IoT dashboards  

## 🔹 8. Battery & Low-Power Design
- Add rechargeable battery support  
- Implement sleep modes for energy-efficient systems  

---
