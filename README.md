# OpenCore B560-PLUS (Comet Lake)
OpenCore Hackintosh configuration example for the **ASUS PRIME B560-PLUS** motherboard with an Intel® Core™ i7-10700KF. 

<img src="IMAGE" alt="" width="1400"/>
<p align="center"><i>IMAGE ADDED SOON</i></p>

<br>

## What works?

### macOS

- [x] macOS Sonoma

### Hardware

- [x] Dedicated GPU (RX 560)
- [x] NVMe drives
- [x] SATA drives
- [x] USB 3.1 (XHCI)
- [x] Ethernet
- [ ] Wi-Fi
- [x] Bluetooth
- [x] Camera
- [x] Sound
  
### Software

- [ ] AirDrop
- [x] iMessage
- [x] FaceTime
- [ ] Unlock with Apple Watch
- [x] QE/CI graphics acceleration
- [x] Metal support (Metal 2)
- [x] Temperature sensors
- [x] Sleep / Wake
- [x] RTC (protection)
- [x] Hyperthreading
- [x] Virtualisation
- [x] Memory bank configuration
  
<br>

***

## Problems

<ul>
<li><b>Bluetooth devices are not currently picked up</b></li>
While bluetooth CAN be enaabled, at present, no devices can be located or connected to. This also means the machine is also not visible to other devices. I belive this problem is being caused by an incorrect kext being used.

</ul>

<ul>
<li><b>WIFI</b></li>
Due to me having a PCIe wireless card (Realtek RTL8192EE Wireless), I have not yet got WIFI working. This is on my list of things to get working.

</ul>

<ul>
<li><b>Airdrop (a given)</b></li>
Considering the problems with both BT and WIFI, airdrop does not currently work.
</ul>

***

## System

The specs of the main system that the OpenCore configuration targets.

| **Motherboard** |                  ASUS PRIME B560-PLUS                 |
|-----------------|:-------------------------------------------------------------:|
| **CPU**         |                      Intel® Core™ i7-10700KF                     |
| **Chipset**     |                             400 Series                            |
| **Generation**  |                           Comet Lake                          |
| **Memory**      |                       32GB PCS PRO DDR4 2666MHz (4 x 8GB)                       |
| **Storage**     |                     **512GB PCS m.2 SSD PRO** (boot drive) <br>1TB Samsung 870 QVO SATA SSD <br> 120GB V Series SATA SSD <br>120GB Kingston SH103S31 SATA SSD                 |
| **GPU**         | AMD Radeon RX 560<br>~~NVIDIA RTX 2060~~ * |
| **NIC**         |                  Intel(R) I219-V                 |

> [!NOTE]
> The system contains an **NVIDIA RTX 2060** graphics card, but it has been intentionally disabled through a *DeviceProperties* patch.

***

## ACPI

SSDTs used:
- SSDT-AWAC
- SSDT-EC-USBX-DESKTOP
- SSDT-PLUG-DRTNIA
- SSDT-RHUB


  
***

## DeviceProperties

The following tables display the added PCI devices and their child keys.

### PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x0)

Disable NVIDIA RTX 2060 Patch

| **Key**                  | **Type** |   **Value**  |
|--------------------------|:--------:|:------------:|
| disable-gpu                |   Boolean   | True |

<br>

### PciRoot(0x0)/Pci(0x1b,0x0)

Apple ALC

| **Key**                  | **Type** |   **Value**  |
|--------------------------|:--------:|:------------:|
| AAPL,ig-platform-id      |   Data   | ``0300220D`` |
| layout-id                |   Data   | ``01000000`` |


***

## Kernel

The following shows the kernel configuration.

### Kexts

Kexts used:
- Lilu
- WhateverGreen
- Unknown

### Patches

Unknown

***

## Security

**SecureBootModel 》** j185

**Vault 》** Optional

> [!NOTE]
> The secure boot model ``j185`` corresponds to an ``iMac20,1`` from August 2020.

***

## NVRAM

Contents stored in NVRAM.

<br>

### 4D1EDE05-38C7-4A6A-9CC6-4BCCA8B38C14

| **Key**                | **Type** |   **Value**  |
|------------------------|:--------:|:------------:|
| DefaultBackgroundColor |   Data   | ``00000000`` |

<br>

### 4D1FDA02-38C7-4A6A-9CC6-4BCCA8B30102

| **Key**       | **Type** | **Value** |
|---------------|:--------:|:---------:|
| rtc-blacklist |   Data   |           |

<br>

### 7C436110-AB2A-4BBB-A880-FE41995C9F82

| **Key**                   | **Type** |                                    **Value**                                   |
|---------------------------|:--------:|:------------------------------------------------------------------------------:|
| ForceDisplayRotationInEFI |  Number  |                                        0                                       |
| SystemAudioVolume         |   Data   |                                     ``46``                                     |
| boot-args                 |  String  | -v keepsyms=1 debug=0x100 alcid=1 |
| csr-active-config         |   Data   |                                  ``00000000``                                  |
| prev-lang-diags:kbd       |   Data   |                                 ``656E2D47 42``                                |
| prev-lang:kbd             |   Data   |                               ``656E2D47 423A32``                              |
| run-efi-updater           |  String  |                                       No                                       |
| StartupMute               |   Data   |                                     ``00``                                     |

***

## SMBIOS

### iMac20,1

Due to the system having an 8-core i7-10700KF, the CPU model is most like the one found in an **iMac 5K 27-inch (i7, 2020)**, with a model identifier of ``iMac20,1``.

***



## UEFI

Drivers in use:

- HFSPlus
- OpenCanopy
- OpenRuntime
- ResetNvramEntry
  
***

## Gallery

<img src="https://github.com/Coopydood/OpenCore-Z490E-CometLake/assets/39441479/9dd5dda0-92c3-4cc7-a7e4-3aab714671db" width="30%"></img> <img src="https://github.com/Coopydood/OpenCore-Z490E-CometLake/assets/39441479/4694291b-adcd-4847-99e2-a4f89c9c1ac9" width="60%"></img> <img src="https://github.com/Coopydood/OpenCore-Z490E-CometLake/assets/39441479/569407bd-0893-4974-82f0-ff669d317783" width="45%"></img> <img src="https://github.com/Coopydood/OpenCore-Z490E-CometLake/assets/39441479/c3ec115d-fe2c-4382-9fa3-d73d3c10cfd2" width="45%"></img>

***

## Disclaimer

EnterDisclaimer


