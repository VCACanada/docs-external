# VCA Canada Enable PXE for ThinStation on HP T530

## Objective

These instructions will show you how to disable SATA booting and enable PXE booting. 

## Add Mac Address to Smartsheet

Before you PXE enable the thin client, you will need to add the Mac address to our Smartsheet. **Please ensure you put in the mac address with uppercase letters.** You can do this by [filling out the form](https://app.smartsheet.com/b/form/8d0cb66b6c024986930edec268d4420d) or by [accessing the smartsheet directly](https://app.smartsheet.com/sheets/4FGfG9QcC9m8gx8w2FvFV5653jPWqjh2WRXxP6w1?view=grid). You need to fill in the Mac, Stage, Hostname, and Model. The stage is almost always `prod` and the model will either be `T530` or `T540`. The hostname must match the sticker on the Thin Client.

## PXE enable Thin Client

After 15-20 seconds the Smartsheet is saved, our DHCP server is automatically updated, so we're ready to PXE enable the thin client. After this is complete, it should load up ThinStation, our Linux OS.

* Reboot thin client, and keep pressing F10 until you end up in the HP Setup Utility
* Choose Security -> Device Security
  * Set "SATA0" to "Device hidden" with the arrow keys
  * Press F10 to save
* Choose Security -> Secure Boot Configuration
  * Press F10 to continue
  * Set "Legacy Support" to "Enable"
  * Set "Secure Boot" to "Disable"
  * Press F10 to save
* Choose Storage -> Boot Order
  * Use arrow keys to select "Network Controller" under the "Legacy Boot Sources" header.
  * Press enter to 'drag', then use the arrow keys to move it to the top of the "Legacy Boot Sources" list, then press enter to 'drop'
  * Press F10 to save
* Choose File -> Save Changes and Exit (say yes you're sure when prompted)

## Notes

### T540 note

For T540's, we support using UEFI, so you do NOT need to enable legacy support, but secure boot does need to be disabled. The boot order also needs to favor UEFI over legacy options. 
