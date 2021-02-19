# SLICE-DHV-Firmware-Upgrade
Repository for the latest released firmware for the SLICE DHV

## Requires 
  Vescent SLICE_Firmware_Upgrade_Utility available at:
  
  https://github.com/Vescent/FFC_Firmware_Upgrade_Utility
## Instructions
 
  Left click on SLICE_Firmware_Update_Instructions.docx and then click 'Download' to download the instructions for use.

  Left click on the upgrade package (SC-x-xx-HV-x-xx.zip) and then click 'Download' to download the firmware package to your hard drive.
  
  The three files in the .zip file need to be placed in the folder described in the instructions. DO NOT RENAME THEM!
## Configuration S1.79_HV1.18
 1. Adds:
    Ability to identify R04 or R03 ICE2-HVA board and enable switching output mode on R04 equipped units.
    Includes GUI access to switching via a dropdown menu and Serial API commands
    OPMODE [channel] [mode] 0 selects Current Limited, 1 selects Full Bandwidth
    OPMODE? [channel] Queries output mode
    OPMDAVL? returns 0 for R03 hardware, 1 for R04 hardware
 2. Adds:
    A startup function that tests saved user limits settings against defined in code macros. This function tests limits saved in the EEPROM against 
    hard coded defined limits in the firmware. 
    If a saved value exceeds one of these limits, it coerces the value to the limit.
    Affected values are:
    Voltage Limit
    dcBiasVoltage_setpoint (must not exceed Voltage Limit)
    Minimum Sweep Rate
    Maximum Sweep Rate
3.  Revise RESET API Command to trigger a soft reset of the processor to allow entering the bootloader without the need for a power cycle. 
    Products to date have cycled power to the ICE2 board in order to enter the bootloader code for debugging. 
    This only works on SLICE models which have a single board since the power to all ICE2 boards is controlled through a common trace.
    Being able to selectively reboot ICE2 boards is necessary to do in field USB firmware upgrades on multiple ICE2 board configurations.
4.  Fixes:
    PySerial library 3.x versions no longer require a Python library modification to work with SLICE devices.
5.  Fixes:
    Blue Button Press is no longer required for initiating USB firmware upgrades for software versions going forward. 
    (blue button is still required to upgrade to S1.79_HV1.18 from S1.75_HV1.15)
6.  Adds:
    The ability to accept any of the following API serial command terminators.
    \r, \n, \r\n, or \n\r
7.  Adds the SCPI ***RST**  command to allow the device to be restarted from a serial API command.
8.  Fixes:
    Erratic results in rotary edit window when a rotary knob is spun at faster than 60 RPM.

## Configuration S1.75_HV1.15
    Original Production Release


       
