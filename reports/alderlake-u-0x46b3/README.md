# [Bring-up / Bug] Alder Lake-U (0x46B3) - HP 15s-fq5326tu halts at physical-owner/binding selection

## Description

Hello developers, and thank you for your ongoing hard work on the WhateverXe project.

This is a comprehensive update combining my initial diagnostics and subsequent testing phase. I am testing the experimental driver stack on an Alder Lake-U mobile platform to help push bring-up forward for this specific hardware variant (0x46B3).

While the kext stack successfully injects and loads into kernel memory, I have not observed successful hardware binding or graphics acceleration.

---

## Hardware & Environment

| Component                   | Specification                                                                         |
| :-------------------------- | :------------------------------------------------------------------------------------ |
| Laptop Model                | HP 15s-fq5326tu (Nothing Replaced)                                                    |
| CPU                         | Intel Core i3-1215U (Alder Lake-U)                                                    |
| iGPU                        | Intel UHD Graphics (64 EUs, Device ID: `0x46B3`)                                      |
| macOS Version               | macOS Sonoma 14.8.9 (Downgraded from a newer version to achieve full Wi-Fi stability) |
| Kext Chain                  | Lilu.kext → AMFIPass.kext → WhateverXe.kext                                           |
| WhateverXe Graphics Package | Successfully installed inside macOS prior to reboot                                   |

---

## Boot Arguments

```text
-v debug=0x100 keepsyms=1 -vi2c-force-polling revpatch=sbvmm -allow3d -disablegfxfirmware amfi_get_out_of_my_way=1
```

---

## The Issue

OpenCore logs, `kmutil showloaded`, and system diagnostics confirm that both `org.b00t0x.AppleIntelTGLCompat` and `com.apple.driver.AppleIntelTGLGraphicsFramebuffer` load successfully into kernel memory.

However, the driver does not appear to bind to the hardware. This results in 7 MB of reported VRAM and no Metal support, as shown by `system_profiler SPDisplaysDataType`.

The last relevant initialization message observed in the kernel log is:

```text
kernel: (AppleIntelTGLCompat) AppleIntelTGLCompat : revision 0.5.0 started, physical-owner/binding selection
```

I have not observed successful hardware binding or subsequent graphics acceleration initialization.

### Expected vs. Actual Behaviour

| Expected Behaviour                             | Actual Behaviour                |
| :--------------------------------------------- | :------------------------------ |
| iGPU successfully binds to the graphics driver | ❌ Hardware binding not observed |
| Hardware acceleration initializes successfully | ❌ No hardware acceleration      |
| Metal support becomes available                | ❌ Metal unavailable             |
| Proper graphics memory is reported             | ❌ 7 MB VRAM reported            |

### Relevant Kernel Log

```text
kernel: (AppleIntelTGLCompat) AppleIntelTGLCompat : revision 0.5.0 started, physical-owner/binding selection
```

---

## Attached Diagnostics

**Directory:** `AlderLake-U-WhateverXe_Logs`

1. `01_kernel_graphics.log` — Complete kernel log from initial test runs.
2. `02_system_profiler.log` — Initial display state export.
3. `03_ioreg_dump.log` — Initial iGPU PCI topology capture.
4. `04_kextstat.log` — Initial loaded kext verification.
5. `05_nvram.log` — Active boot arguments and environment variables.
6. `06_Display_Hardware_Profile.txt` — Refined system profiler export verifying hardware IDs.
7. `07_IOReg_Graphics.txt` — Full device tree capture mapping out active display controller nodes.
8. `08_PCI_Bus_Tree.txt` — Complete system PCI bus topology.
9. `09_WhateverXe_test.txt` — Targeted kernel log showing the initialization and binding halt point.
10. `opencore-bootlogs.txt` — OpenCore boot log confirming kext injection.

---

## Next Steps / Assistance

Would you consider integrating support or providing guidance for binding this specific mobile variant (0x46B3)?

I remain fully available to test alternative builds, apply custom patches, or collect any additional telemetry logs you might require.

Hopefully, these logs and diagnostics prove helpful in advancing the implementation and driver bring-up for this specific mobile GPU variant.

Thank you again for your time, dedication, and amazing work on this project!

---

## Help & Contributions

I'm actively testing WhateverXe on Intel Alder Lake-U hardware (i3-1215U, GPU Device ID `0x46B3`).

At the moment, the driver loads its kexts, but graphics hardware binding and acceleration are still not working.

If you're a developer familiar with Intel graphics, macOS graphics drivers, WhateverXe, or Hackintosh internals, I'd appreciate any guidance, suggestions, or help investigating this issue.

If you're a user with similar Alder Lake-U hardware, your testing results and experiences would also be valuable for comparison.

Whether you can help with debugging, testing, identifying potential issues, or simply sharing relevant information, feel free to reach out.

### Contact

* **Reddit:** [u/Belugaa_01](https://www.reddit.com/user/Belugaa_01/)
* **Telegram:** [MultiVerse42](https://t.me/MultiVerse42)

I'm open to collaborating and testing experimental builds or potential fixes.

Any help is appreciated. Thank you!
