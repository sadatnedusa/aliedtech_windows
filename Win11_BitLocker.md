# To remove **BitLocker** encryption from Windows 11, you need to decrypt the drive that has BitLocker enabled. 
---
## Here’s how you can do it:

### 1. **Turn off BitLocker via Control Panel**
   1. Press `Win + S`, type **Control Panel**, and open it.
   2. Navigate to **System and Security** → **BitLocker Drive Encryption**.
   3. Find the drive that is encrypted and click **Turn off BitLocker**.
   4. A confirmation window will pop up; click **Turn off BitLocker** again to start the decryption process.
   5. The decryption process might take some time depending on the drive size. You can still use the computer during this time, but performance might be affected.

### 2. **Turn off BitLocker via Settings**
   1. Press `Win + I` to open **Settings**.
   2. Go to **Privacy & security** → **Device encryption** (if you see this option; it's for devices that support encryption).
   3. If **Device encryption** is turned on, click the toggle to turn it off.
   4. You may need to confirm and enter your BitLocker password or recovery key.

### 3. **Turn off BitLocker via Command Prompt**
   1. Press `Win + S`, type **cmd**, right-click **Command Prompt**, and select **Run as administrator**.
   2. In the Command Prompt window, type the following command and press Enter:
      ```
      manage-bde -off C:
      ```
      (Replace `C:` with the drive letter of the encrypted drive if it's different.)
   3. The decryption process will begin, and you can monitor the progress in the Command Prompt window by typing:
      ```
      manage-bde -status
      ```

### 4. **Turn off BitLocker via PowerShell**
   1. Press `Win + S`, type **PowerShell**, right-click it, and choose **Run as administrator**.
   2. To turn off BitLocker, enter the following command:
      ```powershell
      Disable-BitLocker -MountPoint "C:"
      ```
      (Again, replace `C:` with the correct drive letter if necessary.)
   3. This will start the decryption process.

Once decryption is complete, BitLocker will be removed from the drive. Keep in mind that removing BitLocker will make the data on your drive no longer encrypted, which reduces its security.
