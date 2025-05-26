# TozedP11_Openwrt
Install Openwrt on Tozed P11 ODU

## Device Information

<img src="https://github.com/user-attachments/assets/34ff8e63-27e7-4d2d-9fd6-12563e586fd4" alt="ODU" width="300"/>

<img src="https://github.com/user-attachments/assets/13a94e63-55cf-4d45-96f9-1d3ed5609395" alt="IDU" width="300"/>


### ODU UART Access
##### 1. Open the ODU (Outdoor Unit):
Carefully disassemble the unit to access the main PCB. Take precautions to avoid damaging the casing or components.

##### 2. Locate the UART Header:
Identify the UART pin header on the PCB  
<img src="https://github.com/user-attachments/assets/01a16874-02e7-43a0-b43a-20e76711f15a" alt="ODUuart" width="200"/>

##### 3. Connect a USB-to-TTL Adapter:

    TX (adapter) → RX (board)
    RX (adapter) → TX (board)
    GND → GND
    Leave VCC disconnected unless needed (most times not required).

##### 4. Use a Serial Terminal:

    Open software like PuTTY, screen, minicom, or Tera Term.
    Set baud rate to 115200
    Configure with 8N1 (8 data bits, No parity, 1 stop bit)
    No flow control

Power on the ODU and monitor the boot log. You should see U-Boot or kernel messages if everything is connected properly.

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
