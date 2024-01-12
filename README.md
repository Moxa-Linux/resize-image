# Moxa image resize utility

Moxa image resize utility is used to shrink the dumped image file size.

## Usage

```
# ./resize-img <image_type> <image_file>
```

---

## Steps to create a customized Image

Here we take UC-8100 as illustration:

#### 1. Install and modify all the applications and configurations you want on the UC-8100

#### 2. Dump the image by `dd` command. There are two methods to copy the whole system

- 2.a - Dump via ethernet and save it to another Linux PC with enough storage
	```
	# dd if=<device> | ssh <Username of Linux PC>@<IP address of Linux PC> dd of=<dumped_image_file>
	```
	
	The device can be checked by `lsblk` command:
	
	![lsblk](/lsblk.PNG)
	
	In this example, root is mounted at "/dev/mmcblk0p2", so the device is "/dev/mmcblk0":
	
	```
	# dd if=/dev/mmcblk0 | ssh user@192.168.3.100 dd of=/tmp/uc8100_dump.img
	```

- 2.b Dump the image to the local storage such as USB disk
	```
	# dd if=<device> of=<dumped_image_file>
	```
	
	![lsblk-usb](/lsblk_usb.PNG)
	
	In this example, root is mounted at "/dev/mmcblk2p2", so the device is "/dev/mmcblk2":
	
	```
	# dd if=/dev/mmcblk2 of=/media/usb/uc8100_dump.img
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
	* UC-8410A series (V3.2 and older version):

		including UC-8410A-NW-T-LX, UC-8410A-NW-LX, UC-8410A-T-LX, UC-8410A-LX
	* UC-8540 series (V1.3 and older version):

		including UC-8540-LX, UC-8540-T-LX, UC-8540-T-CT-LX
	* UC-8580 series (V1.3 and older version):

		including UC-8580-LX, UC-8580-T-LX, UC-8580-T-CT-LX, UC-8580-Q-LX, UC-8580-T-Q-LX, UC-8580-T-CT-Q-LX
* Type B
	* UC-2100 series:

		including UC-2101-LX, UC-2102-LX, UC-2104-LX, UC-2111-LX, UC-2112-LX, UC-2112-T-LX
	* UC-3100 series:

		including UC-3101-T-US-LX, UC-3101-T-EU-LX, UC-3101-T-AU-LX, UC-3101-T-AP-LX, UC-3111-T-US-LX,
		UC-3111-T-EU-LX, UC-3111-T-AU-LX, UC-3111-T-AP-LX, UC-3121-T-US-LX, UC-3121-T-EU-LX, UC-3121-T-AU-LX,
		UC-3121-T-AP-LX, UC-3111-T-EU-LX-NW, UC-3111-T-AP-LX-NW, UC-3111-T-US-LX-NW
	* UC-5100 series:

		including UC-5101-LX, UC-5101-T-LX, UC-5102-LX, UC-5102-T-LX, UC-5111-LX, UC-5111-T-LX, UC-5112-LX, UC-5112-T-LX
	* UC-8100A-ME series:

		including UC-8112A-ME-T-LX, UC-8112A-ME-T-US, UC-8112A-ME-T-EU, UC-8112A-ME-T-AP
	* UC-8410A series (V4.0.2 and newer version):

		including UC-8410A-NW-T-LX, UC-8410A-NW-LX, UC-8410A-T-LX, UC-8410A-LX
	* UC-8540 series (V2.0 and newer version):

		including UC-8540-LX, UC-8540-T-LX, UC-8540-T-CT-LX
	* UC-8580 series (V2.0 and newer version):

		including UC-8580-LX, UC-8580-T-LX, UC-8580-T-CT-LX, UC-8580-Q-LX, UC-8580-T-Q-LX, UC-8580-T-CT-Q-LX
* Type C
	* UC-8200 series:

		including UC-8210-T-LX, UC-8210-T-LX-S, UC-8220-T-LX, UC-8220-T-LX-US-S ,UC-8220-T-LX-EU-S ,UC-8220-T-LX-AP-S
