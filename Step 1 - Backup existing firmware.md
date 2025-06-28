
**Backup existing firmware**

Before you do any permanent flashing, it is recommended to take a full flash backup so you can revert back to original firmware. 
To do that, you will need following equipments

 - CH341A Mini Programmer 
 - SOIC8 SOP8 Flash Chip IC Test Clips Socket
   Adapter

<img src="https://res.cloudinary.com/dckmedia/image/upload/v1751113360/CHA341a_iib8vz.jpg" alt="cha341a" width="500"/>

Install the correct drivers for your CHA341A. Turn the ODU powe off and unplug thernaet cable. Connect SOP8 200mil connector to the MX25L6436F chip properly. Make sure you have a good solid connection. Then plug the programmer in to your linux or windows computer. 

<img src="https://res.cloudinary.com/dckmedia/image/upload/v1751113196/Tozed_P11/pin_configuration.jpg" alt="cha341a" width="600"/>

Use [flashrom](https://github.com/flashrom/flashrom) if you are using Linux or use [AsProgrammer dregmod](https://github.com/therealdreg/asprogrammer-dregmod)r for windows to backup the existing full flash of your device.

Keep the spi backup in secure location so you can write it back using the CHA341a Programmer if needed.
