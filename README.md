# ModernOldWin
ModernOldWin is a guide to setting up old versions of windows (eg. Windows 7) on new hardware, such as Ryzen 5 or Intel 12-14th gen.

> DISCLAIMER: I AM NOT RESPONSIBLE FOR WHAT YOU DO TO YOUR COMPUTER. This is simply a guide for what worked for me. If you are not good at troubleshooting, I would advise you not to do this. For me to even get to this point I spent 11 hours coming up with different ways I could get it to work on my computer. It sucked. It shouldn't take you 11 hours, but make sure you back up your data to a reliable drive and that you have a Windows 10/11 installer or another computer also ready in case anything goes wrong. Good luck!

## Prerequisites

- Old Windows ISO (with USB/NVME drivers if you don't have PS/2) [Download Link](https://board.eclipse.cx/viewtopic.php?t=401)
- Latest Windows 10 ISO [Download Link](https://www.microsoft.com/en-us/software-download/windows10ISO)
> If the Windows 10 ISO page comes up with a Media Creation tool, enter Inspect and set the view to mobile, then refresh the page. It will refresh into the real ISO download page, and you can then close inspect.
> You can also use a Windows 11 ISO, just make sure it has the traditional setup experience. As of right now, there is no benefit to using a Windows 11 ISO but it might add compatibility in the future when Windows 10 is too old for modern hardware
- DISM++ [Download Link](https://www.majorgeeks.com/files/details/dism.html)
- 7zip [Download Link](https://www.7-zip.org/)
- A USB flash drive
- Graphics, network, etc. drivers for your machine
- Rufus (latest version that your system allows) [Download Link](https://rufus.ie/en/)
- Recommended: Rufus portable, compatible with Windows 7 [Download Link](https://github.com/pbatard/rufus/releases/download/v3.22/rufus-3.22p.exe)
- Recommended: a lightweight linux ISO (eg. ArchBang [Download Link](https://sourceforge.net/projects/archbang/?source=typ_redirect))

## Stage 1 of setup

### Step 1: Use 7-zip to extract both ISOs.
I recommend creating a folder for the extracted ISOs. Make sure there are no spaces in the path to either of the files (including the name of the ISOs). You must also be able to tell which folder is for which ISO, so name them clearly.

### Step 2: Locate/Convert install.wim or install.esd.
Look for the install.wim or install.esd file on both your Windows 10 ISO and your Windows 7 ISO. This will be in (ISO FOLDER PATH)\Sources.
You may find install.esd, which may not work under certain configurations. For this to work smoothly, use DISM++ to convert the Old Windows install.wim/install.esd to whatever format the Windows 10/11 install file is. In my case, the Windows 10 ISO had install.wim whereas the Windows 7 ISO had install.esd. Converting the Windows 7 install.esd to install.wim made it run smoothly on my computer.
> From here forward, install.wim will stand for both install.wim and install.esd.

### Step 3: Copy your Old Windows install.wim file to the Windows 10/11 ISO.
Copy the install.wim file from your Old Windows Sources folder to the Sources folder in your Windows 10/11 ISO. This part is pretty straightforward, just make sure you are replacing the file because otherwise you will have "install - Copy.wim" and that won't work. Make sure it's named install.wim (or install.esd).

### Step 4: Use DISM++ to convert the folder into an ISO file.
Use DISM++ to convert the Windows 10/11 ISO folder into an actual ISO file. You could theoretically do this with 7zip as well, but the compression settings are specific and under certain situations may not work. Using DISM++ makes it far easier to convert the files, as it has dedicated sections just for that.

Ensure that the file you have now is a .iso file and that the files are not nested within an additional folder.

### Step 5: Use rufus to burn the ISO to the USB.
Ensure that the settings are for UEFI and GPT, as newer hardware usually requires these to even boot without changing BIOS settings. They are also more up-to-date and will provide a smoother experience.

### Step 6: Put required drivers in a new folder on your USB drive.
Make sure they work on Windows 7. Remember that even though we are using a Windows 10/11 setup, we are installing Windows 7 which will not be compatible with many new drivers. At some point I might make a list of the most up-to-date drivers I can find for modern hardware. This is also where you should put your portable Rufus and your lightweight linux ISO.

## Good Precautions
I __strongly__ recommend backing up your data. **You will not be able to install this over a current Windows install. It's not possible.** I also strongly recommend unplugging hard drives other than the one you're installing to. Windows has a reputation of messing with drives you didn't select, and it has happened to me multiple times before (even if I tripe check which drive I format).

## Stage 2 of setup

### Step 7: Plug the USB into your computer and boot to it.
Most computers have a boot menu that you can access by pressing F12, but check for your system to make sure you're pressing the right key. After this, there should be a menu of boot options. The one you want to click will usually be the brand of your USB, followed by UEFI and a partition number. You want to use the first partition you see, so if there is Partition 1, 2, and 3 use partition 1. If you see Partition 0 and 1 then use Partition 0. If you are unsure, just try options until you see a setup screen. No harm should be done to your computer if you choose the wrong one.

### Step 8: Install Windows as normal
This part should feel just like installing Windows 10. If you are using the ISO I provided earlier, there will be 6 options. They will be along the lines of 2016-something and 2020-something. The 2020 versions are recommended, but if you care a lot about telemetry etc. use the 2016 versions. They have all the same basic drivers, just the 2020 one has additional "feature" updates from Microsoft. For most cases, use Windows 7 Ultimate. The only benefit the other versions really give is that they take up less space.
> Features: Ultimate,
> Middle Child: Professional,
> Lightweight: Home Premium.

## Stage 3 of setup

### Step 9: Install Drivers
This is the tricky part. The issue is, if your network drivers are not compatible with Windows 7, you will have to get them from another computer or a live linux install on your USB. If you didn't get the right drivers, this is the part where the linux ISO and Rufus is useful (ESPECIALLY if you don't have a second computer). Either use your other computer or your linux ISO to get working drivers onto your computer. If there are no drivers that work, you are almost out of luck. The last thing you can try is to take the .inf files from the driver installers and install those manually. At that point, I can't help you because I personally did not have to do that.

### Step 10: Personalize!
You're done! Now you can activate Windows (if you didn't during the install), install your apps, etc. At the time of writing this (Jan. 2024), most apps still have Windows 7 installers and many Windows 10 apps still work on Windows 7, however this may change in the future.


Thanks for reading :)
  - Riley
