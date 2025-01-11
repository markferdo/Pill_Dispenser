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
The calibration process starts when the opto-fork is triggered. Following the trigger, the motor will run 2 full cycles to get the average steps per revolution. Once the system has the average steps, it can dispense pills. We have three main functions for this purpose: motor running, calibration, and run function. These three functions are responsible for energizing the motor, calibrating it, and then dispensing the pills. 
