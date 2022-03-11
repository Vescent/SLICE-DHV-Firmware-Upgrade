# SLICE-DHV-Firmware-Upgrade
Repository for the latest released firmware for the SLICE DHV

## Requires 
  Vescent SLICE_Firmware_Upgrade_Utility available at:
  
  https://github.com/Vescent/SLICE-FFC_Firmware_Upgrade_Utility
## Instructions
 
  Left click on SLICE_Firmware_Update_Instructions.pdf and then click 'Download' to download the instructions for use.

  The V1.23 firmware upgrader automatically retrieves the upgrade files from this repository. However, if your system does not allow this,  
  You may need to perform the following steps:  
  
       Left click on the upgrade package (SC-x-xx-HV-x-xx.zip) and then click 'Download' to download the firmware package to your  
       hard drive.
  
       The 2 files in the .zip file need to be placed in the folder described in the instructions. DO NOT RENAME THEM!  
	   
## Configuration S1.95_HV.24 
###(NOTE: This Upgrade Will Be Recognized As A Different COM Port Number After The Upgrade)
 1.	Adds:
	 Non-volatile memory storage of the modulation mode during SLICE-DHV power off state.
 2. Fixes:
	 Modulation voltage bleed through when selected as a front panel input after a SLICE-DHV power cycle
 3.	Fixes:
	 Voltage output of greater than 100mV when channels were disabled.
 4.	Fixes:
	 Duplicate "Settings are Locked" message screens requiring two button presses to release them.
 5.	Fixes:
	 Modal window inversion that could place a pop up selection menu on top of the “Settings are Locked” 
	 message screen which required extra steps to dismiss both windows.
 6.	Fixes:
	 Touching and sliding your finger off of an external I/O selection button on the I/O screen would cause 
	 the current entry to disappear.
 7. Fixes:
	 Lock/Unlock icon would sometimes disappear from view during manipulation of the locked/ unlocked state.
 8.	Fixes:
	 Possibility of a GUI lockup requiring a power cycle if a side bar button was pressed while adjusting 
	 Volume or Display Back-light values with a rotary knob.
 9.	Revises:
	 I2C architecture to eliminate random communication errors between the System Controller and ICE2 board.
10. Adds:
	 SLICE-DHV and the unit’s serial number are now included in the USB descriptor data.
11.	Adds:
	 Serial number is now displayed on general settings screen.
12.	Fixes:
	 Front Panel B input selection now shows the correct Ch 2 designation when chosen.
13.	Fixes:
	 Output trigger selection now immediately clears the non-selected channel (if previously selected) 
	 when a channel is selected.
14. Fixes:
	 Cross talk within the System Controller firmware that resulted in attempts to use some SLICE-QTC I2C 
	 commands to talk with the ICE2-HV board. (would result in a GUI lockup)
	 
## Configuration S1.86_HV.21
 1. Fixes:  
     Bug where it was possible to set invalid values in the "Range [V]" field via keypad entry.  
     The values are now properly clamped to the acceptable range before they are allowed to be applied. 
 2. Fixes:  
     Bug wherein rotary knob adjustment of Voltage Setpoint could cause a fatal lockup.   
 3. Fixes:  
     Bug wherein rotary knob adjustment during TUNE mode could cause the SLICE-DHV to lockup (non-fatally).  
 4. Fixes:  
     Bug involving redundant warning dialogs.  A check function has been added to the code so that if a dialog  
     box is already being displayed, a new one will not be spawned.  
 5. Fixes:  
     Prevents a possible rare lockup associated with TUNE mode, Settings Lock, and the General Settings menu.  
 
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


       
