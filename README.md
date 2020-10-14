# PlatformIO Zephyr board test

Adds a new board definition for Zephyr. 

# Project structure 

This project is structured so that no modifications to any platform or framework packages must be done. 

The board JSON definition is located in `boards/`. 

The Zephyr board file (device tree, Kconfigs etc) is placed in `zephyr/boards/arm/nixie_watch`. This works in conjunction with the 

```cmake 
set (BOARD_ROOT "${CMAKE_CURRENT_SOURCE_DIR}")
```
line in the `zephyr/CMakeLists.txt`

See @valeros blog post at https://piolabs.com/blog/engineering/platformio-zephyr-custom-hardware.html.


# Execution 

Run with `Verbose build` or `pio run -v` to see verbose output. 

```
Reading CMake configuration...
-- Application: C:/Users/Maxi/Desktop/nixie/zephyr
-- Zephyr version: 2.3.0 (C:/Users/Maxi/.platformio/packages/framework-zephyr)
-- Found Python3: C:/Users/Maxi/AppData/Local/Programs/Python/Python37/python3.exe (found suitable exact version "3.7.6") found components: Interpreter
-- Board: nixie_watch
-- Found dtc: C:/Users/Maxi/.platformio/packages/tool-dtc/dtc.exe (found suitable version "1.4.7", minimum required is "1.4.6")
-- Found toolchain: gnuarmemb (C:/Users/Maxi/.platformio/packages/toolchain-gccarmnoneeabi)
-- Found BOARD.dts: C:/Users/Maxi/Desktop/nixie/zephyr/boards/arm/nixie_watch/nixie_watch.dts
-- Generated zephyr.dts: C:/Users/Maxi/Desktop/nixie/.pio/build/nixie_watch/zephyr/zephyr.dts
-- Generated devicetree_unfixed.h: C:/Users/Maxi/Desktop/nixie/.pio/build/nixie_watch/zephyr/include/generated/devicetree_unfixed.h
Parsing C:/Users/Maxi/.platformio/packages/framework-zephyr/Kconfig

Loaded configuration 'C:/Users/Maxi/Desktop/nixie/zephyr/boards/arm/nixie_watch/nixie_watch_defconfig'

Configuration saved to 'C:/Users/Maxi/Desktop/nixie/.pio/build/nixie_watch/zephyr/.config'

Kconfig header saved to 'C:/Users/Maxi/Desktop/nixie/.pio/build/nixie_watch/zephyr/include/generated/autoconf.h'

-- The C compiler identification is GNU 8.2.1
-- The CXX compiler identification is GNU 8.2.1
-- The ASM compiler identification is GNU
-- Found assembler: C:/Users/Maxi/.platformio/packages/toolchain-gccarmnoneeabi/bin/arm-none-eabi-gcc.exe
-- Cache files will be written to: C:\Users\Maxi\AppData\Local/.cache/zephyr
-- Configuring done
-- Generating done
-- Build files have been written to: C:/Users/Maxi/Desktop/nixie/.pio/build/nixie_watch```
```

Should show that the correct board and DTS file is used.

Otherwise just build non-verbose. Should give

```
Checking size .pio\build\nixie_watch\firmware.elf
Building .pio\build\nixie_watch\firmware.hex
Advanced Memory Usage is available via "PlatformIO Home > Project Inspect"
RAM:   [=         ]   7.8% (used 5116 bytes from 65536 bytes)
Flash: [          ]   2.3% (used 11872 bytes from 524288 bytes)
============================= [SUCCESS] Took 16.73 seconds =========================
```