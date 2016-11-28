# Benevue/Ikon R70AC Kids tablet reset details.

The R70AC (or any generic low cost tablet in my experience) really tends to (soft?)brick itself (freezes at the android logo) every now and then and I keep forgetting the ways to reset it, so I'll document it here. Linux instructions only.

The R70AC's SoC is Rockchip, presumably the RK3026. I bundled some old factory image (it's around 930 MB) using git lfs.

## Factory reset

Stuck at the android logo? Connect it to a computer running linux with adb, run the adb server as root, `adb devices` should list the device, do `adb reboot recovery` to go to recovery.

Clearing the data or cache from that recovery seems to be of no use though. Flash via fastboot? It's not even there.

Go to OEM's 'recovery mode' by doing something like this:

1. Ensure device is fully charged.
2. Power down the device (press the reset pin for a few seconds and leave the device untouched for around 2-3 minutes)
3. Plug in the USB cable the computer that's already booted up. (not the tablet, yet)
4. Hold the VOL+ button.
5. Without releasing the VOL+ button, plug in the USB cable to the tablet.
6. Without releasing the VOL+ button, hold the POWER button.
7. Wait for about 10-15 seconds.

Run the rockchip's proprietary linux x86_64 binary as root (it's inside Linux_Upgrade_Tool_v1.21.zip). `sudo ./update_tool` to check if the rockchip device is listed. Proceed to install the firmware I bundled here by doing `sudo ./update_tool uf R70AC.img`. The device should reboot automatically after the update process.

## Related links

* [https://github.com/linux-rockchip](https://github.com/linux-rockchip) ([http://linux-rockchip.org/](http://linux-rockchip.org))
