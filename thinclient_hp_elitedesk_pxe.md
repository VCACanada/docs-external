# VCA Canada Enable PXE for ThinStation on HP Elite Mini 66 G9

## Objective

These instructions will show you how to disable M.2 booting and enable PXE booting. 

## Print off Thin Client label

Before you PXE enable the thin client, you need to print off the label for the thin client. We use 2" by 4" labels. You can use [this link](https://thinstation-inventory.vcacanada.com/) to access the label generator.

## PXE enable Thin Client

After 15-20 seconds the Smartsheet is saved, our DHCP server is automatically updated, so we're ready to PXE enable the thin client. After this is complete, it should load up ThinStation, our Linux OS.

* Reboot thin client, and keep pressing F10 until you end up in the HP Setup Utility
* Choose Advanced -> System Options
  * Set "M.2 SSD 1" and M.2 SSD 2" to unchecked
  * Press F10 to save
* Choose Security -> Secure Boot Configuration
  * Press F10 to continue
  * Set "Secure Boot" to unchecked
  * Press F10 to save
* Choose Advanced -> Boot Options
  * Ensure that the network controller is the only option in the boot order; move it to the top of the list if it is not already
  * Press F10 to save
* Choose File -> Save Changes and Exit (say yes you're sure when prompted)