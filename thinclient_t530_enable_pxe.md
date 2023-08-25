# VCA Canada Enable PXE for ThinStation on HP T530

## Objective

These instructions will show you how to disable SATA booting and enable PXE booting. 

## Print off Thin Client label

Before you PXE enable the thin client, you need to print off the label for the thin client. We use 2" by 4" labels. You can use [this link](https://thinstation-inventory.vcacanada.com/) to access the label generator.

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
