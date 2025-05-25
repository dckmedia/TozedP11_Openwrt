# TozedP11_Openwrt
Install Openwrt on Tozed P11 ODU

## Device Information
This device consist of seperate outdoor unit and indoor unit. 

### ODU UART Access
#### 1. Open the ODU (Outdoor Unit):
Carefully disassemble the unit to access the main PCB. Take precautions to avoid damaging the casing or components.

#### 2. Locate the UART Header:
Identify the UART pin header on the PCB  
<img src="https://github.com/user-attachments/assets/01a16874-02e7-43a0-b43a-20e76711f15a" alt="ODUuart" width="200"/>

#### 3. Connect a USB-to-TTL Adapter:

    TX (adapter) → RX (board)
    RX (adapter) → TX (board)
    GND → GND
    Leave VCC disconnected unless needed (most times not required).

#### 4. Use a Serial Terminal:

    Open software like PuTTY, screen, minicom, or Tera Term.
    Set baud rate to 115200
    Configure with 8N1 (8 data bits, No parity, 1 stop bit)
    No flow control

Power on the ODU and monitor the boot log. You should see U-Boot or kernel messages if everything is connected properly.

### Load Openwrt initramfs
Carefully look at the Uart terminal and stop autoboot by pressing any key.

    athrs27_phy_setup ATHR_PHY_CONTROL 0 :1000
    athrs27_phy_setup ATHR_PHY_SPEC_STAUS 0 :10
    athrs27_phy_setup ATHR_PHY_CONTROL 1 :1000
    athrs27_phy_setup ATHR_PHY_SPEC_STAUS 1 :10
    athrs27_phy_setup ATHR_PHY_CONTROL 2 :1000
    athrs27_phy_setup ATHR_PHY_SPEC_STAUS 2 :10
    athrs27_phy_setup ATHR_PHY_CONTROL 3 :1000
    athrs27_phy_setup ATHR_PHY_SPEC_STAUS 3 :10
    eth1 up
    eth0, eth1
    Hit any key to stop autoboot:  0

