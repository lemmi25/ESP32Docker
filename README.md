# Docker for ESP32

install [docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/) and docker compose

```
sudo apt-get install docker-compose
```

To build your own project with docker simply change the blink folder with your project.

connect your dev board (I used the [ESP-WROVER-KIT V4.1](https://docs.espressif.com/projects/esp-idf/en/latest/hw-reference/get-started-wrover-kit.html)) to the pc via usb

## Start Docker

in this directory were the Dockerfile is run

```
sudo docker-compose build esp32-builder
```

afterwards

```
sudo docker-compose run --rm esp32-builder
```

now you should be in the docker environment in your consol. If you do this for the first time you have to configure your board with

```
make menuconfig
```

a menu will appear select

```
Serial flasher config --->
```

hit enter and enter again now insert

```
/dev/ttyUSB1
```

if this is already the default then leave it as is.

Save changes and run:

```
make -j10
```

or if you want to flash to the ESP32 directly

```
make flash -j10
```

or to monitor LOGs

```
make flash monitor
```

(to end press **ctrl + ]**, do not run this in VisualCode console)

**Now your ESP32 dev board should blink (LCD screen black and white)**

to gain access to all files after pressing **ctrl+d** in the consol run

```
sudo chown -R \$USER .
```
