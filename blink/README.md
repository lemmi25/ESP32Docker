## Docker for ESP32

install docker compose and docker
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

