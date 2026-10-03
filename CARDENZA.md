# Cardenza support

Build with `pio run -e cardenza -j4` using PlatformIO Core 6.2.0, Espressif32 6.7.0 / Arduino-ESP32 2.0.16.

This port is based on upstream main `aaffde91c3cd0e02ffcc65660dd788b514f36f09`. Original hardware targets remain available.

Hardware: original Cardputer V1 keyboard, 240x135 display and SPI SD; ES8156 DAC at I2C0x08 (SDA2/SCL1), stereo Philips I2S BCLK41/LRCK43/DOUT42; PDM microphone CLK43/DATA46. Keyboard LED EN21 is held high (off), and backlight uses GPIO38. No battery ADC, gyro, onboard RGB or PSRAM is assumed. The target checks codec identity before setup.

The default upstream main branch has one display. The Cardenza target selects the stereo I2S DAC automatically and uses internal RAM for SF2/MIDI allocations. Larger soundfonts may exceed available heap. M5Unified 0.2.22 and M5GFX 0.2.31 are pinned so Power/RGB linker wrappers intercept their separately compiled initialization.

Install only the application image through Software Launcher. Do not flash generated bootloader, partition table, merged images or erase the shared NVS. This target uses the Launcher's existing partition layout; a generated project partition table is only for local build sizing.

The Cardenza-only partition erase wrapper rejects whole-NVS resets while allowing normal NVS page garbage collection and other partition erases. Run `python tests/cardenza_nvs_guard.py` with a host C++ compiler to check the actual wrapper. M5Unified is pinned to separately compiled code so the Power/RGB guards remain effective.

The upstream application has no explicit license file. TinySoundFont, TinyMidiLoader and the vendored Cardenza HAL keep their own licenses; these do not grant a license for the upstream application.

A successful build is not a hardware test. These refreshed images require physical display, keyboard, audio/microphone and storage checks before claiming functional validation.
