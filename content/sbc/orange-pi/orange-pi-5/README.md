<br>

<div align="center">

# **Orange Pi 5 series Tutorials and Troubleshooting**

![Badge](https://badgen.net/github/license/kaveh-kaviani/tutorials?color=red)
![Badge](https://badgen.net/github/forks/kaveh-kaviani/tutorials?icon=git&color=blue)
![Badge](https://badgen.net/github/watchers/kaveh-kaviani/tutorials?icon=awesome&color=green)
![Badge](https://badgen.net/github/stars/kaveh-kaviani/kaveh-kaviani?icon=graphql&color=blue)
![Badge](https://badgen.net/github/commits/kaveh-kaviani/tutorials?icon=graphql&color=red)

</div>

# Introduction:

Welcome to the Orange Pi 5 series Tutorials and Troubleshooting guide! This collection of tutorials aims to assist users of the versatile Orange Pi 5 single-board computers (SBCs) in various applications, from electronics and home labs to edge computing and enterprise development.

This folder contains tutorials for the Orange Pi 5 series Single Board Computers which have a vast majority of usage from Electronic, Home-Lab, Edge Computing, Artificial Intelligence (AI), Cloud Computing, AR/VR, Intelligent Security, Smart Home to Small Development and Enterprises.

# Table of Contents:

- [**Orange Pi 5 series Tutorials and Troubleshooting**](#orange-pi-5-series-tutorials-and-troubleshooting)
- [Introduction:](#introduction)
- [Table of Contents:](#table-of-contents)
- [Tutorials](#tutorials)
- [Additional Information](#additional-information)
  - [Orange Pi 5 Specifications](#orange-pi-5-specifications)
  - [Orange Pi 5B Specifications](#orange-pi-5b-specifications)
  - [Orange Pi 5 Pro Specifications](#orange-pi-5-pro-specifications)
  - [Orange Pi 5 Plus Specifications](#orange-pi-5-plus-specifications)
- [References](#references)

<br>

<br>

# Tutorials
- [Boot Linux from eMMC:](/content/sbc/orange-pi/orange-pi-5/boot-linux-from-emmc/README.md)
  
<br>
  
<br>
  
<br>

<div align="center">

<span style="color: red; font-size: 25px; font-family: roboto;"> **Note!!! For models without eMMC or SPI Flash:** </span>

</div>

<span style="font-size: 20px; font-family: roboto;"> 

**Orange Pi 5**: This model does not have built-in eMMC storage. You can utilize a MicroSD card or the M.2 M-key slot for NVMe SSD or SATA SSD.

**Orange Pi 5B**: This model does not have built-in SPI FLASH. You can utilize the eMMC Storage, MicroSD card or the M.2 M-key slot for NVMe SSD or SATA SSD.

**Orange Pi 5 Pro**: This model supports either an eMMC module or SPI Flash (not both simultaneously). The default SPI Flash slot is empty. </span>

<br>

<div align="center">

**Note**: The tutorials are tested on Debian 12 (Bookworm) and may not work on other versions of Ubuntu or other Linux distributions.

</div>

<br>

# Additional Information

## [Orange Pi 5](#orange-pi-5) Specifications

- **CPU:** Rockchip RK3588S 8-core 64-bit processor, 4x Cortex-A76, 4x Cortex-A55 up to 2.4GHz main frequency
- **GPU:** ARM Mali-G610, built-in 3D GPU
- **NPU:** Built-in AI accelerator NPU with up to 6 TOPS, supports INT4/INT8/INT16 mixed operation
- **RAM:** 4GB/8GB/16GB/32GB LPDDR4X
- **Storage:** 16MB SPI Flash, MicroSD card slot, M.2 M-key slot for **2242** NVMe SSD or SATA SSD <span style="color: red;"> **Does not have eMMC Storage** </span>
- **Video Output:** HDMI2.1, up to 8K @60Hz, DP1.4 (DisplayPort), DP1.4 and USB3.1 ports are multiplexed, and the port is shared with Type-C, 2 * MIPI D-PHY TX 4Lane, configurable up to 4K @60Hz
- **Audio:** CODEC: ES8388, 3.5mm headphone jack audio input/output, Input: Onboard MIC, HDMI 2.1 eARC
- **Connectivity:** Gigabit Ethernet, Support custom PCIe Wi-Fi6+BT5.0 module
- **USB:** 1x USB 3.1 ports, 2x USB 2.0 ports, 1x USB Type-C port
- **Expansion:** 40-pin GPIO header, 2x MIPI-DSI, 2x MIPI-CSI
- **Power:** Support Type-C power supply, 5V @ 4A
- **Dimensions:** 62 x 100 x 1.6 mm
- **Weight:** 46 grams
- **Operating System:** Android 12, Debian 12, Ubuntu 22.04, etc.

<br>

## [Orange Pi 5B](#orange-pi-5b) Specifications


- **CPU:** Rockchip RK3588S 8-core 64-bit processor, 4x Cortex-A76, 4x Cortex-A55 up to 2.4GHz main frequency
- **GPU:** ARM Mali-G610, built-in 3D GPU
- **NPU:** 6TOPS computing power
- **RAM:** 4GB/8GB/16GB/32GB LPDDR4X
- **Storage:** 32GB/64GB/128GB/256GB eMMC, MicroSD card slot <span style="color: red;"> **Does not have SPI Flash and M.2 M-key slot for NVMe SSD or SATA SSD** </span>
- **Video Output:** HDMI2.1, up to 8K@60Hz, DP1.4 (DisplayPort), maximum output resolution up to 8K@30Hz, 2 * MIPI D-PHY TX 4Lane, configurable up to 4K @60Hz
- **Audio:** CODEC: ES8388, 3.5mm headphone jack audio input/output, Input: Onboard MIC, HDMI 2.1 eARC
- **Connectivity:** 802.11 b/g/n/ac WiFi 6, Bluetooth 5.3, Gigabit Ethernet
- **USB:** 1x USB 3.1 ports, 2x USB 2.0 ports, 1x USB Type-C port
- **Expansion:** 40-pin GPIO header, 2x MIPI-DSI, 2x MIPI-CSI
- **Power:** Support Type-C power supply, 5V@4A
- **Dimensions:** 62 x 100 x 1.6 mm
- **Weight:** 52 grams
- **Operating System:** Android 12, Debian 12, Ubuntu 22.04, etc.

## [Orange Pi 5 Pro](#orange-pi-5-pro) Specifications

- **CPU:** Rockchip RK3588S 8-core 64-bit processor, 4x Cortex-A76, 4x Cortex-A55 up to 2.4GHz main frequency
- **GPU:** ARM Mali-G610, built-in 3D GPU supporting OpenGL ES1.1/2.0/3.2, OpenCL 2.2, Vulkan 1.2
- **NPU:** 6TOPS, supports INT4/INT8/INT16 mixed computing
- **RAM:** 4GB/8GB/16GB LPDDR5
- **Storage:** 32GB/64GB/128GB/256GB eMMC or 16MB SPI Flash, MicroSD card slot, M.2 M-key slot for NVMe SSD or SATA SSD <span style="color: red;"> **supports for eMMC module or SPI Flash (either one) by default SPI Flash place is empty** </span>
- **Video Output:** HDMI2.1 up to 8K @60Hz, HDMI2.0, up to 4K @60Hz, DP1.4 ALT 2Lane to HDMI2.0: LT8711UXD_U2, MIPI 4 Lane, up to 4K @60Hz
- **Audio:** CODEC: ES8388, 3.5mm headphone jack audio input/output, Input: Onboard MIC, HDMI 2.1 eARC
- **Connectivity:** Onboard Wi-Fi5+BT 5.0/BLE module: AP6256, Gigabit Ethernet with PoE+ support **(PoE+ HAT required)**
- **USB:** 1x USB 3.1 ports, 3x USB 2.0 ports
- **Expansion:** 40-pin GPIO header, 2x MIPI-DSI, 2x MIPI-CSI
- **Misc:** IR receiver, RTC battery header
- **Power:** Supports Type-C power supply, 5V @ 5A
- **Dimensions:** 89 x 56 x 1.6 mm
- **Weight:** 62 grams
- **Operating System:** Android 11, Debian 12, Ubuntu 20.04, etc.

<br>

## [Orange Pi 5 Plus](#orange-pi-5-plus) Specifications

- **CPU:** Rockchip RK3588 8-core 64-bit processor, 4x Cortex-A76, 4x Cortex-A55 up to 2.4GHz main frequency
- **GPU:** ARM Mali-G610, built-in 3D GPU supporting OpenGL ES1.1/2.0/3.2, OpenCL 2.2, Vulkan 1.2
- **NPU:** 6TOPS, supports INT4/INT8/INT16 mixed computing
- **RAM:** 4GB/8GB/16GB/32GB LPDDR4X
- **Storage:** 16MB/32MB SPI FLASH, MicroSD card slot up to 128GB, 16GB/32GB/64GB/128GB/256GB eMMC module, M.2 2280 slot for NVMe SSDs (PCIe 3.0 x4) up to 2,000 MB/s
- **Video Output:** 2x HDMI 2.1 out up to 8k@60FPS, 1x Type-C with DP TX 1.4A，up to 8K@30FPS, 1x HDMI in with up to 4K@60FPS, 1 x MIPI DSI TX 4 Lane，up to 4K @60Hz
- **Audio:** CODEC:ES8388, 1x Audio 3.5mm jack with mic, 1x MIC In, 1x HDMI 2.1 eARC, 1x SPK
- **Connectivity:** 2x PCIe 2.5G LAN RTL8125BG Ethernet ports, M.2 E-Key slot that supports Wi-Fi6/BT modules <span style="color: red;"> **This M.2 slot is E-Key and separate from the M.2 for NVMe SSD** </span>
- **USB:** 2x USB 3.1 ports, 2x USB 2.0 ports, 1x USB Type-C port
- **Expansion:** 40-pin GPIO header, 2x MIPI-DSI, 2x MIPI-CSI
- **Misc:** IR receiver, RTC battery header
- **Power:** Support Type-C power supply, 5V@4A
- **Dimensions:** 100 x 75 x 1.6 mm
- **Weight:** 86.5 grams
- **Operating System:** Android 12, Debian 12, Ubuntu 22.04, etc.

<br>

# References

- [Orange Pi Official site](http://www.orangepi.org/html/hardWare/computerAndMicrocontrollers/index.html)