\--------------------------------------------------



TITLE:



\[Bring-up / Bug] Alder Lake-U (0x46B3) - HP 15s fq5326tu halts at physical-owner/binding selection





\--------------------------------------------------



DESCRIPTION:



Hello developers, and thank you for your ongoing hard work on the WhateverXe project. This is a comprehensive update combining my initial diagnostics and subsequent testing phase. I am testing the experimental driver stack on an Alder Lake-U mobile platform to help push bring-up forward for this specific hardware variant (0x46B3). 





While the kext stack successfully injects and loads into kernel memory, execution consistently halts right at the hardware binding stage.





\--------------------------------------------------



HARDWARE \& ENVIRONMENT:



\- Laptop Model: HP 15s-fq5326tu (Nothing Replaced)



\- CPU: Intel Core i3-1215U (Alder Lake-U)



\- iGPU: Intel UHD Graphics (64 EUs, Device ID: 0x46B3)



\- macOS Version: macOS Sonoma 14.8.9 (Downgraded from a newer version to achieve full Wi-Fi stability)



\- Kext Chain: Lilu.kext -> AMFIPass.kext -> WhateverXe.kext



\- WhateverXe Graphics Package: Successfully installed inside macOS prior to reboot.





\--------------------------------------------------



BOOT ARGUMENTS:



\-v debug=0x100 keepsyms=1 -vi2c-force-polling revpatch=sbvmm -allow3d -disablegfxfirmware amfi\_get\_out\_of\_my\_way=1





\--------------------------------------------------



THE ISSUE:



OpenCore logs, kmutil showloaded, and system diagnostics confirm that both org.b00t0x.AppleIntelTGLCompat and com.apple.driver.AppleIntelTGLGraphicsFramebuffer load successfully into kernel memory. However, the driver fails to bind to the hardware, resulting in 7 MB VRAM and no Metal support (system\_profiler SPDisplaysDataType).





The targeted kernel log explicitly halts at the hardware handshake without throwing an error or panic:



kernel: (AppleIntelTGLCompat) AppleIntelTGLCompat : revision 0.5.0 started, physical-owner/binding selection```



\### Expected vs. Actual Behaviour



| Expected Behaviour | Actual Behaviour |

|---|---|

| iGPU successfully binds to the graphics driver | Hardware binding not observed |

| Hardware acceleration initializes successfully | No hardware acceleration |

| Metal support becomes available | Metal unavailable |

| Proper graphics memory is reported | 7 MB VRAM reported |



\### Relevant Kernel Log



```text

kernel: (AppleIntelTGLCompat) AppleIntelTGLCompat : revision 0.5.0 started, physical-owner/binding selection

\--------------------------------------------------



ATTACHED DIAGNOSTICS (Directory: AlderLake-U-WhateverXe\_Logs):



1\. 01\_kernel\_graphics.log — Complete kernel log from initial test runs.



2\. 02\_system\_profiler.log — Initial display state export.



3\. 03\_ioreg\_dump.log — Initial iGPU PCI topology capture.



4\. 04\_kextstat.log — Initial loaded kext verification.



5\. 05\_nvram.log — Active boot arguments and environment variables.



6\. 06\_Display\_Hardware\_Profile.txt — Refined system profiler export verifying hardware IDs.



7\. 07\_IOReg\_Graphics.txt — Full device tree capture mapping out active display controller nodes.



8\. 08\_PCI\_Bus\_Tree.txt — Complete system PCI bus topology.



9\. 09\_WhateverXe\_test.txt — Targeted kernel log showing the initialization and binding halt point.



10\. opencore-bootlogs.txt — OpenCore boot log confirming kext injection





\--------------------------------------------------



NEXT STEPS / ASSISTANCE:



Would you consider integrating support or guidance for binding this specific mobile variant (0x46B3)? 



I remain fully available to test alternative builds, apply custom patches, or pull any extra telemetry logs you might require. Hopefully, these logs and diagnostics prove helpful for advancing the implementation and driver bring-up for this specific mobile GPU variant. Thank you again for your time, dedication, and amazing work on this project!

Help & Contributions:

I'm actively testing WhateverXe on Intel Alder Lake-U hardware (i3-1215U, GPU Device ID 0x46B3).

At the moment, the driver loads its kexts, but graphics hardware binding and acceleration are still not working.

If you're a developer familiar with Intel graphics, macOS graphics drivers, WhateverXe, or Hackintosh internals, I'd appreciate any guidance, suggestions, or help investigating this issue.

If you're a user with similar Alder Lake-U hardware, your testing results and experiences would also be valuable for comparison.

Whether you can help with debugging, testing, identifying potential issues, or simply sharing relevant information, feel free to reach out.

Contact:

Reddit: https://www.reddit.com/user/Belugaa_01/
Telegram: https://t.me/MultiVerse42

I'm open to collaborating and testing experimental builds or potential fixes.

Any help is appreciated. Thank you!
```

