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
