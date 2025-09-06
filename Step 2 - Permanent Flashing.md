## Flashing Permanantly 
Please make sure you have followed the [Backup existing firmware procedure](https://github.com/dckmedia/TozedP11_Openwrt/blob/main/Step%201%20-%20Backup%20existing%20firmware.md) before begin. 
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

#### 5. Check mtd partitions
Using putty UART terminal and enter the below and check the partition layout

        cat /proc/mtd

You will see below partition layout

        dev:    size   erasesize  name
        mtd0: 00010000 00010000 "u-boot"
        mtd1: 007d0000 00010000 "firmware"
        mtd2: 00227761 00010000 "kernel"
        mtd3: 005a889f 00010000 "rootfs"
        mtd4: 001f0000 00010000 "rootfs_data"
        mtd5: 00010000 00010000 "mib0"
        mtd6: 00010000 00010000 "ART"

#### 6. Download relevent files
Donwload following 2 files from the release,
openwrt-ath79-generic-tozed_p11-squashfs-bootm.bin
u-boot_p11.bin

#### 7. Upload files using winscp
Using Winscp, upload both files in to into /tmp directory

<img src="https://res.cloudinary.com/dckmedia/image/upload/v1757149044/Tozed_P11/winscp.png" alt="uart" width="500"/>

#### 8. Use mtd write to flash the firmware image

        cd /tmp
        mtd write u-boot_p11.bin u-boot
        mtd write openwrt-ath79-generic-tozed_p11-squashfs-bootm.bin firmware

When the writing has completed, reboot the router
