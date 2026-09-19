# Cardiac Monitor PCB

Open-source PCB design for a portable cardiac monitor, built around the 
STM32F407 with a dedicated ADS1292R analog front-end. Designed as part 
of my internship at CSF.

## Features
- Full galvanic patient isolation (power + digital), rated for IEC 60601 (4kV)
- ADS1292R AFE for 2-channel ECG acquisition
- On-device edge AI (NanoEdge AI) — real-time classification: Normal, 
  Bradycardia, Tachycardia, Arrhythmia
- Encrypted data logging to SD card (AES-256-CBC + HMAC-SHA256, 
  Encrypt-then-MAC)
- ESP32-WROOM for wireless connectivity (BLE/MQTT)
- Companion Android app for real-time monitoring
- LCD display (I2C) + physical decrypt/mode buttons + status LEDs/buzzer

## Hardware Overview
- **MCU:** STM32F407VGTx
- **AFE:** ADS1292R (Texas Instruments)
- **Isolation:** MORNSUN B0505MT-1WR3 (DC-DC isolated) + ADuM1401 
  (digital isolators)
- **Wireless:** ESP32-WROOM-32E
- **Storage:** microSD via native SDIO
- **Power:** USB-C charging (MCP73831) + LiPo battery + LDO regulation

## Repository Structure
- Schematic sheets: `01_power_digital.kicad_sch` through `08_hmi.kicad_sch`
- `cardiac.kicad_pcb` — PCB layout
- `libs/` — custom component libraries (ADS1292IRSMT)
- Firmware repo: [cardiac_monitor](https://github.com/Adamos-khalilos/cardiac_monitor)

## Status
🚧 In progress — schematic complete (ERC validated), PCB routing complete, 
DRC cleanup in progress.

## License
MIT — see [LICENSE](LICENSE)
