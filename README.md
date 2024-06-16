# Lenovo-Yoga-370
A fully functioning Opencore EFI for the Lenovo Yoga 370

<details>
  <summary>Me Yapping a little</summary>
  This is my first OpenCore EFI (well, my first EFI in general). Despite my inexperience, it is fully functional except for Airdrop, which can be a little flaky at times. I haven't been able to add the boot chime to the OpenCore drive picker, likely due to my inexperience. However, this EFI is stable and runs fine. If you have improvements or questions, please DM me or reach out on Discord: knyyl. Thanks to y'all.
</details>
*Installation*          
BIOS Settings:
    Note: Most of these options may not be present in your firmware, I recommend matching up as closely as possible but don't be too concerned if many of these options are not available in your BIOS


Disable

    Fast Boot
    Secure Boot
    Serial/COM Port
    Parallel Port
    VT-d (can be enabled if you set DisableIoMapper to YES)
    Compatibility Support Module (CSM) (Must be off in most cases, GPU errors/stalls like gIO are common when this option is enabled)
    Thunderbolt (For initial install, as Thunderbolt can cause issues if not setup correctly)
    Intel SGX
    Intel Platform Trust
    CFG Lock (MSR 0xE2 write protection)(This must be off, if you can't find the option then enable AppleXcpmCfgLock under Kernel -> Quirks. Your hack will not boot with CFG-Lock enabled)


Enable

    VT-x
    Above 4G Decoding
    Hyper-Threading
    Execute Disable Bit
    EHCI/XHCI Hand-off
    OS type: Windows 8.1/10 UEFI Mode (some motherboards may require "Other OS" instead)
    DVMT Pre-Allocated(iGPU Memory): 64MB or higher
    SATA Mode: AHCI

# macOS Installation Guide

## Downloading macOS
1. Clone the OpenCorePkg repository from GitHub:
   ```sh
   git clone https://github.com/acidanthera/OpenCorePkg.git
   ```
2. Navigate to the `Macrecovery` directory:
   ```sh
   cd OpenCorePkg/Utilities/Macrecovery
   ```
3. Open a terminal window and run the following command to download the recovery image:
   ```sh
   python3 ./macrecovery.py -b Mac-42FD25EABCABB274 -m 00000000000000000 download
   ```
4. Copy the `com.apple.recovery` folder, you will need it later.

## Making the Installation USB
### On Windows:
1. Download and open [Rufus](https://rufus.ie/).
2. Set the USB as non-bootable and the partition scheme as GPT.
3. Paste the `com.apple.recovery` file into the root directory of the USB drive (Root directory = The page that loads when you first open the USB).
4. Copy the **unzipped** `EFI` folder to the root directory of the USB drive as well.

## Booting from the USB
1. Reboot your computer and press `Enter`, then `F12` to choose a startup disk.
2. Boot from your USB drive and select the macOS recovery image (if it doesn't show, press the space bar).
3. Format your drive as APFS. (You can dual boot, just make sure to copy the contents of your existing EFI into the new one).
4. After formatting, you can copy your `EFI` from the USB stick to your PC so it can boot up without the USB stick.

## Post-Installation
1. Once you have booted into macOS, open a terminal window and type:
   ```sh
   diskutil list
   ```
2. Identify the drive which contains your EFI partition, usually `/dev/disk0s2`.
3. Copy the `EFI` folder to your desktop as a backup.
4. Replace the EFI on your drive with the **unzipped** `EFI` from the USB stick.

## Troubleshooting
If you encounter any issues, feel free to DM me for assistance.

Good luck! x3  
*Knyyl*
