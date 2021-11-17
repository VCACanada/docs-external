# VCA Canada Enable PXE for ThinStation on HP T530

## Objective

These instructions will show you how to disable SATA booting and enable PXE booting.

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
* Choose File -> Save Changes and Exit (say yes you're sure when prompte*

## Notes

### T540 note

We have not tested these steps against a T540, but we expect them to work the same on the newer models.
