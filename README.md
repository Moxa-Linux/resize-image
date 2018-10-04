# Moxa image resize utility

Moxa image resize utility is used to shrink the dumped image file size.

## Usage

```
# ./resize-img <image_type> <image_file>
```

---

## Steps of making a customed image

Here we take UC-8100 as illustration:

#### 1. Install and modify all the applications and configurations you want on the UC-8100

#### 2. Dump the image by `dd` command and save it to another Linux PC with enough storage
```
# dd if=<device> | ssh <Username of Linux PC>@<IP address of Linux PC> dd of=<dumped_image_file>
```

The device can be checked by `lsblk` command:

![lsblk](/lsblk.PNG)

In this example, root is mounted at "/dev/mmcblk0p2", so the device is "/dev/mmcblk0":

```
# dd if=/dev/mmcblk0 | ssh user@192.168.3.100 dd of=/tmp/uc8100_dump.img
```

#### 3. Clone or download this repository on your Linux PC
```
# git clone https://github.com/Moxa-Linux/resize-image
# cd resize-image
```

#### 4. Resize the image

The image type can be found at "Image type table" below (The image type of "UC-8100" is type A)

```
# ./resize-img A /tmp/uc8100_dump.img
```

The output image file will be named as "resize.img"

---

## Image type table

* Type A
	* UC-8100 series:

		including UC-8131-LX, UC-8132-LX, UC-8162-LX, UC-8112-LX, UC-8112-LX1
	* UC-8100-ME series:

		including UC-8112-ME-T-LX, UC-8112-ME-T-LX1, UC-8112-ME-T-LX-US-LTE, UC-8112-ME-T-US-LTE-LX1
* Type B
	* UC-2100 series:

		including UC-2101-LX, UC-2102-LX, UC-2104-LX, UC-2111-LX, UC-2112-LX, UC-2112-T-LX
	* UC-3100 series:

		including UC-3101-T-US-LX, UC-3101-T-EU-LX, UC-3101-T-AU-LX, UC-3111-T-US-LX, UC-3111-T-EU-LX, UC-3111-T-AU-LX, UC-3121-T-US-LX, UC-3121-T-EU-LX, UC-3121-T-AU-LX
	* UC-5100 series:

		including UC-5101-LX, UC-5101-T-LX, UC-5102-LX, UC-5102-T-LX, UC-5111-LX, UC-5111-T-LX, UC-5112-LX, UC-5112-T-LX
