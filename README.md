\# WhateverXe — Alder Lake-U Testing



Independent hardware testing and compatibility research for \[WhateverXe](https://github.com/b00t0x/WhateverXe).



This repository documents my attempts to get WhateverXe working on Intel Alder Lake-U integrated graphics, particularly the Intel UHD Graphics found in the Core i3-1215U.



\## Hardware



| Component         | Specification       |

| ----------------- | ------------------- |

| Laptop            | HP 15s series       |

| Processor         | Intel Core i3-1215U |

| GPU               | Intel UHD Graphics  |

| Execution Units   | 64 EU               |

| Device ID         | `0x46B3`            |

| Wi-Fi / Bluetooth | Realtek RTL8822CE   |



\## Current Testing Status



\* WhateverXe kext loading: Successful

\* Hardware binding: Not observed

\* Graphics acceleration: Not working

\* Metal support: Unavailable

\* Reported graphics memory: 7 MB



\## Testing Environment



\* macOS Sonoma 14.8.9

\* OpenCore

\* Experimental WhateverXe configuration



\## Reports and Diagnostics



\[View the Alder Lake-U 0x46B3 testing report](reports/alderlake-u-0x46b3/README.md).



The report includes detailed findings and 10 diagnostic files covering kernel logs, IORegistry, loaded kexts, PCI information, display hardware and OpenCore boot logs.



\## Project Reference



Original project: \[b00t0x/WhateverXe](https://github.com/b00t0x/WhateverXe).



This is an independent, unofficial hardware-testing repository. It is not maintained by or affiliated with the original project author.



\## Contributions and Contact



Developers familiar with Intel graphics, macOS graphics drivers and Hackintosh internals, as well as users with similar hardware, are welcome to share suggestions, testing results and debugging assistance.



See the detailed report for contact information.



