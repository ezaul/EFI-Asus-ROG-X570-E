<img src="https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/Logos/OpenCore_with_text_Small.png" width="200" height="48" /> 

# EFI Ryzentosh - Asus ROG STRIX X570-E GAMING +AMD Ryzen 9 5950X 16-Core + AMD Radeon RX 5700 XT (Navi 10 XT)

Monterey install with Zen Series CPU and Asus ROG STRIX X570-E GAMING motherboard

## Hardware - Hackintosh Config

|       Type       | Item                                   |
|:----------------:|----------------------------------------|
|     **CPU**      | [ AMD Ryzen 9 5950X 16-Core ]                     |
| **Motherboard**  | [ Asus ROG STRIX X570-E GAMING ]    |
|     **RAM**      | [ 64GB G.SkillTrident Z NeoRGB,(4x16GB),3600MHz,DDR4,CL16-F4-3600C16D-32GTZNC ]   |
|     **GPU**      | [ AMD Radeon RX 5700 XT (Navi 10 XT) ] |
|     **SSD**      | [ NVMe Corsair Force MP600 1TB ]  |
| **Power Supply** | [ Asus ROG-THOR-1200P, 1200W, 80 Plus Platinum ]  |
|                  |                                        |
|    **SMBIOS**    | [ MacPro7,1 ]                          |
|    **MacOS**     | [ Ventura 13.3]                        |
|   **Opencore**   | [ 0.9.1 ]                              |


## Bios Settings

|        Config                                                    | Status                     |
|:----------------------------------------------------------------:|----------------------------|
| **Enter BIOS -> Press Delete ->**                                | [ Enter Setup ]            |
| **Exit ->**                                                      | [ Load Optimised Defaults ]|
| **Ai Tweaker -> Ai Overclock Tuner ->**                          | [ D.O.C.P.]                |
| **Advanced -> APM Configuration -> Power On By PCIe ->**         | [ Disable ]                |
| **Advanced -> PCI Subsystem Settings -> Above 4G Decoding ->**   | [ Enabled ]                |
| **Advanced -> PCI Subsystem Settings -> Re-Size BAR Support ->** | [ Enabled ]                |
| **Advanced -> USB Configuration -> Legacy USB Support ->**       | [ Auto or Disabled ]       |
| **Boot -> Boot Configuration -> Fast boot ->**                   | [ Disable ]                |
| **Boot -> CSM -> Launch CSM ->**                                 | [ Disable ]                |
| **Boot -> Secure boot -> OS Type ->**                            | [ Windows UEFI mode ]      |
| **Boot -> Secure boot -> Key Management ->**                     | [ Clear Secure Boot Keys ] |


## OpenCore 0.9.1 EFI Update , 03th April 2023.

The EFI has now been updated to the my latest version.

## Changes made include,

* Lilu 1.6.4
* AppleALC 1.8.1
* WhateverGreen 1.6.4
* VirtualSMC 1.3.1
* RestrictEvents 1.1.0
* LucyRTL8125Ethernet 1.1.0
* NVMeFix 1.1.0
* SMCRadeonGPU.kext 0.3.3
* AppleMCEReporterDisabler 1.2
* SmallTreeIntel812576Ethernet 1.3
* USBMap.kext

New Universal AMD Patches Monterey 13.3 Compatible

2.5Ghz Ethernet Auto Negotiation Fixed,
Memory Mapping is now Being done via RestrictEvents,
About This Mac now displays the correct AMD Processor info done via RestrictEvents,

Plus other minor tweaks and changes to the config.

Note 1 - If your not using a RX 6800 or any other Navi/BigNavi GPU then remove agdpmod=ignore from the boot arguments.

Note 2 - If you are using a 6 or Less Core Ryzen then go into the Config,plist and under PlatformInfo->Generic Change the ProcessorType from 0 to 1537, This will list your CPU info correctly inside About This Mac.

Note 3 - The SmallTreeIntel82576.kext is now fully working as of Monterey 12.0 Beta 8

Note 4 - BIOS SETTING CHANGE - Since Bios Revision 4010 Power On By PCIe can break shut down on some peoples builds so ensure the following setting is now set as disabled.

Advanced -> APM Configuration -> Power On By PCIe -> Disabled
For OpenCore Using PlistEdit Pro add your details by modifying the following

<img src="https://i.imgur.com/mZeZ7ts.png" width="736" height="625" /> 

IMPORTANT PATCH INFO TO SET THE CORRECT CORE COUNT FOR YOUR CPU

Patches are now universal across 15h, 16h, 17h, and 19h by utilizing the OpenCore kernel Quirk ProvideCurrentCpuInfo. OpenCore 0.7.1 or newer is required.

Make sure to enable this quirk or the system won't boot.

Note for Zen 4: Zen 4 (Ryzen 7000) requires patching for IOPCIFamily.kext.
This patch is enabled by default. Please ensure that you've added it to your current config for Zen 4 stability. This patch also allows MSI A520, B550, and X570 boards to boot macOS Monterey and newer.

Core Count patch needs to be modified to boot your system. Find the four algrey - Force cpuid_cores_per_package patches and alter the Replace value only.

## See the table below for the values matching your CPU Core Count.

|        CoreCount      | Hexadecimal |
|:---------------------:|------------ |
|     **4 Core**        | [   04    ] |
|     **6 Core**        | [   06    ] |
|     **8 Core**        | [   08    ] |
|     **12 Core**       | [   0C    ] |
|     **16 Core**       | [   10    ] |
|     **24 Core**       | [   18    ] |
|     **32 Core**       | [   20    ] |

So for example, a user with a 6-core processor should use these Replace values: B8 06 0000 0000 / BA 06 0000 0000 / BA 06 0000 0090 / BA 06 0000 00
EXAMPLE



<img src="https://i.imgur.com/BbGgsap.png" width="736" height="625" /> 


Finally and as always, MAKE SURE YOU RESET YOUR NVRAM BEFORE BOOTING INTO THE NEW EFI
