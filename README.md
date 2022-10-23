# MicroPython

A python version that runs on various hardware platforms such as ESP32, RaspberryPi pico ... For more information's take a look at the projects [Homepage](https://micropython.org).

## Installing a micropython on a device (e.q. ESP8266)

Load the latest firmware from https://micropython.org/download/esp8266/

Install esptool on the mac <code>pip install esptool</code>

Clear the device <code>esptool.py --port /dev/ttyUSB0 erase_flash</code>

Install teh firmware on the device <code>esptool.py --port /dev/tty.usbserial-1420 --baud 460800 write_flash --flash_size=detect -fm dout 0 esp8266.bin</code>

After the installation you can simply connect via a serial terminal to check the installation.

<code>screen /dev/tty.usbserial-1420 115200</code>

You should than see a simple python prompt beginning with >>> . You can type CTRL + D to soft reboot the device and see the actual installed version.

<code>
>>>

MPY: soft reboot

MicroPython v1.19.1 on 2022-06-18; ESP module with ESP8266

Type "help()" for more information.

\>>>
</code>

## Setup VSCode to work with micro python

Install the extension Pico-W-Go. Maybe you have to define the serial port to use for the extension. CMD + Ship + P -> Pico-W-Go \> Global Settings . Setup the field <b>Manual Com Device</b> and disable <b>Auto Connect</b>. Restart VSCode

## Setup rshell to manage files on the micro python device

First install rshell <code>python -m pip install rshell</code> Restart terminal. After restart check if it was installed correct <code>which rshell</code> should result in the installation path.

Connect to the device via rshell <code>rshell -p /dev/tty.usbserial-1420</code>. The file system of the device should be under /pyboards

## Make a script permanent

To survive a reboot the file which is copied to the device should be named main.py