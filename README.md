# Lenovo-Yoga-370
A fully functioning Opencore EFI for the Lenovo Yoga 370


Okayy so this is my first Opencore efi (Well my first EfI in general but eh). Regardless of that it is fully Funktional, except for airdrop, it is a little flumys sometimes.
I haven't been able to add the boot chime to the OpenCore drive picker, but that is probably since im inexperienced. However, this EfI stable and runs fine.
If you have improvements or Questions, please dm me or write me on Discord: knyyl. Thanks to y'all.
EFI Works with MacOs Big Sur

*Installation*
BIOS Settings:
    Note: Most of these options may not be present in your firmware, we recommend matching up as closely as possible but don't be too concerned if many of these options are not available in your BIOS


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

Downloading Macos:
  https://github.com/acidanthera/OpenCorePkg/tree/master              
  Clone this repo and go into Utilites and then Macrecovery            
  Open a terminal window and type: python3 ./macrecovery.py -b Mac-42FD25EABCABB274 -m 00000000000000000 download             
  Copy the recovery.apple.com, you will need it later                
Makeing the installation Usb:                 
  If you're on windows, Download Rufus. set the Usb as non bootable and the partition as gpt.           
  Then, paste the recovery.apple.com into the Root directory of the drive (Root directory = The page that loads when you first open the Usb)       
  Copy the !UNZIPPED! EFI there aswell.       
Reboot, and hit enter and then F12 to choose a startup disk. Once you booted of your usb, choose the Macos recovery image (if it doesnt show, press the space bar).      
Format your drive as apfs. (You can dual boot, just make sure to copy the contents of your existing efi into the new one).         
After that, you can copy your EFI from the Usb stick to your pc so It can boot up without the Usb stick.          
Once you loaded into macos, open a terminal window and type "diskutil list".          
Then choose the drive which contains your EFI. Its usually /dev/disk0s2           
Copy the EFI to your desktop, incase something goes wrong, and then put the !UNZIPPED! EFI from the Usb stick there.         
You should be good to go rn, if you're not, feel free to dm me and Ill help with your issue.      
Good luck x3 Knyyl       
