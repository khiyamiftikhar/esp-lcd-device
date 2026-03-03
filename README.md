esp-lcd-device

A reusable ESP-IDF component that provides device-level LCD panel drivers for ESP32 platforms.

esp-lcd-device abstracts individual LCD controller implementations (ILI9486, SSD1306, etc.) behind a clean, device-agnostic API while leveraging ESP-IDF’s esp_lcd subsystem.

This component is designed to be:

Modular

Scalable (easy to add new LCD controllers)

Hardware-focused (no UI framework coupling)

Suitable for multi-product firmware projects

✨ Features

Device-agnostic LCD initialization

Kconfig-based device selection

Clean separation between public API and private drivers

Compatible with ESP-IDF 5.x+



Designed to integrate cleanly with LVGL or other graphics stacks

📦 Repository Structure
esp-lcd-device/
│
├── CMakeLists.txt
├── Kconfig
├── idf_component.yml
│
├── include/
│   └── esp_lcd_device.h        # Public API
│
├── src/
│   └── esp_lcd_device.c        # Core logic
│
└── devices/
    ├── ssd1306
    │   ├── ssd1306.c
    │   └── ssd1306.h
    │
    ├── ili9586/
    │   ├── ili9486.c
    │   └── ili9486.h
    

include/ → Public headers exposed to other components

src/ → Core abstraction logic

devices/ → Private device-specific implementations

🚀 Installation (ESP-IDF Managed Component)

Add to your project’s idf_component.yml:

dependencies:
  esp-lcd-device:
    git: "https://github.com/yourname/esp-lcd-device.git"

Then run:

idf.py reconfigure
⚙ Configuration

Select your LCD controller via:

idf.py menuconfig

Navigate to:

Component config → LCD Device Selection