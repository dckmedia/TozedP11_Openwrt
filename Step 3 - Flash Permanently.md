### Flash Permanently

Load initramfs as per Step 2 instructions

Access terminal using putty and enter the below and check the partition layout

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

Using Winscp, upload the openwrt-ath79-generic-tozed_p11-squashfs-bootm.bin file into /tmp directory and cd in to it

Use mtd write to flash the firmware image\

        mtd write openwrt-ath79-generic-tozed_p11-squashfs-bootm.bin firmware

When the writing has completed, reboot the router

<img src="https://res.cloudinary.com/dckmedia/image/upload/v1751116756/flashing_xs5ucz.jpg" alt="cha341a" width="600"/>

Upon reboot, you may see in uart Bad Magic Number. This means you have to update your u-boot bootargs. Use the following commands and reboot the router. 

        setenv bootargs 'console=ttyS0,115200 root=/dev/mtdblock1 rootfstype=squashfs,jffs2 rw init=/sbin/init mtdparts=ath-nor0:64k(u-boot),6528k(rootfs),448k(rootfs_data),1024k(uImage),64k(mib0),64k(ART)'

        saveenv

To boot it without restarting

        bootm 0x9f010000
