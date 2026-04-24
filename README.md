# Edge-AI Camouflage Detection System

A lightweight, headless computer vision pipeline designed to detect camouflaged targets in real-time. Built specifically for Raspberry Pi, this system processes wireless video feeds and renders YOLOv5 bounding boxes directly to a raw hardware framebuffer, eliminating the need for a heavy desktop GUI.

## 🚀 Features
* **Headless Rendering:** Bypasses X11/Wayland by drawing OpenCV matrices directly to `/dev/fb0` using the Linux `fbi` utility.
* **Zero-Latency Threading:** Utilizes a custom background thread to flush old network frames, ensuring the AI only processes the absolute newest frame from the wireless stream.
* **Accurate Spatial Scaling:** Implements custom letterboxing and matrix transposition to perfectly map the AI's 640x640 brain back to raw TFT dimensions.
* **Wireless IP Streaming:** Pulls live video feeds dynamically from a smartphone over local Wi-Fi.

## 🛠 Hardware Requirements
* **Raspberry Pi** (Pi 4 or newer recommended)
* **Waveshare 3.5" TFT LCD**
* **Smartphone** (Running 'IP Webcam' for Android or 'IP Camera Lite' for iOS)
* **MicroSD Card** (16GB+ Class 10/A1)

## 📦 System & Software Setup

### 1. OS & Display Drivers
The system requires a headless setup of Raspberry Pi OS (64-bit).
Install the framebuffer imageviewer:
```bash
sudo apt update
sudo apt install fbi
