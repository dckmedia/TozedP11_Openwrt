
### Load Openwrt initramfs
#### UART Boot Instructions for Tozed P11
##### 1. Access the UART Terminal
Connect to the device via UART (115200 baud rate). You’ll see boot logs similar to:

    athrs27_phy_setup ATHR_PHY_CONTROL 0 :1000
    athrs27_phy_setup ATHR_PHY_SPEC_STAUS 0 :10
    ...
    eth1 up
    eth0, eth1
    Hit any key to stop autoboot:  0

##### 2. Interrupt the Boot Process
When you see Hit any key to stop autoboot, press any key quickly to access the U-Boot prompt.

##### 3. Configure TFTP Boot Parameters
Set the device (router) and TFTP server (your PC) IP addresses:

    setenv ipaddr 192.168.8.1         # IP address of the router
    setenv serverip 192.168.8.100     # IP address of your PC (running TFTP server)

Make sure your PC is running a TFTP server and the openwrt-ath79-generic-tozed_p11-initramfs-kernel.bin file is placed in the TFTP root directory.

##### 4. Load OpenWrt via TFTP
    tftpboot 0x81000000 openwrt-ath79-generic-tozed_p11-initramfs-kernel.bin
    
Wait for the transfer to complete.

##### 5. Boot OpenWrt in RAM

    bootm 0x81000000

The device will now boot into the OpenWrt initramfs image from RAM.
