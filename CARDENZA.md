# Runtime Cardenza support

Based on preserved upstream `aaffde91c3cd0e02ffcc65660dd788b514f36f09`. Default `unified` and CI-compatible alias `cardenza` use the exact M5Unified fork `203Null/M5Unified@74fe31c6d9a2bd7c04f81eb4f8f0af99262e3bc2` (upstream0.2.24), M5GFX0.2.31, M5Cardputer1.1.1. Hardware is selected at runtime using ES8156 identity; original Cardputer keyboard identity is preserved. The fork owns LED hold, no Cardenza battery ADC/RGB and codec initialization. No app-local hardware HAL or Power/RGB linker wrappers remain.

Preserved newer single-display UI, HSPI SD and restored upstream keyboard/menu shortcuts; runtime original Cardputer uses onboard Speaker, Cardenza raw16-bit stereo32fs, ADV ES8311. No deleted upstream TFT/dual-display assets were restored.

The independent `LAUNCHER_NVS_GUARD` and erase wrapper preserve shared Launcher NVS full-partition recovery; normal page GC and app/filesystem erase continue. The actual existing host guard test passes. Existing workflow and prepare.py bytes were preserved; prepare.py generated the raw app image and original dependency licensing notices successfully.

Final publishing-tree build PASS (`pio run -e cardenza`), 640176 bytes, SHA-256 `62ee88376cf844b2cbf2d61d439b9597236d8468a6e49286f93be95ef8e28419`. This image was not flashed or physically validated. Historical device results for earlier images do not prove this image's hardware behavior.
