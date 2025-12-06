

## Choosing the Correct SPI-NOR Flash Chip**

When upgrading a router from 8MB → 16MB flash, it is essential to select a compatible SPI-NOR chip. The replacement must match the electrical, protocol, and command set characteristics of the original chip.

✔️ Original chip

MX25L6436F — 64Mbit (8MB), 3.3V, SPI NOR, JEDEC-compatible.

✔️ New upgraded chip

MX25L12833F — 128Mbit (16MB), 3.3V, SPI NOR, JEDEC-compatible.

Both chips share:

 - Same voltage (3.3V)
 - Same SPI mode support
 - Same erase/write commands
 - Compatible JEDEC ID structure
 - Same 4KB sector erase size
 - Same page size (256 bytes)
 - Same W25Q/MX25 command set

Because of this compatibility, the router’s bootloader and kernel SPI drivers can interface with the new chip without modification—as long as the DTS flash size is updated.

<img width="239" height="271" alt="old" src="https://github.com/user-attachments/assets/11c1514a-9660-4d1e-9192-9894c47de83b" />

<img width="239" height="271" alt="new" src="https://github.com/user-attachments/assets/0b2b6d1c-a0dd-4e66-96fb-e8df24be9149" />

## How to upgrade

 1. **Download the full 16 MB SPI flash image** - Download the file tozed_p11_16mb_spi_flash.bin from the repository
    
 2. **Flash the new SPI chip** - Use a hardware SPI programmer (e.g., CH341A) to write the full 16 MB image to the new MX25L12833F SPI chip.
    
 3. **Replace the old chip on the P11 PCB** - Carefully remove the original 8 MB SPI chip from the PCB.
    
 4. **Solder the new 16 MB SPI chip in its place.**
    
 5. **Boot the router** - Power on the router — it should now boot from the restored 16 MB SPI chip with all partitions intact.
<img width="1360" height="1386" alt="16mb" src="https://github.com/user-attachments/assets/1b64ef9d-4940-4c79-9d59-e1c1ff1646b9" />
