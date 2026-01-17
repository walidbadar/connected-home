# Connected Home 🔌

## Overview

This project implements a smart home automation solution that allows users to control electrical appliances both remotely via MQTT messaging and manually through GPIO interrupts. The system is designed to be efficient, reliable, and compatible with modern IoT ecosystems.

The firmware is based on the [Zephyr RTOS](https://www.zephyrproject.org) and can easily be ported to other boards
that support Wi-Fi or Ethernet by providing a overlay.

## Getting Started

Building the connected home firmware requires a proper Zephyr development environment. Follow the
official [Zephyr Getting Started
Guide](https://docs.zephyrproject.org/latest/getting_started/index.html) to establish one.

### Prerequisites

- MQTT broker (local or cloud-based)

### Installation

#### 1. Clone the repository:
```bash
git clone https://github.com/walidbadar/connected-home.git
cd connected-home
```

#### 2. Build the firmware
```bash
west build -p auto -b esp32_devkitc/esp32/procpu .
```

#### 3. Configure your WiFi and MQTT broker settings
```bash
west build -t menuconfig
```
![menuconfig](img/menuconfig.gif)

#### 4. Flash the firmware
```bash
west flash
```
### Build and run with native_sim board

#### 1. Setup tap interface
```bash
sudo apt install -y socat libpcap-dev
git clone https://github.com/zephyrproject-rtos/net-tools
cd net-tools
make

./net-setup start
```

#### 2. Build and run
```bash
cd connected-home
west build -p auto -b native_sim .
west build -t run
```
![native_sim](img/native_sim.png)
