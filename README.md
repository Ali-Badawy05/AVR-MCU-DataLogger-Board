# AVR MCU DataLogger Board

A graduation-project PCB designed in **KiCad** around the
**ATmega328P-AU** microcontroller. The board is designed as an MCU-based
data logger with persistent storage, real-time timestamping, status
indicators, and accessible communication interfaces.

## Project Overview

The board combines:

-   **ATmega328P-AU** as the main microcontroller
-   **2 × 24LC1025 I2C EEPROMs** for persistent data storage
-   **DS1337S I2C Real-Time Clock (RTC)** for timestamped logging
-   SPI, UART, I2C, and GPIO breakout headers
-   Power and SPI-clock indicator LEDs
-   Reverse-polarity protection
-   A double-layer PCB with a bottom-layer ground plane
-   Manufacturing outputs including Gerber and drill files

## Main Components

  Reference   Component                Purpose
  ----------- ------------------------ ----------------------------------
  U1          ATmega328P-AU            Main microcontroller
  U2, U3      24LC1025 ×2              I2C EEPROM data storage
  U4          DS1337S                  Real-time clock for timestamping
  Y1          16 MHz crystal           MCU clock
  Y2          32.768 kHz crystal       RTC clock
  D4          Power LED                Power indication
  D5          SPI-clock LED            SPI clock activity indication
  D7          Reverse-polarity diode   Power protection
  SW1         Push button              MCU reset
  J1          Power connector          Board power input
  J2          SPI header               SPI interface
  J3          UART header              UART interface
  J4          I2C header               I2C interface
  J6          GPIO header              GPIO breakout

## Key Design Features

### Microcontroller

The central controller is the **ATmega328P-AU**, using an external **16
MHz crystal**.

The MCU section includes:

-   External clock circuit
-   Reset push button
-   10 kΩ reset pull-up
-   AREF filtering

### Data Storage

Two **24LC1025** EEPROM devices are connected to the I2C bus.

-   2 EEPROM chips
-   128 KB per chip
-   Used for persistent data logging

### Real-Time Clock

The **DS1337S** provides real-time information for timestamping logged
data.

It uses a dedicated **32.768 kHz crystal** and communicates through the
same I2C bus as the EEPROMs.

### Interfaces

The PCB provides dedicated breakout headers for:

-   **SPI**
-   **UART**
-   **I2C**
-   **GPIO**

### Power & Indicators

The power section includes:

-   Power input connector
-   Reverse-polarity protection
-   10 µF bulk capacitor
-   Power LED
-   SPI-clock activity LED

The I2C bus uses shared **4.7 kΩ pull-up resistors**.

## PCB Design

The PCB is a **double-layer board** with functional component placement
and routed traces.

Design details:

-   MCU placed centrally
-   EEPROMs and RTC arranged to reduce unwanted coupling
-   0.2 mm signal traces
-   Bottom-layer GND plane
-   14 vias
-   DRC verification completed
-   Zero DRC violations
-   Zero unconnected nets

The project documentation states that the 0.2 mm signal traces were
checked against IPC-2221 for the board's stated load of less than 200
mA.

## Repository Structure

A clean GitHub repository can be organized as follows:

``` text
AVR-microcontroller/
│
├── README.md
│
├── KiCad/
│   ├── AVR_microcontroller.kicad_pro
│   ├── AVR_microcontroller.kicad_sch
│   ├── AVR_microcontroller.kicad_pcb
│   ├── DS1337S.pretty/
│   └── Connectors/
│
├── Gerbers/
│   ├── Gerber files...
│   └── Drill files...
│
├── Documentation/
│   └── presentation.pdf
│
└── .gitignore
```

## Files Not Recommended for GitHub

The following are local/generated files and normally should not be
included:

``` text
.history/
pcb_logs.pretty/
*_pro.lck
*.kicad_prl
```

The `.kicad_prl` file contains local KiCad settings, while the lock file
is temporary. The history/log folders are also not required to reproduce
the PCB design.

## Manufacturing Files

The repository includes the generated **Gerber and drill files**
required for PCB fabrication.

These files are kept separately from the editable KiCad design files so
that the repository contains both:

1.  The original editable PCB project
2.  The manufacturing-ready output files
## Tools

-   **KiCad 10**
-   PCB schematic and layout design
-   Gerber/drill generation
-   Design Rules Check (DRC)

## Project Status

-   [x] Schematic completed
-   [x] PCB layout completed
-   [x] DRC completed
-   [x] Zero unconnected nets
-   [x] Gerber files generated
-   [x] Drill files generated
-   [x] 3D board render completed

## Author
Aly Badawy

**Aly Badawy**\
IMT School

------------------------------------------------------------------------

*AVR MCU DataLogger Board --- Graduation Project*
