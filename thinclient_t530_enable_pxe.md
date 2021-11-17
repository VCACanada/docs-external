# VCA Canada Enable PXE for ThinStation on HP T530

## Objective

These instructions will show you how to disable SATA booting and enable PXE booting.

1) Reboot thin client, and keep pressing F10 until you end up in the HP Setup Utility
2) Choose Security -> Device Security
   1) Set "SATA0" to "Device hidden" with the arrow keys
   2) Press F10 to save
3) Choose Security -> Secure Boot Configuration
   1) Press F10 to continue
   2) Set "Legacy Support" to "Enable"
   3) Set "Secure Boot" to "Disable"
   4) Press F10 to save
4) Choose Storage -> Boot Order
   1) Use arrow keys to select "Network Controller" under the "Legacy Boot Sources" header.
   2) Press enter to 'drag', then use the arrow keys to move it to the top of the "Legacy Boot Sources" list, then press enter to 'drop'
   3) Press F10 to save
5) Choose File -> Save Changes and Exit (say yes you're sure when prompted)

## Notes

### T540 note

We have not tested these steps against a T540, but we expect them to work the same on the newer models.
