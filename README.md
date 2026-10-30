# WhateverXe — Alder Lake-U Testing

Independent hardware testing and compatibility research for [WhateverXe](https://github.com/b00t0x/WhateverXe).

This repository documents my attempts to get WhateverXe working on Intel Alder Lake-U integrated graphics, particularly the Intel UHD Graphics found in the Core i3-1215U.

## Hardware Specifications

| Component             | Specification       |
| :-------------------- | :------------------ |
| **Laptop**            | HP 15s-FQ5326TU       |
| **Processor**         | Intel Core i3-1215U |
| **Integrated GPU**    | Intel UHD Graphics  |
| **Execution Units**   | 64 EU               |
| **GPU Device ID**     | `0x46B3`            |
| **Wi-Fi / Bluetooth** | Realtek RTL8822CE   |

## Current Testing Status

| Component                | Status         |
| :----------------------- | :------------- |
| WhateverXe kext loading  | ✅ Successful   |
| Hardware binding         | ❌ Not observed |
| Graphics acceleration    | ❌ Not working  |
| Metal support            | ❌ Unavailable  |
| Reported graphics memory | 7 MB           |

## Testing Environment

| Component        | Details                               |
| :--------------- | :------------------------------------ |
| Operating System | macOS Sonoma 14.8.9                   |
| Bootloader       | OpenCore                              |
| Graphics Driver  | Experimental WhateverXe configuration |


## Reports & Diagnostics

### Alder Lake-U — Device ID 0x46B3

A detailed report documenting the current testing results, observed issues and experimental configuration.

**[View Full Testing Report](reports/alderlake-u-0x46b3/README.md)**

The report includes 10 diagnostic files covering:

* Kernel graphics logs
* System profiler information
* IORegistry dumps
* Loaded kernel extensions
* NVRAM information
* Display hardware profile
* PCI bus information
* WhateverXe test results
* OpenCore boot logs

## Project Reference

Original project: [b00t0x/WhateverXe](https://github.com/b00t0x/WhateverXe).

This is an independent, unofficial hardware-testing repository. It is not maintained by or affiliated with the original project author.

## Help & Contributions

I'm actively investigating compatibility issues with WhateverXe on Alder Lake-U hardware.

Developers familiar with Intel graphics, macOS graphics drivers, WhateverXe or Hackintosh internals are welcome to contribute suggestions and debugging assistance.

Users with similar hardware are also welcome to share their experiences and testing results.

**Contact:**

* Reddit: https://www.reddit.com/user/Belugaa_01/
* Telegram: https://t.me/MultiVerse42

I'm open to collaborating, comparing diagnostic results and testing potential fixes.

Any help is appreciated!
