# VCA Canada Cellphone Meraki MDM Setup

## Preamble

This guide is written as a reference for Imagine Wireless (Rogers) when enrolling new mobile devices into the VCA Canada MDM.

## New iOS Device Enrollment (via Apple Business Manager)

Enroll new iPhones using the Apple Business Manager, once added via that platform complete the following within the Meraki MDM:

1. Locate the new device in the Meraki MDM (under the "VCA MDM" network) using its serial number
2. Add the "Cellphone-Canada" tag
3. Rename the device in the MDM to match the following naming convention: VCACMobile - {SERIAL NUMBER}
   1. Ex. VCACMobile - SN0987654321

## New Android Device Enrollment (via Android Enterprise)

Enroll new iPhones using the Android Enterprise platform, once added via that platform complete the following within the Meraki MDM:

1. Locate the new device in the Meraki MDM (under the "VCA MDM" network) using its serial number
2. Add the "Cellphone-Canada" tag
3. Rename the device in the MDM to match the following naming convention: VCACMobile - {SERIAL NUMBER}
   1. Ex. VCACMobile - SN0987654321
