
## Backup existing firmware

Before you do any permanent flashing, it is recommended to take a full flash backup so you can revert back to original firmware. 
To do that, you have 2 mothods

#### Method 1 - Using UART console + initramfs boot

#### 1. Interrupt the Boot Process

    athrs27_phy_setup ATHR_PHY_CONTROL 0 :1000
    athrs27_phy_setup ATHR_PHY_SPEC_STAUS 0 :10
    ...
    eth1 up
    eth0, eth1
    Hit any key to stop autoboot:  0

#### 2. Configure TFTP Boot Parameters
Copy and paste the following in to the uboot prompt to set the device (router) and TFTP server (your PC) IP addresses:

    setenv ipaddr 192.168.8.1
    setenv serverip 192.168.8.100

Make sure your PC is running a TFTP server and the openwrt-ath79-generic-tozed_p11-initramfs-kernel.bin file is placed in the TFTP root directory.

#### 3. Load OpenWrt via TFTP
Copy and paste the following in to the uboot prompt

    tftpboot 0x81000000 openwrt-ath79-generic-tozed_p11-initramfs-kernel.bin
    
Hit Enter and wait for the transfer to complete.

#### 4. Boot OpenWrt in RAM
Copy and paste the following in to the uboot prompt

    bootm 0x81000000

Hit Enter and the device will now boot into the OpenWrt initramfs image from RAM.

#### 5. Check the mtd partitions
On the openwrt root shell loaded type and hist enter.

    cat /proc/mtd

    dev:    size   erasesize  name
    mtd0: 00040000 00010000 "u-boot"
    mtd1: 00040000 00010000 "u-boot-env"
    mtd2: 00040000 00010000 "art"
    mtd3: 00740000 00010000 "firmware"

#### 6. Backup 
Backup each partition in to /tmp directory of the router and then tranfer them to your PC using WinScp

    mtd read /tmp/mtd0_u-boot.bin /dev/mtd0
    mtd read /tmp/mtd1_u-boot-env.bin /dev/mtd1
    mtd read /tmp/mtd2_art.bin /dev/mtd2
    mtd read /tmp/mtd3_firmware.bin /dev/mtd3


#### Method 2 - Using CHA341A mini programmer + flashrom
You will need following equipments

 - CH341A Mini Programmer - (should support 3.3v - if not, [follow this video](https://www.youtube.com/watch?v=C53-aqp4hbI) to modify the programmer)
 - SOIC8 SOP8 Flash Chip IC Test Clips Socket
   Adapter

<img src="https://res.cloudinary.com/dckmedia/image/upload/v1751113360/CHA341a_iib8vz.jpg" alt="cha341a" width="500"/>

Install the correct drivers for your CHA341A. Turn the ODU powe off and unplug thernaet cable. Connect SOP8 200mil connector to the MX25L6436F chip properly. Make sure you have a good solid connection. Then plug the programmer in to your linux or windows computer. 

<img src="https://res.cloudinary.com/dckmedia/image/upload/v1751113196/Tozed_P11/pin_configuration.jpg" alt="cha341a" width="600"/>

Use [flashrom](https://github.com/flashrom/flashrom) if you are using Linux or use [AsProgrammer dregmod](https://github.com/therealdreg/asprogrammer-dregmod)r for windows to backup the existing full flash of your device.[Install flashrom on Ubuntu](https://installati.one/install-flashrom-ubuntu-22-04)

Keep the spi backup in secure location so you can write it back using the CHA341a Programmer if needed.

#### Next topic
[Permanent Flashing](https://github.com/dckmedia/TozedP11_Openwrt/blob/main/Step%202%20-%20Permanent%20Flashing.md)
