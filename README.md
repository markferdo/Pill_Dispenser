# Pill_Dispenser
### Automated system that calibrates and dispenses pills in certain intervals
## 💻 Technologies and Tools Used:
💠Opto fork sensor (Configured as an input with pull-up resistor)
###
💠Piezo sensor (Configured as an input with pull-up resistor)
### 
💠Stepper motor
### 
💠EEPROM
### 
💠I2C protocol
### 
💠LED
### 
💠Buttons
## 💡 Key Features of the Device:
###  
💠 The device remembers its state even if the power goes off.
### 
💠 After powering back on, it continues from where it stopped. 
### 
💠 If power is lost during dispensing, it recalibrates automatically without dispensing the pills. 
## How the device works: 
### 💠 Calibration process
The calibration process starts when the opto-fork is triggered. Following the trigger, the motor will run 2 full cycles to get the average steps per revolution. Once the system has the average steps, it can dispense pills. The system has three main functions for this purpose: motor running, calibration, and run function. These three functions are responsible for energizing the motor, calibrating it, and then dispensing the pills.
### 💠 State management
In this system, it saves the state each time it changes. To write and read it uses EEPROM and i2c protocols. In the main program, switch cases are used to decide which state to perform based on the EEPROM values.
####
The device mainly has two EEPROM functions: writing and reading. During the process, the system tracks three main states: calibration state, dispense state, and compartment number. 
###
This state tracking helps to detect that the calibration is completed (ready to dispense pills), dispense completed, and the current compartment. These states are useful for running the motor properly even if there is a power failure during the dispensing and switch-off scenario.
### 💠 Dispensing logic 
If the average steps are available, the device is ready to dispense pills. It waits for the button press to start the process. When dispensing, it moves one compartment at a time, and there is a 30-second time duration between two dispenses.
###
Piezo sensor helps to detect whether the pill is dispensed or not. Piezo sensor is initialized as an interrupt and once it is triggered it will update the compartment number and move on to the next compartment. This process continues until all the pills are dispensed. If there are no pills to detect during the dispensing, then the system waits a minimum time to catch the event, if there are no pills detected during the waiting, the system detects this as ‘no pill dispensed’. It updates the situation and moves on to the next. Likewise, the dispensing process continues for a full cycle (7-compartment run) even 
if there are no pills. 
