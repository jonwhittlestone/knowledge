# Root guide and Tethering hide for Nexus 5 and Android Lollipop

## Prerequisites
* Turn USB debugging on

* Have Android SDK. Android Studio comes with this so I use:
        /Users/jon/Library/Android/sdk/platform-tools/adb devices

1. Wipe device

Either by choosing menu option and downloading official Google image and choosing `flash-all.sh`

2. WHen back into stock Android, turn USB debugging back on and check phone can be seen
3. Unloack bootloader
4. Check can boot into fastboot
5. Download TWRP
       https://twrp.me/devices/lgnexus5.html  
      
6. Follow Instructions
    /Users/jon/Library/Android/sdk/platform-tools/fastboot flash recovery ~/Downloads/twrp-3.1.1-0-hammerhead.img
7. Boot into TWRP recovery mode
8. Choose to root from this screen
9. Reboot and Android and wait for optimising apps
10. Let all Android apps update

### IMEI hiding

This needs Xposed Framework
    https://forum.xda-developers.com/showthread.php?t=3034811

11. Download the framework to Phone
    http://dl-xda.xposed.info/framework/sdk22/arm64/xposed-v87-sdk22-arm64.zip
    
13. Boot into bootloader
    /Users/jon/Library/Android/sdk/platform-tools/adb reboot bootloader
14. Go into recovery mode and use TWRP to install zip from step 11.
15. 

    
----
# Hide Tethering by rooting Nexus 5x first

To flash Nexus 5 back to stock Andoroid 5.x
    https://dl.twrp.me/hammerhead/
Use flash-all.sh in that archive which has several commands to run fastboot
## Resources

1. Have Developer Options unlocked and USB Debugging Mode Enabled

2. Download the SuperSU for the Google Nexus 5X smartphone directly to the computer and then open up the Downloads folder on the computer to find your file.
    - Ensure Android File Transfer on Mac sees the phone by selecting 'MTP' in Developer Options > Select USB Configurations
  
3. Ensure you have ADB Driver so you can run ADB commands 
    - With Android Studio on Mac this is at 
    
        /Users/jon/Library/Android/sdk/platform-tools/adb devices
        /Users/jon/Library/Android/sdk/platform-tools/adb reboot bootloader
        /Users/jon/Library/Android/sdk/platform-tools/adb flash recovery twrp.img       
       
 4. Download TWRP for Nexus 5x and move to the ADB directory above
 
 5.  adb reboot booatloader
    - 'unauthorized' then reboot
 6. Download twrp
   https://twrp.me/devices/lgnexus5.html  
 7. Follow instructions
   https://twrp.me/devices/lgnexus5.html  

fix optimising app by locking dex file with this app 
 https://play.google.com/store/apps/details?id=in.co.giis.optimisingappfixer
