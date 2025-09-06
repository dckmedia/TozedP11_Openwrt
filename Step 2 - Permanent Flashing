
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
