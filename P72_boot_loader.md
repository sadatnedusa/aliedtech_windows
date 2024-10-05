# ThinkPad P72 Boot Loader issue.
---
Typically, when purchasing a ThinkPad P72, it comes with a 500GB NVMe drive. Later on, you may add a 2.5-inch SSD and eventually another 1TB NVMe drive to increase storage capacity. However, if you remove the 1TB NVMe drive, the boot order may become misconfigured, causing boot issues, as the laptop may fail to start without the removed drive.
---
## **NOTE**

# Disclaimer:

## I am not responsible for any data loss or corruption. The following information is shared solely for informational purposes and reflects my personal experience with my laptop. You are encouraged to use your own judgment or seek professional assistance if needed. Please note that the information provided is not a substitute for expert advice, and any actions taken are at your own risk.


### **How to resolve/fix such issues.**

- To check and correct the boot loader configuration on your **ThinkPad P72 laptop**, you can follow these steps.
- We'll begin by checking the boot loader disks and then proceed with correcting any issues if needed.

### Step 1: **Check Boot Loader Disks**
#### 1. **Access BIOS/UEFI Settings**
   - Turn off your ThinkPad P72.
   - Turn it back on and immediately press the **Enter** key (or sometimes **F1**) repeatedly until the **Lenovo logo** appears. This will take you to the **BIOS/UEFI** menu.
   - Once in the BIOS, navigate to the **Boot** tab to check the boot order and available disks.
   
   Look for the following:
   - Ensure that the **boot priority** is set correctly, with your main OS disk (usually your SSD or HDD) listed first.
   - If multiple disks are present, note their names (such as NVMe SSD or SATA).

#### 2. **Check Boot Loader with Windows**
   If you can boot into Windows, you can check the boot loader settings using these methods:

   - **Using Command Prompt:**
     1. Press `Win + X` and select **Command Prompt (Admin)**.
     2. Run the following command to view the boot configuration data (BCD):
        ```
        bcdedit /enum
        ```
     3. This command lists all the boot entries in your system. Make sure that the correct disk/partition is listed as the default boot loader.

   - **Using Disk Management:**
     1. Press `Win + X` and choose **Disk Management**.
     2. Check if the partition marked as **Active** is the correct one that contains the boot loader (usually the `C:` drive).

### Step 2: **Correct Boot Loader Configuration**

#### Method 1: **Fix Boot Loader Using Windows Recovery**
   If the boot loader is not set up properly, you can use the Windows recovery environment to repair it:

   1. **Create Windows Installation Media** (if you don’t have it):
      - Download the **Windows 11 installation tool** from Microsoft's website and create a bootable USB drive.

   2. **Boot into the Recovery Environment:**
      - Insert the USB drive and restart your ThinkPad.
      - Press **Enter** or **F12** to access the boot menu and select the USB drive.

   3. **Select Your Language Preferences** and click **Next**.

   4. Choose **Repair your computer**.

   5. Navigate to **Troubleshoot** → **Advanced Options** → **Command Prompt**.

   6. In the Command Prompt, use the following commands to rebuild the boot loader:
      - To repair the MBR (Master Boot Record), type:
        ```
        bootrec /fixmbr
        ```
      - To write a new boot sector, type:
        ```
        bootrec /fixboot
        ```
      - To scan for and add missing Windows installations, type:
        ```
        bootrec /scanos
        ```
      - To rebuild the BCD (Boot Configuration Data):
        ```
        bootrec /rebuildbcd
        ```

   7. Once the process is complete, close the Command Prompt and restart your laptop.

#### Method 2: **Fix Boot Loader Using UEFI Settings**
   If you're using **UEFI**, the boot loader may have issues due to incorrect UEFI settings:

   1. **Access BIOS/UEFI settings** (follow the same steps as in Step 1).
   2. Go to the **Boot** tab and check if **UEFI/Legacy Boot** is set to **UEFI Only** (this is recommended for modern systems).
   3. Make sure that **Secure Boot** is enabled (if applicable) or try disabling it to see if it solves boot issues.
   4. Save the changes and exit.

#### Method 3: **Fix Boot Loader via Linux (Optional)**
   If you have a dual-boot system with Linux and the boot loader issue involves **GRUB**, you can reinstall GRUB:

   1. Boot into a **Live Linux USB** (such as Ubuntu).
   2. Open a terminal in the live environment and run the following commands to reinstall GRUB:
      ```
      sudo mount /dev/sda1 /mnt  # replace /dev/sda1 with your root partition
      sudo grub-install --root-directory=/mnt /dev/sda
      sudo update-grub
      ```
   3. Reboot and check if the boot loader works properly.

### Step 3: **Verify Boot Loader Setup**
   After making changes, you can reboot and press **F12** (or **Enter**) to check the boot menu. Ensure that the correct disk is set as the default boot option.

If everything is done correctly, your ThinkPad should boot properly using the right boot loader configuration.

Let me know if you encounter any issues during the process!
