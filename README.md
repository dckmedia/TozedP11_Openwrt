# TozedP11_Openwrt
Install Openwrt on Tozed P11 ODU

## Device Information

<img src="https://res.cloudinary.com/dckmedia/image/upload/v1751110135/Tozed_P11/oduidu.jpg" alt="ODUuart" width="600"/>

## Why Openwrt ?
The ODU can be used as the seperate device with POE adapter and can be connected to any indoor router you have with a WAN port. Once Openwrt installed, you can replace the out of the box 4g module with any supporting mPCIe module. The mPCIe slot inside the ODU use USB lines to connect the 4g module in to the main board. So your choice of 4g module must be usb supporting one. For my testing, i have used Tozed LT72-A 4g module extracted from Tozed S12 pro cat 6 router.

Special thanks to - [Lakshan Technology](https://www.facebook.com/share/1AXsUXrdP9/?mibextid=wwXIfr) for providing me a device at low cost for testing and debugging.

### ODU UART Access
##### 1. Open the ODU (Outdoor Unit):
Carefully disassemble the unit to access the main PCB. Take precautions to avoid damaging the casing or components.

##### 2. Locate the UART Header:
Identify the UART pin header on the PCB  
<img src="https://res.cloudinary.com/dckmedia/image/upload/v1751113055/Tozed_P11/uart.jpg" alt="uart" width="200"/>

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
