# SmartGlass-Firmware
# 🕶️ SmartGlass Firmware (ESP32-P4)

![ESP-IDF](https://img.shields.io/badge/ESP--IDF-v5.5.3-red)
![C++](https://img.shields.io/badge/Language-C++-blue)
![Hardware](https://img.shields.io/badge/Hardware-ESP32--P4-green)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

Welcome to the official firmware repository for the **SmartGlass Project**. This repository contains the C++/FreeRTOS codebase running on the ESP32-P4, providing a fully integrated AI wearable experience featuring real-time voice processing, low-latency video streaming, and seamless companion app connectivity.

## ✨ Key Features

* 🎙️ **Real-Time AI Voice Assistants**: Native WebSocket integration with **Google Gemini** and **OpenAI Realtime** APIs. Includes onboard wake-word detection (WakeNet) and Voice Activity Detection (VAD).
* 📹 **WebRTC & UDP H.264 Video Streaming**: Supports ultra-low-latency H.264 video transmission from the SmartGlass camera to companion applications using both **WebRTC** and a custom **UDP streaming pipeline**. WebRTC provides NAT traversal, adaptive bitrate control, and secure real-time communication, while UDP mode offers minimal overhead and reduced latency for local-network viewing and embedded receiver applications. Supports hardware-encoded H.264 video, configurable bitrate/FPS, and direct streaming to Android and ios.
* 📲 **BLE Companion App Sync**: Uses Bluetooth Low Energy (NimBLE) for fast Wi-Fi provisioning, API key syncing, and real-time hardware diagnostics.
* 🔄 **Safe Over-The-Air (OTA) Updates**: Automated background updates directly from GitHub Releases using dual-partition fallback protection.
*  🔌 **USB OTG Mass Storage (MSC) Support**: Supports USB OTG Mass Storage Class (MSC) mode, allowing the SmartGlass to appear as a removable storage device when connected to a PC, smartphone, or tablet. Enables direct access to captured photos, videos, logs, and firmware files without requiring a companion application.
* ⚡ **ESP32-C6 / ESP32-C5 Co-Processor OTA Updates**: Supports Over-The-Air (OTA) firmware updates for connected ESP32-C6 and ESP32-C5 co-processors. The ESP32-P4 can securely download, verify, and deploy firmware images to auxiliary wireless controllers, enabling synchronized multi-chip updates, simplified maintenance, and reliable recovery mechanisms.
* 💳 **Onboard Vision & QR Scanning**: Built-in QR decoding for automatic UPI payment routing and AI computer vision integration.
* 🔋 **Advanced Diagnostics**: Real-time battery monitoring, IMU tracking (MPU6050), and dynamic audio hardware configuration (ES8311 Codec).

## 🛠️ Hardware Specifications

* **Microcontroller**: Espressif ESP32-P4 (Dual-core, 400 MHz)
* **Memory**: 32MB PSRAM + 32MB SPI Flash
* **Camera**: OV5647 (800x640 @ 15fps H.264 Hardware Encoded)
* **Audio**: ES8311 I2S Codec (High-fidelity Mic Input & Speaker Output)
* **Motion**: MPU6050 6-Axis Accelerometer/Gyroscope
* **Storage**: MicroSD Card + SPIFFS for internal caching

## 🚀 Over-The-Air (OTA) Update System

This device supports seamless, app-triggered OTA updates hosted directly from this repository. 

### How to release a new update:
1. Update the hardcoded version string in `OtaManager.cpp` or use ESP-IDF git tags (e.g., `v1.0.8`).
2. Build the binary using ESP-IDF:
   ```bash
   idf.py build
