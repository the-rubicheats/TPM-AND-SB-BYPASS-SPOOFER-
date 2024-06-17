# ONLY WORKS FOR WINDOWS 10 22H2
## STATUS - Unknown

### REQUIREMENT

#### STEP 1:
Convert the disk in which you will install windows into MBR partition. FOLLOW THIS IF YOU DON'T KNOW:
[https://learn.microsoft.com/en-us/windows-server/storage/disk-management/change-a-gpt-disk-into-an-mbr-disk](https://learn.microsoft.com/en-us/windows-server/storage/disk-management/change-a-gpt-disk-into-an-mbr-disk)

#### STEP 2:
Download ghost spectre windows 10 22H2 iso file, you can use any other but make sure that it's 22H2.

#### STEP 3:
Install RUFUS, select the USB which you will use to install windows. MAKE SURE TO SELECT MBR IN PARTITION STYLE.

#### STEP 4:
Go into your BIOS and change the boot mode to legacy (It can be a little different for different mobos), then Turn off TPM and SB. After this, boot from your USB stick.

**IMPORTANT INFORMATION:**
During the boot selection, do not select the drive which is labeled with UEFI!!! (you cannot install windows in a MBR disk if you are in EFI environment). Select the one which is labeled as USB.

#### STEP 5:
Delete all the partitions except the one which you converted into MBR, then install windows in it.

#### STEP 6:
Once windows is completely installed, search for System Information. Check if your "BIOS MODE" is set to LEGACY. If not, start again from STEP 1.

#### STEP 7:
Spoof your PC

##### STEP 7.01:
FLASH YOUR BIOS TO A DIFFERENT VERSION. (GOOGLE -- "YOUR MOBO NAME" bios download). After flashing, MAKE SURE TO RECHECK THAT TPM AND SB ARE TURNED OFF.

##### STEP 7.1 [for those who don't know how to spoof]:
(I WOULD RECOMMEND YOU TO DO STEP 7.2 instead)

Download THIS (credit @WH12)
1. Click refresh, take a screenshot of the HWID.
2. Click spoof. Then your PC will restart.
3. Open it again, click refresh, check if everything has changed.
4. If not, follow STEP 7.2 (You can still follow it even if STEP 7.1 worked, for good measures).

##### STEP 7.2 [for those who don't know how to spoof EFI METHOD]:

1. Make a .bat file and put this code inside it and run it.

```batch
    ECHO OFF
    TITLE UC CHECKER
    ECHO **********************************
    Color 0F
    ECHO **********************************
    :start
    cls
    wmic diskdrive get model, serialnumber
    ECHO CPU 
    wmic cpu get serialnumber
    ECHO BIOS
    wmic bios get serialnumber
    ECHO Motherboard
    wmic baseboard get serialnumber
    ECHO smBIOS UUID
    wmic path win32_computersystemproduct get uuid
    getmac
    echo Press any key to get your hardware serials again.
    pause>nul
    goto start
```

2- Take a screenshot.
3- Download RUFUS
4- Select your USB drive, Select non-bootable and change the partition style to GPT. Click start.
3- Download THIS
4-open startup.nsh file, and change all the HWID's to something random like this

```batch
    AMIDEEFIx64.efi /BS VCXZBHJSDGFYUASVDF          <--- ANYTHING RANDOM(any length), DO THIS FOR ALL THE COMMANDS
    except   AMIDEEFIx64.efi /SU AUTO
```

5 Now paste them into your USB drive . It should look something like this.

```batch
    USB:
           efi
           afuefix64.efi
           amideefix64.efi
           Startup.nsh
```

6-Now, restart and go into your BIOS.
7-Go into your BOOT ORDER
8-Assign the #1 BOOT PRIORITY (or something like that) to your USB.
9-Then boot from your USB.
10-It will start to spoof your PC (<5 seconds) and your windows will open automatically.
11-Compare your MOTHERBOARD SerialNumber and UUID.
12-If changed, you have successfully spoofed your PC.
13-If not, open the startup.nsh file inside the EFI folder.
14-Replace all the code with this.

```batch
    fs0:
    startup.nsh
```
15-Still not ? change all the amideefix64.efi into afuefix64.efi and try again. Like this.
```batch
    AMIDEEFIx64.efi /BS VCXZBHJSDGFYUASVDF    
    to
    afuefix64.efi /BS VCXZBHJSDGFYUASVDF    (do this for both startup.nsh files)
```

#### STEP 8:
run cmd as admin, paste
```batch
    bcdedit /set hypervisorlaunchtype off
```

#### YOU CAN CONTINUE USING UR OLD ACCOUNT (in some cases, old accounts will get a TPM prompt:
Download VALORANT and enjoy 
