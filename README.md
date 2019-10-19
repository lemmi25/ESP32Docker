# Microcontroller Repo

When opening the Projects in Eclipse it is possible that some includes and variables can not be resolved.

Click the “Providers” tab

In the list of providers, click “CDT Cross GCC Built-in Compiler Settings”. Change “Command to get compiler specs” to

xtensa-esp32-elf-gcc ${FLAGS} -std=c++11 -E -P -v -dD "$INPUTS}".

In the list of providers, click “CDT GCC Build Output Parser” and change the “Compiler command pattern” to

xtensa-esp32-elf-(gcc|g\+\+|c\+\+|cc|cpp|clang)

## For debugging

From Openocd copy

~/esp/openocd-esp32/share/openocd/contrib/99-openocd.rules

to

/etc/udev/rules.d

to start debugger launch

cd ~/esp/openocd-esp32
bin/openocd -s share/openocd/scripts -f interface/ftdi/esp32_devkitj_v1.cfg -f board/esp-wroom-32.cfg

covert image to baseline:

convert -strip -interlace Plane <image_none_baseline>.jpg <image_baseline>.jpg

image will only work in RGB mode from GIMP

## Docker

instal docker compose and docker
connect your dev board to the pc via usb

To start Docker run:

sudo docker-compose build esp32-builder

and to run it

sudo docker-compose run --rm esp32-builder

run

make menuconfig

select

Serial flasher config --->

hit enter and enter again

now insert

/dev/ttyUSB1

if this is already the default the leave it as it is.

Save changes and run:

make -j10

or if you want to flash to the ESP32 directly

make flash -j10

or to monitor LOGs

make flash monitor (to end press ctrl + ], do not run this in VisualCode console)

Now your ESP32 dev board should blink (LCD screen black and white)

to gain access to all files after pressing ctrl+d in the consol run

sudo chown -R \$USER .
