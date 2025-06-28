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
