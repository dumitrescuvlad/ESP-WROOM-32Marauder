# ESP32 Marauder – WROOM-32 + ILI9341 Build

A fork of [justcallmekoko/ESP32Marauder](https://github.com/justcallmekoko/ESP32Marauder) adapted for the **ESP32-WROOM-32** and a **3.2" ILI9341 SPI TFT display**.

This setup uses the standard ESP32 DevKit v1 pin layout and supports Wi-Fi, Bluetooth, GPS (optional), and device tools directly on the touchscreen interface.

---

## Overview

This guide shows how to connect a **3.2" TFT SPI ILI9341 display with touch and SD slot** to an **ESP32-WROOM-32** board.

All wiring has been verified and tested to work with the official **ESP32 Marauder firmware**.

---

## Hardware Setup

| Component | Description |
|------------|--------------|
| **MCU** | ESP32-WROOM-32 DevKit v1 |
| **Display** | 3.2" TFT LCD (ILI9341 Driver, XPT2046 Touch, SD Card) |
| **Interface** | SPI |
| **Resolution** | 240x320 px |

---

## Pin Connections

| TFT Pin | Function | ESP32 GPIO |
|----------|-----------|-------------|
| `VCC` | Power | 3.3V |
| `GND` | Ground | GND |
| `CS` | Chip Select (TFT) | GPIO 15 |
| `RESET` | Reset | GPIO 4 |
| `DC` | Data/Command | GPIO 2 |
| `SDI (MOSI)` | SPI Data | GPIO 23 |
| `SCK` | SPI Clock | GPIO 18 |
| `SDO (MISO)` | SPI MISO | GPIO 19 |
| `LED` | Backlight | 3.3V (or GPIO 21 if PWM dimming desired) |

### Touch

| Touch Pin | Function | ESP32 GPIO |
|------------|-----------|-------------|
| `T_IRQ` | Touch Interrupt | GPIO 36 |
| `T_DO` | MISO | GPIO 19 |
| `T_DIN` | MOSI | GPIO 23 |
| `T_CS` | Chip Select | GPIO 22 |
| `T_CLK` | Clock | GPIO 18 |

### SD Card (Optional)

| SD Pin | Function | ESP32 GPIO |
|---------|-----------|-------------|
| `SD_CS` | Chip Select | GPIO 5 |
| `SD_MOSI` | Data In | GPIO 23 |
| `SD_MISO` | Data Out | GPIO 19 |
| `SD_SCK` | Clock | GPIO 18 |

---

## Wiring Diagram

### ESP32 WROOM-32 Pinout
<p align="center">
  <img src="https://i.imgur.com/RaIseSb.png" width="640" alt="ESP32 Pinout">
</p>

### TFT Display (ILI9341)
<p align="center">
  <img src="https://i.imgur.com/BHhOXux.png" width="640" alt="ESP32 Pinout">
</p>
### Final Build Example
<p align="center">
  <img src="https://i.imgur.com/zjWNWWo.jpeg" width="640" alt="ESP32 Pinout">
</p>

---

## Firmware Flashing

1. Clone this repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/ESP32Marauder.git
   ```
2. Open the project in **Arduino IDE** or **PlatformIO**.
3. Select:
   - **Board:** ESP32 Dev Module  
   - **Partition Scheme:** Huge APP (3MB)
4. Flash the firmware.
5. Connect via serial (115200 baud) or view the on-screen UI.

---

## Notes

- Make sure to use **3.3V logic** — the display is *not* 5V-tolerant.
- If your screen stays white, double-check **CS, DC, RESET** pin mappings in `TFT_eSPI/User_Setup.h`.
- The ILI9341 driver must be enabled:
  ```cpp
  #define ILI9341_DRIVER
  ```
- For touch input (XPT2046), verify that `T_CS` and `T_IRQ` match your wiring.

---

## Credits

- Original project: [ESP32 Marauder by JustCallMeKoko](https://github.com/justcallmekoko/ESP32Marauder)
- Adapted wiring and documentation: *https://github.com/dumitrescuvlad*

---

## License

MIT License – see [LICENSE](LICENSE) for details.
