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
