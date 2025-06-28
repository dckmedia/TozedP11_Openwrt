
**Backup existing firmware**

Before you do any permanent flashing, it is recommended to take a full flash backup so you can revert back to original firmware. 
To do that, you will need following equipments

 - CH341A Mini Programmer 
 - SOIC8 SOP8 Flash Chip IC Test Clips Socket
   Adapter
<img src="https://github.com/dckmedia/TozedP11_Openwrt/blob/main/CHA341a.jpg?raw=true" alt="CHA341a" width="200"/>

Install the correct drivers for your CHA341A. Turn the ODU powe off and unplug thernaet cable. Connect SOP8 200mil connector to the MX25L6436F chip properly. Make sure you have a good solid connection. Then plug the programmer in to your linux or windows computer. 

<img src="https://github.com/dckmedia/TozedP11_Openwrt/blob/main/pin_configuration.JPG" alt="CHA341a pin config" width="600">

Use [flashrom](https://github.com/flashrom/flashrom) if you are using Linux or use [AsProgrammer dregmod](https://github.com/therealdreg/asprogrammer-dregmod)r for windows to backup the existing full flash of your device.
