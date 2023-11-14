# Agon Binaries
This git contains precompiled binaries for the Agon platform.

## Valid MOS CRC32 checksums
For use with the [agon-flash](https://github.com/envenomator/agon-flash) utility

| MOS version | CRC32      |
|-------------|------------|
| [Quark 1.02](https://github.com/envenomator/agon-binaries/raw/master/MOS/1.02/MOS.bin)    | 0xFE59E98D |
| [Quark 1.03](https://github.com/breakintoprogram/agon-mos/releases/download/v1.03/MOS.bin)    | 0x81E397C9 |
| [Quark 1.04](https://github.com/breakintoprogram/agon-mos/releases/download/v1.04/MOS.bin)    | 0x74E3BDFD |
| [Console8 2.0.0](https://github.com/AgonConsole8/agon-mos/releases/download/v2.0.0/MOS.bin)    | 0xF57D0202 |
| [Console8 2.1.0](https://github.com/AgonConsole8/agon-mos/releases/download/v2.1.0/MOS.bin)    | 0x3ADBB188 |

## Flashing VDP
### Using a commandline script
Each VDP version directory has both a Windows Batchfile and Unix shell script to flash the ESP32 using Espressif's esptool. The redistributable esptool.exe is provided for Windows. The Unix version requires the installation of esptool.py with 'pip install esptool'

The windows batchfile needs your COM port as first argument, with the baudrate as optional second argument.
The Unix shell script defaults to using /dev/ttyUSB0 and 921600 baudrate.

### Using the ESP Flash download tool (Windows)
The latest version of this tool can be downloaded [from the Espressif support website](https://www.espressif.com/en/support/download/other-tools?keys=&field_type_tid%5B%5D=13)

Connect your AgonLight board to your PC, using an appropriate USB interface cable. This will provide serial connectivity between the ESP32 on your AgonLight and the PC.

After installation of the Espressif ESP Flash download tool, run it and fill in the fields as follows:

Select the **ESP32** platform for *Chiptype*:

![espressif settings1](/flash-settings1.png)

Leave **WorkMode** at *Develop*:

![espressif settings2](/flash-settings2.png)

Next, on the main screen, take care to specify these exact addresses for:

|    Filename    | Address |
|:--------------:|--------:|
| bootloader.bin |  0x1000 |
| partitions.bin |  0x8000 |
|  firmware.bin  | 0x10000 |

And **make sure** to **SELECT** the checkboxes on the left, to select all files to flash.

![espressif settings2](/flash-tool.png)

- SPI speed is 80Mhz
- SPI mode can be DIO, or QIO
- Please don't use the CombineBin/Default buttons
- Leave the *DoNotChgBin* option selected
- provide your own serial port details from the **DROPDOWN** and don't type it in.
 
Then press 'Start' and wait for the tool to finish. It might be necessary to press the 'reset' button after the tool is done.